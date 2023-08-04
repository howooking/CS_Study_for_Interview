# Prototpye

## 자바스크립트의 Prototype 이란?
<img width="344" alt="image" src="https://github.com/howooking/CS_Study_for_Interview/assets/87072568/c60df264-353c-47e5-b60e-6ea15faf3607">

- 브라우저 콘솔에 아무 객체나 생성하고 찍어보면 내가 만들지도 않은 <b>[[Prototype]]: Object</b> 가 있다.

<img width="282" alt="image" src="https://github.com/howooking/CS_Study_for_Interview/assets/87072568/880839c9-1ea0-4105-9d14-1854120791a9">

- 열어보면 알 수 없는 일들이 가득함
- Prototype 개념을 class 개념으로 이해하면 안된다.
  - 자바스크립트에서는 class가 없다
  - 자바스크립트에서는 '복사'를 통한 상속이 없다.
  - Prototype은 클래스, 객체의 내용 복사 없이도 상속을 구현할 수 있게 하는 방법
  - Prototpye은 상속이 아니라 연결이다.

# 자바스크립트가 객체를 찍어내는 방법
```js
function Cat(name) {
  this.name = name;
  this.meow = function () {
    console.log(`MEOW! my name is ${this.name}`);
  };
}

const howoo = new Cat('howoo');
```

<img width="692" alt="image" src="https://github.com/howooking/CS_Study_for_Interview/assets/87072568/4027e49f-df8f-45f7-9fe7-4e38d63d5a89">
```js
class Cat {
  constructor(name) {
    this.name = name;
    this.meow = function () {
      console.log(`MEOW! my name is ${this.name}`);
    };
  }
}

```
