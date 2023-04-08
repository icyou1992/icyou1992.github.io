---
title: github blog 만들기
author: icyou
date: 2023-01-21 00:01:00 +0900
categories: [Life, Blog]
tags: [github, blog]
pin: false
---

# github blog
먼저, github는 개발자들이 인터넷을 통해 자신의 source code를 저장하는 저장소다.
여기서 개발자들이 github를 통해 source를 공개하면서 blog로 활용하는 것을 보고, github는 자신의 subdomain으로 web hosting을 할 수 있는 서비스까지 제공했다.
즉, github blog의 본질 또한 source code다.

# github blog 만들기
## 1. github에 회원가입을 한다.

## 2. github에 repository를 만든다. 
[**반드시 1. (myID.github.io)라는 이름, 2. public 설정으로 생성해야 한다.**]() 

이 repository에 blog의 source 및 contents가 저장된다.

## 3. index.html 만들기
index.html를 만들고 hello world로 해당 url이 homepage, blog로서 기능을 하는지 테스트한다. 해당 내용이 바로 반영되지는 않는다. (30분에서 1시간은 걸리는 것 같다.)

## 4. local에 해당 repository를 내려받는다. 
보통 `git clone`을 통해 내려받는다.(ex: C:\workspace\blog) 이는 web hosting 하는 것과는 관련이 없다. `git clone`으로 source 전부를 내려받고, `git push`로 수정한 내역 전체를 다시 올리는 것이 작업하기에 편리하기 때문에 내려받는다. 

(git이라는 명령어를 사용하기 위해 local에 git을 설치해야한다.)

git이 익숙하지 않은 경우, git desktop을 사용할 수도 있다.

## 5. jekyll theme을 고르고 내려받는다.  
[http://jekyllthemes.org/](http://jekyllthemes.org/)에서 마음에 드는 blog 테마를 골라, local에서 blog를 내려받은 곳에(ex: C:\workspace\blog) 덮어쓰기 한다. 기존의 테스트용 index.html(+ readme.md)은 삭제되어야 한다. 

## 6. local의 source를 github repository에 올린다.
`git push` 명령어를 통해 repository에 source를 올리고, myID.github.io에 반영되었는지 확인한다. 내용이 반영되는데는 시간이 좀 걸린다.