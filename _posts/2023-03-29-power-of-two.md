---
title: Power of Two
author: icyou
date: 2023-03-29 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Power of Two
주어진 수 n이 2의 거듭제곱이 되는 수인지를 판별하는 문제입니다.

```
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        x = 0
        while x < n:
            if 2 ** x == n: return True 
            x += 1
        return False
```
간단하게 1씩 늘려가면서 n인지를 확인하려고 했으니 시간초과가 떴습니다.  

```
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        low = 0
        high = 31
        while low <= high:
            mid = (low + high) // 2
            if 2 ** mid == n:
                return True
            elif 2 ** mid < n:
                low = mid + 1
            else:
                high = mid - 1
        return False
```
해서 한계 범위의 중간부터 이진 탐색 방식으로 찾아가는 방식으로 바꿔서 통과했습니다.  

```
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        return n>0 and n&(n-1)==0
```
solution의 풀이입니다.  
bit 연산을 통해 한 줄로 풀 수도 있네요.  
하지만 이진 탐색 방식의 풀이가 더 성능이 좋습니다. solution의 풀이는 O(1)이고, 이진 탐색의 풀이는 O(logn)이므로 testcase가 많아지고 숫자가 커진다면 solution의 풀이가 더 효율적일 것 같습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/power-of-two/submissions/924150169/](https://leetcode.com/problems/power-of-two/submissions/924150169/)
- [https://leetcode.com/problems/power-of-two/solutions/948641/python-o-1-solution/?languageTags=python](https://leetcode.com/problems/power-of-two/solutions/948641/python-o-1-solution/?languageTags=python)