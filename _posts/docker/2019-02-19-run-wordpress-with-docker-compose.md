---
layout: post
title: Docker compose로 wordpress 구동하기
category: docker
tags: [docker]
comments: true
---

# Docker compose로 wordpress 구동하기

## Docker compose 설치
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose version
```

## docker-compose.yml 파일 작성
docker-compose.yml 파일을 아래와 같이 작성한다.
```yml
version: '3.3'

services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
       WORDPRESS_DB_NAME: wordpress
volumes:
    db_data: {}
```
실행하려면 아래 명령어를 입력한다. background에서 실행시키려면 -d 옵션을 추가로 입력한다.
```bash
$ docker-compose up
```


# 참고
## Docker volume
컨테이너 내부 지정된 path에 저장될 내용은 모두 host에 저장하는 옵션.
### 볼륨 목록 조회
```bash
$ docker volume ls
```
### 저장된 경로 확인
```bash
$ docker volume inspect <volume_name>
```

## 참고 사이트
* https://docs.docker.com/compose/install/
* https://docs.docker.com/compose/wordpress/
* https://www.joinc.co.kr/w/man/12/docker/Guide/DataWithContainer