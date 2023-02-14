---
title: Remove Duplicates from Sorted List
author: icyou
date: 2023-02-14 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm]
pin: true
math: true
---

## Leetcode Problem

### Remove Duplicates from Sorted List
정렬된 linked list가 주어졌을 때, 중복된 수들을 제거한 linked list를 구하는 문제입니다.

```
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        h = head
        while head:
            while head.next and head.val == head.next.val:
                head.next = head.next.next
            head = head.next
        return h
```
linked list는 어차피 정렬되어 있기 때문에, 중복된 수들은 모여있습니다. 따라서, 중복된 수들 중 첫번째 수의 next를 다음에 이어지는 다른 수와 연결되면 중복된 수들이 제거된 linked list를 구할 수 있습니다.

<br/><br/>
```
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        current = head
        while current and current.next: 
            if current.val == current.next.val:
                current.next = current.next.next
            else:
                current = current.next
        return head
```
solution에서 본 풀이입니다.  
logic은 같지만 좀 더 깔끔해서 가독성이 좋습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/remove-duplicates-from-sorted-list/submissions/897812662/](https://leetcode.com/problems/remove-duplicates-from-sorted-list/submissions/897812662/)