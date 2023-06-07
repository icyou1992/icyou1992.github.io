---
title: Route Table Propagation이란
author: icyou
date: 2023-06-07 00:00:00 +0900
categories: [Cloud, AWS]
tags: [AWS, Propagation]
pin: true
math: true
---

### Route Table Propagation이란
traffic의 이동 경로를 route table로 설정할 때 propagation이 aws 공식 문서를 봐도 잘 와닿지 않아 간략하게 정리합니다.  
  
virtual gateway나 transit gateway가 vpc에 붙고 direct connect가 연결되는 경우, route table 경로를 propagation으로 설정할 수 있는데, 이 때 direct connect에 반대편 gateway에 연결된 경로들을 가져와서 자동으로 route table에 등록해줍니다.  

network layer의 gateway는 router로서 다른 router로 향하는 경로들을 저장하고 있기 때문에 반대편 router가 저장한 경로를 가져와 route table에 저장시켜주는 것이 propagation으로 이해했습니다.

<br/><br/><br/><br/>
참고  
- [https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/WorkWithRouteTables.html#EnableDisableRouteProp](https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/WorkWithRouteTables.html#EnableDisableRouteProp)