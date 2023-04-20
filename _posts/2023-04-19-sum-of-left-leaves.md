---
title: Sum of Left Leaves
author: icyou
date: 2023-04-19 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Sum of Left Leaves
Leaf Node 중 왼쪽 node값의 합을 구하는 문제입니다.

```
class Solution:
    def sumOfLeftLeaves(self, root: Optional[TreeNode]) -> int:
        return self.dfs(True, root.left) + self.dfs(False, root.right)

    def dfs(self, isLeft: bool, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        if not root.left and not root.right and isLeft:
            return root.val
        return self.dfs(True, root.left) + self.dfs(False, root.right)
```
dfs 함수를 하나 만들고 자식 노드로 순회할 때 left node인지에 대한 정보를 parameter로 건네줍니다. 이후 dfs 순회를 통해 leaf node까지 도달하면 이 parameter를 이용하여, left node에 대해서만 값을 반환합니다.
코드의 길이를 좀 더 줄이고 싶었지만, left node인지를 판별하기 위해서는 이전의 노드에 대한 정보가 있어야만 하고 다른 함수가 필요할 수밖에 없다고 생각했습니다.

```
class Solution:
    def sumOfLeftLeaves(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        if root.left and not root.left.left and not root.left.right:
            return root.left.val + self.sumOfLeftLeaves(root.right)
        else:
            return self.sumOfLeftLeaves(root.left) + self.sumOfLeftLeaves(root.right)
        
```
solution의 풀이입니다.  
하지만, 이렇게 풀면 다른 함수가 필요 없네요. 훨씬 가독성도 좋아보입니다.

```
class Solution:
    def sumOfLeftLeaves(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        cnt = x.val if (x := root.left) and not x.left and not x.right else self.sumOfLeftLeaves(root.left)
        return cnt + self.sumOfLeftLeaves(root.right)
```
solution의 풀이입니다.  
:= 연산자라는 것을 처음 알게 되었습니다.  
이 연산자를 사용하면 do while을 편리하게 구현할 수 있겠네요. 

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/sum-of-left-leaves/submissions/936308551/](https://leetcode.com/problems/sum-of-left-leaves/submissions/936308551/)
- [https://leetcode.com/problems/sum-of-left-leaves/solutions/1558223/python-dfs-recursion-easy-intuitive/?languageTags=python3](https://leetcode.com/problems/sum-of-left-leaves/solutions/1558223/python-dfs-recursion-easy-intuitive/?languageTags=python3)