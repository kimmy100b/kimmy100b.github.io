---
layout: post
title: "aboutme 코드리뷰 - BE(백엔드)"
categories:
    - CodeReview
excerpt: " "
comments: true
share: true
tags:
    - CodeReview
    - aboutme
date: 2020-08-18T09:34:00-0:05:00
---

> "나를 소개하는 페이지" 백엔드 코드 리뷰

<br><br>

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

해당 생성자는 이클립스에서 서블릿 생성시 자동으로 생성해주는 디폴트 생성자로 알고 있습니다. 하지만, 자바는 디폴트 생성자는 정의하지 않으면 자바 컴파일러에서 다음과 같이 동일한 형태로 디폴트 생성자가 생성됩니다. 객체 생성시 별다른 로직이 없다면 삭제해도 무방합니다.<br><br>

# TODO 주석

```java
    public TodayServlet() {
        super();
        // TODO Auto-generated constructor stub
    }
```

위 디폴트 생성자와 같이 이클립스에서 서블릿 생성시 자동 생성하는 주석으로 알고 있습니다. 불필요한 또는 잘못된 주석은 같이 협업하는 개발자로 하여금 혼란을 야기 시킬 수 있습니다. TODO 주석에 경우 할 일을 명시해 놓는 주석이며 IDE(이클립스, 인텔리J)에서 TODO 주석만 따로 볼수 있도록 기능을 제공합니다. 추후 개발시 활용해보는 것도 개발에 많은 도움이 될 것입니다.<br> <https://cocomo.tistory.com/65> <br><br>

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

doGet 메소드는 HttpServlet의 doGet 메소드를 오버라이드하여 재정의한 메소드 입니다. 따라서 오버라이드한 메소드들을 `@Override` 어노테이션을 붙여주는 것이 좋습니다. 이유는 해당 메소드가 오버라이드 된 메소드라는 것을 명시적으로 알 수 있으며, 컴파일 시 상속한 부모 클래스에 해당 메소드가 있는지 여부등을 통해 예외를 발생할 수 있어 오류를 인지할 수 있기 때문입니다. 자세한 내용을 아래 링크 참고 부탁드립니다.<br> 
<https://onsil-thegreenhouse.github.io/programming/java/2017/12/20/java_tutorial_1-17/><br><br>

# 비슷한 의미 변수

```java
LocalDateTime now = LocalDateTime.now();
DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("yyyy/MM/dd hh:mm");
String nowString = now.format(dateTimeFormatter);
```

비슷한 의미 변수가 있어 변수명을 작성하기 애매하셨을 것입니다. 이럴 경우 변수를 합칠 수 있다면 하나로 합치는 것도 하나의 방법입니다. 아래 코드를 참고부탁드립니다.<br>

```java
String now = LocalDataTime.now().format(DateTimeFormatter.ofPattern("yyyy/MM/dd hh:mm"));
```

<br><br>

# 이클립스 들여쓰기

들여쓰기에 기준을 한가지로 통일하시는 것이 좋습니다. 이유는 다음과 같습니다. 현재 제가 사용하는 IDE의 tab 기준은 스페이스 4 크기로 설정되어 있습니다. 만일 회사의 코드 포멧 표준이 들여쓰기를 tab으로 해야되며 tab의 크기는 스페이스 2로되어 있다면 해당 코드의 들여쓰기는 들쭉날쭉할 것입니다.<br> 실무에서는 각 회사에 대한 코드 포멧 표준 가이드가 존재하며 이를 숙지하고 들여쓰기를 맞춰주는 것이 좋습니다. 이러한 코드 포멧을 맞춰주는 것을 IDE에서 제공해주며 아래 링크 참조 부탁드립니다. (실무에서는 IDE에서 제공하는 코드 스타일 포멧을 사용하거나 회사에서 제공하는 코드 포멧터로 설정합니다.)<br>
 <https://m.blog.naver.com/PostView.nhn?blogId=samurae83&logNo=220405281014&proxyReferer=https%3A%2F%2Fwww.google.com%2F>
