---
title: Binary Tree Paths
author: icyou
date: 2023-03-17 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Binary Tree Paths
주어진 Binary Tree에서 각 leaf node까지의 경로를 구하는 문제입니다.

```
class Solution:
    def binaryTreePaths(self, root):
        if not root:
            return []
        res = []
        self.dfs(root, "", res)
        return res
    
    def dfs(self, root, ls, res):
        if not root.left and not root.right:
            res.append(ls+str(root.val))
        if root.left:
            self.dfs(root.left, ls+str(root.val)+"->", res)
        if root.right:
            self.dfs(root.right, ls+str(root.val)+"->", res)

```
solution의 풀이입니다.  
결국 문제를 못 풀었습니다. 거의 다 풀었는데, 
if root.left: return self.dfs(root.left, ls+str(root.val)+"->", res)로 풀어서 답이 안 나왔습니다.  
return을 할 필요가 없다는 것은 이해했지만, return을 넣으면 if root.right 조건이 실행되지 않기 때문에 return을 넣으면 안됩니다.  

```
class Solution:
    def binaryTreePaths(self, root):
        if not root:
            return []
        res, queue = [], collections.deque([(root, "")])
        while queue:
            node, ls = queue.popleft()
            if not node.left and not node.right:
                res.append(ls+str(node.val))
            if node.left:
                queue.append((node.left, ls+str(node.val)+"->"))
            if node.right:
                queue.append((node.right, ls+str(node.val)+"->"))
        return res
```
solution의 풀이로 이전 풀이는 dfs를 활용했고 지금은 bfs를 활용한 풀이입니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/binary-tree-paths/solutions/68272/python-solutions-dfs-stack-bfs-queue-dfs-recursively/](https://leetcode.com/problems/binary-tree-paths/solutions/68272/python-solutions-dfs-stack-bfs-queue-dfs-recursively/)