---
layout: post
title: "redirect & forward - BE"
categories:
    - redirect & forward
excerpt: " "
comments: true
share: true
tags:
    - redirect 
    - forward
date: 2020-09-15 T14:48:54-0:05:00
---

# 리다이렉트(Redirect)
- 리다이렉트는 HTTP프로토콜로 정해진 규칙이다.
- 서버는 클라이언트의 요청에 대해 특정 URL로 이동을 요청할 수 있다. 이를 리다이렉트라고 한다.
- 서버는 클라이언트에게 HTTP 상태코드 302로 응답하는데 이때 헤더 내 Location 값에 이동할 URL 을 추가한다. 클라이언트는 리다이렉션 응답을 받게 되면 헤더(Location)에 포함된 URL로 재요청을 보내게 된다. 이때 브라우저의 주소창은 새 URL로 바뀌게 된다.
- 클라이언트는 서버로부터 받은 상태 값이 302이면 Location헤더값으로 재요청을 보내게 된다. 이때 브라우저의 주소창은 전송받은 URL로 바뀌게 된다.
- 서블릿이나 JSP는 리다이렉트하기 위해 HttpServletResponse 클래스의 sendRedirect() 메소드를 사용한다.

## 요청하는 예제 소스코드
- redirect01.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%
    response.sendRedirect("redirect02.jsp");
%>   
```

## 브라우저에서 리다이렉트 확인
- F12 > Network탭 선택
- 서버로부터 응답코드로 302를 받는 것을 알 수 있음.(302 : Found, 요청한 리소스의 URI가 일시적으로 변경되었음)

## 예제 동작 설명
![](https://kimmy100b.github.io/assets/images/JSP/redirect.png){: .align-center}
- 클라이언트가 요청을 두 번 보내게 된다
    - 항상 요청이 들어갈 때, 요청 객체와 응답 객체가 생긴다.
    - 처음 redirect01이 들어왔을 때 생겼던 요청 객체와 응답 객체랑 다시 들어와서 redirect02가 요청이 들어갔을 때 생기는 요청 객체와 응답 객체는 다른 객체이다.
- URL은 결국 두 번째인 redirect02.jsp로 바뀌어있음

## 장단점
- 장점
    - 서버의 의도에 맞는 가이드를 클라이언트에게 편하게 제공할 수 있다. 예를 들어, 의도치 않은 url로 이동할 경우 우회할 수 있도록 도와준다.
- 단점
    - get방식으로 데이터를 주고받기 때문에 보안에 좋지 않다

<br>

# Forward
- WAS의 서블릿이나 JSP가 요청을 받은 후 그 요청을 처리하다가, 추가적인 처리를 같은 웹 어플리케이션안에 포함된 다른 서블릿이나 JSP에게 위임하는 것
- URL은 바뀌지 않는다.
    - 클라이언트가 요청을 보내고 서버 쪽에서 그 요청에 대해서 혼자 처리했는지, 다른 누군가한테 부탁해서 처리했는지는 몰라도 됨

![](https://kimmy100b.github.io/assets/images/JSP/forward.png){: .align-center}

1. 웹 브라우저에서 Servlet1에게 요청을 보냄
2. Servlet1은 요청을 처리한 후, 그 결과를 HttpServletRequest에 저장
    - 일정한 부분까지만 Servlet1이 혼자 처리하고 나머지 부분을 다른 서블릿한테 넘김
3. Servlet1은 결과가 저장된 HttpServletRequest와 응답을 위한 HttpServletResponse를 같은 웹 어플리케이션 안에 있는 Servlet2에게 전송(forward)
    - 이렇게 넘겨주는 작업을 forward
4. Servlet2는 Servlet1으로 부터 받은 HttpServletRequest와 HttpServletResponse를 이용하여 요청을 처리한 후 웹 브라우저에게 결과를 전송

## 예제 소스코드
서블릿으로 만들기
- FrontServlet.java
    - java Resource > src 폴더 밑에 파일 생성(service만 오버라이드 해주기)
    - forword 주의사항 : 경로는 반드시 '/'로 시작, 같은 웹 애플리케이션 안에서만 가능

```java
import java.io.IOException;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class FrontServlet
 */
