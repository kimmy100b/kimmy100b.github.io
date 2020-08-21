---
layout: post
title: "[PHP] include와 require"
categories:
  - PHP
excerpt: " "
comments: true
share: true
tags:
  - php
  - include
  - require
date: 2020-08-21 T17:42:00-0:05:00
---

# 하나의 코드를 여러 개의 파일로 분리하는 이유

- 자주 사용되는 코드를 별도의 파일로 만들어서 필요할 때마다 재활용할 수 있다.
- 코드를 개선하면 이를 사용하고 있는 모든 애플리케이션의 동작이 개선된다.
- 코드 수정 시에 필요한 로직을 빠르게 찾을 수 있다.
- 필요한 로직만을 로드해서 메모리의 낭비를 줄일 수 있다.
  <br><br>
  다른 php파일을 코드 안으로 불러오는 방법에 대해 알아보자

  <br><br>

# include

```php
<?php
function welcome(){
    return 'Hello world';
}
echo welcome();
?>
```

위 코드는 문제가 없다. 만약, welcome이라는 함수를 자주 사용한다면 필요할 때마다 이 함수를 정의해서 사용하는 것은 유지보수도 어렵고 낭비가 될 것이다.<br><br>

그래서 include를 사용하는 것이다.

```php
<?php
function welcome(){
    return 'Hello world';
}
?>
```

```php
<?php
include 'greeting.php';
echo welcome();
?>
```

<br><br>

# 외부의 PHP 파일을 로드하는 방법 4가지

- include
- include_once
- require
- require_once

  <br><br>

include와 require의 차이점은 존재하지 않는 파일의 로드를 시도했을 때 include가 warning을 일으킨다면 require는 fatal error를 일으킨다는 점이다.<br>
(fatal error는 warning보다 심각한 에러이기 때문에 require가 include보다 엄격한 로드방법이다.)<br>
\_once가 붙은 것은 파일을 로드 할 때 단 한번만 로드하면 된다는 의미이다.<br>

<br>

# 참고

[생활코딩 - include와 namespace](https://opentutorials.org/course/62/5138)
