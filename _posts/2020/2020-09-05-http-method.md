---
layout: post
title: "HTTP METHOD"
categories:
    - Tech
excerpt: " "
comments: true
share: true
tags:
    - HTTP
    - HTTP METHOD
date: 2020-09-05 T00:11:54-0:05:00
---

-   POST, GET, PUT, DELETE 이 4가지 메소드를 가지고 CRUD를 할 수 있다.
-   4가지 외 다양한 메소드들도 있다.

# POST

-   특정 리소스에 엔티티를 제출할 때 쓰인다.
-   URL를 요청하면 리소스를 생성한다.
-   종종 서버의 상태의 변화나 부작용을 일으킨다.

# GET

-   특정 리소스의 표시를 요청한다.
-   해당 리소스를 조회하고 해당 도큐먼트에 대한 자세한 정보를 가져온다.
-   오직 데이터를 받기만 한다.

# PUT

-   목적 리소스 모든 현재 표시를 요청 payload로 바꾼다.
-   해당 리소스를 수정한다.

# DELETE

-   특정 리소스를 삭제한다.

# PATCH

참고로 알아두기 5가지라고 하면 PATCH 포함

-   리소스의 부분만을 수정하는데 쓰인다.

## 참고

[HTTP 요청 메서드](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods)