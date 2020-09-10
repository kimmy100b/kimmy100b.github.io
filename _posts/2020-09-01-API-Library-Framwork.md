---
layout: post
title: 'API vs Library vs Framework'
categories:
    - Tech
excerpt: ' '
comments: true
share: true
tags:
    - API
    - Library
    - Framework
date: 2020-09-01T10:11:00-0:05:00
---

# API(Application Programming Interface)
- 응용 프로그램에서 운영 체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스
- 프로그램과 인간 사이를 연결시켜주는 다리
- 예)
  - 아래 그림을 통해서 이 프로그램의 기능을 이용한다.

## API의 특징
- 구현과 독립적으로 사양만 정의되어 있다.
- API에 따라 접근 권한이 필요할 수 있다.
- Java API, 여러 기업들의 오픈 API

<br>

# Library
- 응용 프로그램 개발을 위해 필요한 기능(함수)를 모아 놓은 소프트웨어
- Apache Commons, Guava, Lombok, jQuery 등이 있다.

## Library의 특징
- 독립성을 가진다.
  - 해당 라이브러리는 다른 라이브러리를 의존하지 않는다라는 것을 의미한다.
- 응용 프로그램이 능동적으로 라이브러리를 사용한다.

<br>

# Framework
- 응용 프로그램이나 소프트웨어의 솔루션 개발을 수월하게 하기 위해 제공된 소프트웨어 환경
- Spring Framework, Junit, Ruby on Rails 등이 있다.

## Framework의 특징
- 상호협력하는 클래스와 인터페이스의 집합이다.
- 응용 프로그램이 수동적으로 프레임워크에 의해 사용된다.

<br>

# API vs Library
- Library와 API의 차이점은 구현 로직의 유무이다.
  - API는 구현 로직이 없고 Library는 구현 로직이 있다.

# Library vs Framework
- Library와 Framework의 차이점은 응용 프로그램의 흐름 주도권을 누가 가지고 있느냐이다.(누가 누구를 컨트롤 하는가?)
  - 내가 코딩하다가 라이브러리가 필요할 때 부르는 것
  - 프레임워크가 나를 부르는 것

- 누군가 정해준 규칙을 따라하고 있는가?
  - 프레임워크로 일을 할 때는 프레임워크의 규칙을 따라야한다.

# 참고

[10분 테코톡](https://www.youtube.com/watch?v=We8JKbNQeLo)
