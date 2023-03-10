---
title: Longest Substring Without Repeating Characters
author: icyou
date: 2023-03-09 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Longest Substring Without Repeating Characters
주어진 문자열에서 문자가 겹치지 않는 가장 긴 부분 문자열을 구하는 문제입니다.

```
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        char_set = set()
        max_len, start = 0, 0
        for i, c in enumerate(s):
            while c in char_set:
                char_set.remove(s[start])
                start += 1
            char_set.add(c)
            max_len = max(max_len, i - start + 1)
        return max_len
```
solution의 풀이입니다. dp 문제 같은 느낌은 났는데, 아직 갈 길이 멉니다.  
s 문자열을 순회하면서 c 문자가 char_set에 있어서 부분 문자열과 겹치게 되는 경우, 지금까지 나온 문자들을 차례대로 지웁니다. 이 아이디어는 생각해냈는데, dictionary 자료구조를 활용하려고 해서 해결하지 못했습니다.  
이후, 최댓값을 반환합니다.  
dictionary 뿐만 아니라 set도 잘 써먹어야겠습니다.  



<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/longest-substring-without-repeating-characters/solutions/3160192/python-simple-solution-efficient-solution/](https://leetcode.com/problems/longest-substring-without-repeating-characters/solutions/3160192/python-simple-solution-efficient-solution/)