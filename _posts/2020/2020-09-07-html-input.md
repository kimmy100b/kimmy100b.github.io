---
layout: post
title: "Input태그 변경 못하게 막는 방법(읽기만 가능)"
categories:
  - HTML, CSS
excerpt: " "
comments: true
share: true
tags:
  - readonly
  - disabled
date: 2020-09-07T21:58:00-0:05:00
---

# 1. Readonly

- form으로 값을 보낼때 readonly의 값은 전송된다.

```html
<input type="text" value="test1" readonly />
```

# 2. Disabled

- form으로 값을 보낼때 disabled의 값은 전송되지 않는다.

```html
<input type="text" value="test2" readonly />
```

# type="radio"

```html
<input type="radio" name="test2" value="선택1" checked readonly />선택1
<input type="radio" name="test2" value="선택2" readonly />선택2
```

이렇게 할 경우 잘~ 수정할 수 있다!
<br><br>
그래서 `disabled`인 속성을 주거나 `onclick="return(false);"`을 속성으로 준다.

```html
<input
  type="radio"
  name="test2"
  value="선택1"
  checked
  onclick="return(false);"
/>선택1
<input type="radio" name="test2" value="선택2" onclick="return(false);" />선택2
```

# 참고

- [input 속성 readonly/disabled/차이](https://heojju.tistory.com/75)
- [Radio버튼을 변경 못하게 막는 방법](https://pgmaru.tistory.com/188)
