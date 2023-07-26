---
title: Jenkins -> Windows
author: icyou
date: 2023-07-01 00:00:00 +0900
categories: [CICD, Jenkins]
tags: [Jenkins, Windows]
pin: true
math: true
---

### Jenkins -> Windows
- Jenkins에서 Windows 서버로 pipeline을 구성할 때 원격으로 명령을 내리기 위해서는 WinRM client, Publish Over SSH 등의 Plugin을 사용할 수 있습니다.

- winrm을 사용할 경우 서버에서 winrm을 활성화시켜야 하고, ssh를 사용할 경우 openssh를 활성화시켜야 합니다.

- build file 실행을 서비스로 등록을 하면 안정성을 높일 수 있습니다.

- build file을 그대로 덮어쓰면 해당 file은 사용 중이므로 에러가 발생하며 pipeline이 실패합니다. 덮어쓰기 전에 기존 file을 삭제해야 하는데, 서비스로 해당 file이 실행 중인 경우 중지되는 데에 수 초가 걸릴 수 있으므로 중지하고 바로 삭제하려할 때 여전히 실행중인 경우가 있을 수 있습니다.(해당 원인은 log도 찍히지 않아, 찾느라 시간을 많이 썼습니다.) 문제를 해결하기 위해서는 삭제 전 실행 중인지 check하는 batch script를 작성하거나 sleep, timeout 등을 활용해야 합니다.

- log가 찍히지 않아 원인을 찾기 어려운 경우, stage를 세분화하면 최소한 어디서 문제가 발생하는 것인지 추측할 수 있습니다.




<br/><br/><br/><br/>
참고  
- [https://svrforum.com/software/76940](https://svrforum.com/software/76940)
- [https://www.lainyzine.com/ko/article/how-to-run-openssh-server-and-connect-with-ssh-on-windows-10/](https://www.lainyzine.com/ko/article/how-to-run-openssh-server-and-connect-with-ssh-on-windows-10/)