---
title: Binary Tree Tilt
author: icyou
date: 2023-05-20 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Binary Tree Tilt
Tree에서 왼쪽 child node들과 오른쪽 child node들의 합을 tilt라 합니다. Binary Tree가 주어졌을 때, 모든 node의 tilt의 합을 구하는 문제입니다.   
```
class Solution:
    def __init__(self, tilt = 0): 
        self.tilt = tilt
    def getSum(self, node):
        if not node:
            return 0
        else:
            sr = self.getSum(node.right)
            sl = self.getSum(node.left)
            self.tilt += abs(sr - sl)
            return sr + sl + node.val
    def findTilt(self, root: Optional[TreeNode]) -> int:
        self.getSum(root)
        return self.tilt
```  
instance variable로 tilt를 설정하고 각 노드들의 합을 구할 때, 왼쪽 자식 노드들의 합과 오른쪽 자식 노드들의 합의 차이를 tilt에 더해주면서 모든 tilt의 합을 구해줍니다.  


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/binary-tree-tilt/submissions/953643739/](https://leetcode.com/problems/binary-tree-tilt/submissions/953643739/)