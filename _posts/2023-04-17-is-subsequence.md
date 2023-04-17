---
title: Is Subsequence
author: icyou
date: 2023-04-16 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Is Subsequence
문자열 s와 t가 주어졌을 때 s가 t의 subsequence인지를 판별하는 문제입니다.  
(s가 t의 subsequence이려면 s의 문자가 모두 t에 들어가있고, 순서가 일치해야 합니다.)

```
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i = -1
        for ss in s:
            j = t.find(ss, i + 1)
            if i >= j:
                return False
            i = j
        return True
```
s 문자열을 차례로 순회하면서 t에서 find 함수를 이용해 i + 1 index부터 s 의 문자를 차례로 찾습니다. s 문자를 더 이상 못 찾는 경우 False를 반환하고 다 찾는 경우 True를 반환합니다.  

```
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i, j  = 0, 0
        while i < len(s) and j < len(t):
            if s[i] == t[j]:
                i += 1
            j += 1
        return i == len(s)
```
solution에 있는 댓글의 풀이입니다.  
논리는 같지만 명확하여 가독성이 좋아보입니다. 다만, t 문자열의 끝까지 순회해야만 한다는 점에서 성능이 조금 더 떨어져보입니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/is-subsequence/submissions/935171598/](https://leetcode.com/problems/is-subsequence/submissions/935171598/)
- [https://leetcode.com/problems/is-subsequence/solutions/1811508/python-javascript-easy-solution-with-very-clear-explanation/](https://leetcode.com/problems/is-subsequence/solutions/1811508/python-javascript-easy-solution-with-very-clear-explanation/)