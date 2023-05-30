---
title: Design HashSet
author: icyou
date: 2023-05-27 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Design HashSet
hashset을 사용하여 add, remove, contains 함수를 구현하는 문제입니다.

```
class MyHashSet:
    def __init__(self):
        self.hash = {}
    def add(self, key: int) -> None:
        self.hash[key] = 1
    def remove(self, key: int) -> None:
        if key in self.hash:
            del self.hash[key]
    def contains(self, key: int) -> bool:
        return True if key in self.hash else False
```  
python의 dictionary와 hash가 같으므로 dictionary를 활용했습니다.
 
<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/design-hashset/submissions/960289432/](https://leetcode.com/problems/design-hashset/submissions/960289432/)