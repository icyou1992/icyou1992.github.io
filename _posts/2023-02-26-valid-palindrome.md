---
title: Valid Palindrome
author: icyou
date: 2023-02-23 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Valid Palindrome
주어진 문자열을 공백, 특수문자를 제거하고 전부 소문자 형식으로 만들었을 때 palindrom인지를 판별하는 문제입니다.

```
import re
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = re.sub(r"[^a-zA-Z0-9]", "", s).lower()
        return s == s[::-1]
```
문자열에서 공백을 제거하고 숫자와 문자만 남긴다 해서 정규표현 함수를 찾아보고 활용했습니다.

```
class Solution:
    def isPalindrome(self, s: str) -> bool:
        raw = ''.join(ch for ch in s if ch.isalnum()).lower()
        return raw[::-1] == raw
```
정규표현 함수 필요 없이 더 간단하게 구할 수 있을 줄은 몰랐습니다. ㅋㅋ
join 함수로 문자와 숫자만을 가져온 후에 소문자로 만들어서 문자열을 반환합니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/valid-palindrome/submissions/905266361/](https://leetcode.com/problems/valid-palindrome/submissions/905266361/)