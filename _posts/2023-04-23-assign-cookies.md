---
title: Assign Cookies
author: icyou
date: 2023-04-21 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Assign Cookies
각각의 쿠키의 양이 입력된 배열 s와 필요 쿠키 양이 입력된 아이들의 배열 g가 주어졌을 때, 주어진 쿠키들을 아이들을 최대한 만족하도록 나누는 문제입니다.

```
class Solution:
    def findContentChildren(self, g: List[int], s: List[int]) -> int:
        happy, children, cookies = 0, sorted(g), sorted(s)
        while children and cookies: 
            if cookies[-1] >= children.pop():
                cookies.pop()
                happy += 1
        return happy
```
g와 s를 정렬시킨 후 필요 쿠키 양이 큰 순서부터 아이들에게 가장 큰 쿠키부터 나눠줍니다. 이러면, 필요 쿠키 양이 많은 아이에게 순서대로 나누어주었을 때 쿠키 양이 만족되지 않는 경우 그 아이는 어떤 쿠키로도 만족되지 않으므로 skip 합니다. 이랬을 때 최대로 쿠키를 나누어줄 수 있습니다.




<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/assign-cookies/submissions/938436557/](https://leetcode.com/problems/assign-cookies/submissions/938436557/)