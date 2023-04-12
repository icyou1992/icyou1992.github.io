---
title: Intersection of Two Arrays
author: icyou
date: 2023-04-10 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Intersection of Two Arrays
nums1, nums2 배열이 주어졌을 때, 두 배열의 교집합을 구하는 문제입니다.

```
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        return list(set(nums1).intersection(set(nums2)))
```
set 자료형으로 간단히 해결할 수 있습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/intersection-of-two-arrays/submissions/931240395/](https://leetcode.com/problems/intersection-of-two-arrays/submissions/931240395/)