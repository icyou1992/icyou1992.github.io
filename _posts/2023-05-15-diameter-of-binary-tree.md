---
title: Diameter of Binary Tree
author: icyou
date: 2023-05-12 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Diameter of Binary Tree
주어진 Binary Tree에서 왼쪽 끝 노드부터 오른쪽 끝 노드까지의 최대 길이를 구하는 문제입니다.

```
class Solution:
    def __init__(self, maxi = 0):
        self.maxi = maxi

    def dfs(self, node):
        if not node:
            return 0
        nl = self.dfs(node.left)
        nr = self.dfs(node.right)
        self.maxi = max(self.maxi, nl + nr)
        return max(nl, nr) + 1
        
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        self.dfs(root)
        return self.maxi
```
solutions의 풀이를 정리했습니다.  
instance variable을 활용하여 dfs 함수가 각 노드를 돌면서 왼쪽 최대 길이와 오른쪽 최대 길이의 합을 구하고, 최댓값을 구합니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/diameter-of-binary-tree/solutions/3443234/python-simple-clean-recursive-solution/?languageTags=python3](https://leetcode.com/problems/diameter-of-binary-tree/solutions/3443234/python-simple-clean-recursive-solution/?languageTags=python3)