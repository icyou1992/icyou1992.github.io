---
title: Number of Steps to Reduce a Number to Zero
author: icyou
date: 2023-02-07 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm]
pin: true
math: true
---

## Leetcode Problem

### Number of Steps to Reduce a Number to Zero
주어진 수를 0으로 만드는 과정의 횟수를 구하는 문제입니다.

```
class Solution:
    def numberOfSteps(self, num: int) -> int:
        step = 0
        while num > 0:
            step += 1
            if num % 2 == 0:
                num /= 2
            else:
                num -= 1
        return step
```
평범하게 푼 풀이입니다.

```
class Solution:
    def numberOfSteps(self, num: int) -> int:
        if num == 0:
            return 0
        return 1 + self.numberOfSteps(num - 1 if num & 1 else num >> 1)
```
solution에서 본 풀이인데, 정말 멋있는 풀이 같습니다. 컴퓨터를 잘 이해한 사람이 작성한 풀이 같습니다. 가독성 면에서는 떨어질 수 있긴 하지만, bit 연산을 활용하고 재귀를 활용하기 때문에 memory, 성능 면에서 좋을 것 같습니다.   
2로 나누거나 곱할 수 있는 경우는 bit 연산이 가능하다는 것을 기억해야겠습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/submissions/893285760/](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/submissions/893285760/)