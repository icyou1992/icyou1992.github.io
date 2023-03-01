---
title: Intersection of Two Linked Lists
author: icyou
date: 2023-03-01 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Intersection of Two Linked Lists
두 linked-list가 합쳐지는 부분의 노드를 구하는 문제입니다.

```
class Solution:
    def getList(self, head: ListNode):
        return [head.val] + self.getList(head.next) if head else []
    def findNode(self, head: ListNode, val: int):
        return head if head.val == val else self.findNode(head.next, val)
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        arr1 = self.getList(headA)[::-1]
        arr2 = self.getList(headB)[::-1]
        if not headA or not headB or (arr1[0] != arr2[0]):
            return None 
        i = 0
        while i < min(len(arr1), len(arr2)):
            if arr1[i] != arr2[i]:
                break
            i += 1
        nodea = self.findNode(headA, arr1[i-1])
        nodeb = self.findNode(headB, arr2[i-1])
        while nodea != nodeb:
            nodea = nodea.next
            nodeb = nodeb.next
        return nodea
```
문제를 비효율적으로 푼 느낌입니다.  
두 linked list를 거꾸로 보면 합쳐진 노드들이 먼저 나열된 후, 분리되는 지점이 나옵니다.  
그래서 생각해낸 것이 linked list를 list로 만들고 뒤집은 후에 일치하는 부분만을 분리해 냅니다. 그리고 일치하는 부분의 끝의 값을 linked list를 순회하면서 찾아낸 후, A linked list와 B linked list의 노드 값이 일치하는 부분부터 차례대로 순회하며 노드 자체가 일치하는 노드를 찾아냅니다.  
(노드값이 일치하는 것과 노드 자체가 일치하는 것은 다릅니다.)  

```
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        lenA, lenB = 0, 0
        currA, currB = headA, headB
        while currA:
                lenA += 1
                currA = currA.next
        while currB:
                lenB += 1
                currB = currB.next
        currA, currB = headA, headB
    
        if lenA > lenB:
            for i in range(lenA - lenB):
                currA = currA.next
        elif lenB > lenA:
            for i in range(lenB - lenA):
                currB = currB.next
    
        while currA and currB:
            if currA == currB:
                return currA
            currA = currA.next
            currB = currB.next    
        return None
```
solution에서 본 풀이입니다.  
이 풀이는 문제를 거리 개념으로 접근했습니다.  
노드가 일치하는 부분부터는 끝까지의 거리가 같을 수밖에 없으므로 A linked list와 B linked list의 끝까지의 거리를 같게 하기 위해 A, B의 거리를 계산하여 길이가 더 긴 곳을 차이만큼 시작점에서 미리 옮겨줍니다. 그러면 A와 B 모두 끝까지의 거리가 같게 되어 두 노드가 일치하는 지만 비교하면 됩니다.    

```
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        pA = headA
        pB = headB
        while pA != pB:
            if not pB:
                pB = headA
            else:
                pB = pB.next
            if not pA:
                pA = headB
            else:
                pA = pA.next
        return pA
```
두 번째 풀이를 보지 않고 이 풀이부터 봐서 이해하는데 애먹었습니다..ㅋㅋ    
이 풀이도 마찬가지로 거리 개념을 이용합니다. 예를 들어 A linked list는 3짜리 거리고 B linked list는 4짜리 거리고, 두 거리는 1인 지점에서 노드가 일치한다고 가정합니다. A와 B는 0 지점에서 출발하고 1씩 이동하는데, 자신의 마지막 지점이 끝나고 상대방의 거리까지 돌고 나면 거리의 합이 같기 때문에 시작점이 일치하게 됩니다.  
A: 3+4, B: 4+3으로 7만큼 이동하고 같은 시작점에 위치하게 됩니다.  
이 때부터는 A와 B가 1 지점에서 일치하므로 8에서 pA == pB를 만족하고 return하게 됩니다. 만일 일치하는 지점이 없을 경우 둘 다 끝까지 간 후, None으로 도착하며 pA == pB를 만족하고 None을 return 합니다.  



<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/valid-palindrome/submissions/905266361/](https://leetcode.com/problems/valid-palindrome/submissions/905266361/)
- [https://leetcode.com/problems/intersection-of-two-linked-lists/solutions/3176186/solution/](https://leetcode.com/problems/intersection-of-two-linked-lists/solutions/3176186/solution/)
- [https://leetcode.com/problems/intersection-of-two-linked-lists/solutions/3200014/finding-the-intersection-of-two-linked-lists-using-two-pointers/?languageTags=python3](https://leetcode.com/problems/intersection-of-two-linked-lists/solutions/3200014/finding-the-intersection-of-two-linked-lists-using-two-pointers/?languageTags=python3)