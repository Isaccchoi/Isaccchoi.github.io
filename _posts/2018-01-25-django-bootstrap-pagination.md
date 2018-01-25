---
layout: post
title: "Django Bootstrap Pagination Package"
date: 2018-01-12 21:51:00
lang: en
nav: post
category: Programing
tags: [Django, Boostrap, pip]
---

# django-bootstrap-pagination

## 사용법
[django-bootstrap-pagination](https://github.com/jmcclell/django-bootstrap-pagination)

 - 기본 

	```
	{% bootstrap_paginate page_obj %}
	```
	한줄만 적으면 끝

- range: 밑에 버튼으로 몇개를 표시해줄건지 범위를 정할 수 있음

	```
	{% bootstrap_paginate page_obj range=숫자 %}
	```
	
- show\_prev\_next: 이전 버튼, 다음버튼 표시 여부

	```
	{% bootstrap_paginate page_obj show_prev_next="불리언" %}
	```
- show\_first\_last: 처음과 마지막 버튼 표시 여부 

	```
	{% bootstrap_paginate page_obj show_first_last="불리언" %}
	```
	
- 각종 파라미터 및 앵커 등등 추가 가능


### Django 1.10+ 버전의 호환성 오류 확인 

`urlreslovers` django  import Error 발생함 확인

django 1.10이후 `django.core.urlresolvers`가 `django.urls`로 변경됨 

import 부분 해결 후 사용시 정상작동

<s>contibutor 해보려고 했으나 이미 누군가 12월에 같은 코드로 pull requests 날렸던건 안비밀</s>

package가 잘 관리는 안되고 있으나 편함 