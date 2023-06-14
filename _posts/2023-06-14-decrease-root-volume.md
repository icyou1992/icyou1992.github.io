---
title: Root Volume의 크기를 줄이는 방법
author: icyou
date: 2023-06-07 00:00:00 +0900
categories: [Cloud, AWS]
tags: [AWS, Root, OS]
pin: true
math: true
---

### Root Volume의 크기를 줄이는 방법
Root Volume은 일반적인 방법으로 크기를 줄일 수 없습니다.  
AWS EBS volume은 생성된 상태에서 크기를 늘릴 수만 있고 줄일 수는 없습니다. 마찬가지로 snapshot으로 root volume을 backup하고 복구하는 경우에도 기존 volume의 크기보다 크거나 같은 volume으로만 복구가 가능합니다.  
root volume의 크기를 줄이기 위해서는 다음과 같은 방법을 사용해야 합니다.

1. ebs volume을 알맞은 크기로 줄여서 생성
2. 새로운 volume을 instance에 붙여 기동시킨 후 rsync를 통해 / 경로를 backup
3. grub2-install 을 활용하여 boot loader install
4. root volume ebs를 떼고 새로운 생성한 volume을 /dev/xvda 경로로 attach

큰 흐름으로 나누었을 때 이렇게 나눌 수 있으며, 각 과정 중에 세부 작업 등은 생략했습니다.  

- 이 방식은 amazon linux 외의 다른 os에서는 제대로 작동하지 않는 경우도 있었습니다.


<br/><br/><br/><br/>
참고  
- [https://fitdevops.in/how-to-reduce-aws-ebs-root-volume-size/](https://fitdevops.in/how-to-reduce-aws-ebs-root-volume-size/)