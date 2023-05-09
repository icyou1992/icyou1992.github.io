---
title: Fibonacci Number
author: icyou
date: 2023-05-09 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Fibonacci Number
n번째 Fibonacci 수를 구하는 문제입니다.

```
class Solution:
    def fib(self, n: int) -> int:
        return n if n < 2 else self.fib(n - 1) + self.fib(n - 2)
```
재귀로 간단하게 풀 수 있지만, 성능은 좋지 않습니다.

```
class Solution:
    def fib(self, n: int) -> int:
        arr = [0, 1]
        for i in range(2, 31):
            arr.append(arr[i-1] + arr[i-2])
        return arr[n]
```
이전 함수의 결괏값을 저장하고 다음에 같은 함수 연산이 나올 경우, 저장한 값을 활용하는 memoization으로 반복되는 연산을 줄일 수 있습니다. 

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/fibonacci-number/submissions/947012896/](https://leetcode.com/problems/fibonacci-number/submissions/947012896/)