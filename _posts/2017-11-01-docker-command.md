---
layout: posten
title: "Docker Command"
date: 2017-11-01 10:08:00 +0800
lang: en
nav: post
category: Programing
tags: [Docker, ]
---

# Docker

## 커멘드

### docker ps
돌아가고 있는 컨테이너를 보여줌

### docker ps -a
돌아가지 않고 있는 컨테이너도 보여줌


### docker exec
run되어 있는 컨테이너에 들어간다

### docker stop
run되고 있는 컨테이너를 중지 시킨다

### docker run -p <컨테이너밖 포트>:<컨테이너안 포트>
포트를 연결 시켜줌 <컨테이너밖 포트>에 접속하면 <컨테이너안 포트>로 연결이 된다.
