---
layout: post
title: "Python Regular Expression"
date: 2017-09-18 10:08:00 +0800
lang: en
nav: post
category: Programing
tags: [Python, ]
---

# Regular Expression

## Match
처음에서 부터 일치하는 문자열을 찾으며 Match object를 리턴

## Search
*첫번째* 일치하는 패턴을 찾는다.

## findall
일치하는 *모든 패턴*을 찾는다

## split
패턴으로 나눈다
*string의 split과 유사*하다

## sub
패턴 대체하기
*string의 replace와 비슷*하다

## 정규표현식의 패턴 문자

패턴 | 문자
---|---
\d|숫자
\D|비숫자
\w|문자
\W|비문자
\s|공백 문자
\S|비공백 문자
\b|단어 경계(\w \W의 경계)
\B|비단어 경계


## 정규표현식의 패턴 지정자(Pattern specifier)

패턴|의미
---|---
abc|리터럴```abc```
(expr)|expr
expr1\|exprt2|exprt1또는 expr2
```.```|```\n```을 제외한 모든 문자
```^```|소스 문자열의 시작
```$```|소스 문자열의 끝
expr```?```| 0또는 1회의  expr
expr```*```| 0회 이상의 최대 expr
expr```*?```|0회 이상의 최대 expr
expr```+```|1회 이상의 최대  expr
expr```+?```|1회 이상의 최소 expr
expr```{m}```|m회의 expr
expr```{m,n}```|m에서 n회의 최대 expr
expr```{m,n}?```|m에서 n회의 최소 expr
[abc]|a or b or c
[^abc]|not(a or b or c)
expr1(?=expr2)|뒤에 expr2가 오면 expr1에 해당하는 부분
expr1(?!expr2)|뒤에 expr2r가 오지 *않으면* expr1에 해당하는 부분
(?<=expr1)expr2|앞에 expr1이 오면 expr2에 해당하는 부분
(?<!expr1)expr2|앞에 expr1이 오지 *않으면* expr2에 해당 하는 부분
