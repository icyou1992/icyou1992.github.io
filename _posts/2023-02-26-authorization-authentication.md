---
title: Authentication vs Authorization
author: icyou
date: 2023-02-26 00:00:00 +0900
categories: [Frontend]
tags: [Frontend, Auth]
pin: true
math: true
---

## Authentication vs Authorization
- Authentication(인증): Login
- Authorization(인가): Authority(권한)

![Desktop View](/assets/img/posts/20230226/auth.jpg){: .w-70 .normal}

| Authentication | Authorization |
|:-|-:|
| 사용자가 요청자인지 확인 | 사용자의 접근 가능 여부 확인 |
| 사용자가 자격 증명을 확인하도록 요청 | 정책 및 규칙을 통해 접근 가능 여부 확인 |
| authorization 전에 완료 | authentication 이후 허용 | 
| ID token을 통해 정보 전송 | Access token을 통해 정보 전송 | 
| oidc protocol | OAuth 2.0 framework |


<br/><br/><br/><br/>
참고 
- [https://gruuuuu.github.io/security/ssofriends/](https://gruuuuu.github.io/security/ssofriends/)
- [https://baek.dev/post/24/](https://baek.dev/post/24/)
- [https://dev.to/caffiendkitten/authentication-vs-authorization-25lc](https://dev.to/caffiendkitten/authentication-vs-authorization-25lc)
- [https://auth0.com/docs/get-started/identity-fundamentals/authentication-and-authorization](https://auth0.com/docs/get-started/identity-fundamentals/authentication-and-authorization)