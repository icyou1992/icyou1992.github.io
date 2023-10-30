---
title:  Terraform import 시 유의할 점
author: icyou
date: 2023-10-31 00:00:00 +0900
categories: [Cloud]
tags: [Terraform]
pin: true
math: true
---

### Terraform import 사용 시 유의할 점
- cloud console 상의 직접 만들어진 resource들을 terraform code로 가져오고 싶을 때, terraform import \[terraform resource 선언 위치\] \[resource 주소\]로 resource를 가져오는데, 같은 유형의 resource를 일괄적으로 가져오고 싶은 경우, 당신의 terraform code는 for_each를 통해 object 또는 array로 선언되어 있을 것입니다. 선언된 resource를 각각 import 할 때, \[\\"key 값\\"\]으로 각각 선언된 resource에 접근하여 import 할 수 있습니다.  

```
ex)
terraform import aws_instance.instance[\"a_instance"\] i-1234567
```