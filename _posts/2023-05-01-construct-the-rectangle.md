---
title: Construct the Rectangle
author: icyou
date: 2023-05-01 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Construct the Rectangle
사각형의 넓이가 주어졌을 때, 사각형의 길이와 너비의 차이가 최소가 되도록 하는 길이와 너비를 구하는 문제입니다. 단, 길이가 너비보다 크거나 같아야 합니다.

```
class Solution:
    def constructRectangle(self, area: int) -> List[int]:
        a = int(area ** (1/2))
        while area % a != 0:
            a += 1
        return [a, area//a] if a > area // a else [area//a, a]
```
길이와 너비가 최소가 되려면 사각형의 넓이를 1/2 거듭제곱한 수에서 하나씩 늘려가면 최소 차이의 길이와 너비를 구할 수 있습니다.

```
class Solution:
    def constructRectangle(self, area: int) -> List[int]:
        for l in range(int(area**0.5), 0, -1):            
            if area % l == 0: 
                return [area // l, l]
```
solution의 풀이입니다.  
이렇게 for문을 이용해서 logic을 더 간단하게 구현할 수 있었습니다.






<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/construct-the-rectangle/submissions/942379414/](https://leetcode.com/problems/construct-the-rectangle/submissions/942379414/)
- [https://leetcode.com/problems/construct-the-rectangle/solutions/899176/python-a-simple-for-loop/?languageTags=python3](https://leetcode.com/problems/construct-the-rectangle/solutions/899176/python-a-simple-for-loop/?languageTags=python3)