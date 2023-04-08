---
title: Pascal's Triangle II
author: icyou
date: 2023-02-24 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Pascal's Triangle II
rowIndex가 주어졌을 때, 파스칼 삼각형에서 해당 층의 배열을 구하는 문제입니다.

```
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        pascal = [[1]]
        for i in range(1, rowIndex+1):
            pascal.append([x + y for x, y in zip([0] + pascal[i-1], pascal[i-1] + [0])])
        return pascal[rowIndex]
```
이전 solution의 풀이를 활용하여 해답을 구했습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/pascals-triangle-ii/submissions/904046846/](https://leetcode.com/problems/pascals-triangle-ii/submissions/904046846/)