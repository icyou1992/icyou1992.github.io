---
title: Design Underground System
author: icyou
date: 2023-05-31 00:00:00 +0900
categories: [Computer Science, Algorithm]
tags: [Algorithm, Leetcode]
pin: false
math: true
---

## Leetcode Problem

### Design Underground System
UndergroundSystem class에서 checkIn과 checkOut 함수가 주어졌을 때 두 함수를 이용해 getAverageTime 함수를 구하는 문제입니다.

```
class UndergroundSystem:

    def __init__(self):
        self.d = {}

    def checkIn(self, id: int, stationName: str, t: int) -> None:
        self.d[id] = {}
        self.d[id][stationName] = self.d[id][stationName] + t if stationName in self.d[id] else t
        print(self.d)

    def checkOut(self, id: int, stationName: str, t: int) -> None:
        self.d[id][stationName] = self.d[id][stationName] + t if stationName in self.d[id] else t
        print(self.d)

    def getAverageTime(self, startStation: str, endStation: str) -> float:
        time, cnt = 0, 0
        for id in self.d:
            if startStation in self.d[id] and endStation in self.d[id]:
                time += self.d[id][endStation] - self.d[id][startStation]
                cnt += 1
        return time / cnt
```
해당 풀이는 dictionary 안에 dictionary를 써서 endStation과 startStation을 구분할 수 없기 때문에 틀렸습니다.  

```
class UndergroundSystem:

    def __init__(self):
        self.journey = {}
        self.history = {} # (startStation, endStation) => (allTime, allCount)

    def checkIn(self, id: int, startStation: str, t: int) -> None:
        self.journey[id] = (startStation, t)
        

    def checkOut(self, id: int, endStation: str, endTime: int) -> None:
        startStation, startTime = self.journey.pop(id)
        key = (startStation, endStation)
        allTime, allCount = self.history.get(key, (0, 0))
        self.history[key] = (allTime + (endTime - startTime), allCount + 1)
        

    def getAverageTime(self, startStation: str, endStation: str) -> float:
        key = (startStation, endStation)
        allTime, allCount = self.history.get(key, (0, 0))
        return allTime / allCount
```  
solution의 풀이입니다.  
checkOut 실행 시에 journey에서 pop한 후에 startStation, endStation으로 key를 만들고 간 시간(도착 시각 - 출발 시각)과 평균을 구하기 위한 횟수를 history dictionary에 저장합니다.  
getAverageTime 함수에서 간 시간과 횟수를 나누어 평균을 구합니다.


 
<br/><br/><br/><br/>
참고 
- [https://leetcode.com/problems/design-underground-system/submissions/960934236/](https://leetcode.com/problems/design-underground-system/submissions/960934236/)