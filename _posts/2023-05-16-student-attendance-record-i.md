---
title: Student Attendance Record I
author: icyou
date: 2023-05-12 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Student Attendance Record I
문자 'A', 'L', 'P'로만 이루어진 문자열 s가 주어졌을 때, 'A'는 최대 한 번만 나타나고 'L'은 연속으로 세 번 나오지 않는 경우에 대해서만 True를 반환하는 문제입니다.

```
class Solution:
    def checkRecord(self, s: str) -> bool:
        return False if "LLL" in s or s.count('A') > 1 else True
```
조건은 두 개이므로, 두 조건 중 하나도 만족하지 못하면 False, 모두 만족하면 True를 반환합니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/student-attendance-record-i/submissions/951386430/](https://leetcode.com/problems/student-attendance-record-i/submissions/951386430/)