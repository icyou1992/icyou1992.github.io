---
title: terraform으로 eks 작성 시 주의사항
author: icyou
date: 2023-03-05 00:00:00 +0900
categories: [Cloud, AWS]
tags: [Kubernetes, eks]
pin: true
math: true
---

## terraform으로 eks 작성 시 주의사항
- terraform으로 eks를 작성하는데, `getting credentials ~` 혹은 `no kind "ExecCredential" is registered ~`라는 에러가 발생한다면 사용환경의 aws cli version이 낮아서 생기는 문제일 가능성이 있습니다.  
aws cli의 version이 낮고, 따라서 provider의 version이 낮아 kubernetes에서 token을 가져오지 못해서 생기는 문제일 수 있습니다.



<br/><br/><br/><br/>
