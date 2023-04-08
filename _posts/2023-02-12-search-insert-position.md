---
title: Search Insert Position
author: icyou
date: 2023-02-12 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Search Insert Position
정렬된 배열에서 주어진 값의 index를 찾는 문제입니다.  
배열에서 주어진 값이 없을 경우, 그 값이 들어갈 index를 반환해야 합니다.  

```
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        def binarySearch(i: int, diff: int, nums: List[int], target: int):
            print(i, nums[i], diff, target)
            if nums[i] == target:
                return i
            elif diff == 0:
                if nums[i] > target:
                    if i > 0 and nums[i - 1] >= target:
                        return i - 1
                    else:
                        return i
                else:  
                    if i < len(nums) and nums[i + 1] < target:
                        return i + 2
                    else:
                        return i + 1
            elif nums[i] > target:
                return binarySearch(i - diff, diff//2, nums, target)
            else:
                return binarySearch(i + diff, diff//2, nums, target)
        return binarySearch(len(nums)//2, len(nums)//4, nums, target)
```
$$ O(log{n}) $$ 기준을 만족하기 위해 이진 탐색 기법을 사용하려고 시도했습니다. 중간값을 기준으로 좌우로 검색한다는 발상을 토대로 위와 같은 풀이를 구상했지만 결국 풀지 못했습니다.  
<br/><br/>
```
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        def binarySearch(nums: List[int], target: int, low: int, high: int):
            mid = (low + high) // 2
            print(mid, target, low, high)
            if low > high:
                if mid < 0:
                    return 0
                elif mid >= len(nums):
                    return len(nums) - 1
                elif nums[mid] > target:
                    return mid
                elif nums[mid] < target:
                    return mid + 1
                else:
                    return mid
                    
            if nums[mid] == target:
                return mid
            elif nums[mid] > target:
                return binarySearch(nums, target, low, mid-1)
            else:
                return binarySearch(nums, target, mid+1, high)
        return binarySearch(nums, target, 0, len(nums)-1)

```
이진 탐색을 찾아보고 나온 풀이입니다. 양 끝단의 index를 함수의 매개변수로 건네줘야한다는 것을 생각해내지 못했습니다.  
범위의 양 끝단의 index를 건네줘야하는 이유는, nums[mid] != target일 경우 mid가 양 끝단 중 하나가 될 것이고 이 값은 탐색을 끝냈으므로 포함이 되지 않아야 하기 때문입니다.  
첫 번째 풀이 시도처럼 중간값만을 매개변수로 건네줄 경우, nums[mid]를 해당 범위에 포함시키지 않을 수 있는 방법이 없습니다. 결국 diff가 0이 되는 상황에서 target과 nums[mid]의 값의 차이가 많이 나게 됩니다.  
<br/><br/>
```
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums)-1
        while right>=left:
            mid = (left + right)//2

            if nums[mid]==target:
                return mid
            elif nums[mid]<target:
                left = mid+1
            else:
                right = mid-1
                
        return left
```
solution에서 본 풀이입니다.  
이진 탐색을 반복문으로 처리했습니다.  
좀 더 깔끔한 부분은, 별다른 처리를 하지 않아도 마지막 `return left`를 통해 target이 존재하지 않을 경우에 대한 처리가 가능하다는 것입니다.  
이를 제 풀이에 적용한다면, 
```
if low > high:
    return low
```
이렇게 줄일 수 있습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/search-insert-position/submissions/896530133/](https://leetcode.com/problems/search-insert-position/submissions/896530133/)