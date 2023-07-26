---
title: Terraform에서 EBS encrypt
author: icyou
date: 2023-07-26 00:00:00 +0900
categories: [Cloud, Terraform]
tags: [Terraform, AWS]
pin: true
math: true
---

### Terraform에서 EBS encrypt
- terraform으로 aws infra code 작성 시, ebs volume을 encrypt할 때 aws managed key를 사용하고 싶을 경우, 아래와 같이 활용할 수 있습니다.

```
data "aws_ebs_default_kms_key" "current" {}

resource "aws_ebs_volume" "example" {
  availability_zone = "us-west-2a"

  encrypted  = true
  kms_key_id = data.aws_ebs_default_kms_key.current.key_arn
}
```

* 이렇게 활용할 때, syntax error가 발생하는 경우가 있습니다. key_arn 반환값이 실제로 id로 반환하여 발생하는 에러입니다. 이 경우에는 아래와 같이 data.aws_kms_key.current를 활용합니다.

```
data "aws_ebs_default_kms_key" "current" {}

data "aws_kms_key" "current" {
  key_id = data.aws_ebs_default_kms_key.current.key_arn
}

resource "aws_ebs_volume" "example" {
  availability_zone = "us-west-2a"

  encrypted  = true
  kms_key_id = data.aws_kms_key.current.arn
}
```


<br/><br/><br/><br/>
참고  
- [https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/ebs_default_kms_key](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/ebs_default_kms_key)
- [https://github.com/hashicorp/terraform-provider-aws/issues/15137](https://github.com/hashicorp/terraform-provider-aws/issues/15137)