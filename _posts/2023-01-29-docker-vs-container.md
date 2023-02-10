---
title: docker -> containerd
author: icyou
date: 2023-01-29 00:00:00 +0900
categories: [Infra, OS]
tags: [OS, docker]
pin: true
math: true
---

### 기존 Docker의 문제점
docker는 monolithic system으로, image build, 관리, 공유 실행 등 너무 많은 기능이 탑재되어 있어, 무거울 뿐만 아니라 장애 발생 시, 모든 기능에 장애가 생기는 single point of failure가 될 위험이 있다.

## CRI(Container Runtime Interface)
- kubernetes의 등장으로 인해 기존 monolithic 방식의 docker는 container 실행 기능뿐만 아니라, kubernetes kubelet에는 필요없는 기능들도 포함되어 있어, 이를 분리하고 container runtime을 표준화할 필요성이 대두되었다. 이 표준을 정립하기 위해 AWS, Google, MS, IBM등의 주요 회사가 OCI(Open Container Initiative)를 구성하여 표준을 구성했고, 이후 kubernetes의 container runtime으로 CRI가 등장하였다. 그래서 container runtime이 CRI에 맞춰 구현되면, kubelet을 고치지 않고 plugin으로 추가하는 방식으로 해결할 수 있게 되었다.
- container의 실행 단계는 `1. image download 2. bundle로 이미지 압축 해제 3. bundle로 container 실행`으로 나뉘어 있고, 3번째 단계인 container 실행 부분만 표준화하는 경우 Low Level Container Runtime과 1, 2번째 단계 등까지 표준화된 High Level Container Runtime으로 나뉜다.

## Containerd
- docker에서 OCI 표준을 준수하여 만든 container runtime
- 현재는 docker engine도 containerd에 plugin을 추가한 방식으로 구성됨

<br/><br/><br/><br/>
참고 
- [https://s-core.co.kr/insight/view](https://s-core.co.kr/insight/view/oci%EC%99%80-cri-%EC%A4%91%EC%8B%AC%EC%9C%BC%EB%A1%9C-%EC%9E%AC%ED%8E%B8%EB%90%98%EB%8A%94-%EC%BB%A8%ED%85%8C%EC%9D%B4%EB%84%88-%EC%83%9D%ED%83%9C%EA%B3%84-%ED%9D%94%EB%93%A4%EB%A6%AC%EB%8A%94/)
- [https://cwal.tistory.com/31](https://cwal.tistory.com/31)