---
layout: post
title: 'Servlet 라이프 싸이클'
categories:
    - Servlet
excerpt: ' '
comments: true
share: true
tags:
    - Servlet
    - Servlet Life Cycle
date: 2020-09-10T10:54:00-0:05:00
---

# Servlet 생명주기
WAS는 서블릿 요청을 받으면 해당 서블릿이 메모리에 있는지 확인한다. <br>
 if (메모리에 없음) {<br>
 - 해당 서블릿 클래스를 메모리에 올림
 - init() 메소드를 실행
}<br>
 - service()메소드를 실행
was가 종료되거나, 웹 어플리케이션이 새롭게 갱신될 경우 destroy() 메소드가 실행된다.<br>

# LifecycleServlet을 구현
HttpServlet의 3가지 메소드를 오버라이딩
- init()
- service(request, response)
- destroy()

## 소스코드
```java
import java.io.IOException;
import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/LifecyleServlet")
public class LifecyleServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    public LifecyleServlet() {
        System.out.println("LifecyleServlet 생성");
    }

	public void init(ServletConfig config) throws ServletException {
		System.out.println("init 호출");
	}
	
	public void destroy() {
		System.out.println("destroy 호출");
	}

	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		System.out.println("service 호출");
	}
}
```

## 결과
//todo
[이미지]*2
