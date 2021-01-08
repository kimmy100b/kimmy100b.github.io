---
layout: post
title: "[JAVA] String Constant Pool in Java"
categories:
  - Java
excerpt: " "
comments: true
share: true
tags:
  - Java
date: 2020-10-21 T11:39:00-0:05:00
---

# String Constant Pool in Java
```java
// Program 1 : 리터럴을 이용한 String 변수 생성 후 비교
import java.util.*; 
  
class GFG { 
    public static void main(String[] args) 
    { 
        String s1 = "abc"; 
        String s2 = "abc"; 

        if (s1 == s2) 
           System.out.println("Yes"); 
        else
           System.out.println("No"); 
    } 
} 
```
결과값 : Yes

```java
// Program 2 : new 연산자를 이용한 String 변수 생성 후 비교
import java.util.*; 
  
class GFG { 
    public static void main(String[] args) 
    { 
        String s1 = new String("abc"); 
        String s2 = new String("abc"); 
  
        // Note that this == compares whether 
        // s1 and s2 refer to same object or not 
        if (s1 == s2) 
           System.out.println("Yes"); 
        else
           System.out.println("No"); 
    } 
} 
```
결과값 : No<br>

이렇게 다른 결과값이 나오는 이유가 무엇일까.<br>
Java에서 문자열의 가장 중요한 특성 중 하나는 변경 불가능하다는 것이다. 즉, 생성되면 문자열의 내부 상태는 프로그램 실행 내내 동일하게 유지된다. 이 불변성은 힙에서 String Constant Pool을 사용하여 이루어지는 것이다.<br>
String Constant Pool은 힙 메모리의 별도 위치(힙 메모리에 있는 작은 캐시)이다. 문자열을 선언하면 스택에 String 유형의 객체가 생성되고 힙에는 문자열 값이 있는 인스턴스가 생성된다. 문자열 변수에 값을 표준 할당하면 변수에 스택이 할당되고 값은 문자열 상수 풀의 힙에 저장된다. 해당 예제를 살펴보자

```java
String str1 = "Hello";
```
![](https://kimmy100b.github.io/assets/images/java/string_pool_01.png){: .align-center}

문자열 개체가 스택에 생성되고 값 "Hello"가 생성되어 힙에 저장된다. 일반적으로 값을 할당했으므로 힙의 상수 풀 영역에 저장된다. 스택의 개체는 포인터로 힙에 저장된 값을 가리킨다. 동일한 값을 갖는 여러 문자열 변수를 사용한 예제를 살펴보자.

```java
String str1 = "Hello";
String str2 = "Hello";
```
![](https://kimmy100b.github.io/assets/images/java/string_pool_02.png){: .align-center}

이 경우 두 문자열의 개체가 모두 Stack에 생성되지만 "Hello" 값의 다른 인스턴스는 힙에 생성되지 않고 "Hello"의 이전 인스턴스가 다시 사용된다. String constant pool을 사용하면 주로 메모리 사용량을 줄이고 메모리에서 기존 인스턴스의 재사용을 개선하기 위해 존재한다. 문자열 객체에 다른 값이 할당될 경우의 예제를 살펴보자.

```java
String str1 = "Hello"; 
String str2 = "Hello"; 
String str3 = "클래스";
```

![](https://kimmy100b.github.io/assets/images/java/string_pool_03.png){: .align-center}

문자열 객체에 다른 값이 할당되면 새 값이 별도의 인스턴스로 String constant pool에 등록된다.<br>

메모리 할당을 건너 뛰는 한 가지 방법은 new 연산자를 사용하여 새 문자열 개체를 만드는 것이다. `new` 키워드는 동일한 값이 이전에 사용되었는지 여부와 관계없이 항상 새 인스턴스를 생성하도록한다. 

```java
String str1 = new String ("John"); 
String str2 = new String ("Doe");
```

![](https://kimmy100b.github.io/assets/images/java/string_pool_04.png){: .align-center}

# 참고
- [자바의 String constant pool](https://www.geeksforgeeks.org/string-constant-pool-in-java/)