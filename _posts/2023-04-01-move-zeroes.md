---
title: Move Zeroes
author: icyou
date: 2023-03-31 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Move Zeroes
nums 배열을 in-place 방식으로 0을 배열의 맨 뒤로 보내는 문제입니다.

```
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        def goback(i: int, k: int):
            swp = 0
            for j in range(i, len(nums) - 1 - k):
                swp = nums[j]
                nums[j] = nums[j + 1]
                nums[j + 1] = swp
        
        k = 0
        i = 0
        while i < len(nums) - 1 - k:
            if nums[i] == 0:
                goback(i, k)
                i -= 1
                k += 1
            i += 1
```
0을 swap을 통해 맨 뒤로 보내는 goback 함수를 만듭니다.  
이후 main에서 반복문을 돌면서 nums 배열의 모든 0을 맨 뒤로 보내는데, 0을 맨 뒤로 보낼 경우 0 이후의 모든 원소의 index가 앞으로 한 칸씩 당겨지므로 i에서 1을 빼서 다음 반복문에서도 한 칸 앞의 원소를 검사할 수 있도록 합니다.

```
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        i = 0
        for j in range(len(nums)):
            if nums[j] != 0:
                nums[i], nums[j] = nums[j], nums[i]
                i += 1
```
solution의 풀이입니다.  
0을 뒤로 보낸다는 개념으로 접근하지 않고 0이 아닌 원소들을 전부 앞으로 보낸다고 생각합니다.
i는 nums\[j\]가 0이 아닐 경우만 증가하므로, i 앞의 원소들은 전부 0이 아닌 정수들만 모이게 되며, i는 항상 0을 가리키게 되고, j가 0이 아닌 원소들을 i로 가져오게 되므로 0이 아닌 원소들의 순서가 바뀔 수는 없습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/move-zeroes/submissions/925851592/](https://leetcode.com/problems/move-zeroes/submissions/925851592/)
- [https://leetcode.com/problems/move-zeroes/solutions/3236411/283-space-96-33-solution-with-step-by-step-explanation/?languageTags=python](https://leetcode.com/problems/move-zeroes/solutions/3236411/283-space-96-33-solution-with-step-by-step-explanation/?languageTags=python)