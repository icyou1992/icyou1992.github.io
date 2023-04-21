---
title: First Unique Character in a String
author: icyou
date: 2023-04-12 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### First Unique Character in a String
문자열 s가 주어졌을 때, s 내에서 유일한 각각의 문자들 중, 첫 번째 문자의 index를 구하는 문제입니다.

```
from collections import Counter
class Solution:
    def firstUniqChar(self, s: str) -> int:
        m = Counter(s)
        for i in range(len(s)):
            if m[s[i]] == 1:
                return i
        return -1
```
각 원소와 원소의 개수를 map 형태로 변환하는 counter 함수를 이용하여 풀었습니다.  
counter의 value 값이 1일 경우 유일한 문자이므로 m의 key값인 s를 순회하면서 value가 1일 경우 해당 index를 반환합니다.  

```
class Solution:
    def firstUniqChar(self, s: str) -> int:
        freq = {}
        for c in s:
            freq[c] = freq.get(c, 0) + 1
        for i in range(len(s)):
            if freq[s[i]] == 1:
                return i
        return -1
```
dictionary 자료형의 get이라는 함수를 이용하면 counter를 쉽게 구현할 수 있습니다. 


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/first-unique-character-in-a-string/submissions/933425874/](https://leetcode.com/problems/first-unique-character-in-a-string/submissions/933425874/)
- [https://leetcode.com/problems/first-unique-character-in-a-string/solutions/3254711/387-space-93-87-solution-with-step-by-step-explanation/?languageTags=python3](https://leetcode.com/problems/first-unique-character-in-a-string/solutions/3254711/387-space-93-87-solution-with-step-by-step-explanation/?languageTags=python3)