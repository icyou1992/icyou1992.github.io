---
title: Add Two Numbers
author: icyou
date: 2023-03-08 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Add Two Numbers
두 ListNode의 덧셈의 결과를 ListNode로 반환하는데, 이 ListNode는 한 자리씩만을 노드로 가지고 있습니다.

```
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        h1 = h2 = l3 = ListNode(0)
        while l1 and l2:
            l3.next = ListNode(l1.val + l2.val)
            l1 = l1.next
            l2 = l2.next
            l3 = l3.next
        while l1:
            l3.next = ListNode(l1.val)
            l1 = l1.next
            l3 = l3.next
        while l2:
            l3.next = ListNode(l2.val)
            l2 = l2.next
            l3 = l3.next
        while h2:
            if h2.val > 9:
                h2.val -= 10
                if h2.next:
                    h2.next.val += 1
                else:
                    h2.next = ListNode(1)
            h2 = h2.next
        return h1.next
```
두 ListNode를 돌면서 겹치는 부분은 덧셈을 하고 남는 부분은 그대로 잇는 새로운 ListNode를 만듭니다.  
만든 ListNode는 각 노드의 val이 10이 넘는 경우가 존재하므로, 10이 넘을 경우는 10을 빼고 다음 노드의 val에 1을 더해줍니다.

```
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        carry = 0
        res = n = ListNode(0)
        while l1 or l2 or carry:
            if l1:
                carry += l1.val
                l1 = l1.next
            if l2:
                carry += l2.val
                l2 = l2.next
            carry, val = divmod(carry, 10)
            n.next = n = ListNode(val)
        return res.next
```
덧셈의 결괏값을 저장하는 carry라는 변수가 존재하고 이를 10으로 나누면서 val 값을 ListNode로 만듭니다.  
carry는 l1.val과 l2.val을 더하면서 10이 넘을 경우 1을 가지고 있기 때문에, 다음 덧셈에 활용됩니다.  
n.next = n = ListNode(val)을 통해 반복문을 돌면서 노드를 할당해줄 수 있다는 tip도 얻어갑니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/add-two-numbers/submissions/911469783/](https://leetcode.com/problems/add-two-numbers/submissions/911469783/)
- [https://leetcode.com/problems/add-two-numbers/solutions/3238219/simplest-python-solution/](https://leetcode.com/problems/add-two-numbers/solutions/3238219/simplest-python-solution/)