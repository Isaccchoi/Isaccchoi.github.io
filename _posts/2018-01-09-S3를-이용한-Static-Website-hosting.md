---
layout: post
title: "S3를 이용한 정적사이트 웹 호스팅"
date: 2018-01-09 17:12:00
lang: en
nav: post
category: Programing
tags: [AWS, S3, Deploy]
---

# S3를 이용한 Static Website hosting

## Bucket 생성

S3 콘솔: [https://s3.console.aws.amazon.com/](https://s3.console.aws.amazon.com/)

1. 콘솔에 접속하여 `버킷 만들기` 버튼을 눌러 새로운 버킷을 생성한다.
2. 이름을 입력하고 `다음`을 누른다.
3. 버킷의 이름은 `DNS`형식이여야하며 배포시 URL로 사용을 할 것이기 때문에 연결할 `URL이름`으로 지정한다.
![버킷생성](/images/s3_deploy/create_bucket.png)
4. 속성은 따로 지정을 하지 않고 `다음`을 누른다
5. 권한 설정에서 퍼블릭 권한관리 부분을 `이 버킷에 퍼블릭 읽기 권한을 부여함`으로 변경한다.
![버킷권한](/images/s3_deploy/bucket_permission.png)
6. `버킷 만들기`를 눌러 버킷 생성을 완료 한다.

## Bucket 업로드 및 설정

1. 버킷 리스트에서 생성한 버킷 이름을 눌러 들어간다.
2. `업로드` 버튼을 눌러 파일을 업로드한다.(드래그 앤 드롭 으로 하면 편하다)
3. 업로드 하는동안 `속성`탭에 들어간다
4. `정적사이트 웹 호스팅`에 들어간다.
5. `이 버킷을 사용하여 웹 사이트를 호스팅합니다`를 선택한다.
6. 빌드된 파일에 맞는 index문서를 입력한 후 저장을 누릅니다.
![bucket-property](/images/s3_deploy/static_web_site_hosting.png)
7. `권한` 탭에 들어갑니다.
8. `버킷 정책`을 클릭합니다.
9. 아래의 코드를 각자에 맞게 변경하여 작성후 `저장`합니다.

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": {
                "AWS": "*"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::<<bucket name>>/*"
        }
    ]
}
```

업로드 및 위의 설정이 완료되었으면 `속성`탭의 `정적 사이트 웹 호스팅`에 들어가 `엔드포인트`에 적혀 있는 URL에 들어갑니다.
사이트가 정상 구동 된다면 <span style='font-size: 20px;'>**성공!!!**</span>
![bucket-deploy](/images/s3_deploy/deploy_complete.png)
