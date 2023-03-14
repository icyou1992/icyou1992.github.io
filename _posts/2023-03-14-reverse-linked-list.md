---
title: Reverse Linked List
author: icyou
date: 2023-03-14 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Reverse Linked List
주어진 Linked List를 역순으로 하는 Linked List를 구하는 문제입니다.

```
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        n = None
        while head:
            tmp = ListNode(val=head.val, next=n)
            n = tmp
            head = head.next
        return n

```
ListNode를 순회하면서 head의 값을 가졌지만, next는 반대를 향하는 tmp 노드를 만들고 그것을 n 노드와 이어줍니다.  
마지막까지 순회한 후 n을 return 합니다. 

```
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev = None
        while head:
            next = head.next
            head.next = prev
            prev = head
            head = next
        return prev
```
swap 처럼 임시 변수 하나만을 사용하고 head의 pointer를 차례로 방향만 이전 노드로 바꾸는 방식을 고민했습니다.  
결론적으로는 다음 노드를 저장할 변수 하나와 pointer의 방향을 바꾸기 위해 이전 노드를 저장할 변수가 하나, 해서 두 개의 변수가 필요한 것 같습니다.  


<br/><br/><br/><br/>
참고 
-[https://leetcode.com/problems/reverse-linked-list/submissions/914992460/](https://leetcode.com/problems/reverse-linked-list/submissions/914992460/)
- [https://leetcode.com/problems/reverse-linked-list/submissions/915019633/](https://leetcode.com/problems/reverse-linked-list/submissions/915019633/)