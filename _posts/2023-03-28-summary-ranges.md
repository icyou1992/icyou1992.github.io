---
title: Summary Ranges
author: icyou
date: 2023-03-28 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Summary Ranges
주어진 nums 배열을 다 포함하는 범위를 나타내는 새로운 배열을 만드는 문제입니다.

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
문자열이 끊어지는 경우는 nums\[i\]와 nums\[i + 1\]의 관계가 연속적이지 않을 때뿐이므로, 연속적이지 않을 경우 nums\[i\]까지를 범위로 나타내고 배열에 넣은 다음 nums\[i + 1\]을 새로운 범위의 시작점으로 설정합니다.  
for문을 돌고 남은 마지막 문자열에 대한 처리는 return 에서 해줍니다.



<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/summary-ranges/submissions/923609525/](https://leetcode.com/problems/summary-ranges/submissions/923609525/)