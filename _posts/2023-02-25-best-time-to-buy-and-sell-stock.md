---
title: Best Time to Buy and Sell Stock
author: icyou
date: 2023-02-25 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Best Time to Buy and Sell Stock
주식의 가격이 적힌 배열이 주어지고, 이 주식을 사고 판다고 가정할 때 얻을 수 있는 최대 수익을 계산하는 문제입니다.  

```
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit, buy = 0, 0
        for i in range(1, len(prices)):
            if prices[buy] > prices[i]:
                buy = i
            if prices[i] - prices[buy] > profit:
                profit = prices[i] - prices[buy]
        return profit
```

dp 문제임을 직감했지만, dp 문제를 너무 오랜만에 풀어서 맞게 풀었는지는 모르겠습니다.  
profit이라는 변수를 두고, 이를 for loop를 돌면서 profit의 최댓값을 찾습니다. 이 때 i는 파는 시점, buy는 사는 시점인데 prices\[i\]가 prices\[buy\]보다 낮으면 사는 가격이 더 싸지므로 buy를 i로 바꿉니다.  

```
class Solution:
    def maxProfit(self, prices):
        min_price, max_profit = float('inf'), 0
        for price in prices:
            if price < min_price:
                min_price = price
            else:
                max_profit = max(max_profit, price - min_price)
        return max_profit
```
solution의 풀이입니다.  
논리 구조는 틀리지 않았지만, 가독성은 solution의 풀이가 더 좋아 보입니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/pascals-triangle-ii/submissions/904046846/](https://leetcode.com/problems/pascals-triangle-ii/submissions/904046846/)