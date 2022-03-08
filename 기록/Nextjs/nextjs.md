next.js 의 경우 프레임워크이기 때문에 react를 사용할 때처럼 route를 따로 설정해주지 않아도 되며 pages안의 파일명을 url로 사용한다.

단, index의 경우는 localhost:3000으로, localhost:3000/index 를 써줄 필요가 없다.

예를 들어 juzzang.js 라는 파일을 만들어서 export 했다면 localhost:3000/juzzang 으로 들어가면 juzzang.js안에 있는 컴포넌트가 보여지게 되는 것

react의 경우 컴포넌트의 이름을 써줘야 하는 것에 반해 next의 경우 컴포넌트의 이름은 중요하지 않으나 export default를 꼭 컴포넌트 앞에 붙여줘야 한다.

## anchor, Link 

+ a 태그를 사용하는 경우 새로운 요청을 통해 페이지 전체를 새롭게 갱신하기 때문에 상태값들이 보존되지 않고 UX역시 떨어지게 된다.

+ Link 컴포넌트와 href prop을 사용한다.

```js
export default function Home() {
  return (
    <div>
        <a>다시 주짱으로</a>
    </div>
  );
}

위와 같이 쓰지 않고

아래와 같이 사용한다.
import Link from 'next/link';

export default function Home() {
  return (
    <div>
      <Link href='/juzzang'>
        <a>다시 주짱으로</a>
      </Link>
    </div>
  );
}
```

## CSS, styles

CSS를 적용하고 싶을 땐 파일이름.module.css 의 형식으로 파일을 생성한다.

className을 적지않고 자바스크립트 오브젝트에서의 프로퍼티 형식으로 적는다.

```js
// NavBar.js
import styles from './NavBar.module.css';

export default function Nav() {
  return (
    <nav className={styles.nav}>
      <a href='/'>집으로</a>
      <h3>프로젝트입니다.</h3>
    </nav>
  );
}
// NavBar.module.css
.nav{
  display: flex;
  color:red;
  background-color: aqua;
};
```

### Style jsx

이런 방법도 있다.
```js
export default function Nav() {
  return (
    <nav>
      <a href='/' className='active'>집으로</a>
      <h3>프로젝트입니다.</h3>
      <style jsx>{`
        nav {
          display: flex;
          color: red;
          background-color: aqua;
        }
         h3 {
          color: orange;
        }
        .active{
          color: blue;
        }
      `}</style>
    </nav>
  );
}

style 태그에 jsx prop을 사용해서 스타일을 주는 방식
className은 . 선택자를 사용한다.

이 방법을 사용하면 해당 컴포넌트에만 독립적으로 사용이 가능하다
```

### 그렇다면 전역으로 사용해야 할 경우엔?

font-familly, font-size 등과 같이 전역으로 css를 사용하고 싶을 때는

_app.js 라는 파일을 생성한다. (꼭 이 이름을 사용해야 한다.)

* next js는 제일 먼저 app을 확인한다.
```js
//_app.js
export default function NextPrct({ Component, pageProps }) {
  return (
    <div>
      <span>111</span>
      <Component {...pageProps} />
      <style jsx global>{`
        a {
          color: skyblue;
        }
      `}</style>
      <span>aaasd</span>
    </div>
  );
}

<style jsx global> global prop을 추가하고
전역으로 관리할 태그를 사용하면 된다.

```