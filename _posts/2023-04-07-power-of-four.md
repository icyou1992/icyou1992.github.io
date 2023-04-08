---
title: Power of Four
author: icyou
date: 2023-04-07 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Power of Four
주어진 수 n이 4의 거듭제곱인지를 판별하는 문제입니다.

```
class Solution:
    def isPowerOfFour(self, n: int) -> bool:
        low, high = 0, 15
        while low <= high:
            mid = (low + high) // 2
            if 4 ** mid == n: return True
            elif 4 ** mid < n: low = mid + 1
            else: high = mid - 1
        return False
```
power of three 문제와 마찬가지 유형이라 4 ** 15 인 수에서 n을 나눠 나머지가 0인지를 판별하면 되는 줄 알았으나, 4는 소수가 아니기 때문에 적용할 수 없었습니다. 예를 들어 8일 경우, 4의 거듭제곱이 아니지만 4 ** 15를 8로 나눈 나머지는 0입니다.  

```
class Solution:
    def isPowerOfFour(self, n: int) -> bool:
        return n > 0 and not(n & (n - 1)) and n & 1431655765 == n
```
solution의 풀이입니다.  
n & (n - 1)이 0인지를 검증하면서 먼저 2의 거듭제곱인지를 판별한 후에, 4의 거듭제곱을 전부 더한 수인 1431655765에 n을 AND 연산함으로써 4의 거듭제곱인지를 판별합니다.  
n & (n - 1)을 먼저 검증하는 이유는 2의 거듭제곱 수가 아닐 경우 1431655765에 n을 AND 연산한다해도 4의 거듭제곱임을 보장할 수 없기 때문입니다.  



<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/range-sum-query-immutable/submissions/928276245/](https://leetcode.com/problems/range-sum-query-immutable/submissions/928276245/)
- [https://leetcode.com/problems/power-of-four/solutions/2461223/python-99-no-more-loop-or-recursion-one-liner-with-detailed-explanation-and-different-approach/](https://leetcode.com/problems/power-of-four/solutions/2461223/python-99-no-more-loop-or-recursion-one-liner-with-detailed-explanation-and-different-approach/)