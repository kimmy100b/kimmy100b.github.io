---
layout: post
title: "클린코드로 작성하는 법"
categories:
  - CleanCode
excerpt: " "
comments: true
share: true
tags:
  - CleanCode
date: 2020-08-15T23:34:00-0:05:00
---

# 1. 검색이 가능한 이름을 써라

예를 들어, 하루에 총 몇 초인지를 요구하는 함수가 있다면.<br/>
안좋은 예

```javascript
setInterval(eatKimchi, 86400);
```

좋은 예

```javascript
const SECONDS_IN_A_DAY = 86400;
setInterval(eatKimchi, SECONDS_IN_A_DAY);
```

이유

- 다른 팀원이 봤을 때 그 함수가 무엇을 하는 지 이해를 못할 수 있다
- 다른 팀원이 봤을 때 그 숫자가 무엇을 하는 지 이해를 못할 수 있다

<br/><br/>

# 2. 함수명은 반드시 동사를 써라

안좋은 예 - "유저데이터"

```javascript
function userData() {
  //...
}
const data = userData();
```

좋은 예 - "유저데이터 불러오기"

```javascript
function loaduserData() {
  //...
}
const data = loaduserData();
```

이유

- 함수는 단 하나의 동작만 해야한다

<br/><br/>

# 3. 함수의 인수(argument)는 3개 이하가 적당하다

이유

- 너무 많은 인수를 포함하고 있으면 어떤 인수가 무엇을 하는 지 혼란스럽다

만약, 4개 이상의 많은 인수가 필요할 경우?<br/>
한 개의 configuration object를 보내는 것을 추천!<br/>
예를 들어

```javascript
function makePayment({ price, productId, size, quantity, userId }) {
  //...
}

makePayment({
  price: 35,
  productId: 5,
  size: "xs",
  quantity: 2,
  userId: "kimmy",
});
```

<br/><br/>

# 4. boolean 값을 인수로 함수에 보내는 것을 최대한 방지하자!

이건 2번이랑도 연관되어있다.<br/>
boolean값은 참(true)나 거짓(false)인 결과값을 가진다. <br/>
이 결과값을 함수에 보낼 경우, 함수는 if와 else를 가지게 된다.<br/>
그러면 한 함수 내에 두 가지 동작을 하게 됨으로 2번(함수는 한 가지 동작을 해야한다)에 어긋난다.<br/>

<br/><br/>

# 5. 변수명은 너무 축약하지 말 것. 이해할 수 있는 변수명으로!

예를 들어 변수명 u가 아닌 user, e가 아닌 email, t가 아닌 tel로 다른 사람도 이해할 수 있는 변수명으로 작성해야한다.

<br/><br/>

# 참고

<https://www.youtube.com/watch?v=Jz8Sx1XYb04>
