---
title: Minimum Flips to Make a OR b Equal to c
author: icyou
date: 2023-06-07 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Minimum Flips to Make a OR b Equal to c
a | b 연산을 하여 c가 나오게 하기 위해 a와 b의 bit를 몇 개 뒤집어야 하는지 구하는 문제입니다.  

```
class Solution:
    def minFlips(self, a: int, b: int, c: int) -> int:
        a, b, c = bin(a)[2:], bin(b)[2:], bin(c)[2:]
        m = max(len(a), len(b), len(c))
        a, b, c = a.zfill(m), b.zfill(m), c.zfill(m)
        cnt = 0
        for i in range(m):
            if c[i] == '0':
                cnt += (int(a[i]) + int(b[i]))
            else: 
                cnt += max(1 - (int(a[i]) + int(b[i])), 0)
        return cnt
```
먼저, a, b, c를 비교하기 위해 binary로 바꾸고 비교할 때 index error가 나지 않기 위해 문자열로 바꾼 a, b, c의 최대 길이만큼 0을 채워줍니다.
이후 for 문을 돌면서 c에서 0이 나오는 경우는 a와 b bit를 모두 0으로 바꿔야하므로 개수만큼, 1이 나오는 경우는 a와 b bit가 모두 0일 경우, 하나만 바꾸고 1 이상일 경우, 바꾸지 않아야 하므로 max(1 - (int(a\[i\]) + int(b\[i\])), 0) 식을 사용합니다.  

<br/><br/><br/><br/>
참고  
- [https://leetcode.com/problems/minimum-flips-to-make-a-or-b-equal-to-c/submissions/965779303/](https://leetcode.com/problems/minimum-flips-to-make-a-or-b-equal-to-c/submissions/965779303/)