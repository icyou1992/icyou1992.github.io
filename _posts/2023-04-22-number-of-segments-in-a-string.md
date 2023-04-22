---
title: Number of Segments in a String
author: icyou
date: 2023-04-21 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Number of Segments in a String
문자열 s가 주어졌을 때, 띄어쓰기를 기준으로 나뉘어진 문자열 조각의 개수를 구하는 문제입니다.

```
class Solution:
    def countSegments(self, s: str) -> int:
        return len(s.split())
```
split 함수를 통해 간단하게 조각의 개수를 구할 수 있었습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/number-of-segments-in-a-string/submissions/937762572/](https://leetcode.com/problems/number-of-segments-in-a-string/submissions/937762572/)