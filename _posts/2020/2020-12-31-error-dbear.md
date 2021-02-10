---
layout: post
title: "[Error] public key retrieval is not allowed."
categories:
  - Error
excerpt: " "
comments: true
share: true
tags:
  - Error
  - DBeaver
date: 2020-12-31 T10:15:00-0:05:00
---

# 환경

MySQL 버전 : 8.0.22<br>
DBeaver 버전 : 7.3.0

# 문제상황

> public key retrieval is not allowed

![](https://kimmy100b.github.io/assets/images/error/etc/1-1-1.PNG){: .align-center}

# 문제확인

`retrieval` : 검색

공개키 검색이 허락되지 않았습니다.

# 문제해결

`localhost` 우클릭 -> Edit Connection(F4) -> Driver properties -> `allowPublicKeyRetrieval`의 값을 `TRUE`로 변경
![](https://kimmy100b.github.io/assets/images/error/etc/1-1-2.PNG){: .align-center}

# 참고

<https://jjunii486.tistory.com/127>
