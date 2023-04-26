---
title: Island Perimeter
author: icyou
date: 2023-04-26 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Island Perimeter
2차원 배열 grid에서 1은 땅이고 0은 물이라고 하면, 땅의 테두리의 길이를 구하는 문제입니다.  

```
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
        cnt = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == 1:
                    cnt += 4
                    if i > 0 and grid[i - 1][j] == 1:
                        cnt -= 1
                    if i < len(grid) - 1 and grid[i + 1][j] == 1:
                        cnt -= 1
                    if j > 0 and grid[i][j - 1] == 1:
                        cnt -= 1
                    if j < len(grid[0]) - 1 and grid[i][j + 1] == 1:
                        cnt -= 1
        return cnt
```
2차원 배열에서 땅인 부분은 물로만 뒤덮였을 때 길이가 4가 됩니다. 여기서 땅이 테두리에 붙을 때마다 길이가 1씩 감소합니다.  
이를 토대로 배열을 순회하면서 1이 나오면 길이를 4 늘린 후에 사방에 붙은 땅이 있다면 길이를 1씩 감소시킵니다.




<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/island-perimeter/submissions/940058921/](https://leetcode.com/problems/island-perimeter/submissions/940058921/)