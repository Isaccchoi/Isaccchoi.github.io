---
layout: post
title: "MacOS illegal hardware instruction Error"
date: 2018-12-13 23:20:00
lang: ko
nav: post
category: Programing
tags: [brew, python, MacOS]
---

## MacOS 에 illegal hardware instruction 오류가 날 경우 대청 방법

Mac OS X 업데이트 이후 이전에 Brew에서 설치한 프로그램과 충돌이 날 경우 문제가 발생할 수 있음 

## 해결 방법 
`brew install`을 통해서 설치한 항목들을 다시 설치합니다.

```
$ brew list | xargs brew reinstall -v  
```

