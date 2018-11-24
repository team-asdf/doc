---
title: YABOJA API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

국민대학교 소프트웨어융합대학 소프트웨어학부 오픈소스소프트웨어 수업의 TEAM-asdf 입니다.
YABOJA 서비스의 API Reference 입니다.

# Contents

```shell
curl http://angelbeats.tk:3000/api/v1/contents/:page
```

> Example data

```json
[
  {
    "idx": 1,
    "title": "Serverless microservice architecture에서의 inter-communication caching",
    "content": "빙글은 8월에 진행된 서비스 리뉴얼과 함께, 기존의 Ruby on rails 기반의 monolithic 앱에서 구현되어 있던 서비스 로직을 상당부분 Serverless 기반의 microservice architecture로 옮겼다.그걸 하면서도 정말 많은걸 배웠고, 그 과정에서 필요했던 다양한 도구들 (Lambda용 http api framework라던가...",
    "url": "https://medium.com/vingle-tech-blog/serverless-microservice-architecture%EC%97%90%EC%84%9C%EC%9D%98-inter-communication-caching-80a43c979121?source=---------8---------------------",
    "cnt": 6,
    "source": "medium",
    "keyword": "serverless,microservice,architecture",
    "image": null,
    "createdAt": "2017-10-22"
  }
]
```

모든 Article 들을 page 별로 반환합니다.

### HTTP Request

`GET http://angelbeats.tk:3000/api/v1/contents/:page`

### Query Parameters

Parameter | Description
--------- | -----------
page | Page의 숫자

# Select Contents
```shell
curl http://angelbeats.tk:3000/api/v1/contents/:username:/:page
```

> Example data

```json
[
  {
    "idx": 1,
    "title": "Serverless microservice architecture에서의 inter-communication caching",
    "content": "빙글은 8월에 진행된 서비스 리뉴얼과 함께, 기존의 Ruby on rails 기반의 monolithic 앱에서 구현되어 있던 서비스 로직을 상당부분 Serverless 기반의 microservice architecture로 옮겼다.그걸 하면서도 정말 많은걸 배웠고, 그 과정에서 필요했던 다양한 도구들 (Lambda용 http api framework라던가...",
    "url": "https://medium.com/vingle-tech-blog/serverless-microservice-architecture%EC%97%90%EC%84%9C%EC%9D%98-inter-communication-caching-80a43c979121?source=---------8---------------------",
    "cnt": 6,
    "source": "medium",
    "keyword": "serverless,microservice,architecture",
    "image": null,
    "createdAt": "2017-10-22"
  }
]
```

회원이 선택한 주제에 맞게 기사를 page 별로 반환합니다.

### HTTP Request

`GET http://angelbeats.tk:3000/api/v1/contents/:username/:page`


### Query Parameters

Parameter | Description
--------- | -----------
username | 유저 아이디
page | Page의 숫자


# Github ID Checker

```shell
curl -d "userid=gwons" -H \
    "Content-Type: application/x-www-form-urlencoded" \
    -X POST http://angelbeats.tk:3000/api/v1/checker
```

> 만약 아이디를 찾았다면 아래와 같이 반환합니다.

```json
{
  "check": true
}
```

> 만약 아이디를 찾지 못한다면 아래와 같이 반환합니다.

```json
{
  "check": false
}
```

Github에서 아이디를 검색해 결과를 반환합니다.

### HTTP Request

`POST http://angelbeats.tk:3000/api/v1/checker`

### Query Parameters

Parameter | Description
--------- | -----------
userid | 찾을 userid를 입력합니다.

# Search
```shell
curl -d "search=개발" -H \
    "Content-Type: application/x-www-form-urlencoded" \
    -X POST http://angelbeats.tk:3000/api/v1/finder
```

> Example data

