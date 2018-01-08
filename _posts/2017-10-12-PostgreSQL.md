---
layout: posten
title: "PostgreSQL"
date: 2017-10-12 10:08:00 +0800
lang: en
nav: post
category: Programing
tags: [SQL, ]
---

# PostgreSQL

```
>>> brew install postgresql
```
브루를 이용해 postgresql 설치

```
>>> brew services start postgresql
```
브루에서 postgresql 서비스를 자동으로 시작하도록 설정

```
>>> createdb <db 이름> --owner=<user 이름>
```
DB를 생성하며 해당 DB의 소유자를 지정


```
>>>python manage.py dumpdata inheritance making_queries model --indent=4 > dump.json

```
기존에 있던 데이터를 살리기 위해 **dump.json**파일로 빼냅니다.

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': '<db name>',
        'HOST': '<host address>',
        'PORT': '5432',
        'USER': '<user name>',
        'PASSWORD': '<passwords>',
    }
}
```
settings.py에 다음과 같은 형식으로 작성을 합니다.


 - 로컬에서 사용시 HOST에는 localhost를 입력합니다.
 - Password에 User password를 입력하고 없을 경우 공백으로 놓습니다.

```
>>> python manage.py migrate
```
새로운 DB(Postgresql)에 테이블 구조를 생성합니다.

```
>>> python manage.py loaddata dump.json
```
dump.json에서 데이터를 로드해서 새로운 DB에 불러 옵니다.
