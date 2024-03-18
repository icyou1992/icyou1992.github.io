---
title: Blocking/Non-Blocking, Synchronous/Asynchronous
author: icyou
date: 2024-03-18 00:00:00 +0900
categories: [Computer Science, Overview]
tags: [blocking, non-blocking, synchronous, asynchronous]
pin: true
math: true
---

### Blocking vs Non-Blocking
호출된 thread가 다른 thread들의 작업을 막느냐(block), 막지 않느냐(non-block).  
'제어권의 여부'라는 표현은 의미가 중의적일 수 있어서 다른 thread들의 작업을 막느냐 막지 않느냐가 좀 더 명료한 표현으로 보입니다.

<br/><br/>

### Synchronous vs Asynchronous
호출된 thread의 결과값을, 호출한 thread가 물어보면(synchronous), 호출된 thread가 가져다주면(asynchronous).  
결과값을 어떤 thread가 신경쓰는지.  
호출하는 thread가 결과값을 물어보게 되면, 여러 thread를 호출할 때 차례로 호출하므로 결과값도 순서가 정해집니다. 


<br/><br/>

Blocking 방식은 서비스 성능이 느려지는 원인이 될 수 있고, Non-Blocking, Async 방식은 버그의 원인이 될 수 있을 것 같습니다. 



<br/><br/><br/><br/>
참고 
- [https://jh-7.tistory.com/25](https://jh-7.tistory.com/25)
- [https://studyandwrite.tistory.com/486](https://studyandwrite.tistory.com/486)
- [https://velog.io/@sdb016/Blocking-Non-Blocking-SyncAsync](https://velog.io/@sdb016/Blocking-Non-Blocking-SyncAsync)