---
title: Tomcat Trouble Shooting 2
author: icyou
date: 2023-08-04 00:00:00 +0900
categories: [Middleware, Tomcat]
tags: [Tomcat]
pin: true
math: true
---

### Tomcat Trouble Shooting 2
- 문제
tomcat은 잘 기동했으나 api를 test했을 때 404 에러가 발생합니다.

- 원인
server.xml에서 path 설정이 제대로 되지 않았습니다.

- 헤맸던 원인
1. tomcat은 잘 기동되었기 때문에, tomcat의 문제가 아닌 줄 알았습니다.

- 해결
1. server.xml -> context의 path를 api에 맞게 설정해줍니다.


<br/><br/><br/><br/>
