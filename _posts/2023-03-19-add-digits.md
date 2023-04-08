---
title: Add Digits
author: icyou
date: 2023-03-19 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Add Digits
각 자릿 수를 더했을 때 한자릿 수가 될 경우까지 각 자릿 수를 더하여 그 숫자를 구하는 문제입니다.

```
class Solution:
    def addDigits(self, num: int) -> int:
        num = sum(int(x) for x in str(num))
        return num if num < 10 else self.addDigits(num)
```
각 자릿수를 더하기 위해 수를 string으로 만들고 수 전체를 더합니다.  
num이 한자릿 수가 될 때까지 재귀를 반복합니다.  

```
class Solution:
    def addDigits(self, num: int) -> int:
        return num if num < 10 else self.addDigits(num // 10 + num % 10)
```
주어진 수에서 자릿수를 전부 더한 후 재귀를 하는 방식에서 좀 더 개선시켰습니다.  
주어진 수가 세 자리든 네 자리든 10으로 나눈 후 바로 나머지를 더해도 결과값이 바뀌지 않기 때문에 num이 한자릿 수가 될 때까지 10을 나누고 나머지를 바로 더하는 연산을 반복합니다.  
이 방식은 또한 문자열로 변환할 필요가 없습니다.  

```
class Solution:
    def addDigits(self, num: int) -> int:
	    return 0 if num == 0 else 9 if num % 9 == 0 else num % 9
```
solution의 풀이입니다.  
1부터 100까지 add digits의 결과값을 나열하다보면 9번째를 기준으로 규칙성이 나타납니다.  
이를 활용하면 반복문이나 재귀 없이 답을 구할 수 있습니다.  


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/happy-number/submissions/917388277/](https://leetcode.com/problems/happy-number/submissions/917388277/)
- [https://leetcode.com/problems/add-digits/submissions/917789403/](https://leetcode.com/problems/add-digits/submissions/917789403/)
- [https://leetcode.com/problems/add-digits/solutions/1754049/easy-o-1-explanation-with-example/)