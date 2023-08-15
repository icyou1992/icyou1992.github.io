---
title:  Parameter Store VS Secret Manager
author: icyou
date: 2023-08-15 00:00:00 +0900
categories: [Cloud]
tags: [AWS]
pin: true
math: true
---

###  Parameter Store VS Secret Manager
- AWS 서비스인 Secret Manager와 Parameter Store는 Key-Value 정보를 저장한다는 측면에서 비슷한 서비스지만, 쓰임새 또는 사용 목적이 다릅니다.

### Parameter Store
- 간단한 환경변수를 AWS에 저장하여 그것의 사용을 편리하게 하는 것에 목적이 있습니다. 따라서, infra를 구성하거나 application을 배포하는 것을 편리하게 합니다.
- 간단한 정보를 저장하는 것이므로 하나의 key-value 쌍에 많은 정보를 담을 수 있는 공간이 지원되지 않습니다.
- Secret Manager 서비스보다 보안에 취약합니다.
- 기본 서비스는 비용이 부과되지 않습니다.  

### Secret Manager
- 중요한 정보를 암호화하여 저장하는 것에 그 목적이 있습니다.
- 다른 AWS 계정에서 정보에 접근할 수 있는 기능을 지원합니다. 즉 parameter store보다 범용적인 사용을 지원합니다.
- 비용이 부과됩니다.  
- Kubernetes에서 Secret의 보안을 강화하기 위해, AWS Secret Manager를 사용하기도 합니다.

![Desktop View](/assets/img/posts/20230815/AWS-Secrets-Manager-vs-Systems-Parameter-Store.jpg){: .w-70 .normal}


* 결론적으로는 특별히 보안에 신경써야 할 정보가 아니거나, 다른 AWS 계정에서 접근해야하는 정보가 아니라면 parameter store 서비스를 이용하는 것이 비용 효율적이라고 생각합니다.


<br/><br/><br/><br/>
참고  
- [https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/integration-ps-secretsmanager.html](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/integration-ps-secretsmanager.html)
- [https://tutorialsdojo.com/aws-secrets-manager-vs-systems-manager-parameter-store/](https://tutorialsdojo.com/aws-secrets-manager-vs-systems-manager-parameter-store/)