---
title:  EKS Batch 504 Error Trouble Shooting
author: icyou
date: 2024-08-13 00:00:00 +0900
categories: [Cloud, AWS]
tags: [AWS, EKS, "504"]
pin: true
math: true
---

### EKS Batch 504 Error Trouble Shooting
project에서 batch 작업이 필요하여 어떻게 batch 작업에 대한 architecture를 구현할 지 고민하다, AWS Batch를 쓰면   
1. 기존 EKS cluster를 활용할 수 있어 추가 인프라가 필요없다는 점.  
2. 필요 시에만 노드를 기동시키고 job을 돌린 후에 삭제되기 때문에 비용 효율적이라는 점.  
위의 두 가지 이점을 취할 수 있지만, EKS cluster endpoint access를 public으로 열어야 한다는 문제점이 있었습니다. 하지만 비용 효율적인 측면 때문에 AWS Batch 서비스를 사용하기로 결정했습니다.    

AWS Batch와 AWS Load Balancer Controller 환경에서 간헐적으로 504 에러가 발생하는 것을 확인했습니다.
개인적으로 간헐적인 에러 발생이 정말 해결하기 어려운 유형이라고 생각합니다.    

AWS Batch를 통한 노드 생성 시에, 기존 EKS cluster를 활용하여 노드가 생성되는데, 해당 batch 작업이 끝나고 노드가 삭제될 때, 또 다른 batch api가 호출되는 것이 원인이었습니다.    

-> target group 설정 및 target group에 대한 alb controller annotation을 추가적으로 설정하여 문제를 해결했습니다.

