---
title: Summary Ranges
author: icyou
date: 2023-03-28 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Summary Ranges
주어진 nums 배열을 

```
class Solution:
    def summaryRanges(self, nums: List[int]) -> List[str]:
        arr = []
        if not nums: 
            return arr
        s = str(nums[0])
        for i in range(len(nums) - 1):
            if nums[i] + 1 != nums[i + 1]:
                if s == str(nums[i]):
                    arr.append(s)
                    s = str(nums[i + 1])
                else:    
                    arr.append(s + "->" + str(nums[i]))
                    s = str(nums[i + 1])
        return arr + [s] if s == str(nums[-1]) else arr + [s + "->" + str(nums[-1])]
```
이전에 풀었던 문제의 반대 유형입니다.  
이전 풀이와 비슷하게 풀었습니다.



<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/summary-ranges/submissions/923609525/](https://leetcode.com/problems/summary-ranges/submissions/923609525/)