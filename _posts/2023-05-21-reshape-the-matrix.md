---
title: Reshape the Matrix

author: icyou
date: 2023-05-20 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Reshape the Matrix
m * n 행렬을 r * c 행렬로 바꾸는 문제입니다. 바꿀 수 없을 경우 원래 행렬을 그대로 반환합니다.  

```
class Solution:
    def matrixReshape(self, mat: List[List[int]], r: int, c: int) -> List[List[int]]:
        if r * c == len(mat) * len(mat[0]):
            arr = [y for x in mat for y in x]
            return [arr[i:i + c] for i in range(0, len(arr), c)]
        return mat
```  
2차원 배열을 1차원 배열로 flatten하는 방법은 인터넷에서 찾아봤습니다.  terraform에서는 flatten 함수가 있는데, python에서 따로 있진 않은 것 같습니다. 이후, c 간격으로 새로운 배열을 만들어서 넣어주면 됩니다.  


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/reshape-the-matrix/submissions/954409705/](https://leetcode.com/problems/reshape-the-matrix/submissions/954409705/)