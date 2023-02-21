---
title: Longest Common Prefix
author: icyou
date: 2023-02-09 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: true
math: true
---

## Leetcode Problem

### Longest Common Prefix
주어진 수를 0으로 만드는 과정의 횟수를 구하는 문제입니다.

```
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        rslt = ""
        l = min([len(x) for x in strs])
        for i in range(l):
            flag = False
            for x in strs:
                if x[i] != strs[0][i]:
                    flag = True
            if flag == True:
                break
            else:
                rslt += strs[0][i]
        return rslt
```
주어진 배열 중 최소 길이의 문자열을 먼저 구한 다음(index 범위 초과 오류 방지), 최소 길이의 문자열만큼 각 문자가 차례대로 일치하는지 조사합니다.

```
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        l = list(zip(*strs))
        prefix = ""
        for i in l:
            if len(set(i))==1:
                prefix += i[0]
            else:
                break
        return prefix
```
solution에서 본 풀이입니다.  
zip 함수를 이용하면 주어진 배열 중의 최소 길이의 문자열을 구할 필요가 없습니다.
깔끔한 풀이이긴 하지만 성능적으로 전자의 풀이보다 나을지는 zip 함수의 동작과정을 좀 더 조사해봐야할 것 같습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/longest-common-prefix/submissions/894790919/](https://leetcode.com/problems/longest-common-prefix/submissions/894790919/)