---
title: Subtree of Another Tree
author: icyou
date: 2023-05-22 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Subtree of Another Tree
tree와 subtree가 주어졌을 때, tree 안에 subtree가 존재하는지 판별하는 문제입니다.  

```
class Solution:
    def matchTree(self, node1, node2):
        if not node1 and not node2:
            return True
        elif (not node1 and node2) or (node1 and not node2):
            return False
        return node1.val == node2.val and self.matchTree(node1.left, node2.left) and self.matchTree(node1.right, node2.right)
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        if not root:
            return False
        return self.matchTree(root, subRoot) or self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot)
```  
tree의 특정 노드부터 시작되는 tree와 subtree를 비교하는 matchTree라는 함수를 만들고 이를 preorder traversal로 돌면서 tree 내에 subtree가 존재하는지 찾아봅니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/subtree-of-another-tree/submissions/955005574/](https://leetcode.com/problems/subtree-of-another-tree/submissions/955005574/)