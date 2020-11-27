---
layout: post
title: "자바 데이터 타입, 변수 그리고 배열"
categories:
  - Java
excerpt: " "
comments: true
share: true
tags:
  - Java
date: 2020-11-27T18:34:00-0:05:00
---

>목표<br>자바가 제공하는 다양한 연산자를 학습하기

# 연산자(Operator)
- 연산자(operator) : 연산을 수행하는 기호
- 피연산자(operand) : 연산자의 작업 대상(변수, 상수, 리터럴, 수식)

# 산술 연산자
## 사칙 연산자
- `+, -, *, / `
예제)
```java
public static void main(String args[])
{
    int a = 5;
    int b = 2;
    
    System.out.printf("%d + %d = %d\n", a, b, a+b); //더하기
    System.out.printf("%d - %d = %d\n", a, b, a-b); //빼기
    System.out.printf("%d * %d = %d\n", a, b, a*b); //곱하기
    System.out.printf("%d / %d = %d\n", a, b, a/b); //나누기
    System.out.printf("%d / %f = %f\n", a, (float)b, a/(float)b); //실수로 형변환 후 나누기
}
```

실행결과)
```
5 + 2 = 7
5 - 2 = 3
5 * 2 = 10
5 / 2 = 2
5 / 2.000000 = 2.500000
```

나누는 수로 0을 사용할 수 없다. 만약 0으로 나눈다면, 실행 시에 에러가 발생한다.<br>
위 예제에서 `b = 0`으로 바꾼 후 실행하면 오류가 발생한다.
```java
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at Rextester.main(source.java:17)
```
 나누기 연산자를 사용할 때 조심하자.

## 나머지 연산(%)
- 왼쪽의 피연산자를 오른쪽 피연자로 나누고 난 나머지 값을 결과로 반환하는 연산자

# 비교 연산자
- `<, >, <=, >=, ==, =!`

# 비트 연산자
- `

# 관계 연산자

# 논리 연산자


instanceof
assignment(=) operator
화살표(->) 연산자
3항 연산자
연산자 우선 순위
(optional) Java 13. switch 연산자