---
title: Power of Three
author: icyou
date: 2023-03-31 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Power of Three
주어진 수가 3의 거듭제곱인지를 판별하는 문제입니다.

```
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
        low, high = 0, 31
        while low <= high:
            mid = (low + high)//2
            if 3 ** mid == n:
                return True
            elif 3 ** mid > n:
                high = mid - 1
            else:
                low = mid + 1
        return False
```
이전에 풀었던 power of two와 같이 이진 탐색을 이용하여 풀었습니다.

```
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
        return (n > 0) and 1162261467 % n == 0
```
solution의 풀이입니다.  
문제의 범위인 2의 31 거듭제곱보다 낮은 수 중, 3의 거듭제곱에서 가장 큰 수는 3의 19 거듭제곱인 1162261467입니다. 나머지 3의 거듭제곱수는 이 수에서 나눌 경우 나머지가 0이므로 이를 이용하면 O(1) 시간으로 문제를 해결할 수 있습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/power-of-three/submissions/927785166/](https://leetcode.com/problems/power-of-three/submissions/927785166/)
- [https://leetcode.com/problems/power-of-three/solutions/2471285/python-c-one-liner-o-1-easy-solution-with-detailed-explanation-beginner-friendly/](https://leetcode.com/problems/power-of-three/solutions/2471285/python-c-one-liner-o-1-easy-solution-with-detailed-explanation-beginner-friendly/)