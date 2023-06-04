---
title: Range Addition II
author: icyou
date: 2023-06-04 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Range Addition II
ops 배열에서 주어진 범위만큼 숫자가 1씩 증가할 때, 가장 많이 증가한 수의 범위를 구하는 문제입니다.  

```
class Solution:
    def maxCount(self, m: int, n: int, ops: List[List[int]]) -> int:
        return min(ops, key = lambda x:x[0])[0]*min(ops, key = lambda x:x[1])[1] if ops else m*n
```
범위 중, 숫자가 가장 많이 증가하려면 ops에서 나오는 배열의 범위가 가장 많이 겹쳐야 합니다. 최소 범위가 가장 많이 겹치므로 ops 배열에서 m 행을 기준으로 최솟값과 n 열을 기준으로 최솟값을 각각 구하면 범위의 최솟값을 구할 수 있습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/range-addition-ii/submissions/963738752/](https://leetcode.com/problems/range-addition-ii/submissions/963738752/)