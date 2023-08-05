# Prototpye

Java, C++과 같은 클래스 기반 객체지향 프로그래밍 언어와 달리 자바스크립트는 프로토타입 기반 객체지향 프로그래밍 언어이다. 따라서 자바스크립트의 동작 원리를 이해하기 위해서는 프로토타입의 개념을 잘 이해하고 있어야 한다.

클래스 기반 객체지향 프로그래밍 언어는 객체 생성 이전에 클래스를 정의하고 이를 통해 객체(인스턴스)를 생성한다. 하지만 프로토타입 기반 객체지향 프로그래밍 언어는 클래스 없이(Class-less)도 (ECMAScript 6에서 클래스가 추가되었다) 객체를 생성할 수 있다.

## 자바스크립트의 Prototype 이란?
- 자바스크립트의 모든 객체는 자신의 부모 역할을 담당하는 객체와 연결되어 있으며 이 부모 객체를 Prototype이라고 함.

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
const howoo = new Cat('mango');
const howoo = new Cat('rello');
```
 - 대문자로 시작하는 return값이 없는 함수와 new 키워드를 통해서 객체를 생성한다.
   - 빈객체를 생성, {}
   - 빈객체가 this에 바인딩 됨 {} === this
   - 함수 내부가 실행이 되면서 속성을 채워나감
     - {} >> { name: "howoo" } >> { name: "howoo", meow: f }
   - 마지막으로 this(property로 채워진 객체)가 return.
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
