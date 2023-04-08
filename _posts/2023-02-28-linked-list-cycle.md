---
title: Linked List Cycle
author: icyou
date: 2023-02-28 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Linked List Cycle
주어진 linked list가 cycle이 있는지를 판별하는 문제입니다.

```
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        while head:
            if head.val == 111111:
                return True
            head.val = 111111
            head = head.next
        return False
```
노드를 차례대로 방문하면서 value값을 범위 밖의 111111로 설정해주고 111111 값을 만나면 방문한 노드로 다시 돌아온 것이므로 true 아니라면 false를 반환합니다.

```
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        slow = fast = head
        cnt = 0
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                return True
        return False
```
두 pointer가 방문하는 속도를 다르게 해서 cycle을 판정하는 방법입니다. cycle이 있을 경우 두 pointer가 방문할 노드는 무한합니다. 즉 가야할 길은 무한히 돌고 돌기 때문에 두 pointer는 cycle 안에서 만날 수밖에 없다는 점을 이용한 풀이입니다.  
이 풀이는 노드의 val값을 건드리지 않기 때문에 좀 더 세련된 풀이이지만, cycle이 클 경우 두 pointer가 만나는 시간이 길어질 수 있습니다. 즉 성능이 좀 낮을 수 있습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/linked-list-cycle/submissions/906412387/](https://leetcode.com/problems/linked-list-cycle/submissions/906412387/)
- [https://leetcode.com/problems/linked-list-cycle/solutions/3198356/python-clean-simple-floyd-s-cycle-detaction-using-2-pointer-slow-fast/?languageTags=python3](https://leetcode.com/problems/linked-list-cycle/solutions/3198356/python-clean-simple-floyd-s-cycle-detaction-using-2-pointer-slow-fast/?languageTags=python3)