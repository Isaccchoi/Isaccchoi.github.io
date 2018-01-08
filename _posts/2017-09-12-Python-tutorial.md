---
layout: posten
title: "Python Tutoral 1"
date: 2017-09-12 12:08:00 +0800
lang: en
nav: post
category: Programing
tags: [Python, ]
---

pluginslugins=({ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting)
n버전**을 관리하기 위해 사용 함


방향키 관련 이슈가 일어날 수 있기 때문에 하기 명령어로 readline 및 xz를 설치 한다
```
brew install readline xz
```

[Pyenv - Github](https://github.com/pyenv/pyenv/wiki/Common-build-problems)

pyenv global [python version]
시스템에서 사용하는 python에 대한 버전을 pyenv에서 설치한 버전으로 변경

---

### virtualenv
프로젝트별로 Python **개발환경** *(python 패키지 설치 환경)*을 관리하기 위해 사용 함


---


### pyenv-virtualenv
pyenv 제작자가 pyenv 사용시 virtualenv 사용이 편리하도록 만듬

pyenv에서 python 버전 다운로드 이후
```
pyenv virtualenv [python version] [virtualenv name]
```
을 입력 하여 새로운 virtualenv를 만든다

그다음 작업하길 원하는 디렉토리에 들어가 ```pyenv local [virtualenv name] ```을 입력하여 해당 디렉토리에서 pyenv-virtualenv를 적용한다


---


### 용어
--
#### 리터럴
변하지 않는 고정된 데이터


1. 정수형
2. 문자열
3. 부동소수정

#### 표현식
값을 의미하는 표현 또는 값을 반환하는 표현

```
sec=60

365*24*sec
```


#### 구문
값의 의미를 지니지 않으며, 어떠한 목적을 수행하는 코드

```
>>> for char in '안녕하세요':
...   print(char)
...
```

### 변수
--
파이썬의 모든것이 객체(Object)<br>
객체는 데이터의 형태를 결정해주며, 객체의 타입을 변경할 수 없다.

```python
a = 35
```
상기와 같은 코드를 작성했을때 35라는 객체가 변경되지 않는다는 것이며 35의 메모리상의 위치를 가르키는 a는 언제든지 변할 수 있다

*변수**는 <U>이름이며, 데이터를 갖는 것이 아니다.</u>

#### 변수의 타입 확인
type 함수 사용  ```type(var1)```

#### 변수의 이름 제한
예약어 사용불가,숫자로 시작 불가, 대문자로 시작은 가능하나 대문자로 쓰지 않음, 언더스코어(_) - 언더스코어는 특별한 처리방법을 따르므로 일반적으로 사용하지 않는다

#### 변수의 입출력
input, print 함수 사용
```
input()
print()
```


### 숫자
--
연산자|설명|예|결과
---|---|---|---|
\+  | 더하기        | 32 + 7    | 39
\-  | 빼기      | 82 - 2    | 80
\*  | 곱하기        | 3 * 7 | 21
/   | 나누기        | 7 / 2 | 3.5
//  | 정수나누기    | 7 // 2    | 3
%   | 나머지        | 7 % 3 | 1
**  | 지수      | 2**10 | 1024
