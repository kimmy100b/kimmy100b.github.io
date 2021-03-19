---
layout: post
title: "[자바스크립트] 배열"
categories:
  - Javascript
excerpt: " "
comments: true
share: true
  - Javascript
  - array
  - array method
date: 2020-12-24T20:30:00-0:05:00
---

📌 목표<br> 
자바스크립트 배열을 다루는 방법을 알아보기

# 배열

## 배열의 선언
>💡 각각의 값인 요소(element)와 인덱스(index)로 참조되는 정렬된 값의 집합이다.

```javascript
var a = [];
// 배열 안에는 모든 타입이 다 들어갈 수 있다.(함수, 배열, 객체 등)
var a = [1, 2, 3, "hello", null, true, []];
```

new Array() 문으로 선언할 수 있지만 보통은 간단히 `[]`를 사용한다.<br>
배열에는 length속성이 있어 그 길이를 쉽게 알 수 있다.

예제1)

```javascript
var a = [4];
// 배열에 원소 추가는 index번호와 함께 추가할 수 있다.
a[1000] = 3;
console.log(a.length); // 실행결과 : 1001
console.log(a[500]); // 실행결과 : undefined
```

예제2) push 메소드<br>
push메소드를 통해 뒤에 순차적으로 추가할 수 있다.

```javascript
var a = [4];
a.push(5);
console.log(a.length);
```

## 배열의 유용한 메서드들

### indexOf

> 💡 `indexOf()` 메서드는 호출한 String 객체에서 주어진 값과 일치하는 첫 번째 인덱스를 반환한다. 일치하는 값이 없으면 -1을 반환한다.

`str.indexOf(searchValue[, fromIndex])` <br>

**매개변수** <br>

- `searchValue` : 찾으려는 문자열. 아무 값도 주어지지 않으면 문자열 `undefined`를 찾으려는 문자열로 사용<br>
- `fromIndex` : [옵션] 문자열에서 찾기 시작하는 위치를 나타내는 인덱스 값. 기본값은 0이며, 문자열 전체를 대상으로 찾는다.<br>

**반환값** <br>

- `searchValue`의 첫 번째 등장 인덱스. 찾을 수 없다면 -1.

참고. <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf>

### join

> 💡 `join()` 메서드는 배열의 모든 요소를 연결해 하나의 문자열로 만든다.

`arr.join([separator])` <br>

**매개변수** <br>

- `separator` : [옵션] 배열의 각 요소를 구분할 문자열을 지정한다. 만약 생략할 경우, 배열의 요소들이 쉼표로 구분된다. 빈 문자열일 경우 모든 요소들 사이에 아무 문자도 없이 연결된다.

**반환값** <br>

- 배열의 모든 요소들이 연결한 하나의 문자열을 반환한다. 만약, `arr.length`가 0이라면, 빈 문자열을 반환한다.

예제)

```javascript
var a = ["바람", "비", "불"];
var myVar1 = a.join(); // myVar1에 '바람,비,불'을 대입
var myVar2 = a.join(", "); // myVar2에 '바람, 비, 불'을 대입
var myVar3 = a.join(" + "); // myVar3에 '바람 + 비 + 불'을 대입
var myVar4 = a.join(""); // myVar4에 '바람비불'을 대입
```

참고. <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join>

## concat

> 💡 `concat()` 메서드는 인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환한다.

`array.concat([value1[, value2[, ...[, valueN]]]])` <br>

**매개변수** <br>

- 배열 또는 값
- 만약 value1 ~ valueN 인자를 생략하면 기존배열의 얕은 복사본을 반환.

**반환값** <br>

- 새로운 Array 객체

기존 배열을 변경하지 않고 추가된 새로운 배열을 반환한다.

예제1)

```javascript
const array1 = ["a", "b", "c"];
const array2 = ["d", "e", "f"];
const array3 = array1.concat(array2);

console.log(array3); // Array ["a", "b", "c", "d", "e", "f"]
```

예제2 - ES문법)
`...` 연산자를 스프레드 연산자라고 부른다.

```javascript
var origin = [1, 2, 3, 4];
var result = [...origin, 2, 3];
// var result = origin.concat(2,3);

console.log(origin, result);
```

참고. <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/concat>

# 배열 탐색 - (foreach, map, filter)

이 부분을 이해한 후에 reduce를 공부하고, some, every등도 같이 알아보면 좋습니다.

## forEach

`forEach()` 메서드는 주어진 함수를 배열 요소 각각에 대해 실행한다.

예제)

```
const array1 = ['a', 'b', 'c'];

array1.forEach(e => console.log(e));
```

출력)

```
"a"
"b"
"c"
```

## Map

`Map` 객체는 키-값 쌍을 저장하며 각 쌍의 삽입 순서도 기억하는 콜렉션이다. <br>
요소의 삽입 순서대로 원소를 순회한다. `for...of` 반복문은 각 순회에서 `[key, value]`로 이루어진 배열을 반환한다.

참고. <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Map>

## filter

`filter()` 메서드는 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환한다.

예)

```javascript
const words = [
  "spray",
  "limit",
  "elite",
  "exuberant",
  "destruction",
  "present",
];

const result = words.filter((word) => word.length > 6);

console.log(result);
// 출력결과 : Array ["exuberant", "destruction", "present"]
```

참고 . <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter>

## some

`some()` 메서드는 배열 안의 어떤 요소라도 주어진 판별 함수를 통과하면 true, 전부 통과못하면 false 결과를 출력한다.

예)

```javascript
const array = [1, 2, 3, 4, 5];

const even = (element) => element % 2 === 0;
console.log(array.some(even)); // true : 2,4가 통과

const test = (element) => element % 6 === 0;
console.log(array.some(test)); // false : 하나도 통과하지 못했기 때문에
```

참고. <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/some>

## every

`every()` 메서드는 배열 안의 모든 요소가 주어진 판별 함수를 통과하는지 테스트한다.

예)

```javascript
const array1 = [1, 30, 39, 29, 10, 13];

const isBelowThreshold = (currentValue) => currentValue < 40;
console.log(array1.every(isBelowThreshold)); // true

const isBelowThreshold = (currentValue) => currentValue < 35;
console.log(array1.every(isBelowThreshold)); // false : 39가 35 미만이 아니기 때문에
```

참고. <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/every>

# 참고
- [네이버 부스트코스](https://www.boostcourse.org/web316/lecture/16745/?isDesc=false)
- [Javascript Array Object](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [JavaScript Array Reference](https://www.w3schools.com/jsref/jsref_obj_array.asp)
