---
title: Convert Sorted Array to Binary Search Tree
author: icyou
date: 2023-02-15 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Convert Sorted Array to Binary Search Tree
주어진 tree에 대해서 inorder로 순회한 결과를 배열에 저장하는 문제입니다.  

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        arr = []
        def inorder(node: Optional[TreeNode], arr: List[int]):
            if node and node.left:
                inorder(node.left, arr)
            if node:
                arr.append(node.val)
            if node and node.right:
                inorder(node.right, arr)
            return arr
        return inorder(root, arr)
```

traversal의 종류는 세 가지가 있습니다.  
preorder는 노드, 노드 왼쪽, 노드 오른쪽 순으로 순회합니다.  
inorder는 노드 왼쪽, 노드, 노드 오른쪽 순으로 순회합니다.  
postorder는 노드 왼쪽, 노드 오른쪽, 노드 순으로 순회합니다.  

<br/><br/>
```
def preorder(root):
  return [root.val] + preorder(root.left) + preorder(root.right) if root else []

def inorder(root):
  return  inorder(root.left) + [root.val] + inorder(root.right) if root else []

def postorder(root):
  return  postorder(root.left) + postorder(root.right) + [root.val] if root else []

```

멋진 solution입니다.  

![Desktop View](/assets/img/posts/20230215/traversal.png){: .w-70 .normal}


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/binary-tree-inorder-traversal/submissions/898419014/](https://leetcode.com/problems/binary-tree-inorder-traversal/submissions/898419014/)
- [https://leetcode.com/problems/binary-tree-inorder-traversal/solutions/283746/all-dfs-traversals-preorder-inorder-postorder-in-python-in-1-line/?languageTags=python3](https://leetcode.com/problems/binary-tree-inorder-traversal/solutions/283746/all-dfs-traversals-preorder-inorder-postorder-in-python-in-1-line/?languageTags=python3)
