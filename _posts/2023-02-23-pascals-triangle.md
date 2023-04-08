---
title: Pascal's Triangle
author: icyou
date: 2023-02-23 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Pascal's Triangle
numRows가 주어졌을 때, 해당 층 수까지의 파스칼 삼각형을 구하는 문제입니다.

```
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        pascal = [[1]]
        num = 1
        while num < numRows:
            row = [1]
            for i in range(num - 1):
                row.append(pascal[num - 1][i] + pascal[num - 1][i + 1])
            row.append(1)
            pascal.append(row)
            num += 1
        return pascal if numRows > 1 else [[1]]
```
문제에서 이미 파스칼 삼각형의 다음 아래층을 구하는 방법을 알려주었습니다. 바로 윗층의 수들을 두 개 더하는 방식이므로, 그 방식을 그대로 사용하여 원하는 층까지의 파스칼 삼각형을 만들도록 구현했습니다.


```
class Solution:
    def generate(self, numRows):
        pascal = [[1]]
        for i in range(1, numRows):
            pascal.append([x + y for x, y in zip(pascal[-1] + [0], [0] + pascal[-1])])
        return pascal
```
solution에서 본 풀이입니다.  
-1 index를 활용해서 이전 층을 간단하게 표현하고, 또 이전 층의 배열에 [0]을 양쪽에 더한 새로운 두 배열을 만들고 서로 더한다는 아이디어가 기발합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/pascals-triangle/submissions/903450947/](https://leetcode.com/problems/pascals-triangle/submissions/903450947/)
- [https://leetcode.com/problems/pascals-triangle/solutions/3190724/python-clean-simple-fibonacci-like-solution/](https://leetcode.com/problems/pascals-triangle/solutions/3190724/python-clean-simple-fibonacci-like-solution/)