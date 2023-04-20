---
title: Convert a Number to Hexadecimal
author: icyou
date: 2023-04-20 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Convert a Number to Hexadecimal
주어진 수를 16진법으로 바꿔서 출력하는 문제입니다. 음수일 경우 보수를 출력합니다.

```
class Solution:
    def toHex(self, num: int) -> str:
        return "%x" % num if num >= 0 else "%x" % (num + 2**32)
```
음수일 경우 보수 처리를 해야하므로 2*32를 더해줍니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/convert-a-number-to-hexadecimal/submissions/936830881/](https://leetcode.com/problems/convert-a-number-to-hexadecimal/submissions/936830881/)