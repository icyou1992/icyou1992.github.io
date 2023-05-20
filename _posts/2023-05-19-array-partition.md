---
title: Array Partition
author: icyou
date: 2023-05-19 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Array Partition
nums 배열을 두 개씩 짝짓고 그 짝들의 작은 수들의 합을 구하는 문제입니다.

```
class Solution:
    def arrayPairSum(self, nums: List[int]) -> int:
        arr = sorted(nums)
        return sum([arr[i] for i in range(len(nums)) if i % 2 == 0])
```  
합의 최댓값을 구하려면 짝이 될 때 두 수의 차이를 최소화해야 합니다. 따라서 배열을 정렬하고 차례대로 두 개씩 짝지어주면 각 짝들에서 첫번째 원소들의 합이 최대가 됩니다.

```
class Solution:
    def arrayPairSum(self, nums: List[int]) -> int:
        return sum(sorted(nums)[::2])
```
solution의 풀이입니다.  
다음부터는 ::x를 통해 일정 간격의 원소들을 얻을 수 있다는 것을 활용해야겠습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/array-partition/submissions/953052497/](https://leetcode.com/problems/array-partition/submissions/953052497/)
- [https://leetcode.com/problems/array-partition/solutions/3400055/solution/](https://leetcode.com/problems/array-partition/solutions/3400055/solution/)