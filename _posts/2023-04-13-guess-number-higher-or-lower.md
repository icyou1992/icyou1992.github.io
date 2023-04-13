---
title: Guess Number Higher or Lower
author: icyou
date: 2023-04-12 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Guess Number Higher or Lower
예측한 수와 정답이 맞는지를 비교해주는 guess 함수를 통해 정답을 구하는 문제입니다.

```
class Solution:
    def guessNumber(self, n: int) -> int:
        low, high = 0, n
        while low <= high:
            mid = (low + high) // 2
            if guess(mid) > 0:
                low = mid + 1
            elif guess(mid) < 0:
                high = mid - 1
            else:
                return mid
```
이진 탐색을 활용했습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/guess-number-higher-or-lower/submissions/933026324/](https://leetcode.com/problems/guess-number-higher-or-lower/submissions/933026324/)