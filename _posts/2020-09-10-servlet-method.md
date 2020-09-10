---
layout: post
title: 'Servlet 작성방법'
categories:
    - Servlet
excerpt: ' '
comments: true
share: true
tags:
    - Servlet
    - Servlet작성방법
date: 2020-09-10T10:11:00-0:05:00
---

# 버전에 따른 Servlet 작성 방법

## 1. Servlet 3.0 spec 이상에서 사용하는 방법
- web.xml 파일을 사용하지 않습니다.
- 자바 어노테이션(annotation)을 사용합니다.
- 앞에서 실습했던 first web에서 사용합니다.

## 2. Servlet 3.0 spec미만에서 사용하는 방법
- servlet을 등록할 때 web.xml 파일에 등록합니다.

<br>

# Servlet 작성 방법
## 버전확인 및 설정
// TODO
[이미지]

## 소스코드(1부터 10까지 출력)
### 1. 
```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
```
- HttpServletRequest : 브라우저한테 요청
- HttpServletResponse : 브라우저한테 응답

### 2. 
1-10까지 출력이니 응답 객체를 이용해야한다.
```java
response.setContentType("text/html;charset=utf-8");
```
- 응답 결과에다가 이런 타입으로 보내줄께요라는 약속을 여기다가 넣어준다.
- `text/html` : text는 html이다.

### 3.
보낼 내용을 넣어줄 통로를 얻어야 한다.<br>
response 객체에 getWriter()라고 하는 메서드가 있다.<br>
이 메서드를 수행하면 PrintWriter라는 객체가 return 되는 것을 알 수 있다. 
```java
PrintWriter out = response.getWriter();
```
- 변수명은 out인데 아무거나 줘도 상관없다.

### 4.
```java
out.print("<h1>1부터 10까지 출력합니다.<h1>");
```
- println을 쓸지 print를 쓸지 고민하지 말기
    - 둘 다 똑같음 : HTML파일에다가 아무리 Enter을 쳐봐도 줄 안 바뀜 (줄은 반드시 br태그를 써야한다.)
- `System.out.println();`과 `out.print();`는 목적지가 다르다.
    - `System.out`하면 콘솔을 의미한다.

### 5. 
```java
for(int i = 1; i<=10; i++) {
	out.print(i+"<br>");
}
```
- println을 써도 줄을 안 바뀌니깐 `<br>`태그 사용해주기

### 6. 
out객체를 다 사용했으니 close()해주기
```java
out.close();
```

### 7. 
실행하면 Java Resources에 src에 exam이라는 폴더가 만들어짐

<br>

# 전체소스코드
```java
import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class TenServlet
 */
@WebServlet("/ten")
public class TenServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public TenServlet() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setContentType("text/html;charset=utf-8");
		PrintWriter out = response.getWriter();
		out.print("<h1>1부터 10까지 출력합니다.<h1>");
		for(int i = 1; i<=10; i++) {
			out.print(i+"<br>");
		}
		out.close();
	}

}
```

<br>

# 참고
- [부스트코스](https://www.edwith.org/boostcourse-web/lecture/16687/)