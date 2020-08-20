---
layout: post
title: "aboutme 코드리뷰 - FE(프론트엔드)"
categories:
  - codereview
excerpt: " "
comments: true
share: true
tags:
  - codereview
  - aboutme
date: 2020-08-20T16:34:00-0:30:00
---

> "나를 소개하는 페이지" 백엔드 코드 리뷰

클래스명으로 인해 fail당했다..
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/fail1.PNG){: .align-center}

# <html>태그의 lang속성의 값을 지정해주기

lang속성으로 지정한 값은 스크린 리더의 기본 문자셋으로 지정됩니다.

```html
<html lang="ko"></html>
```

![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/1.PNG){: .align-center}

# classname은 통일해주기

- classname을 통일하게 해야한다.
- classname을 보고 어떤 역할인지 알 수 있어야한다.

![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/2.PNG){: .align-center}
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/3.PNG){: .align-center}

# <br> 태그는 단일 태그이다

흠.. git 블로그에 `<br/>`을 많이 썼는데ㅠㅠ
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/3.PNG){: .align-center}
