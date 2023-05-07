---
title: Construct the Rectangle
author: icyou
date: 2023-05-04 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Construct the Rectangle
키보드의 한 줄로만 단어를 구성할 수 있는 경우만 구하는 문제입니다.

```
class Solution:
    def findWords(self, words: List[str]) -> List[str]:
        d = { 'q': 1,'w': 1, 'e': 1, 'r': 1, 't': 1, 'y': 1, 'u': 1, 'i': 1, 'o': 1,  'p': 1, 'a': 2, 's': 2, 'd': 2, 'f': 2, 'g': 2, 'h': 2, 'j': 2, 'k': 2, 'l': 2, 'z': 3, 'x': 3, 'c': 3, 'v': 3, 'b': 3, 'n': 3, 'm': 3 }
        r = []
        for w in words:
            t = d[w[0].lower()]
            for s in w:
                if d[s.lower()] != t:
                    break
            else:
                r.append(w)
        return r
```
키보드의 모든 소문자들을 1, 2, 3번으로 정하고 lower 함수로 단어를 전부 소문자로 변형시킨 뒤 몇번째 줄에 있는지를 구합니다. 줄이 같지 않을 경우 바로 빠져나오고 전부 맞을 경우만 배열에 추가합니다.




<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/keyboard-row/submissions/944336636/](https://leetcode.com/problems/keyboard-row/submissions/944336636/)