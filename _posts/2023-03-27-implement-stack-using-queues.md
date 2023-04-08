---
title: Implement Stack using Queues
author: icyou
date: 2023-03-27 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Implement Stack using Queues
두 개의 queue를 이용하여 stack을 구현하는 문제입니다.

```
class MyStack:

    def __init__(self):
        self.q1 = deque()
        self.q2 = deque()

    def push(self, x: int) -> None:
        self.q2.clear()
        self.q1.append(x)
        for i in range(len(self.q1) - 1,-1,-1):
            self.q2.append(self.q1[i])

    def pop(self) -> int:
        num = self.q2.popleft()
        self.q1.clear()
        for i in range(len(self.q2) - 1,-1,-1):
            self.q1.append(self.q2[i])
        return num

    def top(self) -> int:
        return self.q2[0]

    def empty(self) -> bool:
        if len(self.q1) == 0:
            return True
        return False
```
solutions의 풀이입니다.  
문제를 잘못 읽어서 제 풀이는 쓸모가 없습니다.  
q1은 queue고 q2는 역순으로 된 queue입니다. push일 경우 q2, 역순 queue에 원소를 넣을 경우 나머지 뒤의 원소들을 재배치해야하므로 시간이 걸리기 때문에 q1의 마지막에 원소를 넣습니다.  
반면 pop의 경우, q2, 역순 queue를 이용하면 원소 전체를 순회할 필요없이 0번 원소를 반환하면 되므로 q2를 이용합니다.  



<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/implement-stack-using-queues/solutions/3024087/python-beats-80-original-idea/?languageTags=python3](https://leetcode.com/problems/implement-stack-using-queues/solutions/3024087/python-beats-80-original-idea/?languageTags=python3)