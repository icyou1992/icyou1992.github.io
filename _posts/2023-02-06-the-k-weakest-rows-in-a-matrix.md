---
title: The K Weakest Rows in a Matrix
author: icyou
date: 2023-02-06 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### The K Weakest Rows in a Matrix

m * n의 행렬이 주어졌을 때, 1의 개수가 적은 순서대로 k번째까지 행렬의 index를 출력하는 문제입니다.

```
class Solution:
    def kWeakestRows(self, mat: List[List[int]], k: int) -> List[int]:
        rank = []
        i = 0
        for x in mat:
            rank.append([sum(x), i])
            i += 1
        return [sorted(rank)[j][1] for j in range(k)]
```
군인의 총합을 구하기 위해 각 row를 sum을 통해 더하고 이 결과값과 index를 2차원 배열(rank)로 저장합니다.  
sorted 함수로 오름차순으로 정렬된 rank의 index를 k번째까지 저장한 배열을 return 합니다.  
python으로 알고리즘 문제를 풀다보면 좀 더 적은 코드로 문제를 풀고 싶은 욕구가 생깁니다.  
그래서 줄였습니다.

```
class Solution:
    def kWeakestRows(self, mat: List[List[int]], k: int) -> List[int]:
        rank = [(sum(mat[i]), i) for i in range(len(mat))]
        return [sorted(rank)[i][1] for i in range(k)]
```
옛날에 코드를 줄이기 위해 map, counter, lambda 등을 활용했던 것 같은데 까먹어서 다시 연습해야겠습니다.

<br/><br/>


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/submissions/892576595/](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/submissions/892576595/)