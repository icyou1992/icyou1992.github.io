---
title: Maximum Depth of Binary Tree
author: icyou
date: 2023-02-16 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm]
pin: true
math: true
---

## Leetcode Problem

### Maximum Depth of Binary Tree
binary tree의 최대 깊이를 구하는 문제입니다.

```
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        return max(self.maxDepth(root.left) + 1, self.maxDepth(root.right) + 1) if root else 0

```
이전에 배운 지식을 활용하여 한 줄로 문제를 해결할 수 있었습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/maximum-depth-of-binary-tree/submissions/900277380/](https://leetcode.com/problems/maximum-depth-of-binary-tree/submissions/900277380/)
