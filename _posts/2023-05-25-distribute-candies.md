---
title: Distribute Candies
author: icyou
date: 2023-05-24 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Distribute Candies
candyType 배열이 주어졌을 때, Alice는 candyType에서 배열에서, 길이에서 2를 나눈 만큼의 캔디를 먹을 수 있습니다. Alice가 서로 다른 종류의 캔디를 2개 이상 먹을 수 없을 때, Alice가 먹을 수 있는 최대 캔디 수를 구하는 문제입니다.  

```
class Solution:
    def distributeCandies(self, candyType: List[int]) -> int:
        return min(len(set(candyType)), len(candyType)//2)
```  
candyType 안의 캔디가 각각 2개 이상씩 있을 경우, candyType 최대 길이의 2분의 1만큼의 캔디를 먹습니다. 겹치는 캔디가 많아서 2분의 1보다 적게 먹는 경우는 set를 통해 구할 수 있습니다. 이후 두 값 중 적은 값이 Alice가 최대로 먹을 수 있는 캔디의 수입니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/distribute-candies/submissions/957088645/](https://leetcode.com/problems/distribute-candies/submissions/957088645/)