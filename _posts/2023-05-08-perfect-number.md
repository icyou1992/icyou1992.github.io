---
title: Perfect Number
author: icyou
date: 2023-05-07 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Perfect Number
자기 자신을 제외한 모든 약수의 합이 자신과 같아지는 Perfect Number인지를 판별하는 문제입니다.  

```
class Solution:
    def checkPerfectNumber(self, num: int) -> bool:
        n = 1
        for i in range(2, int(num ** (1/2) + 1)):
            if num % i == 0:
                n += i + num//i
        return n == num if num > 1 else False
```
약수는, 하나의 약수와 원래 수에서 그 약수를 나눈 수와 쌍을 이룹니다. $$ \sqrt{num} $$와 쌍을 이루는 약수는 $$ \sqrt{num} $$ 그 자신이므로 $$ \sqrt{num} $$까지 순회를 하면서 약수를 찾으면 모든 약수를 구할 수 있습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/perfect-number/submissions/946382291/](https://leetcode.com/problems/perfect-number/submissions/946382291/)