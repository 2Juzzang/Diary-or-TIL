```js
function outerFunc() {
  var x = 10;
  var innerFunc = function () {
    console.log(x);
  };
  return innerFunc;
}
const inner = outerFunc();
inner(); // 10
```
자신을 포함하고 있는 외부함수보다 내부함수가 더 오래 유지되는 경우(위에서 inner라는 변수에 내부함수(innerFunc)를 할당했으므로 더 오래 유지되고있다.),

외부 함수(outerFunc()) 밖에서 내부함수가 호출되더라도 외부함수의 지역 변수에 접근할 수 있는데 이러한 함수를 클로저(Closure)라고 부른다.

이렇게 생명주기가 다 했어도 스코프에 접근할 수 있는 이유는 클로저는 자신이 생성될 때의 환경(렉시컬 환경)을 기억하는 함수이기 때문이다.