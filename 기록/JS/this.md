## `this 🔥`

+ this란 무엇인가?
  + this란 함수를 호출하는 방법에 의해 결정되는 자기참조 변수이다.
+ this 바인딩이란?
  + this와 this가 가리키는 객체를 바인딩 하는 것
    + 바인딩이란 식별자와 값을 연결하는 과정을 의미.

함수의 scope는 선언을 기준으로 하지만 <br/>
함수의 this는 호출을 기준으로 한다.

```js
const someone = {
  name: 'jihoon',
  whoAmI: function () {
    console.log(this.name);
  },
};
someone.whoAmI(); 
// function() {console.log(this)}가 실행됐고 호출한 객체는 someone이라 this는 someone을 가리키며 'jihoon'을 반환

const whoAmITwo = someone.whoAmI;
whoAmITwo(); 
// function() {console.log(this)}가 실행됐으나 호출한 객체가 window(global)라 this는 window(global)을 가리키며 'undefined'를 반환

>>> this는 this를 호출한 객체가 됨을 알 수 있다.
```

## 동적으로 변경되지 않는 경우

this는 호출하는 방법에 따라 동적으로 변경되는데, 호출하는 방법에 따라 변경되지 않는 두 가지 경우가 있다.
1. 함수의 bind 메소드를 사용하여 값을 지정해준 경우 this의 값이 고정된다.
```js
const bindedWhoAmI = whoAmITwo.bind(someone);
bindedWhoAmI(); 

// >>> bind 메서드로 this를 someone으로 지정했기 때문에 bindedWhoAmI()를 실행해도 window(global)가 아닌 someone을 가리키게 되는 것이고 따라서 'jihoon'을 반환한다.

```

2. 화살표 함수인 경우
   + 화살표 함수의 this는 상위 스코프의 this를 가리킨다.

+ 일반 함수를 사용한 경우
```js
this.name = 'king';

const someone = {
  name: 'jihoon',
  whoAmI: function () {
    console.log(this.name);
  },
};
someone.whoAmI(); // jihoon을 반환
```
+ 화살표 함수를 사용한 경우
```js
this.name = 'king';

const someone = {
  name: 'jihoon',
  whoAmI: () => {
    console.log(this.name);
  },
};
someone.whoAmI(); // king을 반환
```