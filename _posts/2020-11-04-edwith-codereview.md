---
layout: post
title: "TO-DO LIST 코드리뷰 - FE(프론트엔드)"
categories:
  - Codereview
excerpt: " "
comments: true
share: true
tags:
  - Codereview
  - TO-DO LIST
date: 2020-11-09T16:34:00-0:05:00
---

> "TO-DO LIST" 프론트엔드 코드 리뷰<br>보안 취약점과 관련해서 인사이트를 느낄 수 있도록 커멘트를 드렸습니다.취약한 부분들을 리팩터링해보시면 실력 향상에 도움이 되실 것같습니다.

# 로고 삭제 해주기
![](https://kimmy100b.github.io/assets/images/codereview/todolist/FE/1.jpg)

# 악용을 목적으로 하는 사용자가 개발자도구를 열고 코드 변경
![](https://kimmy100b.github.io/assets/images/codereview/todolist/FE/2.jpg)
![](https://kimmy100b.github.io/assets/images/codereview/todolist/FE/3.jpg)
![](https://kimmy100b.github.io/assets/images/codereview/todolist/FE/5.jpg)

글자 길이 제한 및 NULL 값 제한하기 위한 코드이지만 개발자도구를 열고 코드를 변경할 경우 보안에 취약해진다. 따라서 나는 TodoAddServlet.java를 지우고 writeAction.jsp를 추가해주었다. writeAction.jsp에서는 문자열 길이 제한과 NULL값 제한에 대해 걸어두었다.


# HTML태그의 lang 속성 이용
![](https://kimmy100b.github.io/assets/images/codereview/todolist/FE/4.jpg)
아래 코드로 변경!
```html
<html lang="ko">
```

# Input은 단일 태그
- 저번에 실수한 br태그도 단일태그이다.
![](https://kimmy100b.github.io/assets/images/codereview/todolist/FE/6.jpg)
