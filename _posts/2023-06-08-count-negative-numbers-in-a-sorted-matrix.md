---
title: Count Negative Numbers in a Sorted Matrix
author: icyou
date: 2023-06-08 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Count Negative Numbers in a Sorted Matrix
이중 for문에서 음수의 개수를 구하는 문제입니다.  

```
class Solution:
    def countNegatives(self, grid: List[List[int]]) -> int:
        return len([ y for x in grid for y in x if y < 0 ])
```
음수들을 배열에 저장하기 때문에 성능은 안 좋지만 보기 좋게 한 줄로 풀어봤습니다.  
이중 for문을 한 줄로 표현하는 방법을 쉽게 기억하기 위해서는 처음 y 뒤를 끊고 두 번째 for 앞을 끊어서 생각하면, grid에서 x를 뽑아내고 x에서 y를 뽑아낸다고 생각할 수 있습니다.  


<br/><br/><br/><br/>
참고  
- [https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/submissions/966602526/](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/submissions/966602526/)