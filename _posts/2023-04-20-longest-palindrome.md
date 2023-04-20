---
title: Longest Palindrome
author: icyou
date: 2023-04-20 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Longest Palindrome
주어진 문자열로 만들 수 있는 palindrome 중 최대 길이를 구하는 문제입니다.

```
class Solution:
    def longestPalindrome(self, s: str) -> int:
        d, r, f = {}, 0, 0
        for c in s:
            d[c] = d.get(c, 0) + 1
        for k in d.keys():
            if d[k] % 2 == 0: 
                r += d[k]
            else:
                r += d[k] - 1
                f = 1

        return r if f == 0 else r + 1
```
palindrome을 최대 길이로 만들기 위해서는 중복되는 문자들을 최대의 짝수 개만큼 가져와 양 옆에 붙이고 홀수 개의 문자 중 하나를 가운데에 붙여야 합니다.  
따라서 get 함수를 이용해 문자열 s를 counter로 만들고 d의 key들을 순회하면서 d\[k\]가 홀수인 경우 하나를 빼고 짝수인 경우 전부 가져온 수들의 합이 최대가 됩니다.

```
def longestPalindrome_set(s):
    ss = set()
    for letter in s:
        if letter not in ss:
            ss.add(letter)
        else:
            ss.remove(letter)
    if len(ss) != 0:
        return len(s) - len(ss) + 1
    else:
        return len(s)
```
solution의 풀이입니다.  
set 함수로 모든 중복되는 문자열의 문자들을 하나씩 가지고 있습니다. s를 순회하면서 짝수 개의 문자들은 추가되고 제거되다가 결국 제거되고 홀수 개의 문자들만 남게 됩니다. 그럼 위의 논리와 마찬가지로 s의 길이에, ss는 홀수 개의 문자들을 하나씩만 가지고 있으므로 그 길이만큼만 제거하고 홀수 개의 문자들 중 하나만 가져와 가운데에 추가하면 됩니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/longest-palindrome/submissions/936839233/](https://leetcode.com/problems/longest-palindrome/submissions/936839233/)
- [https://leetcode.com/problems/longest-palindrome/solutions/813721/python-3-solution-using-set/?languageTags=python3](https://leetcode.com/problems/longest-palindrome/solutions/813721/python-3-solution-using-set/?languageTags=python3)