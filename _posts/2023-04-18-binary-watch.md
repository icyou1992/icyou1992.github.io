---
title: Binary Watch
author: icyou
date: 2023-04-16 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Binary Watch
문자열 s와 그 s에 문자 하나를 추가에 순서를 뒤섞은 문자열 t가 주어졌을 때, 어떤 문자가 추가되었는지를 구하는 문제입니다.

```
from collections import Counter
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        return ''.join((Counter(t) - Counter(s)).keys())
```
두 문자열의 counter에서 뺄셈을 하면 추가된 나머지 문자를 구할 수 있습니다.

```
class Solution(object):
    def findTheDifference(self, s, t):
        for i in t:
            if s.count(i) != t.count(i):
                return i
```
solution의 풀이입니다.  
count 함수를 사용하여 간편하게 구할 수도 있습니다. 하지만 성능은 $$O(n^2)$$로 좋지 않지만, 왜인지 모르게 속도는 더 빠르게 나왔습니다. 추가된 문자열의 index가 대부분이 앞에 위치할 경우 더 빠를 수도 있을 것 같습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/find-the-difference/submissions/934647812/](https://leetcode.com/problems/find-the-difference/submissions/934647812/)
- [https://leetcode.com/problems/find-the-difference/solutions/3119345/very-simple-approach-in-python-beats-99-9-python-3-liner-sol/?languageTags=python3](https://leetcode.com/problems/find-the-difference/solutions/3119345/very-simple-approach-in-python-beats-99-9-python-3-liner-sol/?languageTags=python3)