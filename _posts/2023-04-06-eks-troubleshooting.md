---
title: terraform으로 EKS 생성 시 Trouble shooting
author: icyou
date: 2023-04-06 00:00:00 +0900
categories: [Cloud, AWS]
tags: [AWS, EKS]
pin: true
math: true
---

### terraform으로 EKS 생성 시 Trouble shooting
terraform aws module을 사용한다면, 비교적 편리하게 eks를 생성할 수 있지만, 직접 terraform language로 eks resource들을 일일이 생성하려고 시도한다면, 수많은 에러를 마주할 수 있습니다.
  
- `NodeCreationFailure: instances failed to join the kubernetes cluster'` 에러 문구를 마주한다면, 확인해야 할 사항은 다음과 같습니다.  
1. node와 security group에 알맞은 tag가 붙어있는지 확인합니다.
2. node에 붙은 security group이 cluster의 접근을 방해하고 있는지 확인합니다. cluster의 접근을 위해 내부 vpc에 대해 53, 443, 10250 port를 열어놓아야 합니다.
3. private subnet 환경에 eks를 생성하는 경우, nat gateway가 public subnet에 할당되어 cluster와 통신이 가능한지 확인합니다. 즉, 외부와 통신 가능한 환경이 구성되어 있는지 확인합니다.

위의 사항들을 꼼꼼히 확인하는 것은 쉽지 않습니다. AWS에서는 이를 위해서 
`AWSSupport-TroubleshootEKSWorkerNode`라는 runbook을 지원하고 있습니다.
위 runbook을 통해 손쉽게 eks 에러를 잡아낼 수 있습니다.

- `decoding stdout: no kind "ExecCredential" is registered for version "client.authentication.k8s.io/v1beta1" in scheme "pkg/runtime/scheme.go:100"` 에러가 발생한다면, aws cli version을 2 이상의 최신으로 update하면 해결될 수 있습니다.

- kubernetes resource를 생성할 때, `Unauthorized` 에러를 마주한다면, provider 문제일 가능성이 높습니다. 제 경우에는 token이 만료되는 것을 막기 위해 exec plugin을 통해 `eks get-token` 명령어로 token을 받는 provider를 설정하였는데, `Unauthorized` 에러가 발생하였습니다. aws_eks_cluster_auth를 통해 token을 받는 방식으로 바꿨더니 해결되는 것으로 보아 일종의 bug인 것 같습니다.

- `Unable to connect to the server: dial tcp i/o time out` 에러가 발생하는 경우 cluster에 문제가 없다면 security group 문제일 가능성이 있습니다. cluster의 control plane이 kubectl 서버와 통신하기 위해서는 443 port를 열어줘야 합니다.

<br/><br/><br/><br/>
참고 
- [https://docs.aws.amazon.com/eks/latest/userguide/troubleshooting.html](https://docs.aws.amazon.com/eks/latest/userguide/troubleshooting.html)
- [https://docs.aws.amazon.com/eks/latest/userguide/sec-group-reqs.html](https://docs.aws.amazon.com/eks/latest/userguide/sec-group-reqs.html)