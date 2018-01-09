---
layout: post
title: "Python File Handling"
date: 2017-09-18 10:08:00 +0800
lang: en
nav: post
category: Programing
tags: [Python, ]
---

# 파일 다루기
```python
변수 = open(파일명, 모드)
```
#### 모드의 첫 번째 글자
모드|설명
---|---
r|읽기
w|쓰기 (파일이 이미 존재할 경우 덮어쓴다)
x|쓰기 (단, 파일이 존재하지 않을 경우에만)
a|추가 (파일이 존재할 경우 파일의 끝부터 쓴다)


#### 모드의 두 번째 글자

모드|설명
---|---
t 또는 없음|텍스트타입
b|이진데이터 타입
