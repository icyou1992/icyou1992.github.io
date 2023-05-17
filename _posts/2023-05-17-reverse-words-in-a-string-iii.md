---
title: Reverse Words in a String III

author: icyou
date: 2023-05-17 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Reverse Words in a String III
주어진 문자열 s를 단어별로 뒤집은 문자열을 구하는 문제입니다.

```
class Solution:
    def reverseWords(self, s: str) -> str:
        return ' '.join([x[::-1] for x in s.split()])
```
split 함수로 띄어쓰기를 기준으로 분리한 배열을 얻어낸 후, join 함수로 배열의 각 원소를 \[::-1\]로 뒤집은 후 띄어쓰기로 이은 문자열을 구합니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/reverse-words-in-a-string-iii/submissions/951816744/](https://leetcode.com/problems/reverse-words-in-a-string-iii/submissions/951816744/)