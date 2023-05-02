---
title: Teemo Attacking
author: icyou
date: 2023-05-02 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Teemo Attacking
티모가 애쉬를 timeSeries의 배열 때마다 공격했을 때, 애쉬가 받는 총 피해를 구하는 문제입니다. 단 독 데미지는 중첩이 되지 않습니다.

```
class Solution:
    def findPoisonedDuration(self, timeSeries: List[int], duration: int) -> int:
        time = 0
        for i in range(len(timeSeries)):
            if i > 0 and timeSeries[i] - timeSeries[i - 1] < duration:
                time += timeSeries[i] - timeSeries[i - 1]
            else:
                time += duration
        return time
```
독 데미지가 중첩이 되지 않으므로, 독 데미지가 들어가는 동안 다시 공격을 받는다면 독 데미지 기간을 초기화해야 합니다. 따라서, duration 동안 티모가 추가로 공격하지 않을 경우, time에 duration을 더하고 추가로 공격할 경우, 그 시간 차만을 더합니다.

```
class Solution:
    def findPoisonedDuration(self, timeSeries: List[int], duration: int) -> int:
        time = 0
        for i in range(1, len(timeSeries)):
            time = time + timeSeries[i] - timeSeries[i - 1] if timeSeries[i] - timeSeries[i - 1] < duration else time + duration
        return time + duration
```
위의 코드를 좀 더 줄일 수 있었습니다.


```
class Solution:
    def findPoisonedDuration(self, timeSeries: List[int], duration: int) -> int:
        return duration + sum(min(duration, timeSeries[i] - timeSeries[i - 1]) for i in range(1, len(timeSeries)))
```
solution을 참고했더니 더 줄일 수 있었네요.




<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/teemo-attacking/submissions/943210011/](https://leetcode.com/problems/teemo-attacking/submissions/943210011/)
- [https://leetcode.com/problems/teemo-attacking/solutions/2962458/1-line-solution/?languageTags=python3](https://leetcode.com/problems/teemo-attacking/solutions/2962458/1-line-solution/?languageTags=python3)