---
title: Detonate the Maximum Bombs
author: icyou
date: 2023-05-30 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Detonate the Maximum Bombs
bomb이 주어진 배열에서 하나의 폭탄이 터질 경우 최대 터질 수 있는 폭탄의 개수를 구하는 문제입니다.

```
from collections import defaultdict

class Solution:
	def maximumDetonation(self, bombs: List[List[int]]) -> int:
    
		self.graph = self.bombs_to_graph(bombs)
		print(self.graph.graph)
		ans = 1
		self.dp = [0]*len(bombs)
		for i in range(len(bombs)):
			visited = set()
			self.DFS(i, visited)
			ans = max(ans, len(visited))
		return ans




	def DFS(self, v, visited):

		visited.add(v)
		for neigh in self.graph.graph[v]:
			if neigh not in visited:
				self.DFS(neigh, visited)

	def bombs_to_graph(self, bombs):
		graph = Graph()
		for i_s, source in enumerate(bombs):
			for i_d, dest in enumerate(bombs):
				if i_s == i_d: continue

				if self.is_on_range(source, dest):
					graph.add_edge(i_s, i_d)

		return graph

	def is_on_range(self, source, dest):

		dist = ((source[0] - dest[0])**2 + (source[1] - dest[1])**2)**0.5
		return dist <= source[2]
 
    
class Graph:
	def __init__(self):
		self.graph = defaultdict(list)

	def add_edge(self, s, d):
		self.graph[s].append(d)
```
solution의 풀이입니다.  
bfs는 backtracking과 달리 갔던 길에 대해 다시 연산하지 않기 때문에 속도가 더 빠른 것 같습니다.
 
<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/detonate-the-maximum-bombs/submissions/962349237/](https://leetcode.com/problems/detonate-the-maximum-bombs/submissions/962349237/)