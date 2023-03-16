---
title: Contains Duplicate
author: icyou
date: 2023-03-14 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Contains Duplicate
주어진 배열에 겹치는 수가 있는지를 판별하는 문제입니다.

```
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(nums) != len(set(nums))
```
set는 중복되는 수를 제거한다는 점을 이용하여 두 길이가 같지 않을 경우 중복이 되는 수가 있으므로 true를 반환합니다.  

```
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        d = {}
        for n in nums:
            if n in d.keys():
                return True
            else:
                d[n] = 1
        return False
```
첫번째 풀이는 배열의 길이를 구하기 위해 모든 배열을 순회한다는 것을 생각해보면, 배열을 순회하면서 겹치는 수가 나올 경우 바로 true를 return한다면 성능을 더 높일 수 있을 것이라 생각했습니다.  
결과는 두번째 풀이가 성능이 더 좋습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/contains-duplicate/submissions/916178655/](https://leetcode.com/problems/contains-duplicate/submissions/916178655/)
- [https://leetcode.com/problems/contains-duplicate/submissions/916190260/](https://leetcode.com/problems/contains-duplicate/submissions/916190260/)