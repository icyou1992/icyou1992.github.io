---
title: linux package
author: icyou
date: 2023-01-29 00:00:00 +0900
categories: [Infra, OS]
tags: [OS, linux, package]
pin: true
math: true
---

## Linux Package
Linux에서 software를 실행하는 데 필요한 file들의 묶음
Windows에서 zip, msi와 같다.

## source package vs binary package
source packge 방식은 source code가 들어있는 package, compile해서 binary file을 만들어야 실행할 수 있다. 설치 시에 compile도 진행되어 설치 시간이 길다. <br/>
반면, binary package 방식은 compile된 binary가 들어있어 compile 과정이 생략되지만, source code를 수정할 수 없고, binary file에 필요한 특정 library나 다른 package가 없는 경우 같이 설치해주어야 한다. (package dependencies)

## Linux Packaging System 
1. Debian 계열(Debian, Ubuntu, ...): DEB => *.deb
2. RHEL 계열(Red Hat, Fedora, CentOS, ...): RPM => *.rpm

> Low Level Package Tool
- package 설치, 제거
1. Debian 계열(Debian, Ubuntu, ...): dpkg
2. RHEL 계열(Red Hat, Fedora, CentOS, ...): rpm

> High Level Package Tool
- package 설치, 제거, 검색, 의존성 해결을 위한 연관 package 자동 설치
1. Debian 계열(Debian, Ubuntu, ...): apt-get, apt, aptitude
2. RHEL 계열(Red Hat, Fedora, CentOS, ...): yum, dnf

### Linux Package Repository
- package들을 가지고 있는 저장소, install 명령어를 날리면 저장소의 해당 url에서 package를 가져온다.
- apt-get, apt의 경우, /etc/apt/sources.list 경로에 저장된 url에 package의 metadata가 있다면 인터넷을 통해 해당 url에서 package와 연관된 package를 같이 자동 설치해준다.
- yum의 경우, 경로는 /etc/yum.repos.d 이다.
- package 설치 과정
![Desktop View](/assets/img/posts/20230129/linux-package-manager-explanation.webp){: .w-70 .normal}




<br/><br/><br/><br/>
참고 
- [https://bradbury.tistory.com/227](https://bradbury.tistory.com/227)
- [https://minhan2.tistory.com/entry/%EB%A6%AC%EB%88%85%EC%8A%A4-%ED%8C%A8%ED%82%A4%EC%A7%80-%EB%B9%84%EA%B5%90aptdpkgyumrpm](https://minhan2.tistory.com/entry/%EB%A6%AC%EB%88%85%EC%8A%A4-%ED%8C%A8%ED%82%A4%EC%A7%80-%EB%B9%84%EA%B5%90aptdpkgyumrpm)