---
title: Climbing Stairs
author: icyou
date: 2023-02-14 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Climbing Stairs
계단을 올라가는 방법은 1 계단을 오르거나 2 계단을 오르거나 입니다. n번째 계단까지 오르는 가짓수를 구하는 문제입니다.  

```
class Solution:
    def climbStairs(self, n: int) -> int:
        stairs = [1, 1] + [0] * (n - 1)
        for i in range(2, n + 1):
            stairs[i] = stairs[i - 1] + stairs[i - 2]
        return stairs[-1]
```
전형적인 dp 문제입니다.  
n번째 계단까지 오르는 방법은 n - 1번째 계단까지 오르는 방법에서 1 계단을 오르는 방법과 n - 2번째 계단까지 오르는 방법에서 2계단을 오르는 방법 외에는 존재하지 않습니다.  
1번째 계단부터 n번째 계단까지 차례대로 배열에 저장한 값을 활용하면서 경우의 수를 구합니다.  

```
class Solution:
    def climbStairs(self, n: int) -> int:
        def climb(i: int) -> int:
            if i == 1:
                return 1
            elif i == 2:
                return 2
            else:
                return climb(i - 2) + climb(i - 1)
        return climb(n)
```
위와 같이 재귀를 이용하여 문제를 풀면 아래와 같이 동일한 함수의 값을 중복해서 구하게 됩니다.  

![Desktop View](/assets/img/posts/20230214/dp.png){: .w-70 .normal}  

이 불필요한 중복 계산을 피하기 위해 배열에 함숫값을 저장하는 memoization을 사용합니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/climbing-stairs/submissions/897760402/](https://leetcode.com/problems/climbing-stairs/submissions/897760402/)
- [https://hongjw1938.tistory.com/47](https://hongjw1938.tistory.com/47)