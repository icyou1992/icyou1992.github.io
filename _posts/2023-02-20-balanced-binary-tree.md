---
title: Balanced Binary Tree
author: icyou
date: 2023-02-19 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm]
pin: true
math: true
---

## Leetcode Problem

### Balanced Binary Tree
이진 tree가 주어졌을 때, height-balanced한지를 판별하는 문제합니다.

```
class Solution:
    def getHeight(self, root: Optional[TreeNode]): 
        if not root:
            return 0
        return 1 + max(self.getHeight(root.left), self.getHeight(root.right))

    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        if root == None:
            return True
        return True if self.isBalanced(root.left) and self.isBalanced(root.right) and abs(self.getHeight(root.left) - self.getHeight(root.right)) < 2 else False

```
height-balanced하다는 개념을 잘못 이해하여 아래와 같이 잘못 풀었지만, 개념을 검색해보니 AVL tree와 같다는 것을 알아냈습니다.  

- AVL Tree(height-balanced Tree) 
모든 node의 왼쪽과 오른쪽 부분 tree의 높이 차이가 1 이하인 binary tree  
개념을 찾아보고 나서 이 문제는 각 node를 순회하며 높이 차이를 구하는 문제라는 것을 깨달았습니다. 즉, tree를 순회하는 문제와 높이를 구하는 문제를 합친 것입니다. 순회하는 방식은 높이를 구할 때, 즉 해당 node를 순회할 때 연산이 제일 많이 발생하므로, node 순회를 마지막으로 하는 postorder를 활용했습니다.  
  
잘못된 풀이는 아래와 같습니다.  
```
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        if root == None:
            return True
        def isFilled(left: Optional[TreeNode], right: Optional[TreeNode]):
            if left == None and right == None:
                return True
            elif left != None and right != None:
                return isFilled(left.left, left.right) and isFilled(right.left, right.right)
            else:
                return False
        def calHeight(root: Optional[TreeNode]):
            if root == None:
                return 0
            return 1 + max(calHeight(root.left), calHeight(root.right))
        return True if isFilled(root.left, root.right) and abs(calHeight(root.left) - calHeight(root.right)) < 2 else False
```
이 풀이는 제가 height-balanced라는 개념을 오른쪽과 왼쪽 node의 높이 차이가 1일 뿐만 아니라 각 node의 오른쪽 왼쪽 node가 모두 없거나 모두 있는 두 경우만 있다는 것으로 오해하여 잘못 푼 풀이입니다.  


```
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        def getHeight(node):
            if node is None:
                return 0
            left_height = getHeight(node.left)
            right_height = getHeight(node.right)
            if left_height == -1 or right_height == -1 or abs(left_height - right_height) > 1:
                return -1
            return 1 + max(left_height, right_height)
        return getHeight(root) != -1
```
solution에서 본 풀이입니다. 높이 차이가 1 이상이 날 경우 -1로 설정하여 False로 처리했습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/balanced-binary-tree/submissions/901554730/](https://leetcode.com/problems/balanced-binary-tree/submissions/901554730/)
-[https://leetcode.com/problems/balanced-binary-tree/solutions/3191981/convert-sorted-list-to-binary-search-tree-with-step-by-step-explanation/?languageTags=python3](https://leetcode.com/problems/balanced-binary-tree/solutions/3191981/convert-sorted-list-to-binary-search-tree-with-step-by-step-explanation/?languageTags=python3)