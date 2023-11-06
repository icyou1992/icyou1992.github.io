---
title:  Terraform 코드 구조에 대한 고찰
author: icyou
date: 2023-08-18 00:00:00 +0900
categories: [Cloud]
tags: [Terraform, hcl]
pin: true
math: true
---

### Terraform 코드 구조에 대한 고찰
- Devops Enginner로 일하면서 어떻게 하면 terraform code를 효율적으로 구조화할 수 있을지 고민했습니다. 고민한 결과, 제가 생각하는 이상적인 terraform 코드 구조는 다음과 같습니다.

#### 1. terraform 코드에서 module 부분은 다른 repo를 구성하여 따로 넣고 여러 인프라를 구성할 때마다 module repo를 참조하도록 합니다.  
Enterprise 환경에서는 여러 계정에서 동일한 인프라 구성이 필요할 수도 있고, 동일한 서비스를 용도에 따라 여러 개로 배포하는 경우가 있습니다. 여러 서비스에서 module을 사용하게 하려면 해당 module은 유연성이 높아야 합니다. 유연성을 극대화하기 위해서는 terraform code를 거의 그대로 가져와야 환경에 따라 유연하게 서비스 코드를 유연하게 작성할 수 있습니다.  
이렇게 module을 구성하면, 굳이 module을 써야하는지에 대한 의문이 생깁니다. terraform을 거의 그대로 module로 가져오는 경우에 대해서도 다음과 같은 장점이 있습니다.
  1. 서비스 내의 resource들의 연결 관계를 미리 세팅해둘 수 있습니다. 예를 들어, subnet과 route table의 mapping, lambda와 sqs의 연결 등등 자원 간의 연결이 필수적인 것들이 있습니다.  
  2. variables.tf에 default 값을 설정하거나, validation을 통해 알맞은 값들만 가져올 수 있습니다.  

#### 2. terraform 코드에서 실제 인프라 구성 부분은 변경성이 거의 없는 network와 내부 자원들, resources 등으로 나누어 구성합니다.
network 부분은 구성이 바뀔 경우 서비스에 심각한 영향을 끼치고 거의 구성이 바뀌지 않으므로 resources와 분리하고 따로 apply하여 안정성을 더합니다. 단, security group, waf 등 변경성이 많을 수 있는 network 자원은 resources에 두는 것이 편해보입니다. 즉 변경이 자주 있는지, 서비스에 critical한 지로 중요도를 나누어 terraform apply를 따로 할 수 있게 합니다.  

#### 3. .tfvars의 사용을 최대한 지양합니다.
.tfvars 내부에서는 변수를 사용할 수 없습니다. 따라서 .tfvars 보다는 .tf를 사용하고 안에서 locals를 활용하는 것이 좋습니다. 예를 들어, 자원의 이름을 설정할 때 공통적으로 들어가는 부분, 서비스 이름, 용도 또는 업무 용어들은 locals에 변수로 선언하고 이 조합을 활용하여 자원 이름을 지을 때 해당 변수를 활용합니다.  
 
#### 4. 인프라 구성 부분은 main.tf 하나보다는 서비스.tf로 module 마다 파일을 따로 둡니다.
가독성이 좋아집니다.

#### 5. terraform-aws-module 사용은 최대한 지양합니다.
terraform-aws-module은 유연성이 제한됩니다. 뿐만 아니라 output이 정해져 있어서 원하는 resource arn이 output에 없을 경우, data로 해당 resource를 가져와야 하는데, 이도 해당 resource의 정보를 알고 있어야 해서 실용성이 떨어집니다.

#### 6. module의 입력값을 활용하기 위해 flatten을 활용합니다.
aws architecture 상에서 resource 간의 종속성에 따라 variables 입력값을 2중 object 또는 3중 object 형식으로 구성해야할 수 있습니다. 이 때 terraform flatten 함수를 활용합니다.  
example)
```
lambdas_s3_mapping = flatten([
  for kl, vl in lookup(vl, "triggers", []) : [
    for ks, vs in lookup(sv, "s3", []) : {
      key = "${kl}-${ks}"
      lambda = kl
      arn = ~
      sqs = ks
    }
  ]
])

lambdas = {
  lambda_name = {
    triggers = {
      s3 = {
        ~
      }
    }
  }
}
```


