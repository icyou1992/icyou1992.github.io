---
title: Reverse Vowels of a String
author: icyou
date: 2023-04-09 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Reverse Vowels of a String
주어진 s 문자열에서 'aeiouAEIOU' 등의 문자들만 순서를 거꾸로 한 문자열을 반환하는 문제입니다.

```
class Solution:
    def reverseString(self, s: List[str]) -> None:
        s.reverse()
```
python 내장함수로 간단히 해결할 수 있습니다.

```
class Solution:
    def reverseVowels(self, s: str) -> str:
        ss = list(s)
        low, high = 0, len(s) - 1
        while low < high:
            if ss[low] in "aeiouAEIOU" and ss[high] in "aeiouAEIOU":
                ss[low], ss[high] = ss[high], ss[low]
            elif ss[low] in "aeiouAEIOU":
                low -= 1
            elif ss[high] in "aeiouAEIOU":
                high += 1
            low += 1
            high -= 1
        return ''.join(ss)
```
문자열의 처음과 끝 index를 변수로 저장한 후, 해당 처음과 끝 index의 원소 모두가 'aeiouAEIOU'일 경우 둘을 바꿉니다. 하나만 그럴 경우, 그 원소의 index를 그대로 두고 나머지 index만 변경합니다.  
이 방식으로 처음과 끝의 index가 가운데로 모이면서 모음들의 순서를 바꿀 수 있습니다.

```
class Solution:
    def reverseVowels(self, s: str) -> str:
        vowels = re.findall('[aeiouAEIOU]', s)
        return re.sub('[aeiouAEIOU]', lambda _ : vowels.pop(), s)
```
solution의 풀이입니다.  
python 내장함수를 이용하여 문제를 해결했습니다. re.findall 함수를 통해 s 문자열 내의 모든 모음을 찾아 vowels 변수로 저장한 다음, re.sub 함수로 모음들이 발견될 때마다 vowels 변수의 뒤에서 꺼낸 문자들로 교체합니다. 그러면 vowels 변수의 뒤에서부터 순서대로 문자들을 교체하기 때문에 모음들의 순서가 거꾸로 됩니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/reverse-vowels-of-a-string/submissions/930409687/](https://leetcode.com/problems/reverse-vowels-of-a-string/submissions/930409687/)
- [https://leetcode.com/problems/reverse-vowels-of-a-string/solutions/3296384/one-liner-efficient-python-solution-beats-99-97-explained/?languageTags=python](https://leetcode.com/problems/reverse-vowels-of-a-string/solutions/3296384/one-liner-efficient-python-solution-beats-99-97-explained/?languageTags=python)