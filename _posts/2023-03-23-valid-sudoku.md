---
title: Valid Sudoku
author: icyou
date: 2023-03-23 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Valid Sudoku
유효한 스도쿠를 판별하는 문제입니다.

```
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        for i in range(9):
            arr = []
            if not self.isValid(board[i]):
                return False
            for j in range(9):
                arr.append(board[j][i])
            if not self.isValid(arr):
                return False   
        for i in range(0, 9, 3):
            for j in range (0, 9, 3):
                arr = []
                for k in range(i, i + 3):
                    for l in range(j, j + 3):
                        arr.append(board[k][l])
                if not self.isValid(arr):
                    return False
        return True

    def isValid(self, arr: List[str]) -> bool:
        arr = [x for x in arr if x != '.']
        return len(arr) == len(set(arr))
```
행과 열, 3X3 사각형에 대해 1~9까지의 숫자가 한 번씩만 들어가는지 판별합니다.

```
class Solution(object):
    def isValidSudoku(self, board):
        res = []
        for i in range(9):
            for j in range(9):
                element = board[i][j]
                if element != '.':
                    res += [(i, element), (element, j), (i // 3, j // 3, element)]
        return len(res) == len(set(res))
```
solutions의 풀이입니다.  
1. (i, element)는 열이 일치하는 부분에 대해 검사합니다.
2. (element, j)는 행이 일치하는 부분에 대해 검사합니다.
3. (i // 3, j // 3, element)는 3X3 사각형에 대해 검사합니다. 3X3 사각형의 경우 예를 들면, 0, 0부터 3, 3까지의 숫자들은 // 연산에 의해 다 0, 0이 되므로 1~9까지의 수 중, 중복되는 수가 나온다면 set에서 겹치게 됩니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/valid-sudoku/submissions/920479073/](https://leetcode.com/problems/valid-sudoku/submissions/920479073/)
- [https://leetcode.com/problems/valid-sudoku/solutions/3277043/beats-96-78-short-7-line-python-solution-with-detailed-explanation/](https://leetcode.com/problems/valid-sudoku/solutions/3277043/beats-96-78-short-7-line-python-solution-with-detailed-explanation/)