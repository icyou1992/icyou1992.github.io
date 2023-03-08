---
title: Combine Two Tables
author: icyou
date: 2023-03-07 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Combine Two Tables
주어진 두 table을 mysql로 합치는 문제입니다.

```
SELECT FirstName, LastName, City, State
FROM Person LEFT JOIN Address 
ON Address.PersonId = Person.PersonId
```
두 table의 공통 column인 personId를 기준으로 JOIN을 사용했습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/combine-two-tables/submissions/910793114/](https://leetcode.com/problems/combine-two-tables/submissions/910793114/)