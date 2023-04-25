---
title: Hamming Distance
author: icyou
date: 2023-04-25 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Hamming Distance
주어진 두 정수의 이진수에서 서로 다른 bit의 개수를 구하는 문제입니다.

```
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        cnt = 0
        for i in range(31):
            if format(x, '031b')[i] != format(y, '031b')[i]:
                cnt += 1
        return cnt
```
정수의 범위는 2의 31승까지이기 때문에 format 함수를 통해 x와 y를 31자리까지 0으로 채우는 수로 나타낸 후에 이진수를 차례로 순회하면서 서로 다른 bit의 수를 구합니다.

```
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        z = x ^ y
        i = z
        count = 0
        while i > 0:
            count += i % 2
            i = i // 2
        
        return count
```
solution의 풀이입니다.
^, xor 연산을 활용하면 풀이가 편하다는 것을 배웠습니다.

```
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        return format(x ^ y, 'b').count('1')
```
제 풀이와 solution의 풀이를 응용해서 한 줄 풀이로 만들 수 있었습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/hamming-distance/submissions/939456458/](https://leetcode.com/problems/hamming-distance/submissions/939456458/)
- [https://leetcode.com/problems/hamming-distance/solutions/3120649/bitwise-xor-and-divide-by-2-method/?languageTags=python3](https://leetcode.com/problems/hamming-distance/solutions/3120649/bitwise-xor-and-divide-by-2-method/?languageTags=python3)