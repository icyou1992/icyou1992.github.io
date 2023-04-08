---
title: Excel Sheet Column Number
author: icyou
date: 2023-03-04 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Excel Sheet Column Number
Excel Column이 주어졌을 때, 몇 번째 줄인지를 구하는 구하는 문제입니다.  

```
class Solution:
    def titleToNumber(self, columnTitle: str) -> int:
        rs, steps = 0, 1
        for s in columnTitle[::-1]:
            rs += (ord(s) - 64) * steps
            steps *= 26
        return rs
```
이전에 풀었던 문제가 반대로 나왔습니다.  
문자열을 뒤집어서 차례로 받아 숫자로 바꾼 후 자릿수를 곱해서 더해주었습니다.  

```
class Solution:
    def titleToNumber(self, columnTitle: str) -> int:
        if columnTitle == "":
            return 0
        return (ord(columnTitle[-1]) - 64) + 26 * self.titleToNumber(columnTitle[:-1])
```
재귀 방식으로도 풀었습니다.  
성능 측면에서는 반복문이 속도가 훨씬 빠릅니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/excel-sheet-column-number/submissions/908746926/](https://leetcode.com/problems/excel-sheet-column-number/submissions/908746926/)
- [https://leetcode.com/problems/excel-sheet-column-number/submissions/908752565/](https://leetcode.com/problems/excel-sheet-column-number/submissions/908752565/)