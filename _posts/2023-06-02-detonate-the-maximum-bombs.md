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
class Graph:
	def __init__(self):
		self.graph = defaultdict(list)

	def add_edge(self, s, d):
		self.graph[s].append(d)

class Solution:
	def maximumDetonation(self, bombs: List[List[int]]) -> int:
		self.graph = self.bombs_to_graph(bombs)
		ans = 1
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
				if ((source[0] - dest[0])**2 + (source[1] - dest[1])**2)**0.5 <= source[2]:
					graph.add_edge(i_s, i_d)
		return graph
    
```
solution의 풀이입니다.  
dictionary를 graph로 활용합니다. 이후 bombs_to_graph 함수에서 bombs를 두 개 가져와서 짝을 지어 둘 사이의 거리가 폭발 범위보다 작은 지를 확인합니다. 폭발 범위가 더 커서 연쇄 폭발이 일어나는 경우 graph에 index를 추가합니다.  
이후, maximumDetonation 함수에서 dfs로 각 graph를 순회하면서 터질 수 있는 폭탄의 최대 갯수를 구합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/detonate-the-maximum-bombs/submissions/962349237/](https://leetcode.com/problems/detonate-the-maximum-bombs/submissions/962349237/)