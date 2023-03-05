---
title: Reverse Bits
author: icyou
date: 2023-03-05 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Reverse Bits
32bit의 양수형 정수가 주어졌을 때, 이 수의 bit를 전부 거꾸로 뒤집었을 때 나오는 수를 구하는 문제입니다.

```
class Solution:
    def reverseBits(self, n: int) -> int:
        s = bin(n)[:1:-1]
        return int(s + '0'*(32 - len(s)), 2)
```
n을 binary로 변환하면 0b를 prefix로 두고 있는 2진수가 생성됩니다. 이 전체 문자열을 거꾸로 뒤집은 다음 b0 부분을 잘라줍니다.  
32bit이므로 나머지 빈 공간을 0으로 채워준 후 정수를 return합니다.

```
class Solution:
    def reverseBits(self, n: int) -> int:
        res = 0
        for _ in range(32):
            res = (res<<1) + (n&1)
            n>>=1
        return res
```
solutions에서 본 풀이입니다.  
n의 오른쪽에서부터 하나씩 bit를 지워가며 & 연산으로 res에 bit를 추가합니다.  
이렇게 되면 n은 오른쪽부터 없어지지만 res는 왼쪽부터 bit가 생겨나서 순서가 뒤집어집니다.  
<br/>

성능 측면에서 bit연산이 더 빠를 줄 알았는데, 전자의 풀이가 더 성능이 좋습니다. 하지만 전자의 풀이는 memory를 좀 더 씁니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/reverse-bits/submissions/909417951/](https://leetcode.com/problems/reverse-bits/submissions/909417951/)
- [https://leetcode.com/problems/reverse-bits/solutions/1791099/python-3-40ms-real-bit-manipulation-solution/?languageTags=python](https://leetcode.com/problems/reverse-bits/solutions/1791099/python-3-40ms-real-bit-manipulation-solution/?languageTags=python)