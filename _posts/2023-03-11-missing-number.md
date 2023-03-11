---
title: Missing Number
author: icyou
date: 2023-03-11 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Missing Number
0부터 n까지 중에 nums 배열에 없는 빈 숫자를 찾는 문제입니다.

```
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        m, n = max(nums), len(nums)
        return m*(m+1)//2 - sum(nums) if m*(m+1)//2 == n*(n+1)//2 else n
```
배열의 원소의 최댓값을 m이라 하면 m*(m+1)//2은 1부터 m까지의 값을 더한 값입니다.  
그러면 m*(m+1)//2에서 nums의 합을 빼면 빈 숫자를 구할 수 있습니다.  
배열이 0부터 n-1까지 있으면, 빈 원소는 n이 됩니다.  
이 경우에 대해서 배열의 길이는 n이고 배열의 최댓값은 n-1이기 때문에 서로 일치하지 않습니다. 이 경우에 n을 반환하면 모든 경우에 대해 빈 원소를 반환할 수 있습니다.  

```
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        return len(nums)*(len(nums) + 1)//2 - sum(nums)
```
solution의 풀이입니다.  
배열의 원소는 0부터 n까지의 수 중 하나가 빠져있으므로 nums의 길이는 0을 포함하여 n이 됩니다. 
n*(n + 1)//2는 n까지의 총합이므로, 여기서 nums 배열의 합을 빼면 빈 숫자를 구할 수 있습니다.

<br/><br/>

논리는 solution의 풀이가 훨씬 간단하지만, 성능은 첫번째 풀이가 훨씬 좋습니다.  
성능이 더 좋은 이유를 생각해봤을때, `if m*(m+1)//2 == n*(n+1)//2` 비교 연산이 `sum(nums)`의 배열을 전부 더하는 연산보다 훨씬 빠르기 때문에 성능이 더 좋게 나온 것 같습니다.




<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/missing-number/submissions/913230833/](https://leetcode.com/problems/missing-number/submissions/913230833/)
- [https://leetcode.com/problems/missing-number/submissions/913207537/](https://leetcode.com/problems/missing-number/submissions/913207537/)