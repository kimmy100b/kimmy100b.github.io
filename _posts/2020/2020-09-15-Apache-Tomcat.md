---
layout: post
title: "Apache와 Tomcat의 차이점"
categories:
    - Tech
excerpt: " "
comments: true
share: true
tags:
    - Apache
    - Tomcat
    - Apache Tomcat
    - WAS
date: 2020-09-15 T11:48:54-0:05:00
---

# 들어가며
현진이가 물은 질문 중 하나인 "Apache Tomcat 에서 Apache와 Tomcat의 차이와 왜 붙여서 부르는지?" 에 대해 알아보려고 한다.

# Apache
- 아파치 소프트웨어 재단의 오픈소스 프로젝트
- 웹 서버
- 정적 데이터(HTML, CSS, 이미지 등)를 처리한다.
- 처리속도가 매우 빠르고 안정적이다.(정적 데이터만 처리하기 때문에)
- 구조가 단순해서 비용절감, 트래픽 과부하에 강하다.
- 다른 서비스와 상호작용 불가

# Tomcat
- WAS(웹 컨테이너, 컨테이너, 서블릿 컨테이너)이다
- 동적 데이터(JSP, Servlet, DB를 통한 데이터 등)을 처리한다
- 데이터 흐름이 유동적이다
- DB 등 여러 서비스가 가능
- 아파치에 비해 속도가 느리다
- 부가적인 비용이 발생한다
- 트래픽 과부하에 약하다

# Apache Tomcat
- 톰캣이 아파치의 기능 일부를 가져와서 제공해주는 형태이기 때문에 같이 합쳐서 부른다
- WAS이다
- 정적 및 동적 데이터를 처리한다
