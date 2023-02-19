---
title: Convert Sorted Array to Binary Search Tree
author: icyou
date: 2023-02-19 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm]
pin: true
math: true
---

## Leetcode Problem

### Convert Sorted Array to Binary Search Tree
오름차순으로 정렬된 배열이 주어졌을 때, 이를 `height balanced binary search tree`로 바꾸는 문제입니다.

```
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        root = head = TreeNode()
        def makeTree(head: Optional[TreeNode], low: int, high: int):
            mid = (low + high)//2
            head.val = nums[mid]
            if low <= mid-1:
                head.left = TreeNode()
                makeTree(head.left, low, mid-1)
            if mid+1 <= high:
                head.right = TreeNode()
                makeTree(head.right, mid+1, high)
        makeTree(head, 0, len(nums)-1)          
        return root
```
이 문제를 풀기 위해 다음날까지 고민하여 결국 풀어냈습니다.  
처음 헷갈렸던 부분은, `Search Insert Position` 문제에서 헷갈렸던 것처럼 아래처럼 중간값을 기준으로 문제를 풀려고 했던 점이었습니다.
```
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        diff = len(nums)//2
        root = head = TreeNode(nums[diff])

        def makeTree(head: Optional[TreeNode], idx: int, diff: int):
            if head:
                head.val = nums[idx]
            if diff > 0:
                li = idx - 1 - diff
                ri = idx + 1 + diff
                print(li, ri)
                if li > 0: 
                    head.left = TreeNode(nums[li])
                    print(li, head.left)
                if ri < len(nums):
                    head.right = TreeNode(nums[ri])
                    print(ri, head.right)
                makeTree(head.left, li, diff//2), makeTree(head.right, ri, diff//2)
        makeTree(head, diff, diff//2)
        return root

```
이렇게 해결하려고 시도할 경우, 이전 문제처럼 중간값의 index를 계산하는 과정에서 배열의 일부가 누락되거나 겹쳐지는 문제점이 발생합니다. 이 점은 이진 탐색에서 범위의 처음과 끝을 매개변수로 넘기는 방식으로 해결했던 것을 떠올렸지만 아래 풀이에서 다른 문제가 발생했습니다.  
```
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        root = head = TreeNode()
        def makeTree(head: Optional[TreeNode], low: int, high: int):
            if low < high:
                mid = (low + high)//2
                print(low, high, mid)
                head.val = nums[mid]
                if low != high:
                    head.left = TreeNode()
                    head.right = TreeNode()
                    makeTree(head.left, low, mid-1)
                    makeTree(head.right, mid+1, high)
        makeTree(head, 0, len(nums)-1)          
        return root
```
위의 풀이는 left와 right에 node를 만들고 다음 재귀 함수에서 해당 값에 대한 조건을 검사해서 값을 넣기 때문에 실제값이 들어가지 않더라도 0으로 default 값이 입력되는 문제가 있었습니다. 즉, 조건 검사 후 node를 만들어야 하는데, node를 만들고 조건을 검사하는 문제가 있었습니다. 해서 node를 만들기 전 조건 검사를 추가하여 해결할 수 있었습니다.  

<br/><br/>
```
class Solution(object):
    def sortedArrayToBST(self, nums):
        if len(nums) == 0:
            return None
        mid = len(nums)//2
        root = TreeNode(nums[mid])
        root.left = self.sortedArrayToBST(nums[:mid])
        root.right = self.sortedArrayToBST(nums[mid+1:])
        return root
```
이렇게 논리 구조를 간단히 할 수 있다니.. 갈 길이 멉니다..

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/submissions/900783331/](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/submissions/900783331/)
