---
layout: post
title: "[JAVA] 문자열 비교하기 ==과 equals의 차이점"
categories:
  - Java
excerpt: " "
comments: true
share: true
tags:
  - Java
date: 2020-10-21 T11:19:00-0:05:00
---

# String 변수 생성 시 주소할당
String 변수를 생성하는 방법은 두 가지이다.
```java
1. 리터럴을 이용한 방식
String a = "aaa";

2. new 연산자를 이용한 방식
String b = new String("aaa");
```
위의 두 가지 방식에는 큰 차이점이 있다. 리터럴을 사용하게 되면 string constant pool이라는 영역에 존재하게 되고 new를 통해 String을 생성하면 Heap 영역에 존재하게 된다. String을 리터럴로 선언할 경우 내부적으로 String의 intern() 메서드가 호출되게 된다. intern() 메서드는 주어진 문자열이 string constant pool에 존재하는지 검색하고 있다면 그 주소값을 반환하고 없다면 string constant pool에 넣고 새로운 주소값을 반환한다. 

\* [String constant pool의 설명]()

# 주소값 비교(==)와 값 비교(equals)
## `==` 
- 비교하고자 하는 두 대상의 주소값을 비교
- int형, char형 등 일반적인 타입들은 Call by Value형태로 기본적으로 대상에 주소값을 가지지 않는 형태로 사용

## `equals` 
- 비교하고자 하는 두 대상의 값 자체를 비교
- String클래스의 equals 메소드 : 일반적인 타입이 아니라 클래스이다. 클래스는 기본적으로 Call by Reference형태로 생성 시 주소값이 부여된다.

# 예제
## == 예제
```java
class Main {
  public static void main(String[] args) {
    String s1 = "abc";
    String s2 = s1;
    String s3 = "abc";
    String s4 = new String("abc");

    // == 으로 문자열 비교
    if(s1==s2){ // 결과 : 값이 같습니다.
      System.out.println("값이 같습니다.");
    }else{
      System.out.println("값이 다릅니다.");
    }

    if(s1==s3){ // 결과 : 값이 같습니다.
      System.out.println("값이 같습니다.");
    }else{
      System.out.println("값이 다릅니다.");
    }

    if(s1==s4){ // 결과 : 값이 다릅니다.
      System.out.println("값이 같습니다.");
    }else{
      System.out.println("값이 다릅니다.");
    }
  }
}
```

## equals 예제
```java
class Main {
  public static void main(String[] args) {
    String s1 = "abc";
    String s2 = s1;
    String s3 = "abc";
    String s4 = new String("abc");

    // equals로 문자열 비교
    if(s1.equals(s2)){ // 결과 : 값이 같습니다.
      System.out.println("값이 같습니다.");
    }else{
      System.out.println("값이 다릅니다.");
    }

    if(s1.equals(s3)){ // 결과 : 값이 같습니다.
      System.out.println("값이 같습니다.");
    }else{
      System.out.println("값이 다릅니다.");
    }

    if(s1.equals(s4)){ // 결과 : 값이 같습니다.
      System.out.println("값이 같습니다.");
    }else{
      System.out.println("값이 다릅니다.");
    }
  }
}
```

# 참고
- [문자열 비교하기 == , equals() 의 차이점](https://coding-factory.tistory.com/536)