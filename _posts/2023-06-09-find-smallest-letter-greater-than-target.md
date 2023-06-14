---
title: Find Smallest Letter Greater Than Target
author: icyou
date: 2023-06-09 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Find Smallest Letter Greater Than Target
주어진 letters 배열에서 target 다음으로 큰 수를 찾는 문제입니다.

```
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:
        arr = sorted(set(letters + [target]))
        return arr[i + 1] if (i := arr.index(target)) < len(arr) - 1 else arr[0]
```
target과 letters의 각 원소들을 비교해야하므로 차라리 정렬을 하는 것이 빠를 것이라 생각했습니다. set 함수를 통해 target이 중복되는 경우를 제거하고 바로 다음의 index를 구해서 반환합니다. target이 제일 클 경우 문제에서 제시한 대로 첫번째 원소를 반환합니다.  
:= 연산자를 통해 코드의 크기를 줄일 수 있었습니다.  


<br/><br/><br/><br/>
참고  
- [https://leetcode.com/problems/find-smallest-letter-greater-than-target/submissions/967272517/](https://leetcode.com/problems/find-smallest-letter-greater-than-target/submissions/967272517/)