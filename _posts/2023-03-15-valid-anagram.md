---
title: Valid Anagram
author: icyou
date: 2023-03-14 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Valid Anagram
주어진 두 문자열이 anagram인지를 판별하는 문제입니다.

```
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        repo, a = [0] * 26, ord('a')
        for ss in s:
            repo[ord(ss) - a] += 1
        for tt in t:
            repo[ord(tt) - a] -= 1  
        return True if repo == [0]*26 else False
```
```
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        repo = {}
        for ss in s:
            if ss in repo.keys():
                repo[ss] += 1
            else:
                repo[ss] = 1
        for tt in t:
            if tt in repo.keys():
                repo[tt] -= 1
            else:
                return False
        for k in repo.keys():
            if repo[k] != 0:
                return False
        return True
```
처음은 두번째 풀이처럼 dictionary를 이용하려 했지만,
if ss in repo.keys() 조건문을 써야하는데, 이는 문자열이 길어서 repo가 점점 늘어나게 되는 경우 비효율적일 수 있다고 생각했습니다.  
그래서, 소문자는 26자가 전부이니 이를 index로 활용하는 radix 방식을 활용한다면 성능을 개선할 수 있다고 생각했습니다.  
실제로 전자가 후자보다 성능이 좋습니다.  

```
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return sorted(s) == sorted(t)
```
solutions의 풀이입니다.  
깔끔하게 한 줄로 풀 수는 있지만, 성능 측면에서는 첫 번째 풀이가 좋습니다.

<br/><br/><br/><br/>
참고 
-[https://leetcode.com/problems/valid-anagram/submissions/915565271/](https://leetcode.com/problems/valid-anagram/submissions/915565271/)
- [https://leetcode.com/problems/valid-anagram/submissions/915567335/](https://leetcode.com/problems/valid-anagram/submissions/915567335/)
- [https://leetcode.com/problems/valid-anagram/submissions/915567929/](https://leetcode.com/problems/valid-anagram/submissions/915567929/)