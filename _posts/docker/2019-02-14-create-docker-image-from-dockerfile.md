---
layout: post
title: Dockerfile로부터 docker image 만들기
category: docker
tags: [docker]
comments: true
---

# Docker build 명령어
```
docker build [OPTIONS] PATH | URL | -
```

# Build 방법
1. Dockerfile을 작성한다.
2. Dockerfile이 있는 경로에서 `docker build`를 실행(tag 지정을 하려면 -t 옵션 뒤에 tag 명 입력)


# Build 확인
```bash
docker images -a
```
