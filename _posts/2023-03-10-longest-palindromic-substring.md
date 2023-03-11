---
title: Longest Palindromic Substring
author: icyou
date: 2023-03-10 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Longest Palindromic Substring
주어진 문자열에서 가장 긴 부분 palindrome 문자열을 구하는 문제입니다.

```
class Solution:
    def longestPalindrome(self, s: str) -> str:
        n = len(s)
        if n < 2:
            return s
        start, max_len = 0, 1
        for i in range(n):
            odd = s[i - max_len - 1: i + 1]
            even = s[i - max_len: i + 1]
            if i - max_len - 1 >= 0 and odd == odd[::-1]:
                start = i - max_len - 1
                max_len += 2
            if i - max_len >= 0 and even == even[::-1]:
                start = i - max_len
                max_len += 1
        return s[start: start + max_len]
```
solution의 풀이입니다.  
아이디어가 전혀 떠오르지 않았습니다.  
palindrome의 짝수일 때와 홀수일 때 경우가 달라지는데, 짝수일 때의 변수와 홀수일 때의 변수를 따로 둘 생각을 하지 못했습니다.  
odd, even 변수는 홀수일 때의 최댓값, 짝수일 때의 최댓값을 구하기 위한 변수가 아니라 max1, max2 변수라고 생각하시는 것이 이해하기에 더 편합니다. 왜냐하면 max_len = 1일 때, odd = s\[0:1\]이므로 2글자이기 때문입니다. odd와 even은 even == even\[::-1\]을 만족할 때마다 짝수 홀수가 바뀌게 됩니다.  
for 문을 한 번 돌면서 palindrom을 만족하는 경우, odd == odd\[::-1\]일 때는 양 옆의 길이가 늘어나서 더 큰 palindrome을 만족하는지 검사하고, even == even\[::-1\]일 때는 짝수, 홀수에 대해 전부 만족하는지 검사하기 위해, start를 그대로 둡니다.  
반복문을 한 번만 돌기 때문에 O(n)이고 성능 면에서 다른 풀이보다 월등합니다.  




<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/longest-palindromic-substring/solutions/3160241/python-simple-solution/](https://leetcode.com/problems/longest-palindromic-substring/solutions/3160241/python-simple-solution/)