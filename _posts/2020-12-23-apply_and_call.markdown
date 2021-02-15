---
title: Javascript 문법 - apply, call.
author: Roharui
date: 2020-12-23 15:30:00 +0800
categories: [Blogging, Tutorial]
tags: [Javascript]
---

## apply와 call

`apply`와 `call` 전부 함수 객체의 `prototype`입니다. 그런 고로 모든 함수에는 자연스레 두 메소드가 붙어있고 다음과 같이 사용이 가능합니다.

```javascript
function hello(name){
    console.log(`Hello! ${name}!`)
}

hello("Anne")  // Hello! Anne!

hello.call(null, "Anne")    // Hello! Anne!
hello.apply(null, ["Anne"]) // Hello! Anne!
```

둘다 지정된 함수를 실행시키는 일을 하지만 `call`은 매개변수를 따로따로 받는 다면 `apply`는 배열 형태로 매개변수를 받습니다.

## this 지정

하지만 함수를 실행하는 것이 이 메소드의 전부라면 사람들이 사용하지 않았을 겁니다. 
이 메소드의 핵심적인 기능은 `this`를 지정할수 있다는 겁니다.

```javascript
var x = {name:"Pray"}

function hello(name){
    if(this.name){
        name = this.name
    }
    console.log(`Hello! ${name}!`)
}

hello.call(null, "Anne")    // Hello! Anne!
hello.apply(x, ["Anne"])    // Hello! Pray!
```

`call`에서는 이 함수의 `this`를 지정하지 않았기에 `this.name`이 `undefined`가 호출됩니다. 그렇기 입력된 `Anne`이 그대로 출력된 반면.
`apply`에서는 `x`를 함수의 `this`로 지정해 두었기 때문에 `x.name`인 `Pray`가 출력되는 걸 볼수 있습니다.

## 부가 메소드 bind

`call`과 `apply`가 사용하기 불편하다는 분들은 `bind`를 사용해보세요

```javascript
var x = {name:"Pray"}

function hello(name){
    if(this.name){
        name = this.name
    }
    console.log(`Hello! ${name}!`)
}

var hellox = hello.bind(x)

hellox("Anne") // Hello! Pray!
```

`bind`는 `this`를 원하는 객체로 지정한 함수를 리턴합니다.
리턴된 함수는 새로운 객체가 되니 기존에 있는 함수의 `this`가 바꼈다고 생각하지 맙시다.