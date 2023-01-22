---
title: 컴퓨터 개론
author: icyou
date: 2023-01-22 00:00:00 +0900
categories: [Computer Science]
tags: [cs, computer science, 개론, introduction]
pin: true
---

대학교 1학년 때 공부했던 교재를 복습하며 내용을 정리하자.

<br/><br/>

## 컴퓨터 구성

| 중앙처리장치 | CPU | CU(Control Unit), ALU(Arithmetic Logic Unit), Register |
| 주기억장치 | Memory | RAM, ROM |
| 보조기억장치 | Disk, Storage | HDD, SSD, Magnetic Tpe |
| 입력장치 | | Mouse, Keyboard |
| 출력장치 | | Speaker, Monitor |

```
- CU: 제어 장치: 프로그램 명령어 수행
- ALU: 연산 장치: 제어 장치에 의해 연산 수행
- Register: 명령어 수행 중간 과정 또는 결과 저장

- RAM: 휘발성 (컴퓨터를 껐다 켜면 실행했던 프로그램들은 종료된다.)
- ROM: 비휘발성 (컴퓨터를 껐다 켜더라도 BIOS(Basic Input/Ouput System)는 잘 실행된다.)

- CPU와 Memory는 bus를 통해 장치들끼리 통신하며, 입출력 장치와 통신하기 위해서는 포트(port)를 사용한다.
```

<br/><br/>

## 데이터 표현

- [허프만 코딩]()<br/>
사용 빈도 수가 높은 문자를 적은 bit 코드로 변환하여 전체 데이터를 표현하는 데 필요한 bit의 양을 줄인다. 중요한 점은 문자의 코드를 결정할 때, 많은 빈도로 연결한 두 개의 노드가 [새로운 노드]()가 되어 다시 연결된다는 것이다. 

- [2의 보수 표현에서 1을 더하는 이유]()<br/>
1bit는 2개의 수를 저장할 수 있는 공간이다.
주어진 bit에서 0은 1로, 1은 0으로 바꾸는 보수로 음수를 표현하게 되면, 양수는 음수로 바뀌게 되고, +0도 -0으로 바뀐다.(ex: 0000: +0 -> 1111: -0) 하지만 +0과 -0은 같은 0이므로 모든 음수가 차지하는 공간에 1을 더해줌으로써 -0이 차지하는 공간을, +0이 차지하는 공간과 일치시키며 없애준다.
+ 1의 보수 표현에서는 1을 더하는 연산을 하지 않기 때문에 연산 과정에서 cpu의 부하를 줄일 수 있다는 장점이 있고, 2의 보수 표현은 메모리를 확보할 수 있다는 장점이 있을 것이다.

<br/><br/>

## 운영체제(OS: Operating System)
> hardware의 자원을 효율적으로 사용하기 위해 program의 실행 routine을 관리한다.

### OS 작동 과정
1. 전원 켜기
2. ROM에 저장된 BIOS program을 RAM에 올려서 실행 
3. BIOS가 MBR에 저장된 Boot Loader를 RAM에 올려서 실행 
4. Boot Loader가 OS를 RAM으로 옮겨 실행 
> 전원 -> BIOS -> Boot Loader -> OS

### PCB(Process Control Block)
> OS는 process를 제어하기 위해 PCB를 따로 만들어 관리한다.
> PCB는 process의 상태값, 카운터 값, scheduling 정책, 우선 순위, RAM 정보 등을 저장하고 있다.

### Process Scheduling
> multi programming 환경에서 process가 대기 중일 경우 다른 process의 실행을 정하는 정책
1. FCFS(First Come First Served): 먼저 들어온 process의 실행 시간이 길 경우, 나머지 process는 대기 시간이 길어짐
2. Round Robin: Context switch 중에는 process가 실행되지 않으므로 적절할 시간을 할당해야 함
3. 우선 순위: 우선 순위가 낮은 경우 aging을 통해 starvation을 해결 가능

### Memory 관리
> program의 크기가 여분의 RAM보다 큰 경우를 위해 program 실행에 필요한 부분만 RAM에 올리는 가상 memory 방식을 사용한다.
- 이 방식을 구현하기 위해 process를 작은 단위로 쪼개어(paging) 실행에 필요한 page만 RAM의 작은 단위(frame)에 올린다.

```
Page Replacement Algorithm
1. FIFO(First In First Out) -> 성능이 좋지 않음
2. LRU(Least Recently Used) -> 성능이 제일 나음
3. LFU(Least Frequently Used) -> 가장 최근에 부른 페이지가 교체될 수 있음
```

### File system 관리
> MBR(Master Boot Record): Boot Loader가 저장되어 있는 영역, disk의 가장 첫번째 주소에 위치
> exFAT, NTFS, UFS, ext4 기타 등등
> linux의 경우 inode는 pcb와 유사하게 file에 대한 다양한 정보를 저장한다. 
> file의 크기가 너무 커서 inode에 저장할 pointer의 개수를 넘어가면(10개), file block들의 pointer(주소)를 저장된 간접 block pointer를 사용한다.

- Linux File directory <br/>
![Desktop View](/assets/posts/20230122/File_system_tree.jpg){: .w-70 .normal}





<br/><br/><br/><br/>
참고 : [한빛 미디어 컴퓨터 개론](https://www.hanbit.co.kr/store/books/look.php?p_code=B1315669526)

 