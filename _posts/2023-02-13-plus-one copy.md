---
title: Plus One
author: icyou
date: 2023-02-13 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm]
pin: true
math: true
---

## Leetcode Problem

### Plus One
주어진 배열을 숫자로 만들어 1을 더하고 다시 배열로 반환하는 문제입니다.

```
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        s = ""
        for x in digits:
            s += str(x)
        s = str(int(s) + 1)
        return [int(x) for x in s]
```
주어진 배열을 문자열로 바꿔서 더합니다. 더해진 문자열을 int형으로 바꿔서 1을 더한 후에 다시 int형 배열로 바꿉니다.

<br/><br/>
```
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        return map(int,str(int(''.join(map(str, digits))) + 1))
```
간단하게 map과 join을 이용하여 한 줄로도 끝낼 수 있었습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/plus-one/submissions/897091508/](https://leetcode.com/problems/plus-one/submissions/897091508/)