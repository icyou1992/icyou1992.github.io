---
title: Ransom Note
author: icyou
date: 2023-02-05 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm]
pin: true
math: true
---

## Leetcode Problem

### Ransom Note
magazine 문자열 내에 ransomNote 문자들이 각각 들어있는지 판별하는 문제

```
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        dic = {}
        for x in magazine:
            if x in dic.keys():
                dic[x] += 1
            else:
                dic[x] = 1
        for x in ransomNote:
            if x in dic.keys() and dic[x] > 0:
                dic[x] -= 1
            else:
                return False
        return True
```
내 풀이는 dictionary 자료 구조를 이용해서 각 문자열을 dictionary의 key로 넣고 문자가 겹치는 경우를 고려하여 value는 각 문자의 개수로 한다.
다른 풀이는 python의 counter 함수를 활용하였는데, 내 풀이와 발상은 같다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/ransom-note/submissions/891953842/](https://leetcode.com/problems/ransom-note/submissions/891953842/)