---
title: Implement Rand10() Using Rand7()
author: icyou
date: 2023-03-30 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Implement Rand10() Using Rand7()
Rand7() 함수를 이용해서 Rand10()을 구현하는 문제입니다.  
동일한 확률로 각 정수가 출력되어야 합니다.  

```
class Solution:
    def rand10(self):
        """
        :rtype: int
        """
        return rand7() + rand7() % 3
```
`uniform`이라는 단어를 알지 못해서 각 1부터 10까지 나올 확률이 동일해야 한다는 것을 파악하지 못했습니다.  

```
class Solution:
    def rand10(self):
        """
        :rtype: int
        """
        res = 0
        for i in range(10):
            res += rand7()
        return res % 10 + 1
```
이렇게 rand7 함수를 10번 호출해서 10의 나머지를 구한다면 동일한 확률로 1부터 10까지의 정수를 얻을 수 있습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/implement-rand10-using-rand7/submissions/924686134/](https://leetcode.com/problems/implement-rand10-using-rand7/submissions/924686134/)