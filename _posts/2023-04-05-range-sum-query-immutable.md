---
title: Range Sum Query - Immutable
author: icyou
date: 2023-04-05 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Range Sum Query - Immutable
nums 배열과 nums 배열의 left부터 right까지 합을 구하는 함수가 들어간 class를 작성하는 문제입니다.

```
class NumArray:
    def __init__(self, nums: List[int]):
        self.nums = nums
    def sumRange(self, left: int, right: int) -> int:
        s = 0
        for i in range(left, right + 1):
            s += self.nums[i]
        return s
```

```
class NumArray:
    def __init__(self, nums: List[int]):
        arr = [nums[0]]
        for i in range(1,len(nums)):
            arr.append(arr[-1]+nums[i])
        self.arr = arr

    def sumRange(self, left: int, right: int) -> int:
        if left == 0:
            return self.arr[right]
        return self.arr[right] - self.arr[left - 1]
```
solution의 풀이입니다.  
init 과정에서 nums를 그대로 저장하지 않고 n까지 원소의 합으로 저장하면 left-1 원소와 right 원소의 차이로 left부터 right까지의 합을 구할 수 있습니다.  
이 방식이 속도는 더 좋지만 범용성은 떨어질 것 같습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/range-sum-query-immutable/submissions/928276245/](https://leetcode.com/problems/range-sum-query-immutable/submissions/928276245/)
- [https://leetcode.com/problems/range-sum-query-immutable/solutions/3371852/python-o-1-solution-beats-97-85/?languageTags=python3](https://leetcode.com/problems/range-sum-query-immutable/solutions/3371852/python-o-1-solution-beats-97-85/?languageTags=python3)