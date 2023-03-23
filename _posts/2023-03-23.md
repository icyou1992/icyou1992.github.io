---
title: Remove Linked List Elements
author: icyou
date: 2023-03-22 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Remove Linked List Elements
Linked List에서 주어진 수를 제거한 Linked List를 반환하는 문제입니다.

```
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        node = ListNode(0, head)
        while node:
            if node.next and node.next.val == val:
                node.next = node.next.next
            else:
                node = node.next
        return head
```
처음에는 이렇게 풀려고 했는데, ListNode=\[7,7,7,7\], val=7인 경우에서 오류가 생겼습니다.  
이 오류가 왜 생기는지 한참 고민했는데, 문제는 첫번째 node의 값이 val과 일치할 경우 head는 그대로 있고, node의 next만 바뀌기 때문에 head ListNode가 그대로 유지되는 것이 문제였습니다.

```
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        node = head
        while node:
            if node.next and node.next.val == val:
                node.next = node.next.next
            else:
                node = node.next
        return head.next if head and head.val == val else head
```
그래서 결국 node = head로 설정한 후에 return 에서 추가 조건을 주는 식으로 해결했습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/remove-linked-list-elements/submissions/920074263/](https://leetcode.com/problems/remove-linked-list-elements/submissions/920074263/)