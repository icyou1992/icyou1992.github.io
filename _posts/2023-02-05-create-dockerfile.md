---
title: dockerfile 만들어보기
author: icyou
date: 2023-02-05 00:00:00 +0900
categories: [OS, docker]
tags: [OS, docker]
pin: true
math: true
---

### Dockerfile
docker image를 생성하는 file
```
FROM node:12-alpine
RUN apk add --no-cache python3 g++ make
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
```
FROM: docker.io hub에 등록된 OS image
RUN: docker image가 생성되기 전 수행할 shell 명령어들
WORKDIR: 명령어가 수행될 위치
COPY: 
CMD: container 내에서 실행할 file 또는 script

<br/><br/><br/><br/>
참고 
- [https://ajdkfl6445.gitbook.io/study/devops/docker/make-image](https://ajdkfl6445.gitbook.io/study/devops/docker/make-image)
- [https://www.44bits.io/ko/post/how-docker-image-work](https://www.44bits.io/ko/post/how-docker-image-work)
- [https://github.com/AI-Trolls/docker-tutorial/tree/master/docker-file-tutorial](https://github.com/AI-Trolls/docker-tutorial/tree/master/docker-file-tutorial)