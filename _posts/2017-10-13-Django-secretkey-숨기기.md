---
layout: post
title: "Django Secret Key Hiding"
date: 2017-10-07 10:08:00 +0800
lang: en
nav: post
category: Programing
tags: [Django, ]
---

# Django

## Secret Key 숨기기

django project의 settings.py에 있는  ```SECRET_KEY```를 숨겨야 한다.
이럴 경우 데이터를 외부에 저장해서 불러오도록 변경하는 것이 좋다.

```
>>> take .config_secret
```
.config_secret 디렉토리 생성

```
>>> touch settings_common.json
```
JSON 파일 생성

```json
{
	"django": {
		"secret_key": "<settings.py의 secretkey>"
	}
}
```

이렇게 파일을 제작 한다음  settings.py에 들어간다.

```python
# ROOT_DIR 변수 생성
# instagram_project/
ROOT_DIR = os.path.dirname(BASE_DIR)

# CONFIG_SECRET_DIR 변수 생성
# instagram_project/.config_secret/
CONFIG_SECRET_DIR = os.path.join(ROOT_DIR, '.config_secret')

# instagram_project/.config_secret/settings_common.json 파일을 열고 config_secret_common_str 변수에 저장 한다 .
with open(os.path.join(CONFIG_SECRET_DIR, 'settings_common.json')) as f:
    config_secret_common_str = f.read()

# json에서 받아온 문자열을 json.loads 함수를 이용해 dict 형태로 변경한다.
config_secret_common = json.loads(config_secret_common_str)
```


```python
SECRET_KEY = config_secret_common["django"]["secret_key"]
```
settings.py의 SECRET_KEY에 받아온 문자열을 딕셔너리 형태로 찾아 넣는다.
