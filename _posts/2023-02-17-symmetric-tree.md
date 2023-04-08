---
title: Symmetric Tree
author: icyou
date: 2023-02-17 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Symmetric Tree
두 binary tree가 대칭인지를 비교하는 문제입니다.  

```
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        def symmetric(left: Optional[TreeNode], right: Optional[TreeNode]):
            if not left and not right:
                return True
            elif (left and not right) or (not left and right):
                return False
            elif left and right and left.val != right.val:
                return False
            return symmetric(left.left, right.right) and symmetric(left.right, right.left)
        return symmetric(root.left, root.right) if root else False

```
어제의 문제를 참고해서, not left and not right의 경우의 수를 잘 처리했습니다.  

<br/><br/>
```
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        return self.symmetric(root.left, root.right)
    def symmetric(self, left: Optional[TreeNode], right: Optional[TreeNode]):
        if left == None or right == None:
            return left == right
        return left.val == right.val and self.symmetric(left.left, right.right) and self.symmetric(left.right, right.left)
```
어제의 solution을 활용한 풀이입니다.  
`if left == None or right == None: return left == right` 문장 하나로 left와 right가 있는 경우, 한쪽만 있는 경우를 하나로 합쳐줄 수 있습니다.



<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/symmetric-tree/submissions/899718077/](https://leetcode.com/problems/symmetric-tree/submissions/899718077/)
