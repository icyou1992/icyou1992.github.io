---
title: dockerfile 만들어보기
author: icyou
date: 2023-02-05 00:00:00 +0900
categories: [Infra, OS]
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
RUN: RUN 이전의 image를 기반으로 명령어들을 수행하고 새로운 image로 저장
WORKDIR: 명령어가 수행될 위치
COPY: host 내의 file 또는 directory를 container image 안으로 복사
CMD: container 내에서 실행할 file 또는 script

base image에서 container로 명령어를 실행하고, 변경된 내용을 이미지로 저장(RUN)한다.
Dockerfile의 한 줄, 한 줄이 계층화되어 image로 저장되며 한 줄씩 쌓이는 과정 모두 중간 image로 저장된다.
local에서 직접 build할 경우 중간 image에 접근하여 error가 생기는 경우를 해결하고 다시 build할 수 있다.


<br/><br/><br/><br/>
참고 
- [https://ajdkfl6445.gitbook.io/study/devops/docker/make-image](https://ajdkfl6445.gitbook.io/study/devops/docker/make-image)
- [https://www.44bits.io/ko/post/how-docker-image-work](https://www.44bits.io/ko/post/how-docker-image-work)
- [https://github.com/AI-Trolls/docker-tutorial/tree/master/docker-file-tutorial](https://github.com/AI-Trolls/docker-tutorial/tree/master/docker-file-tutorial)