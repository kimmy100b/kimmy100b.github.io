---
layout: post
title: "[자바스크립트] 객체"
categories:
  - Javascript
excerpt: " "
comments: true
share: true
  - Javascript
  - object
date: 2021-03-18T13:30:00-0:05:00
---

📌 목표<br> 
자바스크립트 객체를 선언하고, 값을 얻는 방법을 알 수 있다.

# 객체
>💡 이름(name)과 값(value)으로 구성된 프로퍼티(property)의 정렬되지 않은 집합이다.

- 자바스크립트의 기본 타입은 객체이다.
- Javascript로 데이터를 표현하기 위해서는 Array, Object를 사용한다.

## 객체 선언

```javascript
var obj = { 
  name : "kimmy", 
  age : 25, 
  favorite : [{ food : 'pizza' }, { color : 'purple' }] 
  }

console.log(obj.name) // 출력 : kimmy
console.log(obj["name"]) // 출력 : kimmy
console.log(obj.favorite[0]) // 출력 : {food: "pizza"}
console.log(obj.favorite[0].food) // 출력 : pizza
```
Object형태는 {}로 그 자료를 표현하며, 서버와 클라이언트 간에 데이터를 교환할 때 자바스크립트 객체구조를 본따 정의한 JSON(JavaScript Object Notation)이라는 것이 있다. 

- 객체 안에 배열, 객체가 들어갈 수도 있다.

## 객체 탐색
>💡 키 값이 있는 객체를 탐색하기 위한 for-in문

**Key값 탐색**

```javascript
for(key in obj){
  console.log(key)
}
/* 출력결과
name
age
favorite
*/

console.log(Object.keys(obj))
/* 출력결과(배열로 출력)
["name", "age", "favorite"] 
*/
```

**Value값 탐색**

```javascript
for(key in obj){
  console.log(obj[key])
}
/* 출력결과
kimmy
25
0: {food: "pizza"}
1: {color: "purple"}
*/

Object.keys(obj).forEach(function(v){console.log(obj[v])})
/* 출력결과
kimmy
25
0: {food: "pizza"}
1: {color: "purple"}
*/
```

## 객체의 추가 및 삭제
```javascript
const myFriend = { key : "value", key2 : "value" };
console.log(myFriend);

// 객체 속성 추가
myFriend["name"] = "crong";
console.log(myFriend["name"]);

myFriend.age = 34;
console.log(myFriend.age);

// 객체 속성 삭제
delete myFriend.key;
delete myFriend["key2"];
console.log(myFriend);
```

# 직접 실습해보기

## 실습 1
**문제**<br>
숫자 타입으로만 구성된 요소를 뽑아 배열을 만들어보세요.<br>
[링크 바로가기](https://gist.github.com/crongro/ade2c3f74417fc202c8097214c965f27)<br>
```javascript
//실행결과
["width", "height", "hOffset", "vOffset", "size", "hOffset", "vOffset"]
```

**솔루션**
```javascript
for(key in data){
  if(typeof data[key] === "object"){
    for(oKey in data[key]){
      if(typeof data[key][oKey] === "number"){
        console.log(oKey)
      }
    }
  }
}
```

## 실습 2
**문제**<br>
type이 sk인, name으로 구성된 배열만 출력하세요.<br>
[링크 바로가기](https://gist.github.com/crongro/a9a118977f82780441db664d6785efe3)<br>
```javascript
//실행결과
["Yong", "hary", "solvin", "hani", "chulsu"]
```

**솔루션**
```javascript
function find(data, array) {
  data.forEach(obj => {
    if(obj.type == "sk")
      array.push(obj.name)
    find(obj.childnode, array)
  })
}

var array = []

find(data, array)

console.log(array)
```

# 배열과 객체의 차이
배열 : 순서가 있는 리스트 / 탐색 -> for문, foreach문<br>
객체 : 순서가 없고 키 값이 있음 / 탐색 -> for-in문

# 참고
- [네이버 부스트코스](https://www.boostcourse.org/web316/lecture/16746/?isDesc=false)
- [TCP School](http://www.tcpschool.com/javascript/js_object_concept)
