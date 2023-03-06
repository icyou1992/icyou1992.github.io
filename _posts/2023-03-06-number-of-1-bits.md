---
title: Number of 1 Bits
author: icyou
date: 2023-03-05 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Number of 1 Bits
32bit의 양수형 정수가 주어졌을 때, 1의 개수를 구하는 문제입니다.

```
class Solution:
    def hammingWeight(self, n: int) -> int:
        return bin(n).count('1')
```
내부함수를 이용하여 간단하게 구해줬습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/number-of-1-bits/submissions/910087792/](https://leetcode.com/problems/number-of-1-bits/submissions/910087792/)