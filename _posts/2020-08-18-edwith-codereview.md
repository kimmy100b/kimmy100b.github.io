---
layout: post
title: "aboutme 코드리뷰 - BE(백엔드)"
categories:
  - codereview
excerpt: " "
comments: true
share: true
tags:
  - codereview
  - aboutme
date: 2020-08-18T09:34:00-0:05:00
---

> "나를 소개하는 페이지" 백엔드 코드 리뷰

<br/><br/>

# 디폴트 생성자 삭제

```java
@WebServlet("/today")
public class TodayServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;

    /**
     * @see HttpServlet#HttpServlet()
     */
    public TodayServlet() { //여기부분 삭제
        super();
```

자바에서 디폴트 생성자는 정의하지 않으면 자바 컴파일러에서 다음과 같이 동일한 형태로 디폴트 생성자가 생성된다.<br/> 객체 생성시 별다른 로직이 없다면 삭제!<br/><br/>

# TODO 주석

```java
    public TodayServlet() {
        super();
        // TODO Auto-generated constructor stub
    }
```

불필요한 또는 잘못된 주석은 같이 협업하는 개발자로 하여금 혼란을 야기 시킬 수 있다.<br/>따라서 불필요하거나 잘못된 주석을 삭제해주기!<br/>TODO주석은 할 일을 명시해 놓는 주석이며 IDE(이클립스, 이텔리J)에서 TODO주석만 따로 볼 수 있도록 기능을 제공한다.<br/><br/>

# 어노테이션(Annotation)

```java
@WebServlet("/today")
public class TodayServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
```

doGet 메소드는 HttpServlet의 doGet 메소드를 오버라이드하여 재정의한 메소드이다.<br/>따라서 오버라이드한 메소드들을 `@Override` 어노테이션을 붙여주는 것이 좋다.<br/>이유는 해당 메소드가 오버라이드 된 메소드라는 것을 명시적으로 알 수 있고, 컴파일 시 상속한 부모 클래스에 해당 메소드가 있는지 여부등을 통해 예외를 발생할 수 있어 오류를 인지할 수 있기 때문이다.<br/>다음에 어노테이션에 대해 알아보려고 한다.<br/><br/>

# 비슷한 의미 변수

```java
LocalDateTime now = LocalDateTime.now();
DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("yyyy/MM/dd hh:mm");
String nowString = now.format(dateTimeFormatter);
```

비슷한 의미 변수가 있어서 변수명을 작성하기 애매하다.<br/>이럴 경우 변수를 합칠 수 있다면 하나로 합치는 것도 하나의 방법이다.<br/>

```java
String now = LocalDataTime.now().format(DateTimeFormatter.ofPattern("yyyy/MM/dd hh:mm"));
```

<br/><br/>
