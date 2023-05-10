---
title: Detect Capital
author: icyou
date: 2023-05-09 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Detect Capital
주어진 단어가 다음과 같은 조건을 만족하는지를 판별하는 문제입니다.
1. 모든 문자가 대문자
2. 모든 문자가 소문자
3. 첫번째 문자만 대문자

```
class Solution:
    def detectCapitalUse(self, word: str) -> bool:
        if len(word) < 2: 
            return True
        if 64 < ord(word[0]) < 91:
            if 64 < ord(word[1]) < 91:
                for i in range(2, len(word)):
                    if not 64 < ord(word[i]) < 91:
                        return False
            else:
                for i in range(1, len(word)):
                    if not 96 < ord(word[i]) < 123:
                        return False
        else:
            for i in range(1, len(word)):
                if not 96 < ord(word[i]) < 123:
                    return False
        return True
```
ord 함수를 사용하면 알파벳 범위를 숫자로 간편하게 표현할 수 있습니다. 이후, 조건에 맞게 코드를 만들어줍니다.

```
class Solution:
    def detectCapitalUse(self, word: str) -> bool:
      return word in [word.lower(), word.upper(), word.capitalize()]
```
```
class Solution:
    def detectCapitalUse(self, w: str) -> bool:
        return w.isupper() or w.islower() or w.istitle()
```
solution의 풀이를 참고하면 이런 식으로 간단하게 구현할 수도 있습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/detect-capital/submissions/947617483/](https://leetcode.com/problems/detect-capital/submissions/947617483/)
- [https://leetcode.com/problems/detect-capital/solutions/2984294/one-line-python-3-string-methods/](https://leetcode.com/problems/detect-capital/solutions/2984294/one-line-python-3-string-methods/)
- [https://leetcode.com/problems/detect-capital/solutions/2982041/python3-4-one-liners-contest-style-3-beginner-friendly-interview-style/](https://leetcode.com/problems/detect-capital/solutions/2982041/python3-4-one-liners-contest-style-3-beginner-friendly-interview-style/)