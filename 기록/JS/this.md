## `this ๐ฅ`

+ this๋ ๋ฌด์์ธ๊ฐ?
  + this๋ ํจ์๋ฅผ ํธ์ถํ๋ ๋ฐฉ๋ฒ์ ์ํด ๊ฒฐ์ ๋๋ ์๊ธฐ์ฐธ์กฐ ๋ณ์์ด๋ค.
+ this ๋ฐ์ธ๋ฉ์ด๋?
  + this์ this๊ฐ ๊ฐ๋ฆฌํค๋ ๊ฐ์ฒด๋ฅผ ๋ฐ์ธ๋ฉ ํ๋ ๊ฒ
    + ๋ฐ์ธ๋ฉ์ด๋ ์๋ณ์์ ๊ฐ์ ์ฐ๊ฒฐํ๋ ๊ณผ์ ์ ์๋ฏธ.

ํจ์์ scope๋ ์ ์ธ์ ๊ธฐ์ค์ผ๋ก ํ์ง๋ง <br/>
ํจ์์ this๋ ํธ์ถ์ ๊ธฐ์ค์ผ๋ก ํ๋ค.

```js
const someone = {
  name: 'jihoon',
  whoAmI: function () {
    console.log(this.name);
  },
};
someone.whoAmI(); 
// function() {console.log(this)}๊ฐ ์คํ๋๊ณ  ํธ์ถํ ๊ฐ์ฒด๋ someone์ด๋ผ this๋ someone์ ๊ฐ๋ฆฌํค๋ฉฐ 'jihoon'์ ๋ฐํ

const whoAmITwo = someone.whoAmI;
whoAmITwo(); 
// function() {console.log(this)}๊ฐ ์คํ๋์ผ๋ ํธ์ถํ ๊ฐ์ฒด๊ฐ window(global)๋ผ this๋ window(global)์ ๊ฐ๋ฆฌํค๋ฉฐ 'undefined'๋ฅผ ๋ฐํ

>>> this๋ this๋ฅผ ํธ์ถํ ๊ฐ์ฒด๊ฐ ๋จ์ ์ ์ ์๋ค.
```

## ๋์ ์ผ๋ก ๋ณ๊ฒฝ๋์ง ์๋ ๊ฒฝ์ฐ

this๋ ํธ์ถํ๋ ๋ฐฉ๋ฒ์ ๋ฐ๋ผ ๋์ ์ผ๋ก ๋ณ๊ฒฝ๋๋๋ฐ, ํธ์ถํ๋ ๋ฐฉ๋ฒ์ ๋ฐ๋ผ ๋ณ๊ฒฝ๋์ง ์๋ ๋ ๊ฐ์ง ๊ฒฝ์ฐ๊ฐ ์๋ค.
1. ํจ์์ bind ๋ฉ์๋๋ฅผ ์ฌ์ฉํ์ฌ ๊ฐ์ ์ง์ ํด์ค ๊ฒฝ์ฐ this์ ๊ฐ์ด ๊ณ ์ ๋๋ค.
```js
const bindedWhoAmI = whoAmITwo.bind(someone);
bindedWhoAmI(); 

// >>> bind ๋ฉ์๋๋ก this๋ฅผ someone์ผ๋ก ์ง์ ํ๊ธฐ ๋๋ฌธ์ bindedWhoAmI()๋ฅผ ์คํํด๋ window(global)๊ฐ ์๋ someone์ ๊ฐ๋ฆฌํค๊ฒ ๋๋ ๊ฒ์ด๊ณ  ๋ฐ๋ผ์ 'jihoon'์ ๋ฐํํ๋ค.

```

2. ํ์ดํ ํจ์์ธ ๊ฒฝ์ฐ
   + ํ์ดํ ํจ์์ this๋ ์์ ์ค์ฝํ์ this๋ฅผ ๊ฐ๋ฆฌํจ๋ค.

+ ์ผ๋ฐ ํจ์๋ฅผ ์ฌ์ฉํ ๊ฒฝ์ฐ
```js
this.name = 'king';

const someone = {
  name: 'jihoon',
  whoAmI: function () {
    console.log(this.name);
  },
};
someone.whoAmI(); // jihoon์ ๋ฐํ
```
+ ํ์ดํ ํจ์๋ฅผ ์ฌ์ฉํ ๊ฒฝ์ฐ
```js
this.name = 'king';

const someone = {
  name: 'jihoon',
  whoAmI: () => {
    console.log(this.name);
  },
};
someone.whoAmI(); // king์ ๋ฐํ
```

## bind(), call(), apply()
```js
let person1 = {
  name: 'Jo',
};

let person2 = {
  name: 'Kim',
  study: function () {
    console.log(this.name + '์ด/๊ฐ ๊ณต๋ถ๋ฅผ ํ๊ณ  ์์ต๋๋ค.');
  },
};
person2.study();
person2.study.bind(person1); // ํจ์๋ฅผ ํธ์ถํ์ง ์์
person2.study.call(person1); // Jo์ด/๊ฐ ๊ณต๋ถ๋ฅผ ํ๊ณ  ์์ต๋๋ค.
person2.study.apply(person1); // Jo์ด/๊ฐ ๊ณต๋ถ๋ฅผ ํ๊ณ  ์์ต๋๋ค.
```
call, apply, bind์ ์ฒซ๋ฒ์งธ ๋งค๊ฐ๋ณ์๋ this์ ๊ฐ์ ์ ํ๋ค.
call, apply๋ ํจ์๋ฅผ ํธ์ถํ๋ ๋ฐ๋ฉด, bind๋ ํจ์๋ฅผ ํธ์ถํ์ง ์๋๋ค.

```js
let student = person2.study.bind(person1);
student(); // Jo์ด/๊ฐ ๊ณต๋ถ๋ฅผ ํ๊ณ  ์์ต๋๋ค.
```
bind๋ ๋ณ์๋ฅผ ํ ๋นํ์ฌ ํธ์ถํ๋ ํํ๋ก ์ฌ์ฉํด์ผ ํจ์ ์ ์ ์๋ค.