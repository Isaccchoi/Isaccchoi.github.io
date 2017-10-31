# Docker

[참고사이트](https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html)


깃헙같은 것이나 프로젝트 단위가 아닌 운영체제 단위로 작동한다고 보면 됨

Dockerfile을 작성하여 도커를 생성 후 설치해야될 패키지를 작성

```docker
FROM			ubuntu:16.04
MAINTAINER	isaccchoi@naver.com
RUN				apt-get update
```
- FROM: 사용할 OS
- MAINTAINER: 소유자의 이메일 주소 
- RUN: 실행할 용어

```docker
docker build -t base . -f Dockerfile.base .
```
Dockerfile.base파일을 이용하여 도커 이미지 생성 
