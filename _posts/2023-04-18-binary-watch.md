---
title: Binary Watch
author: icyou
date: 2023-04-18 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Binary Watch
이진 시계에서 turnedOn 정수가 주어졌을 때, 그 수만큼 모든 경우를 구하는 문제입니다.

```
class Solution:
    def readBinaryWatch(self, turnedOn: int) -> List[str]:
        return ['%d:%02d' % (h, m) for h in range(12) for m in range(60)if (bin(h) + bin(m)).count('1') == turnedOn]
```
solution의 풀이입니다.
시간과 분에 대한 모든 경우를 가져와서, 시와 분을 이진수로 표현했을 때 1의 합이 turnedOn과 일치하는 경우에 대해서만 배열에 추가하는 방식으로 해결합니다.

```
class Solution:
    def readBinaryWatch(self, turnedOn: int) -> List[str]:
        possibleTimes = []
        time = "0000000000" 
        def solve(LED,p,time):
            if LED == 0:
                totalMinutes = int(time[4:],2)
                totalHours = int(time[:4],2)
                if totalMinutes < 10 and totalHours < 12:
                    possibleTimes.append(str(totalHours) + ":0" + str(totalMinutes))
                elif totalMinutes < 60 and totalHours < 12:
                    possibleTimes.append(str(totalHours) + ":" + str(totalMinutes))
            else:
                for i in range(p,10):
                    if time[i] == "0":
                        time = time[:i] + "1" + time[i+1:] #change
                        solve(LED-1,i,time) #recur
                        time = time[:i] + "0" + time[i+1:] #backtrack
        if turnedOn > 8:
            return possibleTimes #no possible solution
        solve(turnedOn,0,time)
        return possibleTimes
```
solution의 풀이입니다.  
이 풀이와 같이 backtracking 방식으로 풀어보려 했지만 잘 풀리지 않았습니다.


<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/binary-watch/solutions/88458/simple-python-java/](https://leetcode.com/problems/binary-watch/solutions/88458/simple-python-java/)
- [https://leetcode.com/problems/binary-watch/solutions/2195723/python-backtracking-beats-96-07/?languageTags=python](https://leetcode.com/problems/binary-watch/solutions/2195723/python-backtracking-beats-96-07/?languageTags=python)