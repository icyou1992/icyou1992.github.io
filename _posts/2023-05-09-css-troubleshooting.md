---
title: CSS Trouble shooting
author: icyou
date: 2023-05-04 00:00:00 +0900
categories: [Frontend, CSS]
tags: [CSS]
pin: true
math: true
---

### CSS Trouble shooting
side project를 진행하면서 마주한 문제들을 어떻게 해결했는지 정리합니다.
  
- page가 overflowY: 'auto'를 했음에도 scroll이 활성화되지 않는 이유는 height를 설정하지 않았기 때문입니다.

- div의 가로, 세로 비율은 width와 padding-top 속성을 이용해서 비율을 지정해줄 수 있습니다. 이 경우 div 안의 내용물의 위 또는 아래로 밀릴 수 있는데, 이는 position: 'absolute', top: '0%' 설정으로 원래대로 배치시킬 수 있습니다.

<br/><br/><br/><br/>
참고 
- [https://codingbroker.tistory.com/128](https://codingbroker.tistory.com/128)
- [http://lv100.moirun.com/2016/01/div.html](http://lv100.moirun.com/2016/01/div.html)