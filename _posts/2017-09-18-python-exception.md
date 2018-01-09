---
layout: post
title: "Python Exceptions"
date: 2017-09-18 10:08:00 +0800
lang: en
nav: post
category: Programing
tags: [Python, ]
---

# 예외처리

#### 기본 형태

```python
try:
	시도할코드
except:
	예외가 발생했을 경우 실행할 코드

```
해당 형태일 경우 try안에서 여러 오류가 발생할때 대응을 할 수 없다.

#### 여러가지 예외를 구분할 경우

```python
try:
	시도할 코드
except 에러클래스1:
	에러클래스1이 발생할 경우 시도할 코드
except 에러클래스2:
	에러클래스2가 발생할 경우 시도할 코드
```

#### 에러사항을 변수로 사용할 경우

```python
try:
	시도할 코드
except 에러클래스1 as 변수명:
	변수명을 사용한 코드
```

### try ~ else
```else```문은 ```try```이후 에러가 발생하지 않을 경우 실행 된다.

```python
try:
	시도할 코드
except:
	예외 발생시 시도할 코드
else:
	예외가 발생하지 않을 경우 시도할 코드
```

## try ~ finally
```python
try:
	시도할 코드
except:
	예외 발생시 시도할 코드
finally:
	예외가 발생을 하던지 안하던지 무조건 마지막에 실행을 할 코드
```
