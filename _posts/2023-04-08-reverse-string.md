---
title: Reverse String
author: icyou
date: 2023-04-08 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Reverse String
주어진 s 배열의 순서를 in-place 방식으로 거꾸로 뒤집는 문제입니다.

```
class Solution:
    def reverseString(self, s: List[str]) -> None:
        s.reverse()
```
python 내장함수로 간단히 해결할 수 있습니다.

```
class Solution:
    def reverseString(self, s: List[str]) -> None: 
        while low < high:
            s[low], s[high] = s[high], s[low]
            low, high = low + 1, high - 1 
```
내장함수를 쓰지 않을 경우, 이렇게 첫번째와 마지막 원소부터 차례대로 바꿔주면서 순서를 뒤집을 수 있습니다.  
전에 배웠던 `,`를 활용하여 swap을 위한 추가 변수 없이 원소를 교환할 수 있습니다.  


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/reverse-string/submissions/929897692/](https://leetcode.com/problems/reverse-string/submissions/929897692/)