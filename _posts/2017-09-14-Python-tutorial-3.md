---
layout: posten
title: "Python Tutorial 3"
date: 2017-09-14 10:08:00 +0800
lang: en
nav: post
category: Programing
tags: [Python, ]
---

# 제어문
## if, elif, else(조건문)
기본형태

```python
if 조건:
	조건이 참일 경우
else:
	조건이 참일 경우
```

중첩 조건문

```python
if 조건1:
	조건1이 참일 경우
else:
	조건1이 거짓일 경우
	if 조건2:
		조건1은 거짓이나 조건2는 참일 경우
	else:
		조건1,2 모두 거짓일 경우

```
상위 같은 중첩 조건문의 경우 ```elif```를 사용하려 줄여쓸 수 있음

```python
if 조건1:
	조건1이 참일 경우
elif 조건2:
	조건1은 거짓이나 조건2가 참일 경우
else:
	조건1,2 모두 거짓일 경우
```
## 조건 표현식
```python
참일경우 if 조건식 else 거짓일 경우
```

예시

```python
is_holiday = True
print("Good") if is_holiday else print("Bad")
```


## 중첩 조건 표현식
```
조건1이 참일 경우 if 조건1 else 조건1은 거짓이나 조건2가 참일 경우 if 조건2 else 조건1,2가 모두 거짓일 경우
```


# 순환문

## for문(조건에 따른 순회)