```json
[
  {
    "idx":7,
    "title":"라이더스 개발팀 모바일에서 CI/CD 도입",
    "content":"이 글은 CI/CD를 안드로이드에 도입하게 되면서 정리한 내용입니다.   구축 및 운영하고자 하시는 분에게 경험을 공유하고자 합니다.안녕하세요 라이더스 개발팀 장인수 입니다.우선 라이더스 개발팀이 하는 일을 소개 합니다. 저희 라이더스 개발팀은 배달되지 않는 음식점의 음식을 민트색 헬멧을 쓴 라이더 분들이 오토바이를 이용하여 음식을 픽업 후 고객님에게 배달...",
    "url":"http://woowabros.github.io/experience/2018/06/26/bros-cicd.html",
    "cnt":0,
    "source":"woowabros",
    "keyword":"jenkins",
    "image":null,
    "createdAt":"2018-06-26"
  }
]
```


입력한 단어가 포함된 기사 리스트를 반환합니다.

### HTTP Request

`POST http://angelbeats.tk:3000/api/v1/finder`

### Query Parameters

Parameter | Description
--------- | -----------
search | 제목에 들어간 단어를 입력합니다.


# Languages
```shell
curl http://angelbeats.tk:3000/api/v1/languages
```

> Example data

```json
[
  {
    "id": 1,
    "name": "A# .NET",
    "popular": "false"
  },
  {
    "id": 2,
    "name": "A# (Axiom)",
    "popular": "false"
  },
  {
    "id": 3,
    "name": "A-0 System",
    "popular": "false"
  }
]
```

DB에 저장된 모든 언어 리스트들을 반환합니다.

### HTTP Request

`GET http://angelbeats.tk:3000/api/v1/languages`


# Signup
```shell
curl -d "userid=a&extract_language=python&keyword=" -H \
    "Content-Type: application/x-www-form-urlencoded" \
    -X POST http://angelbeats.tk:3000/api/v1/signup
```

> 만약 가입 성공이라면 아래와 같이 반환합니다.

```json
{
  "check": true
}
```

> 만약 가입 실패라면 아래와 같이 반환합니다.

```json
{
  "check": false
}
```

회원가입할때 유저아이디와 추출된 언어리스트 및 관심 있는 언어가 저장됩니다.


### HTTP Request

`POST http://angelbeats.tk:3000/api/v1/signup`


### Query Parameters

Parameter | Description
--------- | -----------
userid | 회원가입할 아이디를 입력합니다.
extract_language | 추출된 언어를 입력합니다
keyword | 웹에서 고른 관심있는 언어를 입력합니다.

## Keyword update
```shell
curl -d "keyword=css" -H \
    "Content-Type: application/x-www-form-urlencoded" \
    -X POST http://angelbeats.tk:3000/api/v1/signup/:userid
```

> 만약 키워드 업데이트가 성공이라면 아래와 같이 반환합니다.

```json
{
  "update": true
}
```

> 만약 키워드 업데이트가 실패라면 아래와 같이 반환합니다.

```json
{
  "update": false
}
```

회원가입 후 키워드 선택시 데이터를 업데이트 합니다.

### HTTP Request

`POST http://angelbeats.tk:3000/api/v1/signup/:userid`

### Query Parameters

Parameter | Description
--------- | -----------
userid | 회원가입할 아이디를 입력합니다.
keyword | 웹에서 고른 관심있는 언어를 입력합니다.


# Updater
```shell
curl http://angelbeats.tk:3000/api/v1/updater/:idx
```

> 만약 조회 수 증가에 성공했다면 아래와 같이 반환합니다.

```json
{
  "check": true
}
```

> 만약 조회 수 증가에 실패했다면 아래와 같이 반환합니다.

```json
{
  "check": false
}
```

### HTTP Request

`GET http://angelbeats.tk:3000/api/v1/updater/:idx`

### Query Parameters

Parameter | Description
--------- | -----------
idx | 조회수를 증가시킬 글의 idx를 입력합니다.
