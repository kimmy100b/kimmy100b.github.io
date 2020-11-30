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

예제)
```java
public static void main(String args[])
{
    int a = 20;
    int b = 7;
    
    System.out.printf("몫 : %d / %d = %d\n", a, b, a/b);
    System.out.printf("나머지 : %d %% %d = %d\n", a, b, a%b);
}
```

실행결과)
```java
몫 : 20 / 7 = 2
나머지 : 20 % 7 = 6
```

나머지 연산자는 나누는 수를 음수로도 계산할 수 있다. 피연산자의 부호를 무시하고, 나머지 연산을 한 결과에 왼쪽 피연산자의 부호를 붙이면 된다. 
예제)
```java
public static void main(String args[])
{
    System.out.println(-10%8);
    System.out.println(10%-8);
    System.out.println(-10%-8);
}
```

실행결과)
```java
-2
2
-2
```

# 관계연산자(비교 연산자)
| 비교연산자 | 연산결과 |
|-----------|----------|
| > | 좌변 값이 크면, true 아니면 false |
| < | 좌변 값이 작으면, true 아니면 false |
| >= | 좌변 값이 크거나 같으면, true 아니면 false |
| <= | 좌변 값이 작거나 같으면, true 아니면 false |
| == | 두 값이 같으면, true 아니면 false |
| != | 두 값이 다르면, true 아니면 false |

## 문자열의 비교
두 문자열을 비교할 때는, 비교 연산자 `==` 대신 `equals()`라는 메서드를 사용해야한다. <br>
`==`는 두 대상의 주소값을 비교하고 `equals`는 두 대상의 값 자체를 비교한다.<br><br>
참고 내용 : <https://kimmy100b.github.io/java/2020/10/21/java-equals/>

# 비트 연산자
| 비트연산자 | 연산결과 |
|-----------|----------|
| \|(OR연산자) | 피연산자 중 한 쪽의 값이 1이면, 1을 결과로 얻는다. 그 외에는 0을 얻는다. |
| &(AND연산자) | 피연산자 양 쪽의 값이 1이면, 1을 결과로 얻는다. 그 외에는 0을 얻는다. |
| ^(XOR연산자) | 피연산자의 값이 서로 다를 때만 1을 결과로 얻는다. 같을 때는 0을 얻는다. |
| ~(비트 전환 연산자, 1의 보수 연산자) | 피연산자를 2진수로 표현했을 때, 0은 1로, 1은 0으로 바꾼다.(논리부정 연산자'!'와 유사) |
| >> | 2진수로 표현한 피연산자를 오른쪽(>>)으로 이동하는 쉬프트 연산자 |
| x >> n | x * 2<sup>n</sup> |
| << | 2진수로 표현한 피연산자를 왼쪽(<<)으로 이동하는 쉬프트 연산자 |
| x << n | x / 2<sup>n</sup> |

## 비트 연산자의 연산결과

| x | y | x\|y | x&y | x^y |
|---|----|-----|-----|-----|
| 1 | 1 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 | 1 |


# 논리 연산자
| 논리연산자 | 연산결과 |
|-----------|----------|
| \|\|(OR결합) | 피연산자 중 어느 한 쪽만 true이면 true를 결과로 얻는다. |
| && (AND결합) | 피연산자 양쪽 모두 true이어야 true를 결과로 얻는다. |
| ! (논리 부정 연산자) | 피연산자가 true이면 false를, false면 true를 결과로 반환한다. | 


# instanceof 연산자
참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 instanceof연산자를 사용한다. 주로 조거문에 사용되며, instacneof의 왼쪽에는 참조변수를 오른쪽에는 타입(클래스명)이 피연산자로 위치한다. 

# assignment(=) operator
# 화살표(->) 연산자
# 3항 연산자
```
조건식 ? 식1 : 식2
```
조건식이 참이면 식1, 거짓이면 식2가 연산결과가 된다. <br>
참고) 가독성을 높이기 위해 조건식을 괄호()로 감싸지만 필수는 아니다.

연산자 우선 순위
(optional) Java 13. switch 연산자