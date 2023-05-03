---
title: Preact Trouble shooting
author: icyou
date: 2023-05-04 00:00:00 +0900
categories: [Frontend, Preact]
tags: [Preact]
pin: true
math: true
---

### Preact Trouble shooting
Preact로 side project를 진행하면서 마주한 문제들을 어떻게 해결했는지 정리합니다.
  
- 특정 Page가 rendering 되지 않는다면, css에 문제가 있을 수 있습니다. css 파일을 따로 두지 않고, page 안에 styles 변수를 통해 css를 설정할 경우 css 에러를 알 수 없으므로 styles 변수 부분을 주석처리해보면서 debug해야 합니다.


<br/><br/><br/><br/>
참고 
- [https://preactjs.com/guide/v10/getting-started](https://preactjs.com/guide/v10/getting-started)