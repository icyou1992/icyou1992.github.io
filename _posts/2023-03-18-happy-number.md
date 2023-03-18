---
title: Happy Number
author: icyou
date: 2023-03-16 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Happy Number
주어진 수가 happy number인지를 판단하는 문제입니다.  
Happy number는 반복적으로 각 자릿수의 제곱을 더했을 때 마지막에 1이 나오는 수입니다.  

```
class Solution:
    def isHappy(self, n: int) -> bool:
        arr, num = [], n
        while True:
            num = self.plusdigit(num)
            if num in arr:
                arr.append(num)
                break
            arr.append(num)
        return True if arr[-1] == 1 else False
    def plusdigit(self, n: int) -> int:
        res = 0
        while n:
            res += (n % 10)**2
            n //= 10
        return res
```
각 자릿수의 제곱을 더하는 함수를 만들고 while문을 돌면서 각 자릿수의 제곱을 더한 수들이 모여있는 arr에 방금 구한 수가 있는지를 확인합니다. 즉 cycle이 있는지를 확인합니다.  

```
class Solution:
    def isHappy(self, n: int) -> bool:
        num, arr = self.plusdigit(n), []
        while num not in arr[:-1]:
            arr.append(num)
            num = self.plusdigit(num)
        return True if arr[-1] == 1 else False
    def plusdigit(self, n: int) -> int:
        res = 0
        while n:
            res += (n % 10)**2
            n //= 10
        return res
```
위의 풀이와 논리는 같지만 코드를 좀 더 줄였습니다.  
코드를 줄이는 것만으로도 runtime을 41ms에서 31ms로 줄이는 유의미한 성능 개선 효과를 얻을 수 있었습니다.
array를 dictionary로 바꿔 성능을 비교해봤지만, array가 성능이 조금 더 좋았습니다.  
함수를 반복하면서 숫자가 100을 넘기 힘들어, cycle이 금방 형성되기 때문인 것으로 보입니다.  
즉, 배열의 원소가 많지 않다면 array가 dictionary보다 성능이 좋은 것 같습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/happy-number/submissions/917388277/](https://leetcode.com/problems/happy-number/submissions/917388277/)
- [https://leetcode.com/problems/happy-number/submissions/917406417/](https://leetcode.com/problems/happy-number/submissions/917406417/)