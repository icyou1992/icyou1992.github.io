---
title: Tenth Line
author: icyou
date: 2023-03-13 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Tenth Line
bash shell로 file.txt을 받아서 열번째 줄을 출력하는 문제입니다.

```
x=1
while read line; do
  if [[ $x -eq 10 ]]; then
    echo $line
  fi
  x=$x+1
done < file.txt

```
이전 문제 풀이를 참고했습니다.  
if 사용 시의 문법, $를 활용한 변수 선언과 사용에 대해 복습했습니다.  

<br/><br/><br/><br/>
참고 
-[https://leetcode.com/problems/valid-phone-numbers/submissions/913481816/](https://leetcode.com/problems/valid-phone-numbers/submissions/913481816/)