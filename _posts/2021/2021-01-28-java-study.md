---
layout: post
title: "[Java] 자바 변수, 상수, 리터럴(작성중)"
categories:
  - Java
excerpt: " "
comments: true
share: true
tags:
  - Java
date: 2021-01-28T18:34:00-0:05:00
---

# 리터럴(Literal)

리터럴을 알아보기 전 변수, 상수, 리터럴을 구별해 알아보려고 한다.

## 변수, 상수, 리터럴

**변수(variable)란**

> 하나의 값을 저장하기 위한 공간

**상수(constant)란**

> 값을 한번만 저장할 수 있는 공간, 값을 변경할 수 없다.

**리터럴(literal)**

> 그 자체로 값을 의미하는 것

예제)

```java
  int year = 2021;
  // year : 변수, 2021 : 리터럴
  final int SIZE = 500;
  // SIZE : 상수, 500 : 리터럴
```

## 상수(Constant)

> 리터럴에 '의미있는 이름'을 붙이면 상수이다.

**상수가 필요한 이유**<br>
의미있는 이름을 붙여서 코드의 이해와 수정을 쉽게 만들기 위해서이다.

**상수 선언 방법**<br>

- 반드시 선언과 동시에 초기화해야한다.
- 변경이 불가능하다.
- 변수의 타입 앞에 키워드 `final` 붙여줘야한다.
- 예제

  ```java
  final int WIDTH = 20; // 폭
  final int HEIGTH = 10; // 높이

  int rectangleArea = (WIDTH * HEIGHT); // 사각형 면적 구하는 공식
  WIDTH = 30; // 에러. 상수에 새로운 값을 저장할 수 없다.
  ```

# 변수 선언 및 초기화하는 방법

## 변수 선언

- 변수의 명명규칙 추가 25페이지
  **변수 선언방법**

```java
[변수타입] [변수이름];
```

변수타입 : 변수에 저장될 값이 어떤 타입인지를 정하는 것. ex) int, char, String, double 등<br>
변수이름 : 변수에 붙인 이름, 값을 저장할 수 있는 메모리 공간에 이름을 붙여주는 것<br><br>

예제

```java
int age; // age라는 이름의 변수를 선언
char food; // food라는 이름의 변수를 선언
```

## 변수 초기화

> 변수를 사용하기 전에 처음으로 값을 저장하는 것

**변수 초기화를 반드시 해줘야하는 이유**<br>
메모리는 여러 프로그램이 공유하는 자원이므로 전에 다른 프로그램에 의해 저장된 '알 수 없는 값(쓰레기값,garbage value)'가 남아있을 수도 있기 때문이다.

```java
int age = 25;
//age변수를 25로 초기화
```

- 대입연산자(=) : 오른쪽의 값을 왼쪽(변수)에 저장하라라는 뜻

# 변수의 스코프와 라이프타임

## 변수의 스코프(scope)

> 변수에 접근하거나 접근할 수 있는 유효 범위/영역

# 참고

- [자바 2주차 스터디](https://github.com/whiteship/live-study/issues/2)
- <http://www.tcpschool.com/java/java_datatype_typeConversion>
- [상수와 리터럴](https://mommoo.tistory.com/14)
