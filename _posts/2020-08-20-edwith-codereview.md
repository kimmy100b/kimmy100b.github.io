---
layout: post
title: "aboutme 코드리뷰 1탄 - FE(프론트엔드)"
categories:
    - CodeReview
excerpt: " "
comments: true
share: true
tags:
    - CodeReview
    - aboutme
date: 2020-08-20T16:34:00-0:30:00
---

> "나를 소개하는 페이지" 프론트엔드 코드 리뷰

클래스명으로 인해 fail당했다..
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/fail1.PNG){: .align-center}
<br>

# <html>태그의 lang속성의 값을 지정해주기

lang속성으로 지정한 값은 스크린 리더의 기본 문자셋으로 지정됩니다.

```html
<html lang="ko"></html>
```

![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/1.PNG){: .align-center}
<br>

# classname은 통일해주기

-   classname을 통일하게 해야한다.
-   classname을 보고 어떤 역할인지 알 수 있어야한다.

![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/2.PNG){: .align-center}
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/3.PNG){: .align-center}
<br>

# class명과 태그명은 동일하게 써주지말 것

footer의 의미를 나타내고 css에 적용할 때 class로 적용하고 싶어서 그렇게 표현하였지만 좋은 방법이 아님! 그냥 태그로 써주기
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/4.PNG){: .align-center}
<br>

# <br> 태그는 단일 태그이다

흠.. git 블로그에 `<br/>`을 많이 썼는데ㅠㅠ
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/5.PNG){: .align-center}
<br>

# img에 alt태그 넣어주기

alt태그는 이미지가 뜨지 않을 경우 보여주는 태그이다.<br>
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/6.PNG){: .align-center}
<br>

# 시멘틱 태그를 쓰려고 노력하기

무작정 div나 p 같은 태그를 쓰기보단 시멘틱 태그를 생각해보기<br>

`<address>`태그는 문서나 글의 저자 또는 회사와 연락할 수 있는 정보를 명시할 때 사용한다.<br/>
`<body>`요소 안에 존재하는 `<address>`요소는 해당 문서의 연락 정보를 나타내며, `<article>`요소 안에 존재하는 `<address>`요소는 해당 글에 대한 연락 정보를 나타낸다.
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/7.PNG){: .align-center}
<br>

# 참고

[TCP스쿨 - address태그](http://tcpschool.com/html-tags/address)