@WebServlet("/front")
public class FrontServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public FrontServlet() {
        super();
        // TODO Auto-generated constructor stub
    }

    /**
     * @see HttpServlet#service(HttpServletRequest request, HttpServletResponse response)
     */
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            
            int diceValue = (int)(Math.random() * 6) + 1; 
            request.setAttribute("dice", diceValue); 
            // 변수명 , 변수에 들어갈 실제 값
            // 값은 object 타입으로 맡겨짐
            RequestDispatcher requestDispatehcer = request.getRequestDispatcher("/next");
            // forword 만들 때 주의사항 - 경로를 반드시 '/'로 시작, 같은 웹 애플리케이션 안에서만 가능
            requestDispatehcer.forward(request, response); //반드시 request와 response를 넘겨줘야함 
    }

}
```

- NextServlet.java

```java
import java.io.IOException;
import java.io.PrintWriter;
import java.util.Enumeration;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class ForwardServlet
 */
@WebServlet("/forward")
public class ForwardServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public ForwardServlet() {
        super();
        // TODO Auto-generated constructor stub
    }

    /**
     * @see HttpServlet#service(HttpServletRequest request, HttpServletResponse response)
     */
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        // "text/html"로 응답할꺼야
        PrintWriter out = response.getWriter();
        out.println("<html>");
        out.println("<head><title>form</title></head>");
        out.println("<body>");

        int dice = (Integer)request.getAttribute("dice");
        // request한테 setAttribute를 사용해서 "dice"에 값을 맡김
        // 값은 object타입으로 넣어줬기 때문에 형 변환을 시켜줘야함
        out.println("dice : " + dice);
        for(int i = 0; i < dice; i++) {
            out.print("<br>hello");
        }
        out.println("</body>");
        out.println("</html>");
    }

}
```

<br>

# Forward와 Redirect의 차이

| forward() 메서드 | sendRedirect() 메서드 | 
|----|-----|
| 서버 측에서 작동 | 클라이언트 측에서 작동 |
| 동일한 요청 및 응답 객체를 다른 서블릿으로 보냄 | 항상 새 요청을 보냄 |
| URL이 변경되지 않음 | URL이 변경됨 |
| 서버 내에서만 작동 가능 | 서버 내부 및 외부에서 사용 가능 |
| 예 : request.getRequestDispacher ( "servlet2"). forward (request, response); | 예 : response.sendRedirect ( "servlet2"); |

<br>

# servlet & jsp 연동
- 서블릿은 로직을 구현하기에 알맞지만, HTML을 출력하기엔 불편
- JSP는 로직을 구현하는 것은 불편하지만 HTML을 출력하기엔 편리
- 프로그램 로직 수행은 Servlet에서, 결과 출력은 JSP에서 하는 것이 유리
- Servlet과 JSP의 장단점을 해결하기 위해서 Servlet에서 프로그램 로직이 수행되고, 그 결과를 JSP에게 포워딩하는 방법을 사용(servlet & jsp 연동)

![](https://kimmy100b.github.io/assets/images/JSP/servlet_jsp.png){: .align-center}

## 예제 소스코드
- FrontServlet.java
    - service 함수부분만 변경

```java
protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	int diceValue = (int) (Math.random() * 6) + 1;
	int ramValue = (int) (Math.random() * 10) + 1;
	request.setAttribute("dice", diceValue);
	request.setAttribute("ram", ramValue);
	RequestDispatcher requestDispatehcer = request.getRequestDispatcher("/Next.jsp");
	requestDispatehcer.forward(request, response);
}
```

- Next.jsp
    - WebContent 폴더 안에 만듦

```jsp
<%@ page language="java" contentType="text/html; charset=EUC-KR"
	pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>form</title>
</head>
<body>
	<%
		int dice = (Integer) request.getAttribute("dice");
	%>
	<p> dice : <%=dice%></p>
	<p> EL 표기법 : ${ram} </p>
	<%
		for (int i = 0; i < dice; i++) {
	%>
		<p> Hello </p>
	<%
		}
	%>
</body>
</html>
```

\* EL표기법을 사용하는 이유 : JSP에서는 자바코드를 줄이는 것이 좋기 때문에, EL표기법을 사용하면 다른 거 아무것도 없이 ${ }로 출력 가능

<br/>

## 하나의 서블릿이 여러 개의 요청을 받는 방법
- 와일드카드('*'기호)를 사용하기
- [URL Patterns](https://docs.roguewave.com/hydraexpress/3.5.0/html/rwsfservletug/4-3.html)


<br/>

# 참고
- [HTTP 상태코드](https://developer.mozilla.org/ko/docs/Web/HTTP/Status)
- [forward와 redirect의 차이](https://www.javatpoint.com/sendRedirect()-method)