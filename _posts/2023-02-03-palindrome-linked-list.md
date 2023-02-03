---
title: Palindrome Linked List
author: icyou
date: 2023-02-03 00:00:00 +0900
categories: [Algorithm]
tags: [Algorithm]
pin: true
math: true
---

## Leetcode Problem

### Palindrome Linked List

Linked List가 주어졌을 때, 해당 Linked List가 Palindrome인지를 판별하는 문제

```
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        stack = []

        stack.append(head.val)
        while(head.next):
            head = head.next
            stack.append(head.val)

        return True if stack[:len(stack)//2 if len(stack) % 2 == 0 else len(stack)//2 + 1] == list(reversed(stack[len(stack)//2:])) else False           
```

내 풀이는 linked list를 array로 받아서 반을 잘라서 같은 지를 비교한다.

leetcode의 풀이 중에는 재귀를 이용한 풀이가 배울 것이 있어 적어놓는다.

```
def isPalindrome(self, head: ListNode) -> bool:

    self.front_pointer = head

    def recursively_check(current_node=head):
        if current_node is not None:
            if not recursively_check(current_node.next):
                return False
            if self.front_pointer.val != current_node.val:
                return False
            self.front_pointer = self.front_pointer.next
        return True

    return recursively_check()
```

이 풀이는 
```
function print_values_in_reverse(ListNode head)
    if head is NOT null
        print_values_in_reverse(head.next)
        print head.val
```
이 재귀함수가 노드를 역순으로 출력한다는 점에서 풀이를 착안한다.
재귀를 통해 linked list의 끝으로 가서 첫번째 노드의 값과 마지막 노드의 값을 비교한다. 같지 않을 경우 false, 같을 경우 continue -> 맨 첫번째 재귀가 끝나고 두번째 노드의 값과 끝에서 두번째 노드의 값을 비교한다. -> 이런 식으로 재귀가 하나씩 풀리며 모두 풀리는 동안 false가 return되지 않을 경우 true를 return한다.