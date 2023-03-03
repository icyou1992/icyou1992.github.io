---
title: Routing 정리
author: icyou
date: 2023-02-07 00:00:00 +0900
categories: [Computer Science, Network]
tags: [Network]
pin: true
math: true
---

## Routing 정리

### routing
- routing table을 통해 packet을 목적지로 전달하기 위한 경로를 선택하는 과정입니다.

### routing protocol
- routing table을 만들기 위한 규약입니다.
- AS의 외부, 내부를 기준으로 EGP와 IGP로 나뉩니다.
    + EGP(Exterior Gateway Protocol): AS 간의 연결 규약
    + IGP(Interior Gateway Protocol): AS 내부의 연결 규약
    * AS(Anonymous System)는 간단하게 사내망, 내부망, LAN(Local Area Network)이라고 생각하면 될 것 같습니다.

### IGP(Interior Gateway Protocol)
- Distance Vector, Link State를 사용합니다.
    - Distance Vector: Bellman-Ford Algorithm을 사용합니다.
        + 이웃한 router와만 `주기적으로` 연결 정보를 공유하며 자신의 routing table을 계속 갱신합니다.
        + ex) RIP(Routing Information Protocol), IGRP, etc...  

    - Link State: Dijkstra Algorithm을 사용합니다.
        + 각 router마다 이웃 router들의 연결 정보를 전체 router와 공유하여 전체 구성도를 그린다. `변화가 발생할 때마다` 다시 정보를 공유합니다.
        + ex) OSPF(Open Shortest Path First)

### EGP(Exterior Gateway Protocol)
- router들 간의 통신이 되어야 하므로, Path Vector로 통일되어 있습니다.
    - Path Vector: Distance Vector와 같이 Bellman-Ford Algorithm을 사용합니다.
        + Distance Vector와 달리 목적지의 `경로`까지 명시합니다.
        + 명시된 경로를 바탕으로 유효성을 검사할 수 있습니다.
        + ex) BGP4(Border Gateway Protocol)

### BGP 
- BGP는 TCP로 만들어진 규약으로 4 layer에 해당됩니다.
- BGP routing을 생성하기 위해 ASN(AS Number)을 Internet Registry에서 할당 받습니다. 이 번호는 고유합니다.
    + Internet Registry: 인터넷 자원을 관리하는 단체
- ASN을 기반으로 두 router는 BGP session을 통해 정보를 교환하여 서로를 연결합니다. 이를 BGP Peering이라 합니다.  



<br/><br/><br/><br/>
참고 
- [https://www.youtube.com/watch?v=eBiPBsHkIUo](https://www.youtube.com/watch?v=eBiPBsHkIUo)
- [https://blog.cdemi.io/beginners-guide-to-understanding-bgp/](https://blog.cdemi.io/beginners-guide-to-understanding-bgp/)
- [https://networkengineering.stackexchange.com/questions/5595/what-is-the-difference-between-distance-vector-protocol-and-path-vector-protocol](https://networkengineering.stackexchange.com/questions/5595/what-is-the-difference-between-distance-vector-protocol-and-path-vector-protocol)