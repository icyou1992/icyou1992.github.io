---
title: Largest Odd Number in String
author: icyou
date: 2023-03-23 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Largest Odd Number in String
주어진 문자열에서 가장 큰 홀수인 부분 문자열을 구하는 문제입니다.

```
class Solution:
    def largestOddNumber(self, num: str) -> str:
        while num:
            if int(num[-1]) % 2 == 1:
                return num
            num = num[:-1]
        return num
```
문자열 끝에서부터 문자열을 순회하여 홀수가 나온다면 전체 문자열의 첫번째 수부터 그 홀수까지가 가장 큰 홀수가 됩니다.

```
class Solution:
    def largestOddNumber(self, num: str) -> str:
        
        for i in range(len(num) - 1, -1, -1) :
            if num[i] in {'1','3','5','7','9'} :
                return num[:i+1]
        return ''
```
solutions의 풀이입니다.  
나머지가 1이 나오는 연산보다 홀수가 나오는 경우의 수는 1,3,5,7,9 다섯가지이므로 5개의 수 중 일치하는 것이 있는지를 비교하는 연산이 더 성능이 빠르다는 것을 알 수 있습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/largest-odd-number-in-string/submissions/921162428/](https://leetcode.com/problems/largest-odd-number-in-string/submissions/921162428/)
- [https://leetcode.com/problems/largest-odd-number-in-string/solutions/1338138/python-3-99-34-faster-easy-explanation/](https://leetcode.com/problems/largest-odd-number-in-string/solutions/1338138/python-3-99-34-faster-easy-explanation/)