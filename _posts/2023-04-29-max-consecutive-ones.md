---
title: Max Consecutive Ones
author: icyou
date: 2023-04-29 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Max Consecutive Ones
주어진 nums 배열에서 1이 연속하여 나온 길이의 최댓값을 구하는 문제입니다.

```
class Solution:
    def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
        cnt, m = 0, 0
        for n in nums:
            cnt = cnt + 1 if n == 1 else 0
            m = max(m, cnt)
        return m
```
배열을 순회하면서 1이 나타날 때부터 cnt로 개수를 전부 세서 최댓값을 출력합니다. 0이 나올 경우 cnt를 초기화합니다.

```
class Solution:
    def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
        return len(max(''.join(list(map(str,nums))).split("0")))
```
solution의 풀이입니다.
'0'을 인수로 split 함수를 쓰는 아이디어로 한 줄로 풀어냈습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/max-consecutive-ones/submissions/941343677/](https://leetcode.com/problems/max-consecutive-ones/submissions/941343677/)
- [https://leetcode.com/problems/max-consecutive-ones/solutions/3335346/python-one-liner/?languageTags=python3](https://leetcode.com/problems/max-consecutive-ones/solutions/3335346/python-one-liner/?languageTags=python3)