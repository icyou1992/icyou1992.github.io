---
title: Word Pattern
author: icyou
date: 2023-04-02 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Word Pattern
주어진 문자열 s의 형식이 pattern 문자열 형식과 일치하는지를 판별하는 문제입니다.

```
class Solution:
    def wordPattern(self, pattern: str, s: str) -> bool:
        d, arr = {}, s.split()
        if len(arr) != len(pattern):
            return False
        for i in range(len(pattern)):
            if arr[i] in d.keys():
                if d[arr[i]] != pattern[i]:
                    return False
            else:    
                d[arr[i]] = pattern[i]
        return True if len(d) == len(set(pattern)) else False
```
먼저, s의 단어들과 pattern 문자열의 문자가 1:1 대응이므로 서로 길이가 다르면, false를 반환합니다.  
이후 pattern 문자열의 문자들을 dictionary 자료형으로 하나씩 가져오면서 s내의 단어들과 연결시킵니다. 이렇게 되면 1:N으로 연결되는 경우 false를 return 합니다.  
마지막으로 N:1인 경우에 대해, d의 길이와 pattern을 set로 한 자료의 길이를 비교하여 일치하지 않는 경우 false를 반환하여 모든 경우에 대해 1:1이 되도록 처리합니다.  


```
class Solution:
    def wordPattern(self, pattern: str, s: str) -> bool:
        words = s.split() 
        if len(pattern) != len(words):
            return False
        
        pattern_to_word = {} 
        word_to_pattern = {} 
        
        for i in range(len(pattern)):
            p = pattern[i]
            w = words[i]
            if p in pattern_to_word and pattern_to_word[p] != w: 
                return False
            if w in word_to_pattern and word_to_pattern[w] != p: 
                return False
            pattern_to_word[p] = w 
            word_to_pattern[w] = p 
            
        return True 
```
solution의 풀이입니다.  
마지막 N:1의 경우를 dictionary 자료형 하나를 더 만들어 반대로 1:N으로 연결시키는 방식으로 문제를 해결합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/word-pattern/submissions/926362126/](https://leetcode.com/problems/word-pattern/submissions/926362126/)
- [https://leetcode.com/problems/word-pattern/solutions/3236534/290-space-97-92-solution-with-step-by-step-explanation/?languageTags=python](https://leetcode.com/problems/word-pattern/solutions/3236534/290-space-97-92-solution-with-step-by-step-explanation/?languageTags=python)