---
title: Number Complement
author: icyou
date: 2023-04-26 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Number Complement
주어진 수, num의 이진수 표현에서 0을 모두 1로 바꾸고 1을 모두 0으로 바꾼 수를 구하는 문제입니다.

```
class Solution:
    def findComplement(self, num: int) -> int:
        n = ""
        for s in bin(num)[2:]:
            n += str(1 - int(s))
        return int(n, 2)
```
num의 이진수 표현에서 '0b' 부분을 제외하고 문자를 차례로 순회하며, 1에서 해당 문자를 빼면 1은 0을 0은 1을 얻을 수 있습니다. 후에 이를 모두 합쳐서 int로 변환하여 반환합니다.

```
class Solution:
    def findComplement(self, num: int) -> int:
        n = 1
        while n < num:
            n *= 2
        return n - 1 if n == num else n - 1 - num
```
num 바로 위의 2의 거듭제곱 수를 구한 후, num과 거듭제곱 수가 일치하면 num - 1을 반환하고 아닐 경우 거듭제곱 수에서 num + 1을 뺀 값을 반환하면 답을 구할 수 있습니다.



<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/number-complement/submissions/940529869/](https://leetcode.com/problems/number-complement/submissions/940529869/)
- [https://leetcode.com/problems/number-complement/submissions/940546767/](https://leetcode.com/problems/number-complement/submissions/940546767/)