---
title: Merge Two Sorted Lists
author: icyou
date: 2023-02-11 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Merge Two Sorted Lists
주어진 정렬된 두 linked list를 하나의 정렬된 linked list로 합치는 문제입니다.

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        head = ListNode()
        node = head
        while list1 is not None and list2 is not None:
            if list1.val == list2.val:
                node1 = ListNode(list1.val)
                node.next = node1
                node2 = ListNode(list2.val)
                node.next.next = node2
                node = node2

                list1 = list1.next
                list2 = list2.next
            elif list1.val < list2.val:
                node1 = ListNode(list1.val)
                node.next = node1
                node = node1
                
                list1 = list1.next
            else:
                node2 = ListNode(list2.val)
                node.next = node2
                node = node2
                list2 = list2.next
        
        while list1 is not None:
            node1 = ListNode(list1.val)
            node.next = node1
            node = node1
            list1 = list1.next

        while list2 is not None:
            node2 = ListNode(list2.val)
            node.next = node2
            node = node2
            list2 = list2.next
        
        return head.next

```
head라는 변수에 listnode를 넣어주고, 이 linked list에 node들을 추가하기 위해 node라는 변수에 head를 담습니다. 이 node라는 변수를 추가적으로 선언한 이유는 node 변수는 반복문을 돌면서 node가 가리키는 위치가 변하기 때문에, linked list의 시작점(head)을 따로 저장해두기 위함입니다.  
이후, 반복문을 돌면서 list1과 list2를 비교하며 값이 적은 node를 linked list에 추가합니다. list1이나 list2 중 하나를 전부 탐색했다면 남은 list에 대해 반복문을 돌며 남은 node를 전부 추가합니다.  
마지막으로 head.val은 주어진 배열에 들어있는 값이 아니므로 head.next를 반환합니다.  
이렇게 풀었지만, 코드가 상당히 깔끔하지 않다고 생각했습니다.

```
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        head = node = ListNode()
        while list1 and list2:
            if list1.val < list2.val:
                node.next = list1
                list1 = list1.next
            else:
                node.next = list2
                list2 = list2.next
            node = node.next
        
        if list1 or list2:
            node.next = list1 if list1 else list2
        
        return head.next
```
solution에서 본 풀이입니다.  
초기 변수에 listnode를 할당하는 부분을 좀 더 깔끔하게 처리했습니다.  
반복 연산에서 ==으로 비교하는 부분을 생략했습니다. list1.val과 list2.val이 같을 경우, 두 값을 한 번에 추가하기 때문에 연산을 한 번 줄일 수 있지만, 반복문을 돌면서 하는 비교 연산에서 ==을 불필요하게 계속 비교하는 연산이 생기므로 가독성 면에서도, 성능 면에서도 생략하는 것이 더 좋아보입니다.  
반복 연산이 끝난 후, 나머지 list에 대해 반복문을 돌 필요 없이 그대로 list를 추가하는 것이 가독성, 성능 면에서 더 좋습니다.




<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/valid-parentheses/submissions/895263983/](https://leetcode.com/problems/valid-parentheses/submissions/895263983/)