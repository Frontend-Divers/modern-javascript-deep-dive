# 10장 객체 리터럴

## 10.1 객체란?

<br>

- 자바스크립트에서는 원시값을 제외하고 모든 것이 객체다.
- 객체는 타입이라기보다 여러 값을 취급하는 자료구조에 가깝다.
- 객체는 프로퍼티들로 구성되어 있으며 각 프로퍼티는 키, 값의 형태로 관리된다.
- 일반적으로 키는 문자열로 취급되지만 symbol타입을 키로 사용할 수도 있다.
- 프로퍼티에는 자바스크립트에서 취급하는 모든 타입의 값이 들어갈 수 있다.
- 자바스크립트의 객체는 일급 객체이다.

> 일급객체란?
> 
> 18장에서 다루긴하지만 간략하게 언급하자면 일급객체는 다음 3가지 조건을 충족하는 객체를 의미한다.
>
> 1. 값으로써 할당될 수 있다.
> 2. 함수에 인자로 사용될 수 있다.
> 3. 함수의 반환값으로 사용되 수 있다.

## 10.2 객체 리터럴에 의한 객체 생성

### 리터럴이란?
책에서는 리터럴을 두고 '사람이 이해할 수 있는 문자 또는 약속된 기호를 사용하여 값을 생성하는 표기법'이라 정의한다. 쉽게 말하면 '직접 적어서 표현한' 값이라고 할 수 있겠다. 마트에 가서 콜라 한 병을 결제한다고 생각해보자. 우리는 결제수단으로 삼성페이, 실물 카드, 1000원 지폐 3장 등 여러가지 방법을 사용할 수 있다. 그러나 이중 1000원짜리 지폐만이 리터럴로 취급될 수 있다. 카드는 고정적인 값을 가지지 않는다. 쉽게 말해 알바 입장에서는 카드로 실제로 결제가 이루어지기 전까지는 콜라 한 병에 대한 값을 지불할 능력이 있는지 알 수 없다. 이는 카드라는 대상이 고정적인 가치를 지니지 않다는 사실을 내포한다. 그러나 현금은 어떠한가. 현금 3천원은 어제도 3천원이었고, 오늘도 3천원이며 별일 없으면 내일도 3천원일 것이다. 이러한 현금처럼 리터러를 고정적인 값을 가지며 해당하는 타입의 값에 있어 최소 단위가 된다. 1, 1.5, "hey" [1,2,3], { a: 1 } 등으로 표현되는 모든 리터럴 표현은 그 하나하나가 고정적인 하나의 값만을 의미한다.

### 객체 리터럴
- 객체를 생성하는 가장 간단한 방법은 객체 리터럴이다.
- 객체 리터럴은 중괄호({})로 표현하며 하나의 프로퍼티에 대해 콜론(:)을 기준으로 왼편에는 키, 오른편에는 값을 적는다.
- 각 프로퍼티는 쉼표로 구분한다.

```js
const obj = {
  a: "a",
  b: 123
}
```

- 프로퍼티 없이 빈객체로도 선언할 수 있다.

<br>

## 10.3 프로퍼티

<br>

- 앞서 말했듯 프로퍼티는 키와 값을 관리된다.
- 키는 프로퍼티의 식별자 역할을 한다.
- 객체의 키로는 심벌 혹은 문자열이 사용된다.
  - 이외 다른 타입을 사용하면 문자열로 암묵적 형변환 된다.
- 키가 식별자 네이밍 규칙을 준수한다면 따옴표를 생략할 수 있다.
- 대괄호([])를 사용하면 변수의 값을 키로 사용할 수 있다.

```js
const obj = {
  firstName: "...",
  "last-name": "...",
}
```

- 예약어도 프로퍼티의 키로 사용할 수는 있다. 그러나 권장되지 않는다.
- 이미 존재하는 프로퍼티를 한 번 더 선언하면 나중에 선언된 프로퍼티가 기존 것을 덮어쓴다.

<br>

## 10.4 메서드

- 자바스크립트의 프로퍼티 값으로는 모든 타입의 값이 사용될 수 있다.
- 따라서 일급 객체인 자바스크립트의 객체도 프로퍼티 값이 될 수 있으며 함수도 프로퍼티의 값이 될 수 있다.
- 프로퍼티의 값이 함수일 경우 이를 일반 함수와 구분하기 위해 '메서드'라고 부른다.

## 10.5 프로퍼티 접근

- 프로퍼티에 대한 접근은 크게 두가지로 할 수 있다.
  - 점(.) 연산자에 의한 접근
  - 대괄호([]) 연산자에 의한 접근
- 점 연산자로 접근할 경우 점에는 식별자 네이밍 규칙을 준수하는 단어만 올 수 있다.
- 대괄호 안에는 식별자 혹은 리터럴을 넣을 수 있다.
- 프로퍼티에 접근하여 값을 읽을 뿐아니라 값을 변경할 수도 있다.
  ```js
  const obj = {
    "first-value": 1,
    secondValue: 2
  }
  
  // 값을 변경
  obj.["first-value"] = 3;
  obj.secondValue = 4;

  // 값을 참조
  console.log(obj.["first-value"]); // 3
  console.log(obj.secondValue); // 4
  ```
- 객체 안에 없는 프로퍼티를 참조하면 undefined를 반환한다.
- 객체 안에 없는 키에 값을 할당하면 새로운 프로퍼티가 생성된다.
  ```js
  const obj = {};

  console.log(obj.a); // undefined
  obj.a = 1;
  console.log(obj.a); // 1
  ```

  <br>

## 10.8 프로퍼티 삭제

<br>

- delete 연산을 통해 객체의 프로퍼티를 삭제할 수 있다.
- delete 연산의 피연산자는 프로퍼티 값에 접근할 수 있는 표현식이어야 한다.

```js
const obj = { a: 1 }

delete obj.a;
consol.log(obj.a); // undefined;
```

<br>

## 10.9 ES6에서 추가된 객체 리터럴의 확장 기능

### 프로퍼티 축약 표현
- 프로퍼티의 값을 변수를 사용하는 경우 프로퍼티의 키가 변수명과 같으면 이를 축약해서 나타낼 수 있다.

```js
const someValue = "hey!!";
const obj = {
  someValue: someValue,
};

// 위 표현을 아래처럼 나타낼 수 있다.

const someValue = "hey!!";
const obj = {
  someValue,
};

```

### 계산된 프로퍼티 이름
- 대괄호([])를 사용하면 객체 리터럴 상에서 표현식의 평가값을 키로 사용할 수 있다.

```js
const key = "key";

const obj = {
  [key]: 0,
  [key + 1]: 1,
  [key + 2]: 2,
}

// 위 객체는 다음 리터럴과 같이 해석된다.

const obj = {
  key: 0,
  key1: 1,
  key2: 2,
}
```

- 객체의 키로 변수를 포함하는 표현식을 사용하는 순간 이를 '리터럴'로 부를 수 있나 의문이 든다. 좀 더 공부해봐야겠다.

### 메서드 축약 표현
- 메서드 또한 축약 표현이 존재한다.

```js
// 기존에는 메서드를 다음과 같이 정의했다.
const obj = {
  testFn: function() {
    ...
  },
};

// 축약 표현은 다음과 같다.
const obj = {
  testFn() {
    ...
  }
}
```

- 축약이라고는 했지만 사실 전자와 후자로 선언한 메서드는 조금 성격이 다르다. 축약 표현에 경우 constructor로 사용될 수 없는 등 차이점이 있다. 자세한 내용은 26장에서 다룬다.