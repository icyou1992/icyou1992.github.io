---
title: Isomorphic Strings
author: icyou
date: 2023-03-26 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Isomorphic Strings
s, t 두 문자열이 주어졌을 때, s 문자열의 문자들과 t 문자열의 문자들이 서로 일대일 대응인지를 구하는 문제입니다.

```
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        d = {}
        for i in range(len(s)):
            if s[i] in d.keys() and d[s[i]] != t[i]:
                return False
            else:
                d[s[i]] = t[i]
        return len(d) == len(set(t))
```
s의 각 문자들을 t의 문자들과 대응시키기 위해 dictionary 자료구조를 활용했습니다. d를 통해 s 문자열과 t 문자열을 대응시키는 과정에서 하나의 s 문자에 두 개 이상의 t 문자가 들어가서 중복되는 경우 false를 반환합니다.  
이 과정을 거치면 s -> t 관계에 대해서 1:1이 되지만, t -> s 관계에 대해서는 1:1일 경우를 보장하지 못합니다.  
이를 해결하기 위해 d의 길이와 t의 문자열에서 중복을 제거한 원소의 길이가 일치하는지 검사해서 t -> s 관계에서도 1:1인지를 검사합니다.  


```
class Solution(object):
    def isIsomorphic(self, s, t):
        return len(set(s)) == len(set(zip(s, t))) == len(set(t))
```
solutions의 풀이입니다.  
python 내장함수인 zip을 활용하면 두 문자열을 순서대로 대응시켜줄 수 있게 됩니다. 이를 set로 중복을 제거하고 s와 t의 set와 비교하면 1:1 대응인지를 판별할 수 있습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/isomorphic-strings/submissions/922141624/](https://leetcode.com/problems/isomorphic-strings/submissions/922141624/)
- [https://leetcode.com/problems/isomorphic-strings/solutions/3196792/beats-99-8-solution-easy-one-string-using-zip/?page=2](https://leetcode.com/problems/isomorphic-strings/solutions/3196792/beats-99-8-solution-easy-one-string-using-zip/?page=2)