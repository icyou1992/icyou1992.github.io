---
title: Excel Sheet Column Title
author: icyou
date: 2023-03-02 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Excel Sheet Column Title
columnNumber가 주어졌을 때, Excel의 column 이름을 구하는 문제입니다.

```
class Solution:
    def convertToTitle(self, columnNumber: int) -> str:
        return self.convertToTitle((columnNumber - 1)//26) + chr(65 + (columnNumber - 1)%26) if columnNumber > 26 else chr(65 + (columnNumber - 1)%26)
```
n진법으로 변환하는 문제와 논리가 같지만 0이 없다는 점에서 columnNumber에 -1을 해줘야합니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/excel-sheet-column-title/submissions/907679529/](https://leetcode.com/problems/excel-sheet-column-title/submissions/907679529/)