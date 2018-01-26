---
layout: post
title: "Django Bootstrap Pagination Package"
date: 2018-01-12 21:51:00
lang: en
nav: post
category: Programing
tags: [Django, Bootstrap, Python Package]
---

# django bootstrap pagination package

## 사용법
[django-bootstrap-pagination](https://github.com/jmcclell/django-bootstrap-pagination)

`if 문을 사용해서 복잡하게 사용해야했던 Pagination 기능을 한줄로 간단하게 처리할 수 있게 해줌`

 - 기본

	```python
    {% raw %}
	{% bootstrap_paginate page_obj %}
    {% endraw %}
	```

	한줄만 적으면 끝

- range: 밑에 버튼으로 몇개를 표시해줄건지 범위를 정할 수 있음

	```python
    {% raw %}
	{% bootstrap_paginate page_obj range=숫자 %}
    {% endraw %}
	```

- show\_prev\_next: 이전 버튼, 다음버튼 표시 여부

	```python
    {% raw %}
	{% bootstrap_paginate page_obj show_prev_next="불리언" %}
    {% endraw %}
	```

- show\_first\_last: 처음과 마지막 버튼 표시 여부

	```python
    {% raw %}
	{% bootstrap_paginate page_obj show_first_last="불리언" %}
    {% endraw %}
	```

- 각종 파라미터 및 url변경 기능을 추가할 수 있어 편함



### Django 1.10+ 버전의 호환성 오류 확인

`urlreslovers` django  import Error 발생함 확인

django 1.10이후 `django.core.urlresolvers`가 `django.urls`로 변경됨

import 부분 해결 후 사용시 정상작동

**기존코드**

```python
# bootstrap_pagination.py

from django.core.urlresolvers import reverse, NoReverseMatch
```

**변경코드**

```python
try:
	from django.core.urlresolvers import reverse, NoReverseMatch
except ImportError:
	from django.urls import reverse, NoReverseMatch
```

<s>contibute 해보려고 했으나 이미 누군가 12월에 같은 코드로 pull requests 날렸던건 안비밀</s>

package가 잘 관리는 안되고 있으나 편하고 좋습니다.
