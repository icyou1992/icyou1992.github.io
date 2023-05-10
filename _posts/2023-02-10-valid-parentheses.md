---
title: Valid Parentheses
author: icyou
date: 2023-02-10 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Valid Parentheses
주어진 문자열에서 괄호가 순서대로 잘 닫혀있는지 판별하는 문제입니다.  

```
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        for x in s:
            if x == '(' or x == '{' or x == '[':
                stack.append(x)
            elif stack and ((x == ')' and stack[-1] == '(') or (x == '}' and stack[-1] == '{') or (x == ']' and stack[-1] == '[')):
                stack.pop()
            elif x == ')' or x == '}' or x == ']':
                return False
        return True if not stack else False

```
문자열 내의 괄호가 유효하려면 나중에 열린 괄호가 먼저 닫혀야 합니다. 이는 LIFO 자료구조인 stack과 성질이 맞습니다.  
여는 괄호가 나오면 stack에 삽입하고, 닫히는 괄호가 나오면 마지막에 들어온 stack의 괄호를 검사하여 문자열이 유효한지 확인합니다.  
이 경우를 제외하고 닫히는 괄호가 먼저 나오는 경우, 유효한 문자열이 아니므로 False를 return합니다.  
이렇게 풀었는데, 풀이가 개인적으로 깔끔하지 않다고 느꼈습니다.  

```
class Solution(object):
    def isValid(self, s):
        stack = [] #only use append and pop
        pairs = {
            '(': ')',
            '{': '}',
            '[': ']'
        }
        for bracket in s:
            if bracket in pairs.keys():
                stack.append(bracket)
            elif len(stack) == 0 or bracket != pairs[stack.pop()]:
                return False

        return len(stack) == 0
```
solution에서 본 풀이입니다.  
제 풀이와 발상은 비슷하지만 좀 더 깔끔하게 처리한 부분이 몇가지 보입니다.  
dictionary를 이용해서 if 내의 조건을 좀 더 깔끔하게 처리했습니다. 또한 pop 함수가 배열에서 원소를 빼내 가지고 있다는 점을 이용하여 제 풀이에서 밑의 두 조건을 합쳤습니다.

```
class Solution:
    def isValid(self, s: str) -> bool:
        while '()' in s or '[]'in s or '{}' in s:
            s = s.replace('()','').replace('[]','').replace('{}','')
        return False if len(s) !=0 else True
```
위와 같은 풀이는 가독성은 좋을지 몰라도 불필요한 반복문이 많기 때문에 지양해야할 풀이입니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/valid-parentheses/submissions/895263983/](https://leetcode.com/problems/valid-parentheses/submissions/895263983/)