---
layout: post
title: "aboutme 코드리뷰 2탄 - FE(프론트엔드)"
categories:
    - CodeReview
excerpt: " "
comments: true
share: true
tags:
    - CodeReview
    - aboutme
date: 2020-08-22T23:05:00-0:30:00
---

> "나를 소개하는 페이지" 프론트엔드 코드 리뷰

# alt속성의 값은 최대한 의미적이게!

저번 피드백을 받고 어떤 것을 alt에 적어야할 지 모호했는데 어떻게 아시고 이번에도 피드백해주셨다

![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/8.PNG){: .align-center}
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/9.PNG){: .align-center}
<br>

# 최대한 Semantic적으로 태그 사용하기

time 태그는 일반 텍스트로 보이는 날짜와 시간 정보를 진짜 날짜, 시간 정보임을 HTML에게 알려주기 위해 사용한다.
![](https://kimmy100b.github.io/assets/images/codereview/aboutme/FE/10.PNG){: .align-center}
<br>

# 질문

## 질문 1

Q. css를 적용하지 않을 태그면 class명을 안줘도 상관이 없나요? css를 적용하지 않더라도 class명을 줘야하는 경우는 어떤 경우인가요?
<br>
A. class나 id를 사용하는 목적은 크게 두 가지가 있습니다. <br>
첫 번째는 학습자님이 말씀하신데로 공통적 혹은 개인적인 CSS를 적용하기 위함이었고, 두 번째는 Javascript에서 요소들을 셀렉팅하기 위함입니다.<br>
만약 위의 두 개의 경우에 포함되지 않는다면 CSS를 지정하지 않아도 됩니다.

## 질문 2

Q.서블릿에 css를 적용할 때 인라인 말고 파일로 지정해주려고 하면 어떻게 하나요?<br>
`out.print("<link ~");` 이런 식으로 지정해주는 거 맞나요? <br>만약, 맞다면 css파일은 기존 css파일과 같이 있어도 되나요? 아니면 서블릿 파일이 있는 폴더에 있어야하나요?
<br>
A. 서블릿으로 CSS를 적용하고 HTML을 불러오는 경우는 프로젝트1에서 서블릿의 흐름을 알기 위해 루브릭으로 강제한 부분이고, 실제적으로는 자바 서블릿을 통해 저런식으로 구현하지 않습니다.<br>
만약 저런식으로 구현을 한다고 한다면 학습자님이 말한 질문 그대로가 맞습니다.

## 질문 3

Q.코드리뷰 받은 내용을 개인 개발블로그에 올려도 괜찮나요?
<br>
A. 네 코드리뷰 내용은 올리셔도 됩니다. <br>
하지만, 코드 카피의 문제가 있어서 소스코드 첨부는 불가합니다.
<br><br>

# 참고

[MDN - time태그](https://developer.mozilla.org/ko/docs/Web/HTML/Element/time)
