---
layout: post
title: "Django-extensions를 이용한 ERD 만들기"
date: 2018-02-08 13:29:00
lang: ko
nav: post
category: Programing
tags: [Python, Django, Python Package, ERD]
---

# Django-extensions를 이용한 ERD만들기

[django-extentions graph 공식 문서](http://django-extensions.readthedocs.io/en/latest/graph_models.html)

## Django-extensions 설치 
pip를 이용해 django-extions를 설치합니다.<br>
`$ pip install django-extionsions`

settins.py의 INSTALLED\_APPS에 django\_extensions를 넣어줍니다. 

```python
# settions.py
INSTALLED_APPS = (
    ...
    'django_extensions',
)

```
그룹모델 지정 

```python
# settings.py
GRAPH_MODELS = {
  'all_applications': True,
  'group_models': True,
}

```

기본적으로 Django-extensions에 있는 graph model기능을 이용해 dot파일을 생성할 수 있습니다.

`$ ./manage.py graph_models -a > my_project.dot`

![dot file](/images/erd/dot.png)
위와 같이 기본적으로 볼 수는 있으나 보기가 편하지는 않습니다.
조금 더 이쁘게 보기 위해 graphviz 설치가 필요합니다. 

## graphviz

공식문서에는 `$ pip install pygraphviz`를 하면 된다고 나와 있으나 그냥 설치를 하게 되면 오류가 발생을 합니다.

로컬에 graphviz설치가 선행이 되어야합니다.

```$ brew install graphviz```

설치가 완료된 후 `$ pip install pygraphviz`

`$ /manage.py graph_models -a -g -o my_project_visualized.png`

![graphviz](/images/erd/graphviz.png)

위와 같이 그림으로 조금 더 보기 쉽게 바꿀 수 있습니다.

## 원하는 모델만 출력하기 

위의 사진에서 보게 되면 Django에서 기본적으로 만들어놓은 여러 모델들때문에 보기가 이쁘지는 않습니다.

원하는 모델만 출력을 하도록 변경을 해봅니다.

`$ ./manage.py graph_models -a -I User,Center,WorkOutRecord -o my_project_want_model.png`

![just want model](/images/erd/my_project_include.png)
