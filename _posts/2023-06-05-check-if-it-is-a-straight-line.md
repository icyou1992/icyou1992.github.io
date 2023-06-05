---
title: Check If It Is a Straight Line
author: icyou
date: 2023-06-04 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Check If It Is a Straight Line
주어진 점들이 일직선을 이루는 지 판별하는 문제입니다.

```
class Solution:
    def checkStraightLine(self, coordinates: List[List[int]]) -> bool:
        x, y = coordinates[1][0] - coordinates[0][0], coordinates[1][1] - coordinates[0][1]
        for i in range(2, len(coordinates)):
            if x * (coordinates[i][1] - coordinates[0][1]) != y * (coordinates[i][0] - coordinates[0][0]):
                return False
        return True
```
첫번째 점과 두번째 점으로 기울기를 구한 다음, 첫번째 점과 세번째 점부터의 기울기가 일치하는 지를 비교합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/check-if-it-is-a-straight-line/submissions/964145428/](https://leetcode.com/problems/check-if-it-is-a-straight-line/submissions/964145428/)