---
title: Counting Bits
author: icyou
date: 2023-04-06 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Counting Bits
0부터 n까지를 이진수로 표현했을 때, 1의 개수를 넣은 배열을 구하는 문제입니다.  

```
class Solution:
    def countBits(self, n: int) -> List[int]:
        arr, i = [0, 1], 2
        while i < n + 1:
            for j in range(len(arr)):
                arr.append(arr[j] + 1)
            i *= 2
        return arr[:n + 1]
```
testcase에 10000을 넘는 수를 넣고 숫자들의 순서를 보니까 \[0\] 또는 \[0, 1\] 배열을 시작으로, 배열이 스스로를 복제한 배열에 1씩을 더한 배열이 더해지면서 두 배가 되는 패턴을 발견했습니다.  

```
def countBits(self, num: int) -> List[int]:
    counter = [0]
    for i in range(1, num+1):
        counter.append(counter[i >> 1] + i % 2)
    return counter
```
solution의 풀이입니다.  
init 과정에서 nums를 그대로 저장하지 않고 n까지 원소의 합으로 저장하면 left-1 원소와 right 원소의 차이로 left부터 right까지의 합을 구할 수 있습니다.  
이 방식이 속도는 더 좋지만 범용성은 떨어질 것 같습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/range-sum-query-immutable/submissions/928276245/](https://leetcode.com/problems/range-sum-query-immutable/submissions/928276245/)
- [https://leetcode.com/problems/counting-bits/solutions/656849/python-simple-solution-with-clear-explanation/?languageTags=python](https://leetcode.com/problems/counting-bits/solutions/656849/python-simple-solution-with-clear-explanation/?languageTags=python)