---
layout: post
title: "[HTML] Textarea에 값 넣는 방법"
categories:
  - HTML&CSS
excerpt: " "
comments: true
share: true
tags:
  - HTML&CSS
  - Textarea
date: 2020-11-03T16:34:00-0:05:00
---

> `<textarea>`에 value 속성을 주어 값을 넣어주니 들어가지 않는다.

# 문제사항

```html
<input type="text" value="값이 들어가는 곳!" />

<textarea value="값이 들어가는 곳!"></textarea>
```

input에는 값이 잘 들어가지만 textarea에는 값이 들어가지 않는다.

# 해결방법

```html
<textarea>여기에 값을 넣어줘야한다.</textarea>
```
