---
title: Shortest Path in Binary Matrix
author: icyou
date: 2023-05-30 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Shortest Path in Binary Matrix
주어진 2차원 배열에서 (0, 0)에서 (-1, -1)까지 갈 수 있는 최단 거리를 구하는 문제입니다.  

```
class Solution:
    def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
        if grid[0][0] != 0 or grid[-1][-1] != 0:
            return -1
        direction = [(1, 0), (0, -1), (1, -1), (-1, 1), (-1, 0), (-1, -1), (1, 1), (0, 1)]
        visited, count = [ [0] * len(grid[0]) for _ in range(len(grid)) ], 100000
        visited[0][0] = 1  

        def go(i: int, j: int, cnt: int):
            nonlocal count
            if i == len(grid) - 1 and j == len(grid) - 1:
                count = min(count, cnt)
            
            for d in direction:
                if 0 <= i + d[0] < len(grid) and 0 <= j + d[1] < len(grid):
                    if visited[i + d[0]][j + d[1]] == 0 and grid[i + d[0]][j + d[1]] == 0:
                        visited[i + d[0]][j + d[1]] = 1
                        go(i + d[0], j + d[1], cnt + 1)
                        visited[i + d[0]][j + d[1]] = 0
        
        go(0, 0, 1)

        return -1 if count == 100000 else count
```  
backtracking으로 풀려고 했으나 time limit으로 풀지 못했습니다.  

```
class Solution:
    def shortestPathBinaryMatrix(self, grid):
        n = len(grid)
        if grid[0][0] or grid[n - 1][n - 1]:
            return -1

        queue = [(0, 0, 1)]
        grid[0][0] = 1

        for i, j, d in queue:
            if i == n - 1 and j == n - 1:
                return d

            directions = [
                (i - 1, j - 1), (i - 1, j), (i - 1, j + 1),
                (i, j - 1), (i, j + 1),
                (i + 1, j - 1), (i + 1, j), (i + 1, j + 1)
            ]

            for x, y in directions:
                if 0 <= x < n and 0 <= y < n and not grid[x][y]:
                    grid[x][y] = 1
                    queue.append((x, y, d + 1))

        return -1
```
solution의 풀이입니다.  
bfs는 backtracking과 달리 갔던 길에 대해 다시 연산하지 않기 때문에 속도가 더 빠른 것 같습니다.
 
<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/shortest-path-in-binary-matrix/submissions/961660097/](https://leetcode.com/problems/shortest-path-in-binary-matrix/submissions/961660097/)
- [https://leetcode.com/problems/shortest-path-in-binary-matrix/solutions/3584004/python-java-c-simple-solution-easy-to-understand/](https://leetcode.com/problems/shortest-path-in-binary-matrix/solutions/3584004/python-java-c-simple-solution-easy-to-understand/)