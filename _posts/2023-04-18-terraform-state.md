---
title: Terraform state 관리
author: icyou
date: 2023-04-17 00:00:00 +0900
categories: [Cloud, Terraform]
tags: [Terraform]
pin: true
math: true
---

## Terraform state 관리
terraform.tfstate와 실제 cloud infra 사이의 sync가 맞지 않을 경우,
terraform import 또는 terraform state rm을 통해 cloud의 자원을 terraform.tfstate에 저장하거나 cloud에는 이미 삭제된 자원을 tfstate에서도 삭제시켜줄 수 있습니다.


<br/><br/><br/><br/>
참고 
- [https://developer.hashicorp.com/terraform/cli/commands/state/rm](https://developer.hashicorp.com/terraform/cli/commands/state/rm)