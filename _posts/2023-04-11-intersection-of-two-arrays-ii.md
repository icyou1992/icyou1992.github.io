---
title: Intersection of Two Arrays II
author: icyou
date: 2023-04-11 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Intersection of Two Arrays II
nums1, nums2 배열이 주어졌을 때, 두 배열의 교집합을 중복을 허용하여 구하는 문제입니다.

```
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
        arr, n1, n2 = [], sorted(nums1), sorted(nums2)
        i, j = 0, 0
        while i < len(n1) and j < len(n2):
            if n1[i] == n2[j]:
                arr.append(n1[i])
                i += 1
                j += 1
            elif n1[i] < n2[j]:
                i += 1
            else:
                j += 1
        return arr
```
set 자료형은 중복이 제거되므로 사용할 수 없습니다.  
nums1, nums2 배열을 정렬하고 각 두 index의 앞에서부터 차례대로 비교해가며 일치하는 원소들을 새로 배열로 만들어 반환합니다.  




<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/intersection-of-two-arrays-ii/submissions/931873020/](https://leetcode.com/problems/intersection-of-two-arrays-ii/submissions/931873020/)