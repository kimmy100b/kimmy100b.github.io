---
layout: post
title: "[JavaScript] `<textarea>`태그 엔터값 줄 바꿈 처리하기"
categories:
  - Javascript
excerpt: " "
comments: true
share: true
tags:
  - Javascript
  - Textarea
date: 2021-01-16T19:30:00-0:05:00
---

```html
<textarea id="textarea"> </textarea>

<span id="content"></span>
```

# JavaScript를 이용해 바꾸어주기

```javascript
// textarea태그값 받아오기
var str = document.getElementById("textarea").value;

// 값에서 엔터를 <br>태그로 변경하기
str = str.replace(/(?:\r\n|\r|\n)/g, "<br />");

// <br>태그로 변경한 값을 다시 넣어주기
document.getElementById("content").innerHTML = str;
```

# Vue에서 적용할 경우

```html
<div v-html="str"></div>
```

# 참고

- <https://seonkyu.tistory.com/17>
