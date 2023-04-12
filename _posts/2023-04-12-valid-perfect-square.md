---
title: Valid Perfect Square
author: icyou
date: 2023-04-12 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Valid Perfect Square
주어진 수 num이 제곱수인지를 판별하는 문제입니다.

```
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        low, high = 0, num // 2 if num > 1 else 1
        while low <= high:
            mid = (low + high) // 2
            if mid ** 2 < num:
                low = mid + 1
            elif mid ** 2 > num:
                high = mid - 1
            else:
                return True
        return False
```
sqrt 함수를 사용할 수 없기 때문에, 이진 탐색 기법을 활용했습니다.  
`**0.5`를 활용하는 것도 sqrt를 사용하는 것이라고 생각하여 사용하지 않았습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/valid-perfect-square/submissions/932373226/](https://leetcode.com/problems/valid-perfect-square/submissions/932373226/)