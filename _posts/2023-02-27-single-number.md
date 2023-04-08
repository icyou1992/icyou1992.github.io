---
title: Single Number
author: icyou
date: 2023-02-27 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Single Number
정수들의 모여 있는 배열에서 한 개만 있는 정수를 출력하는 문제입니다.

```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        arr = [0] * 60001
        for n in nums:
            arr[n + 30001] += 1
        return arr.index(1) - 30001
```
정수의 범위가 -30000 ~ 30000까지이므로 60001개의 배열을 생성한 후 배열에 있는 정수를 index로 활용하여 배열의 정수들의 개수를 셉니다.  
이렇게 하면 중복되는 수들은 2, 4, 6, ... 등의 짝수로 배열의 값을 가지고 한 개만 있는 정수는 arr\[정수\] = 1로 나타나니, arr의 값이 1인 index를 반환하면 됩니다.  

```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        arr = {}
        for n in nums:
            if n in arr.keys():
                arr[n] += 1  
            else:
                arr[n] = 1
        for key in arr.keys():          
            if arr[key] == 1:
                return key
```
논리가 좀 비효율적인 것 같아서 dictionary 자료형을 활용하여 다시 풀어봤습니다.  
하지만 속도는 이 방법이 더 느렸습니다.  

```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        return reduce(xor, nums)
```
solution에서 본 풀이입니다.  
한 줄도 아니고 한 단어로 끝내버렸습니다. ㅋㅋ  
xor bit 연산을 통해 정수가 두 번 이상 나오면 0이 되고 마지막 하나 남은 수만 남게 됩니다.

```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        r = 0
        for n in nums:
            r = r ^ n
        return r
```
xor 연산을 활용하면서 가독성을 좋게 한다면, 이런 식으로도 풀 수 있습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/single-number/submissions/905799176/](https://leetcode.com/problems/single-number/submissions/905799176/)
- [https://leetcode.com/problems/single-number/solutions/3215764/python-shortest-1-liner-functional-programming/](https://leetcode.com/problems/single-number/solutions/3215764/python-shortest-1-liner-functional-programming/)