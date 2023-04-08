---
title: Implement Queue using Stacks
author: icyou
date: 2023-03-28 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Implement Queue using Stacks
두 개의 stack을 이용하여 queue를 구현하는 문제입니다.

```
class MyQueue:

    def __init__(self):
        self.stack1 = []
        self.stack2 = []

    def push(self, x: int) -> None:
        self.stack1.append(x)
        self.stack2.clear()
        for i in range(len(self.stack1) - 1, -1, -1):
            self.stack2.append(self.stack1[i])

    def pop(self) -> int:
        n = self.stack1[0]
        self.stack2.clear()
        for i in range(len(self.stack1) - 1, 0, -1):
            self.stack2.append(self.stack1[i])
        self.stack1 = self.stack1[1:]
        return n

    def peek(self) -> int:
        return self.stack1[0]

    def empty(self) -> bool:
        return False if self.stack1 else True
```
이전에 풀었던 문제의 반대 유형입니다.  
이전 풀이와 비슷하게 풀었습니다.



<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/implement-queue-using-stacks/submissions/923443463/](https://leetcode.com/problems/implement-queue-using-stacks/submissions/923443463/)