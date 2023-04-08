---
title: Majority Element
author: icyou
date: 2023-03-03 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Majority Element
주어진 배열 내에서 배열 전체 개수의 절반 이상이 나오는 수를 구하는 문제입니다.

```
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        d = {}
        x = 0
        for n in nums:
            if n in d.keys():
                d[n] += 1
            else:
                d[n] = 1
        maximum, key = 0, 0
        for k, v in d.items():
            if maximum < v:
                key = k
                maximum = v
        return key
```
dictionary 자료형을 활용했습니다.
배열내의 수들을 key로 하고 수들이 모여있는 개수를 value로 설정하여 value가 최댓값인 경우의 key를 반환합니다.  

```
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        return sorted(nums)[len(nums)//2]
```
solutions에서 본 풀이입니다.  
단순히 배열에서 가장 많이 들어있는 수를 구하는 문제인 줄 알았는데, 이 풀이를 보고 가장 많은 수는 절반 이상의 개수가 나온다는 조건이 있는 것을 확인했습니다.  
더 짧게 해결할 수 있는데 조금 아쉽습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/majority-element/submissions/908260019/](https://leetcode.com/problems/majority-element/submissions/908260019/)