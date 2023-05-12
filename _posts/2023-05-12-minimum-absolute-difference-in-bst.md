---
title: Minimum Absolute Difference in BST
author: icyou
date: 2023-05-12 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Minimum Absolute Difference in BST
이진 탐색 트리(Binary Search Tree)에서 노드끼리의 최소 차이를 구하는 문제입니다.  

```
class Solution:
    def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
        def dfs(node):
            if not node:
                return []
            return dfs(node.left) + [node.val] + dfs(node.right)
        arr = dfs(root)
        return min([ arr[i + 1] - arr[i] for i in range(len(arr) - 1) ])
```
주어진 트리는 이진 트리이므로 중위 순회(inorder traversal)를 통해 정렬된 배열을 얻을 수 있습니다.  
얻은 배열로 인접한 노드 값의 차이 중 최소값을 구하면 됩니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/minimum-absolute-difference-in-bst/submissions/948830847/](https://leetcode.com/problems/minimum-absolute-difference-in-bst/submissions/948830847/)