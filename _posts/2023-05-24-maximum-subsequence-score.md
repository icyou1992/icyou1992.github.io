---
title: Maximum Subsequence Score
author: icyou
date: 2023-05-24 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Maximum Subsequence Score
nums1, nums2 배열이 주어졌을 때, 각 배열에서 k개의 원소를 고른 다음, nums1에서 k개의 원소의 합과 nums2에서 k개의 원소 중 최솟값을 곱한 것들 중 최댓값을 구하는 문제입니다.

```
class Solution:
    def maxScore(self, nums1: List[int], nums2: List[int], k: int) -> int:
        res, prefixSum, maxHeap = 0, 0, []
        for a, b in sorted(list(zip(nums1, nums2)), key=itemgetter(1), reverse=True):
            prefixSum += a
            heappush(maxHeap, a)
            if len(maxHeap) == k:
                res = max(res, prefixSum * b)
                prefixSum -= heappop(maxHeap)                               
        return res
```  
heap을 사용해야겠다는 생각이 떠오르지 않아서 풀이를 봤습니다.  
zip 함수를 사용해서 nums1과 nums2의 원소를 각각 짝지어주고, nums2를 기준으로 내림차순으로 정렬합니다. 이는 b가 최솟값임을 보장합니다.
이후 prefixSum에 nums1의 k개의 원소를 저장합니다. 이후 for문을 돌면서 나오는 b는 전부 최솟값이 되므로 prefixSum에 b를 곱한 수의 최댓값을 구합니다. prefixSum은 maxHeap에서 원소를 계속 하나씩 빼고 더하면서 최댓값을 비교합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/maximum-subsequence-score/solutions/3557261/python3-heap-prefixsum-beats-98/](https://leetcode.com/problems/maximum-subsequence-score/solutions/3557261/python3-heap-prefixsum-beats-98/)