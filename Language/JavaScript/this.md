## this의 기본 동작 원리

`this`는 함수가 호출되는 방식에 따라 가리키는 대상을 다르게 설정합니다.  
일반 함수로 호출될 때는 전역 객체를 가리키고,
메소드로 호출될 때는 해당 메소드를 호출한 객체를 가리킵니다.

```js
const test = {
  prop: 42,
  func: function () {
    return this.prop;
  },
};

console.log(test.func());
// Expected output: 42
```

> **메서드에서의 this**
> 해당 메서드가 호출된 객체를 참조

```js
// 웹 브라우저에서는 window 객체가 전역 객체
console.log(this === window); // true

a = 37;
console.log(window.a); // 37

this.b = "MDN";
console.log(window.b); // "MDN"
console.log(b); // "MDN"
```

> **전역 함수에서의 this**  
> `strict mode`에서는 `undefined`  
> strict mode가 아닐 때에서는 `window(웹 브라우저)` 또는 `global`

<br />

### 내부 함수에서의 this

내부 함수에서는`this`가 다르게 동작합니다. 내부 함수는 일반적으로 `this`를 상위 함수의 `this`와 공유하지 않습니다.

```js
const obj = {
  value: 42,
  getValue: function () {
    function inner() {
      console.log(this); // 전역 객체 또는 undefined (strict mode)
    }
    inner();
  },
};

obj.getValue();
```

> **내부 함수에서의 this**  
> `strict mode`에서는 `undefined`  
> strict mode가 아닐 때에서는 `window(웹 브라우저)` 또는 `global`

<br />

### call, apply, bind 메서드를 사용한 this의 지정

`call`, `apply`, `bind` 메서드를 사용하면 `this`를 임의로 지정할 수 있습니다.
이 메서드들은 함수의 `this`를 원하는 객체로 설정할 수 있게 해줍니다.
이를 통해 함수의 `this`를 유연하게 조작할 수 있습니다.

```js
function foo() {
  console.log(this.name);
}

const obj = {
  name: "Alice",
};

foo.call(obj); // 'Alice'   첫번째 인자: 참조할 객체, 두번째 인자: 인수
foo.apply(obj); // 'Alice'
const boundFoo = foo.bind(obj);
boundFoo(); // 'Alice'
```

> **call, apply, bind 메서드**  
> 함수의 `this`를 원하는 객체로 설정할 수 있습니다.

<br />

### 클래스에서의 this

클래스 내에서 `this`는 해당 클래스의 인스턴스를 가르킵니다. 클래스의 메소드에서 `this`를 사용하면 해당 메소드를 호출한 인스턴스를 참조하게 됩니다.

왜냐하면 클래스의 메소드는 해당 클래스의 인스턴스를 기반으로 동작하기 때문입니다. 따라서 클래스 내에서 `this`는 항상 해당 클래스의 인스턴스를 가리키게 됩니다.

```js
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
}
```

`constructor`는 클래스의 생성자 메서드
`constructor(name)`은 매개변수로 `name`을 받고, 이를 객체의 `this.name` 속성에 할당합니다.

```js
const alice = new Person("Alice");
```

여기서 `constructor가` 호출되면서 `this.name`에 `'Alice'`가 저장됩니다.
생성된 객체는 `{ name: 'Alice' }` 구조를 가지게 됩니다.

```js
alice 객체는 다음과 같은 구조를 가지고 있습니다.
{
  name: 'Alice',
  greet: function() { ... } // greet 메서드를 상속받음
}
```

```js
alice.greet(); // 'Hello, my name is Alice'
```

> **클래스에서의 this**  
> 해당 클래스의 인스턴스를 가르킵니다.  
> 이를 통해 클래스의 메소드에서 인스턴스의 속성에 접근할 수 있습니다.

<br />

### 화살표 함수와 this

화살표 함수는 일반 함수와는 다르게 `this`를 바인딩하지 않습니다. 화살표 함수 내에서 `this`는 상위 스코프의 `this`를 그대로 사용합니다.

```js
var globalObject = this;
var foo = () => this;
console.log(foo() === globalObject); // true

const obj = {
name: 'Alice',
greet: () => {
console.log(Hello, my name is ${this.name});
}
};

obj.greet(); // 'Hello, my name is undefined'
```

`arrowFunction`: 화살표 함수로 정의되어, `this`는 `obj`의 정의 위치의 상위 스코프에서 결정됩니다. 이 경우 전역 컨텍스트의 `this`(window 또는 undefined)를 사용합니다.

```js
const obj = {
  value: 42,
  regularFunction: function () {
    console.log(this); // 호출한 객체(obj)
  },
  arrowFunction: () => {
    console.log(this); // 정의된 스코프의 this (전역 객체)
  },
};

obj.regularFunction(); // obj 출력
obj.arrowFunction(); // 전역 객체 (window 또는 undefined in strict mode)
```

#### 내부 함수에서 화살표 함수

내부 함수에서 상위 `this`를 유지할 수 있습니다. 이 점때문에 화살표 함수가 메서드 내부에서 자주 사용됩니다.

```js
const obj = {
  value: 42,
  regularMethod: function () {
    const innerFunction = () => {
      console.log(this.value); // this는 regularMethod의 this(obj)
    };
    innerFunction();
  },
};

obj.regularMethod(); // 42
```

> **화살표 함수에서의 this**  
> 호출 방식과 무관하게 정의된 시점의 `this`를 사용  
> 메서드로 화살표 함수를 사용하면 메서드를 호출한 객체가 아니라 전역 객체를 참조하기 때문에 일반적으로 메서드 정의에는 적합하지 않습니다.

<br />

<details>
   <summary>this가 무엇인가요</summary>
<br />

</details>

<details>
   <summary> 바인딩이 무엇인가요?</summary>
<br />

바인딩이란 프로그램의 어떤 기본 단위가 가질 수 있는 구성요소의 구체적인 값, 성격을 확정하는 것을 말합니다.

</details>

### 출처

[MDN-this](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)  
[자바스크립트에서 'this'의 동작 원리와 활용 방법](https://f-lab.kr/insight/understanding-this-in-javascript?gad_source=1&gclid=EAIaIQobChMI64q0yO3siQMVnV0PAh0loxdsEAAYASAAEgL5ZvD_BwE)
