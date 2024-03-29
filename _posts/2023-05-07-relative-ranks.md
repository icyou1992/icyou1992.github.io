---
title: Relative Ranks
author: icyou
date: 2023-05-07 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Relative Ranks
score 배열에서 각 점수의 등수를 구하는 문제입니다.

```
class Solution:
    def findRelativeRanks(self, score: List[int]) -> List[str]:
        d, arr = {}, sorted(score, reverse=True)
        for i in range(len(score)):
            if i + 1 == 1:
                d[arr[i]] = "Gold Medal"
            elif i + 1 == 2:
                d[arr[i]] = "Silver Medal"
            elif i + 1 == 3:
                d[arr[i]] = "Bronze Medal"
            else:
                d[arr[i]] = str(i + 1)
        return [ d[x] for x in score ]
```
index + 1이 등수인 것을 활용해서 1등, 2등, 3등의 경우에만 Medal을 주고 나머지는 그냥 등수를 넣었습니다.

<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/relative-ranks/submissions/945769912/](https://leetcode.com/problems/relative-ranks/submissions/945769912/)