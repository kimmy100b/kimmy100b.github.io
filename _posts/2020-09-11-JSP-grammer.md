---
layout: post
title: "JSP 문법"
categories:
    - JSP
excerpt: " "
comments: true
share: true
tags:
    - JSP
    - JSP grammer
date: 2020-09-11 T00:17:54-0:05:00
---

# 선언문(Declaration)
- 선언문 : `<%! %>`
- 전역변수 선언 및 메소드 선언에 사용
```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
```

# 스크립트릿(Scriptlet)
- 스크립트릿 : `<% %>`
- 가장 일반적으로 많이 쓰이는 스크립트 요소
- 주로 프로그래밍의 로직을 기술할 때 사용
- 스크립트릿에서 선언된 변수는 지역변수

# 표현식(Expression)
- 표현식 : `<%= %>`
- JSP페이지에서 웹 브라우저에 출력할 부분을 표현(즉, 화면에 출력하기 위한 것)

# 주석(Comment)
- 주석 : `<%--주석내용--%>`

# 예
- JSP
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>

<%
for(int i = 1; i <= 5; i++){
%>
<H<%=i %>> <%=i>번째 글자크기 </H<%=i %>>
<%
}
%>
</body>
</html>
```

- HTML
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>

<H1> 1번째 글자크기 </H1>

<H2> 2번째 글자크기 </H2>

<H3> 3번째 글자크기 </H3>

<H4> 4번째 글자크기 </H4>

<H5> 5번째 글자크기 </H5>

</body>
</html>
```

- 서블릿
```servlet
for(int i = 1; i <= 5; i++){

      out.write('\n');
      out.write('<');
      out.write('H');
      out.print(i );
      out.write("> ");
      out.print(i );
      out.write("번째 글자크기 </H");
      out.print(i );
      out.write('>');
      out.write('\n');

}
```