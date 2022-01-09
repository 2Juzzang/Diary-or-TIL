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
자신을 포함하고 있는 외부함수보다 내부함수가 더 오래 유지되는 경우(위에서 inner라는 변수에 내부함수(innerFunc)를 할당했으므로 더 오래 유지되고있다.)

외부 함수(outerFunc()) 밖에서 내부함수가 호출되더라도 외부함수의 지역 변수에 접근할 수 있는데 이러한 함수를 클로저(Closure)라고 부른다.

이렇게 생명주기가 다 했어도 스코프에 접근할 수 있는 이유는 클로저는 자신이 생성될 때의 환경(Lexical Environment)을 기억하는 함수이기 때문이다.

생성 시점에 결정된 Lexical Environment에 의해 오직 클로저에서만 x라는 변수에 접근할 수 있고, 이 x라는 변수가 조작될 여지가 없도록 폐쇄된 모습이다.

## 예제 
전역 변수를 사용하지 않고도 현재 상태(혹은 값)를 기억하고 변경된 최신 상태를 유지할 수 있다.
```html
<!DOCTYPE html>
<html>
<body>
  <div class="box" style="width: 100px; height: 100px; background: green;"></div>

  <script>
    // Box Color Toggler
    const box = document.querySelector('.box');

    const toggleColor = (function () {
      let isGreen = true;
      // 클로저 반환
      return function () {
        box.style.background = isGreen ? 'red' : 'green';
        // 상태 변경
        isGreen = !isGreen;
      };
    })();
    // 박스 클릭 이벤트
    box.addEventListener('click', toggleColor);
  </script>
</body>
</html>
```
이렇게 불필요한 전역 변수를 사용하지 않음으로서 얻는 이득은 상당하다.

의도되지 않은 변경을 개발자가 걱정할 필요가 없기 때문에 코드가 안정적이게 된다. 

**필요한 곳에서만 해당 변수에 접근할 수 있게 하고 그 외부에서는 접근하지 못하게 막는(closure)** 코드는 예상치 못한 부작용을 막을 수 있는 좋은 코드라고 할 수 있다.


+ 토글 기능은 전역 변수로만 해야된다고 생각했는데 클로저를 사용하면 전역 변수를 쓰지 않고도 가능하다는 것을 알게 되었다.

