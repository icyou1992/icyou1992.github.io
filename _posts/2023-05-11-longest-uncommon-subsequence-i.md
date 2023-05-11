---
title: Longest Uncommon Subsequence I
author: icyou
date: 2023-05-11 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Longest Uncommon Subsequence I
a와 b 문자열이 주어졌을 때, 두 문자열이 서로 일치하지 않는 최대 길이를 구하는 문제입니다.

```
class Solution:
    def findLUSlength(self, a: str, b: str) -> int:
        return -1 if a == b else max(len(a), len(b))
```
문제가 잘 이해되지 않아서 testcase를 여러개 추가해보면서 문제의 의도를 파악했습니다.  
"aba", "ababa" 로 testcase를 넣어줬는데도, "aba"를 "ababa"의 부분수열로 인식하지 않고 답이 b의 길이인 5로 나와서 같을 경우만을 제외하고는 최대 길이를 반환하도록 했더니 맞았습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/longest-uncommon-subsequence-i/submissions/948250015/](https://leetcode.com/problems/longest-uncommon-subsequence-i/submissions/948250015/)