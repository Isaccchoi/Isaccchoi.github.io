---
layout: post
title: "Template context-processors를 사용하여 데이터 마음대로 로드하기"
date: 2018-03-02 10:20:00
lang: en
nav: post
category: Programing
tags: [Python, Django]
---

[지난 블로그](http://blog.isaccchoi.com/programing/Django-Custom-Template-Tag%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-Dynamic-Navbar-%EB%A7%8C%EB%93%A4%EA%B8%B0/)에서 custom template tag를 이용해 데이터를 로드 하는 방법에 대한 글을 적었다.
금일 스터디에서 조금 더 편하고 정석적인 방법을 알게되어 소개하고자 한다.

## template context-processors
[context-processors 공식문서](https://docs.djangoproject.com/en/2.0/ref/templates/api/#writing-your-own-context-processors)
간단히 정리하자면 HttpRequest를 인수로 사용하고 사전형(dict) 반환해준다는 내용이다.<br>
설명보다는 코드를 보는게 더 이해가 빠르다.

## 함수 생성 
1. 루트디렉토리(manage.py와 같은 위치)에 python package를 하나 생성한다.
2. 해당 블로그에서는 utils라는 이름으로 생성하였다.<br>
3. 해당 패키지 아래에 context_processors라는 파이썬 파일을 하나 생성한다.(이름을 꼭 맞출 필요는 없는 것 같다)
4. 간단하게 위에서 말한 내용처럼 HttpRequest를 인수로 받으며 dict형을 반환하는 간단한 함수를 제작한다.


```python
# utils/context_processors.py

def categories(request):
    return {'blog_categories': BlogMainCategory.objects.all(), }
```

## settings.py 설정 
생성한 함수를 어디서든 불러올 수 있어야하므로 settings.py의 template(template변수로 사용할 것이므로)의 `options` 아래의 `context_processors`에 넣어준다.

```python
# settings.py
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        ...
        'OPTIONS': {
            'context_processors': [
            		...
            		'utils.context_processors.categories',
            ],
        },
    },
]

```

## 사용 
이제 준비는 다 끝났다 그대로 가져와 사용만 하면 된다. 지난번에 하던것처럼 {% raw %}`{% load custom_tags %}`{% endraw %}같은 내용도 필요 없다 **바로** 템플릿에서 사용할 수 있다.

{% raw %}

```
<ul class="submenu">
    {% for blog_category in blog_categories %}
        <li class="has-submenu">
            <a>{{ blog_category }}</a>
            <ul class="submenu">
                {% for subcategory in blog_category.blogsubcategory_set.all %}
                    <li><a href="{{ subcategory.get_absolute_url }}">{{ subcategory.name }}</a></li>
                {% endfor %}
            </ul>
        </li>
    {% endfor %}
</ul>
```

{% endraw %}

### 날로 먹는 개발 블로그 끝! ㅏㄱ