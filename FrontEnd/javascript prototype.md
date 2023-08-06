# Javascript Prototype
- Java, C++과 같은 class 기반 객체지향 프로그래밍 언어와 달리 자바스크립트는 프로토타입 기반 객체지향 프로그래밍 언어이다.
- 자바스크립트 class는 사실 엄밀히 말해서 class를 따라하는 특별한 함수이다.
- 자바스크립트의 모든 객체는 Prototype이라는 다른 객체와 연결되어 있다.
- 이 프로토타입은 해당 객체가 가지고 있지 않은 속성이나 메서드에 접근할 수 있도록 도와주는 매우 중요한 개념이다.




## 자바스크립트의 Prototype 이란?


```js
const howoo = {
  age: 6,
  color: 'gold',
  isCute: true,
};
```

- 다음과 같이 객체 리터럴로 객체를 생성하면 실제로는 아래와 같은 작업이 일어난다.

```js
const howoo = new Object({ age: 6, color: 'gold', isCute: true });
```

- 즉 Object 생성자 함수를 통해 객체가 생성이 된다.

<img width="312" alt="image" src="https://github.com/howooking/CS_Study_for_Interview/assets/87072568/d17434aa-9387-4503-90b6-54bc2528b16f">

- 생성된 객체에는 <b>[[Prototype]]</b> 이라는 것이 들어 있다.

![image](https://github.com/howooking/CS_Study_for_Interview/assets/87072568/e8f5b57b-c600-43fe-a574-34844fee9870)

- 크롬 과거 버전에서는 __proto__라고 표시 되나 이는 [[Prototype]]과 동일함
- 실제로 [[Prototype]]에 접근하기 위해서는 howoo.__proto__를 해야함.

<img width="301" alt="image" src="https://github.com/howooking/CS_Study_for_Interview/assets/87072568/e91e9739-51bb-41f5-97d6-b02726409c75">














<img width="344" alt="image" src="https://github.com/howooking/CS_Study_for_Interview/assets/87072568/c60df264-353c-47e5-b60e-6ea15faf3607">

- 브라우저 콘솔에 아무 객체나 생성하고 찍어보면 내가 만들지도 않은 <b>[[Prototype]]: Object</b> 가 있다.

<img width="282" alt="image" src="https://github.com/howooking/CS_Study_for_Interview/assets/87072568/880839c9-1ea0-4105-9d14-1854120791a9">

- 열어보면 알 수 없는 것들로 가득함.
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
