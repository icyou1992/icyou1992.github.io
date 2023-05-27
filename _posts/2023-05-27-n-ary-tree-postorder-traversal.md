---
title: N-ary Tree Postorder Traversal
author: icyou
date: 2023-05-27 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### N-ary Tree Postorder Traversal
tree가 주어졌을 때, postorder 수행 결과를 구하는 문제입니다.

```
class Solution:
    def postorder(self, root: 'Node') -> List[int]:
        return sum([self.postorder(x) for x in root.children], []) + [root.val] if root else []
```  
어제 배운 sum 함수를 활용했습니다.
 
<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/n-ary-tree-postorder-traversal/submissions/957994988/](https://leetcode.com/problems/n-ary-tree-postorder-traversal/submissions/957994988/)