---
title: Kth Largest Element in a Stream
author: icyou
date: 2023-05-23 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Kth Largest Element in a Stream
class 안에는 변수 k와 nums 배열과 add 함수가 주어졌습니다. add 함수로 nums 배열에 val을 추가하였을 때, k번째 수를 구하는 문제입니다.

```
class KthLargest:
    def __init__(self, k: int, nums: List[int]):
        self.minHeap, self.k = nums, k
        heapq.heapify(self.minHeap)
        while len(self.minHeap) > k:
            heapq.heappop(self.minHeap)
        
    def add(self, val: int) -> int:
        heapq.heappush(self.minHeap, val)
        if self.k < len(self.minHeap):
            heapq.heappop(self.minHeap)
        return self.minHeap[0]
```  
heap을 사용하면 배열에 원소들이 정렬된 상태로 추가되고 삭제됩니다.  
instance를 초기화할 때 k번째 큰 수까지만 필요하므로 배열 원소의 갯수를 k - 1개까지 유지하고 나머지는 버립니다.
이후 add로 val 변수를 추가하면 배열의 총 원소의 갯수는 k개이므로 heap\[0\]을 반환합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/kth-largest-element-in-a-stream/solutions/3462888/solution/](https://leetcode.com/problems/kth-largest-element-in-a-stream/solutions/3462888/solution/)