---
title: Third Maximum Number
author: icyou
date: 2023-04-21 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Third Maximum Number
주어진 배열에서 중복을 제외하고 세번째로 큰 수를 구하는 문제입니다.

```
class Solution:
    def thirdMax(self, nums: List[int]) -> int:
        return sorted(set(nums))[-3] if len(set(nums)) > 2 else sorted(nums)[-1]
```
set를 통해 중복을 없애주고 정렬된 배열에서 뒤에서 세번째 원소를 가져오면 됩니다. set(nums)의 길이가 3보다 작을 경우 세번째 큰 수가 없으므로 최댓값을 반환합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/third-maximum-number/submissions/937400172/](https://leetcode.com/problems/third-maximum-number/submissions/937400172/)