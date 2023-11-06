---
title:  Terraform flatten
author: icyou
date: 2023-11-07 00:00:00 +0900
categories: [Cloud]
tags: [Terraform, hcl, flatten]
pin: true
math: true
---

### Terraform flatten
1. Terraform HCL은 resource block에서 이중 for문을 지원하지 않습니다. 제 추측으로는 hcl은 resource를 선언 시, 내부적으로 각 CSP의 자원 생성 cli를 활용하는 것 같습니다.
2. 하지만 cloud의 자원들은 서로 연결되어 있습니다. 예를 들면, AWS에서 cloudwatch log가 lambda를 trigger하거나 lambda가 sns를 trigger 하는 식입니다.   
3. 이 연결관계에 따라 code를 구성할 때 이중 for문이 필요해질 수 있습니다. 예를 들면, 여러 개의 sqs queue가 하나의 lambda를 trigger 한다고 했을 때, 이를 연결시켜주는 aws_lambda_event_source_mapping resource를 hcl로 선언 시에 function_name을 여러 번 입력해야만 하게 되고, 이 때 이중 for문이 필요해질 수 있습니다. 
4. 이런 경우에 hcl은 flatten 함수를 제공합니다. 위의 예시를 아래처럼 flatten을 통해 자원을 선언할 수 있습니다.
```
ex)
locals {
  lambda_sqs_mapping = flatten([
    for k, v in var.lambda : [
      for sk, sv in var.lambda[lk].sqs : [
        key = "${lk}${sk}"
        lambda = k
        sqs = sk
      ] 
    ]
  ])
}

resource "aws_lambda_event_source_mapping" "sqs_trigger" {
  for_each = { for v in local.lambda_sqs_mapping : v.key => v }

  funtion_name = aws_lambda_function.lambda[each.value.lambda].arn
  ~
}
```
5. 여러 개의 sqs가 각각의 lambda를 trigger하는 중에, trigger하는 sqs가 없는 lambda도 있는 경우는 lookup 함수를 활용합니다.
```
ex)
locals {
  lambda_sqs_mapping = flatten([
    for k, v in var.lambda : [
      for sk, sv in lookup(var.lambda[lk], "sqs", []) : [
        key = "${lk}${sk}"
        lambda = k
        sqs = sk
      ] 
    ]
  ])
}
```

위와 같은 방식으로 다중 for문을 flatten하게 1차원 배열로 만들어 자원을 생성할 수 있습니다.

<br/><br/><br/><br/>
참고  
- [https://developer.hashicorp.com/terraform/language/functions/flatten](https://developer.hashicorp.com/terraform/language/functions/flatten)
