---
title: Tomcat Trouble Shooting 1
author: icyou
date: 2023-07-29 00:00:00 +0900
categories: [Middleware, Tomcat]
tags: [Tomcat]
pin: true
math: true
---

### Tomcat Trouble Shooting 1
- 이번에 처음 tomcat을 사용해보면서, spring boot backend를 외장 tomcat으로 기동시킬 때 발생한 문제와 원인 및 그 해결책을 정리합니다.

- 문제
내장 tomcat으로 app 기동 시 실행이 잘 되었으나, 외장 tomcat으로 app을 실행할 경우, tomcat만 기동되고 app이 올라오지 않는 문제가 발생했습니다.  

- 원인
tomcat version과 jdk version이 호환되지 않아 app이 기동되지 않았습니다. 내장 tomcat version은 jdk version과 호환되는 version인 반면, 외장 tomcat은 그보다 낮은 version이어서 app 자체가 기동되지 못했습니다.

- 실마리
내장 tomcat으로 app을 기동했을 때, 잘 올라가는데 외장 tomcat으로는 잘 기동되지 않았습니다. (log에 Spring 화면이 나타나지 않았습니다.)

- 헤맸던 원인
1. tomcat 및 spring boot를 아예 처음 써보는 상황이었습니다.
2. 문제의 원인이 외장 tomcat이 소스 경로를 제대로 인식하지 못해서 app을 올리지 못하는 거라고 판단하여 그 방향을 기준으로 문제의 범위를 넓혀갔습니다. 
3. version 문제일 수 있다는 것을 염두하였으나, google 검색 시 호환성에는 문제가 없는 것으로 나와 test까지는 하지 않았습니다.

- 해결
1. 외장 tomcat의 version을 jdk version에 맞춰 올려줍니다.
2. jdk version을 외장 tomcat version에 맞춰 내립니다. 단, 이 경우에 내려진 version에 맞게 dependency를 수정해야 합니다.


<br/><br/><br/><br/>
참고  
- [https://hye0-log.tistory.com/29](https://hye0-log.tistory.com/29)