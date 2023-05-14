---
title: Reverse String II
author: icyou
date: 2023-05-12 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Reverse String II
문자열 s와 숫자 k가 주어졌을 때, k번씩 건너뛰면서 첫번째 문자열은 뒤집고 다음 문자열은 뒤집지 않는 방식으로 끝까지 구한 문자열을 구하는 문제입니다.

```
class Solution:
    def reverseStr(self, s: str, k: int) -> str:
        s1 = ""
        for i in range(0, len(s), k):
            s1 += s[i:i + k][::-1] if i // k % 2 == 0 else s[i:i + k]
        return s1
```
for 문을 돌면서 번갈아서 뒤집고 뒤집지 않은 문자열들을 전부 더합니다.  
여기서 ::-1 연산에서 뒤집는 연산이 먼저 실행되므로 s\[i:i + k\]\[::-1\]로 두번에 나눠서 문자열을 뒤집어야만 원하는 위치의 문자열을 뒤집을 수 있습니다.
```
class Solution:
    def reverseStr(self, s: str, k: int) -> str:
        return ''.join([ s[i:i + k][::-1] if i // k % 2 == 0 else s[i:i + k] for i in range(0, len(s), k) ])
```
고민해서 한 줄로 줄일 수 있었습니다.  


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/reverse-string-ii/submissions/950199373/](https://leetcode.com/problems/reverse-string-ii/submissions/950199373/)