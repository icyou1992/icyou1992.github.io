---
title: Next Greater Element I
author: icyou
date: 2023-05-03 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Next Greater Element I
nums2 배열과 nums2 배열의 부분집합인 nums1이 주어졌을 때, nums1을 순회하면서 nums1 원소를 nums2에서 봤을 때, 다음으로 큰 수를 찾는 문제입니다. 만약 다음으로 큰 수가 없을 경우 그 자리에 -1을 넣습니다.

```
class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        arr = []
        for n in nums1:
            l = nums2.index(n)
            m = max(nums2[l:])
            for i in range(l, len(nums2)):
                if n < nums2[i]:
                    arr.append(nums2[i])
                    break
            else:
                arr.append(-1)
        return arr
```
문제 이해도 쉽지 않았습니다. 여러 번 틀려가며 문제를 이해할 수 있었네요. 
nums1을 순회하면서 nums1 원소에 해당하는 값을 nums2.index로 위치를 찾습니다. 이후 그 위치부터 nums2를 순회하면서 해당 값보다 큰 값이 나오는 경우 그 값을 배열에 넣고 없을 경우 -1을 넣습니다.  

```
class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        next_greater = {}
        stack = []
        
        for num in nums2:
            while stack and num > stack[-1]:
                next_greater[stack.pop()] = num
            stack.append(num)
        
        result = []
        for num in nums1:
            if num in next_greater:
                result.append(next_greater[num])
            else:
                result.append(-1)
        
        return result
```
solution의 풀이입니다.  
stack과 dictionary 자료형을 활용하여 index로 여러번 순회하는 낭비를 덜 수 있습니다.






<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/next-greater-element-i/submissions/943802315/](https://leetcode.com/problems/next-greater-element-i/submissions/943802315/)
- [https://leetcode.com/problems/next-greater-element-i/solutions/3285190/496-space-92-75-solution-with-step-by-step-explanation/?languageTags=python3](https://leetcode.com/problems/next-greater-element-i/solutions/3285190/496-space-92-75-solution-with-step-by-step-explanation/?languageTags=python3)