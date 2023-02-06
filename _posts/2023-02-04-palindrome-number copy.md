---
title: Palindrome Number
author: icyou
date: 2023-02-04 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm]
pin: true
math: true
---

## Leetcode Problem

### Palindrome Number

수가 주어졌을 때, 해당 숫자가 Palindrom인지 아닌지를 판별하는 문제

```
class Solution:
    def isPalindrome(self, x: int) -> bool:
        xs = str(x)
        start = 0
        def recursive(i: int):
            nonlocal start
            if i < len(xs):
                if not recursive(i + 1) or xs[i] != xs[start]:
                    return False
                start += 1
                print(xs[i])
            return True
        return recursive(0)
```
어제 풀었던 Palindrome Linked List 문제의 재귀 풀이가 인상 깊어서 재귀 방식으로 풀려고 시도했지만, 잘 생각나지 않아서 이전 문제의 풀이 방식을 참고하여 풀어냈다.

<br/><br/>

보고 풀어도 잘 안 풀릴만큼 재귀적 방식의 사고는 잘 안되는 것 같다. 
재귀 문제를 많이 풀어봐야겠다.

재귀 방식의 문제 풀이는 크게 점화식의 문제풀이 방법과 비슷하다고 생각했다.
1. $$ a_1 $$항을 구한다.
2. $$ a_{n+1} $$과 $$ a_n $$의 관계를 구한다.
3. 점화식을 구한다.

<br/>

1. 재귀가 끝나는 조건을 구한다.
2. 논리가 반복되는 구조를 구한다.
3. 재귀 함수를 만든다.

그런데, 이래도 잘 모르겠다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/palindrome-number/description/](https://leetcode.com/problems/palindrome-number/description/)