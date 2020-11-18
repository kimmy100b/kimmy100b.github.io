---
layout: post
title: "TO-DO LIST 코드리뷰 - BE(백엔드)"
categories:
  - CodeReview
excerpt: " "
comments: true
share: true
tags:
  - CodeReview
  - TO-DO LIST
date: 2020-10-30T16:34:00-0:05:00
---

> "TO-DO LIST" 백엔드 코드 리뷰

# 클래스의 멤버필드 선언 삭제

메소드 내부에 선언 해두었다면 해당 클래스의 멤버필드로 선언할 필요가 없다!
![](https://kimmy100b.github.io/assets/images/codereview/todolist/BE/1.jpg){: .align-center} \* HTTP 요청 메소드 정리
<https://zorba91.tistory.com/136>

# doGet와 doPost

doPost메소드를 요청할 경우 doGet메소드로 넘어가게 작성하였지만 브라우저에서 doPost메소드를 호출하지 않았음으로 doPost메소드는 불필요한 코드이기에 제거해주어야한다.
![](https://kimmy100b.github.io/assets/images/codereview/todolist/BE/2.png){: .align-center}

# 어노테이션을 붙여주는 것을 잊지말자

![](https://kimmy100b.github.io/assets/images/codereview/todolist/BE/3.png){: .align-center}

- 어노테이션을 선언하는 목적
  - 컴파일러에게 정보를 알려주기
  - 컴파일할 때와 설치 시의 작업을 지정하기
  - 실행할 때 별도의 처리하기

<https://onsil-thegreenhouse.github.io/programming/java/2017/12/20/java_tutorial_1-17/>

# System.out.println 사용을 지양하자

`System.out.println();`은 콘솔에 출력되기 전까지 웹 애플리케이션이 멈추기 때문에 응답의 지연이 발생할 수 있다. 그래서 `e.printStackTrace();`로 코드를 수정하였다.`e.printStackTrace();`는 리턴값이 없고 가장 자세한 예외 정보를 제공한다.
![](https://kimmy100b.github.io/assets/images/codereview/todolist/BE/4.png){: .align-center}

<https://edu.goorm.io/learn/lecture/41/%EB%B0%94%EB%A1%9C%EC%8B%A4%EC%8A%B5-%EC%83%9D%ED%99%9C%EC%BD%94%EB%94%A9-%EC%9E%90%EB%B0%94-java/lesson/39294/%EB%92%B7%EC%88%98%EC%8A%B5%EC%9D%98-%EB%B0%A9%EB%B2%95>

# 변경할 수 없는 변수는 final로 지정

![](https://kimmy100b.github.io/assets/images/codereview/todolist/BE/5.png){: .align-center}

```java
  final private static String dburl = "jdbc:mysql://localhost:3306/edwith?useSSL=false";
  final private static String dbUser = "root";
  final private static String dbpasswd = "mysql";
```

# 생성자에서 com.mysql.jdbc.Driver를 로딩

![](https://kimmy100b.github.io/assets/images/codereview/todolist/BE/6.png){: .align-center}

# try-with-resource

![](https://kimmy100b.github.io/assets/images/codereview/todolist/BE/7.png){: .align-center}
Java 7에서 `AutoCloseable`인터페이스와 `try-with-resource`가 등장했다. `try`블록의 소괄호 `()`안에서 `close()`메서드 호출이 필요한(`AutoCloseable`를 구현한) 객체를 할당해주면 된다.<br>
`try-catch`절이 종료되면 객체의 `close()`메서드가 자동으로 호출된다.
(아래 소스코드와 같이 변경)

```java
try (Connection conn = DriverManager.getConnection(dbUrl, dbUser, dbPasswd);
				PreparedStatement ps = conn.prepareStatement(sql);) {
			ps.setString(1, todo.getTitle());
			ps.setString(2, todo.getName());
			ps.setInt(3, todo.getSequence());

			insertCount = ps.executeUpdate();

		} catch (SQLException e) {
			e.printStackTrace();
		}
```

# 질문

## 질문 1

Q : 문자열의 길이를 제한해줄때 input의 속성인 maxlength으로 주게 되면 XSS와 같은 보안상의 문제가 생길 수 있는 걸로 알고 있습니다. 이 경우 어떤 방법으로 코딩을 해주는 것이 가장 좋은 방법인가요?<br>
A : maxlength는 보안에 취약점도 있지만 예전 브라우저에서 동작하지 않을 수도 있습니다.<br>
따라서, javascript로 글자수를 제한하는 것이 좋다고 생각합니다.

## 질문2

Q : 자바스크립트에서 querySelect를 쓰라고 표기되어있었습니다. getElementId나 태그의 속성인 name을 사용하여 해당 태그를 찾는 것보다 querySelect를 사용하면 좋은 점이 따로 있나요? <br>
A : 성능과 개발의 편의성에 따라 사용하시면 될 것 같습니다.<br>
자세한 내용은 아래 링크참고 부탁드립니다.<br>
<https://hashcode.co.kr/questions/5692/%EA%B0%95%EC%9D%98-4-11-queryselector%EC%97%90-%EC%84%B1%EB%8A%A5%EB%AC%B8%EC%A0%9C%EC%97%90-%EB%8C%80%ED%95%B4-%EC%A7%88%EB%AC%B8-%EB%93%9C%EB%A6%BD%EB%8B%88%EB%8B%A4>
