---
title: Sort Colors
author: icyou
date: 2023-03-20 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Sort Colors
nums 배열을 in-place 정렬을 하는 문제입니다.

```
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        tmp = 0
        for i in range(len(nums) - 1):
            for j in range(len(nums) - 1):
                if nums[j] > nums[j + 1]:
                    tmp = nums[j]
                    nums[j] = nums[j + 1]
                    nums[j + 1] = tmp

```
bubble sort를 사용하여 문제를 해결했습니다.

```
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        nums.sort()
```
이렇게도 해결되는 걸로 봐서 python의 sort 함수는 in-place 조건을 만족하는 듯합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/sort-colors/submissions/919409953/](https://leetcode.com/problems/sort-colors/submissions/919409953/)
- [https://leetcode.com/problems/sort-colors/submissions/919411213/](https://leetcode.com/problems/sort-colors/submissions/919411213/)