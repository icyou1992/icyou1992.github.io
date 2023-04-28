---
title: License Key Formatting
author: icyou
date: 2023-04-28 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### License Key Formatting
주어진 문자열 s를 k 길이마다 -로 연결하는 새로운 형태의 문자열을 만드는 문제입니다. 단, 첫번째 길이만 k 이하의 길이가 될 수 있습니다.

```
class Solution:
    def licenseKeyFormatting(self, s: str, k: int) -> str:
        r, key = "", s.replace("-", "").upper()[::-1]
        for i in range(0, len(key), k):
            r += "-" + key[i:i + k]
        return r[:0:-1]
```
첫번째 길이만 k 이하가 될 수 있으므로 문자열을 뒤집어서 일정한 간격으로 자른 문자열을 다시 뒤집으면 처음만 길이가 k 이하인 일정한 간격의 문자열을 얻을 수 있습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/license-key-formatting/submissions/941064711/](https://leetcode.com/problems/license-key-formatting/submissions/941064711/)