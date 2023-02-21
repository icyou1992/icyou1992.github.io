---
title: Minimum Depth of Binary Tree
author: icyou
date: 2023-02-21 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Minimum Depth of Binary Tree
주어진 binary tree에서, root부터 leaf node까지의 최소 높이를 구하는 문제입니다.  
leaf node는 자식 node가 없습니다.  

```
class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        if not root.left and not root.right:
            return 1
        return 1 + min(self.minDepth(root.left), self.minDepth(root.right)) if root.left and root.right else 1 + self.minDepth(root.left) if root.left else 1 + self.minDepth(root.right)
```
leaf node는 자식이 없어야 하므로 left, right 모두 None이어야 하고 이 경우에 높이를 구해야하므로 leaf node 맨 끝단의 높이인 1을 return합니다.  
그리고 []일 경우에는 높이를 구하기 위해 0을 return 해야하는데, 이 상황에서 최소 높이를 구하는 경우, root에서 left, right 중 한 쪽만 있는 경우에 leaf node까지의 최소 길이를 구할 수가 없습니다.  
이미 `min(self.minDepth(root.left), self.minDepth(root.right))`로 양쪽 자식 node로 순회를 시작해서 한 쪽이 없을 경우 한 쪽에 대한 최소 길이인 1을 return하기 때문입니다.
그래서 return에 자식 node가 있는 쪽으로만 순회를 하도록 조건을 달아주었습니다.  

<br/><br/>
```
class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        if not root.left:
            return self.minDepth(root.right) + 1
        if not root.right:
            return self.minDepth(root.left) + 1
        return min(self.minDepth(root.left), self.minDepth(root.right)) + 1
```
solution을 참고한 풀이입니다.  
함수 내부에서 left가 없는 경우 right가 없는 경우를 간단히 처리해주어서 더욱 가독성이 좋습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/minimum-depth-of-binary-tree/submissions/902189350/](https://leetcode.com/problems/minimum-depth-of-binary-tree/submissions/902189350/)
- [https://leetcode.com/problems/minimum-depth-of-binary-tree/solutions/3191727/python-recursive-code-easy-to-understand/](https://leetcode.com/problems/minimum-depth-of-binary-tree/solutions/3191727/python-recursive-code-easy-to-understand/)