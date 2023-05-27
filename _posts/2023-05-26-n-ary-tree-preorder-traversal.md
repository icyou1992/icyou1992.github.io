---
title: N-ary Tree Preorder Traversal
author: icyou
date: 2023-05-26 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### N-ary Tree Preorder Traversal
tree가 주어졌을 때, preorder 수행 결과를 구하는 문제입니다.

```
class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        return [root.val] + sum([self.preorder(x) for x in root.children], []) if root else []
```  
sum 함수로 이중 배열을 flatten하게 바꿀 수 있다는 것을 배웠습니다.
 
<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/n-ary-tree-preorder-traversal/submissions/957622277/](https://leetcode.com/problems/n-ary-tree-preorder-traversal/submissions/957622277/)