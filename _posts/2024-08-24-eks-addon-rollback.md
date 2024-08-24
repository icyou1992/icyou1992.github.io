---
title: EKS vpc-cni rollback 작업
author: icyou
date: 2024-08-24 00:00:00 +0900
categories: [Cloud, AWS]
tags: [AWS, VPC, addon, "add-on"]
pin: true
math: true
---

### EKS vpc-cni rollback 작업
EKS에 vpc-cni addon이 설치되어 있지 않아서, vpc-cni addon을 설치했는데, vpc-cni가 직접 설치되어 있어서 기존에 있던 addon이 덮어씌워지는 사고가 발생했습니다. rollback하려 했으나 직접 설치된 vpc-cni가 덮어씌워졌기 때문에 rollback할 수 없는 상태가 되었습니다.  

해결방법은 addon으로 설치된 vpc-cni를 지우고 다시 직접 설치하는 것입니다. vpc-cni를 직접 설치하지 않아서 설치 방법을 몰랐지만 다행히도 stg, prd 환경의 eks 구성이 남아있었기 때문에, 이 구성을 보고 빠진 resource를 넣는 방식으로 해결할 수 있었습니다.  

1. 
```
kubectl get po -n kube-system
``` 
명령어로 vpc-cni addon을 지우고 생긴 비정상적인 pod를 파악합니다.
2. 
```
k describe ds aws-node -n kube-system
``` 
명령어로 해당 daemonset에서 무슨 문제가 발생했는지를 파악합니다.
3. 이를 토대로 stg, prd 환경의 eks 구성과 비교하여 어떤 resource가 빠졌는지 확인합니다.
4. daemonset, serviceaccount, secret, clusterrole, clusterrolebinding, customresourcedefinitions, eniconfig 등등이 있었습니다.
5. 
```
k get daemonset aws-node -n kube-system -o yaml > ds-aws-node.yaml
k get sa aws-node -n kube-system -o yaml > sa-aws-node.yaml 
```
명령어 등으로 stg, prd에 있는 자원들을 가져와서 apply를 통해 자원을 설치합니다.