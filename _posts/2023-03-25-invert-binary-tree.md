---
title: Invert Binary Tree
author: icyou
date: 2023-03-25 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Invert Binary Tree
주어진 binary tree를 좌우반전시키는 문제입니다.

```
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root:
            node = root.left
            root.left = root.right
            root.right = node
            self.invertTree(root.left)
            self.invertTree(root.right)
        return root 
```
두 변수의 값을 교환하는 swap 방식을 treenode에도 적용시켰습니다.

```
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root:
            root.left, root.right = self.invertTree(root.right), self.invertTree(root.left)
            return root        
```
solutions의 풀이를 응용했습니다.  
','를 활용하면 swap 방식의 필요가 없어지면서 동시에 recursive를 활용하여 코드의 크기도 줄였습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/invert-binary-tree/submissions/921849761/](https://leetcode.com/problems/invert-binary-tree/submissions/921849761/)
- [https://leetcode.com/problems/invert-binary-tree/solutions/3199836/python-dfs-recursion-clean-simple-21ms/](https://leetcode.com/problems/invert-binary-tree/solutions/3199836/python-dfs-recursion-clean-simple-21ms/)