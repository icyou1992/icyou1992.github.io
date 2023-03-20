---
title: Ugly Number
author: icyou
date: 2023-03-20 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Ugly Number
주어진 수가, 2 또는 3 또는 5 이외를 인수로 가지지 않는 Ugly Number인지를 판별하는 문제입니다. 

```
class Solution:
    def isUgly(self, n: int) -> bool:
        if n == 1:
            return True
        elif n == 0:
            return False
        elif n % 2 == 0:
            return self.isUgly(n//2)
        elif n % 3 == 0:
            return self.isUgly(n//3)
        elif n % 5 == 0:
            return self.isUgly(n//5)
        else:
            return False
```
n이 0인 경우와 1인 경우는 따로 처리하고 2, 3, 5로 나뉠 경우, 재귀를 사용하여 같은 수로 계속 나눠줍니다.

```
class Solution:
    def isUgly(self, n: int) -> bool:
        if n == 0:
            return False
        while n % 2 == 0:
            n //= 2
        while n % 3 == 0:
            n //= 3
        while n % 5 == 0:
            n //= 5
        return True if n == 1 else False
```
논리는 같고 재귀를 반복으로 바꿨습니다. 

```
class Solution:
    def isUgly(self, n: int) -> bool:
        prime_factors = [2, 3, 5]
        if n <= 0:
            return False       
        for pf in prime_factors:
            while n % pf == 0:
                n = n // pf
        return n == 1
```
solution의 풀이입니다.  
논리는 이전 풀이와 같지만 훨씬 더 가독성이 좋고 세련됐습니다.  
에라토스테네스의 체를 사용하는 방식으로도 풀어보려고 했지만, 메모리가 초과됩니다.  


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/ugly-number/submissions/918803416/](https://leetcode.com/problems/ugly-number/submissions/918803416/)
- [https://leetcode.com/problems/ugly-number/submissions/918803184/](https://leetcode.com/problems/ugly-number/submissions/918803184/)
- [https://leetcode.com/problems/ugly-number/solutions/2825974/python-detailed-explanation-fastest-99-faster/](https://leetcode.com/problems/ugly-number/solutions/2825974/python-detailed-explanation-fastest-99-faster/)