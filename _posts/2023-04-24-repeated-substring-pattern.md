---
title: Repeated Substring Pattern
author: icyou
date: 2023-04-24 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Repeated Substring Pattern
문자열 s가 부분문자열의 반복으로 이루어졌는지 판별하는 문제입니다.

```
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:
        d, l = 1, len(s)
        while d <= l // 2:
            if l % d == 0:
                for i in range(0, len(s) - d, d): 
                    if not s[i:i + d] == s[i + d:i + 2*d]:
                        break
                else:
                    return True
            d += 1
        return False

```
부분 문자열이 반복되는 것을 가정하고 문자열 s의 최소 반복 횟수가 2이므로, while문에서 전체 문자열 s의 1/2까지만 순회하면 됩니다. 
for문은 d 간격으로 부분 문자열이 다음 부분 문자열과 일치하는지를 문자열 끝까지 검사합니다. 해서, 전부 일치할 경우 True를 일치하지 않으면 d 간격을 1씩 늘려나갑니다.


```
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:
        return False if not s else (s * 2)[1:-1].find(s) != -1
```
s를 하나 더 복사한 문자열의 처음과 끝 부분을 제외하고 s 문자열을 찾을 수 있다면 True를 반환합니다. `abcdabcd`의 문자열을 예로 들면, abcdabcdabcdabcd에서 `bcdabcdabcdabc`에서 `abcdabcd`를 발견할 수 있기 때문에 True를 반환합니다.  
문자열 s의 부분 문자열이 최소로 반복될 경우 2회가 반복될 수 있습니다. 최소로 반복되는 부분 문자열을 x라 하면, 새로운 문자열은 xxxx입니다. 여기서 양 끝을 제외하면 axxb가 됩니다. xx는 s이므로, 부분 문자열이 최소로 반복된다고 가정해도 새로운 문자열은 최소 1회의 문자열을 포함할 수밖에 없습니다.  

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/repeated-substring-pattern/submissions/938918456/](https://leetcode.com/problems/repeated-substring-pattern/submissions/938918456/)
- [https://leetcode.com/problems/repeated-substring-pattern/solutions/94334/easy-python-solution-with-explaination/](https://leetcode.com/problems/repeated-substring-pattern/solutions/94334/easy-python-solution-with-explaination/)