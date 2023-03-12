---
title: Valid Phone Numbers
author: icyou
date: 2023-03-12 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Valid Phone Numbers
bash shell로 file.txt을 받아서 문제의 조건에 맞는 전화번호를 찾는 문제입니다.  

```
while read line; do
  if [[ $line =~ (^\([0-9]{3}\)[ ]{1}[0-9]{3}-[0-9]{4}$) || $line =~ (^[0-9]{3}-[0-9]{3}-[0-9]{4}$) ]]; then
    echo $line
  fi
done < file.txt
```
solution의 풀이입니다.  
regex 문법을 사용하여 문제를 풀려고는 했지만, bash shell 문법이 워낙 까다로웠습니다.  
bash 문제를 여러개 풀어봐야할 것 같습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/valid-phone-numbers/solutions/2953181/just-bash-regex/](https://leetcode.com/problems/valid-phone-numbers/solutions/2953181/just-bash-regex/)