---
layout: post
title: "PostgreSQL DB 백업후 S3로 업로드 하기"
date: 2018-06-04 10:20:00
lang: ko
nav: post
category: Programing
tags: [zsh, ubuntu]
---

## Ubuntu에 postgresql 설치하기

### 오류가 날 수 있는 부분 

가장 기초적인 아래의 방법으로 진행을 하게 되면 <s>나처럼</s> 오류가 발생해서 많이 헤매게 될 수 있다 

```
$ sudo apt-get update
$ sudo apt-get install postgresql
```

RDS를 사용한다면 요즘 기본으로 제일 위에 올라와 있는 버전이 `9.6.6`일 것이다.

하지만 상기 명령어로 설치를 하게 되면 ubuntu에 설치되는 버전은 `9.5.13`가 되며 아래와 같은 오류가 발생을 하며 진행이 되지 않을 것이다

```
pg_dump: server version: 9.6.6; pg_dump version: 9.5.13
pg_dump: aborting because of server version mismatch
```

### 해결 방법 

하기 명령어를 따라 친다 (ubuntu 16.04 기준)
> [https://www.postgresql.org/download/linux/ubuntu/](https://www.postgresql.org/download/linux/ubuntu/)

```
$ touch /etc/apt/sources.list.d/pgdg.list
$ deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main
$ wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install postgresql-9.6
```

자 다 끝났습니다. 아래의 명령어를 입력해 잘 되는지 확인합니다.

`$ pg_dump -U 유저이름 -h 호스트주소 디비이름 > ~/원하는위치.sql`

계속 상기와 같은 오류가 날 경우 아래의 명령어를 통해 9.5버전을 삭제합니다.

`$ sudo apt-get remove postgresql-9.5`


## boto를 이용해 업로드 하기

> [http://boto3.readthedocs.io/en/latest/reference/services/s3.html#S3.Client.upload_file](http://boto3.readthedocs.io/en/latest/reference/services/s3.html#S3.Client.upload_file)

백업 파일의 경로를 지정해줍니다. (해당 블로그는 /home/ubuntu/db/sql_backup_data/를 경로로 합니다.)

1. 기록이 계속 남지 않도록 백업용 폴더를 초기화 시켜줍니다. 

```python
import os
os.system('rm ~/db/sql_backup_data/dump_*sql')
```

2. 백업용 명령어를 작성 후 실행합니다. (파일을 날짜별로 작업하기 위해 datetime.datetime을 이용합니다.)

```python
import datetime

now = datetime.datetime.now()
date_str = '_'.join(map(str, [now.year, now.month, now.day]))

os.system('rm ~/db/sql_backup_data/dump_*sql')
backup_command = 'pg_dump -U %s -h %s %s > ~/db/sql_backup_data/dump_%s.sql' % (
	유저이름, 호스트 주소, DB이름, date_str
)

os.system(backup_command)

```

3. 데이터 업로드 진행 

```python
impoty boto3
client = boto3.client(
        's3', aws_access_key_id=S3엑세스키,
        aws_secret_access_key=S3시크릿엑세스키,
    )
    
client.upload_file(서버의 파일이름, 저장할 버킷이름, S3파일이름)
    
```

## crontab을 이용해 자동화 하기

2번에서 작업 하였던것을 함수화 시킨다 


```python
# dbbackup.py

import datetime
import os

import boto3


def db_backup():
    now = datetime.datetime.now()
    date_str = '_'.join(map(str, [now.year, now.month, now.day]))

    os.system('rm ~/db/sql_backup_data/dump_*sql')
    backup_command = 'pg_dump -U %s -h %s %s > ~/db/sql_backup_data/dump_%s.sql' % (
		유저이름, 호스트 주소, DB이름, date_str
	)
    file_name = "/home/ubuntu/db/sql_backup_data/dump_%s.sql" % date_str
    s3_file_name = "dump_%s.sql" % date_str
    os.system(backup_command)

    client = boto3.client(
        's3', aws_access_key_id=S3엑세스키,
        aws_secret_access_key=S3시크릿엑세스키,
    )
    
	client.upload_file(서버의 파일이름, 저장할 버킷이름, S3파일이름)

```

크론탭을 실행한다  `$ crontab -e`

다음 항목을 추가한다.

`0 18 * * * 파이썬경로 프로젝트경로/manage.py shell -c "from dbbackup import db_backup; db_backup()"`

앞에는 원하는 날짜 혹은 시간대이며 ec2의 ubuntu의 경우 utc를 이용하기때문에 `시간이 9시간 가량 늦다 주의하자!`

나처럼 shell에 -c를 이용해 import후 사용을 해도 되며 dbbackup.py에 아래의 항목을 추가 해 해당 파일을 불러올 경우 실행이 되도록하는 것도 가능하다!

```python
if __name__ == '__main__':
    db_backup()
```



## 추가 항목

PostgreSQL을 백업할때 비밀번호가 필요하여 작업이 안되는 경우가 있다. 아래와 같이 처리를 하면 된다

`$ sudo vi ~/.pgpass`

```
# ~/.pgpass
hostaddress:5432:dbname:dbusername:password
```

```
$ sudo chown ubuntu ~/.pgpass
$ chmod 600 ~/.pgpass

```
호스트, DB이름, DB유저이름, 비밀번호를 가진 pgpass라는 파일을 생성 후 user에서 소유권을 준뒤 600권한을 준다음 실행하면 된다.
