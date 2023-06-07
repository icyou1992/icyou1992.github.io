---
title: Can Make Arithmetic Progression From Sequence
author: icyou
date: 2023-06-06 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Can Make Arithmetic Progression From Sequence
주어진 배열을 정렬했을 때 등차수열인지 판별하는 문제입니다.

```
class Solution:
    def canMakeArithmeticProgression(self, arr: List[int]) -> bool:
        arr = sorted(arr)
        return len(set([arr[i + 1] - arr[i] for i in range(len(arr) - 1)])) == 1
```
정렬 후, 각 수열의 등차를 배열로 저장한 후 set로 변환했을 때 길이가 1이라면 등차수열이므로 True를 반환합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/can-make-arithmetic-progression-from-sequence/submissions/965135503/](https://leetcode.com/problems/can-make-arithmetic-progression-from-sequence/submissions/965135503/)