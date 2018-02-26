---
layout: post
title: "Django Custom Template Tag를 이용한 Dynamic navbar 만들기"
date: 2018-02-13 15:20:00
lang: en
nav: post
category: Programing
tags: [Python, Django]
---

# Django Custom Template Tag를 이용한 Dynamic Navbar 만들기 

navbar에 카테고리 필터항목을 집어넣고 싶은데 카테고리가 변경될때 마다 html작업을 하는게 <s>매우 귀찮아서</s> 실사용자가 하기 어려운 작업이기 때문에
자동으로 로드되는 카테고리 리스트가 필요했다.

기본적인 방법으로는 모든 view에 해당 queryset을 전달하여 처리하도록 할 수는 있으나 매우 비효율적이라고 느껴져 편하게 작업할 수 있는 번뜩이는 무언가가 필요해 작업을 하게되었다.

해당 내용을 알기전 어렵게 ajax요청으로 데이터를 받아와 jquery를 이용해 template을 재구성 하여 보내는 60줄이 넘는 코드에서 20줄이 내외정도 되는 코드로 해결을 할 수 있게 되었다.

[custom template tag 공식문서](https://docs.djangoproject.com/en/2.0/howto/custom-template-tags/)


## templatetags python 패키지 생성 

1. templatetags python 패키지를 생성합니다. 

	```
	app/
		__init__.py
		models.py
		...
		templatetags/
			__init__.py
			custom_tags.py
	```

2. 불러오는 위치는 상관 없지만 기본적으로 djangoapp안에 templatetags라는 python 패키지로 만들어야 합니다.<br>
        ex) blog app에 만들고 base.html에 적용시켜 어디서든 불러올 수 있습니다.
`관련있는 app에 생성하면 좋을 것 같습니다.`

## template tag생성 
1. 아래와 같이 template_tag를 생성합니다.

	```python
	from django import template
	register = template.Library()
	
	@register.assignment_tag
	def blog_categories():
	    return BlogMainCategory.objects.all()
	
	```
2. assignment_tag를 사용하는 것은 템플릿에서 템플릿변수 처럼 사용할 수 있어서입니다.
3. 표기법은 {% raw %} `{% tag명 as 변수명 %}`{% endraw %} 입니다.


## 실제 적용 코드 
{% raw %}

```html
{% blog_categories as blog_category_list %}
<ul class="submenu">
    {% for blog_category in blog_category_list %}
        <li class="has-submenu">
            <a href="">{{ blog_category }}</a>
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
