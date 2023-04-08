---
title: First Bad Version
author: icyou
date: 2023-03-31 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### First Bad Version
1부터 n번째까지의 version이 있을 때 처음 발생한 잘못된 version을 isBadVersion 함수를 이용하여 찾는 문제입니다.  

```
class Solution:
    def firstBadVersion(self, n: int) -> int:
        low = 1
        high = n
        while low <= high:
            mid = (low + high) // 2
            isBad = isBadVersion((low + high) // 2)
            if isBad == True:
                high = mid - 1
            else:
                low = mid + 1
        return low

```
isBadVersion 결괏값은 false 이후에 계속 true만 나옵니다. 이는 정수들의 대소를 비교할 때와 같이 일관성이 있기 때문에 이진 탐색으로 첫번째 Bad Version을 구할 수 있습니다.  
만약, 1부터 n까지 중, true가 한 번만 나오게 된다면 어디에 true가 있는지 대소 비교로 판단할 수 없으므로 이진 탐색을 사용할 수 없습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/first-bad-version/submissions/925205652/](https://leetcode.com/problems/first-bad-version/submissions/925205652/)