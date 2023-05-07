---
title: Find Mode in Binary Search Tree
author: icyou
date: 2023-05-05 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Find Mode in Binary Search Tree
이진 탐색 트리에서 가장 빈번하게 나오는 수들을 구하는 문제입니다. 가장 많이 나오는 수가 여러개일 경우 전부 구해야 합니다.

```
from collections import Counter
class Solution:
    def traverse(self, root: Optional[TreeNode]) -> List[int]:
        return [root.val] + self.traverse(root.left) + self.traverse(root.right) if root else []
    def findMode(self, root: Optional[TreeNode]) -> List[int]:
        counter = Counter(self.traverse(root))
        return [ x for x in counter if counter[x] == counter.most_common(1)[0][1] ]
```
preorder traversal로 tree 구조를 배열로 바꿉니다. 이후 collections의 counter 함수와 most_common 함수를 이용하여 가장 빈번한 수와 그 횟수를 구한 다음, 그 횟수와 일치하는 모든 수를 배열로 출력합니다.  
하지만 이 풀이 방법은 성능이 좋지 않았습니다.

```
class Solution:
    def findMode(self, root: Optional[TreeNode]) -> List[int]:
        dict = {}
        max_ = -1
        
        def traverse(root):
            nonlocal max_
            if not root:
                return

            traverse(root.left)
            dict[root.val] = 1 + dict.get(root.val, 0)
            if max_ < dict[root.val]:
                max_ = max(max_, dict[root.val])
            
            traverse(root.right)
            
        traverse(root)
       
        lst2= []
        
        for key in dict.keys():
            if dict[key] == max_:
                lst2.append(key)
                
        return lst2
```
solution의 풀이는 순회 중에 가장 빈번한 수가 나오는 횟수를 미리 구하기 때문에 순회를 한번 더할 필요를 줄였습니다.




<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/find-mode-in-binary-search-tree/submissions/944953748/](https://leetcode.com/problems/find-mode-in-binary-search-tree/submissions/944953748/)


