# 4.1 기본 표현식

- 표현식

```jsx
1.23 // -> 숫자 리터럴
"hello" // -> 문자 리터럴
/pattern/ // -> 정규 표현식 리터럴
true // -> 불
null // -> null
this // -> '현재' 객체
undefined // -> 전역 객체의 'undefined' 프로퍼티 값
```

## 4.2  객체와 배열 초기화 표현식

> 새로 생성된 객체나 배열인 표현식

- 배열

```jsx
[] // -> 빈배열
[1+2, 3+4] // -> 요소가 2개인 배열 [3,7]
[[1],[2],[3]] // -> 중첩된 배열
[1,,,,5] // -> 요소가 5개 있는 배열
```

- 객체

```jsx
let p = {x: 2.3, y: -1.2} // -> 프로퍼티가 2개인 객체
let q = {} // -> 프로퍼티가 없는 객체
```

## 4.3 함수 정의 표현식

- function 키워드로 사용하며, 괄호안에 0개 이상의 인자를 넘겨서 중괄호 안에 코드 작성

```jsx
const square = function (x) {
	return x * x
}
```

## 4.4 프로퍼티 접근 표현식

### 4.4.1 **프로퍼티 접근**

- 접근 할 값이 null 또는 undefined 일 경우 TypeError 에러 발생
- 접근 문법
    - expression.identifier
        - 알고있는 유효한 식별자 일 경우 사용
    - expression[identifier]
        - 배열 인덱스로 접근 시 사용
        - 문자열 접근 시 사용

```jsx
let foo = {x:1, y: {z:3}}
let bar = [0, 4,[5,6]];

o.x // -> 1
o.y.z // -> 3
o["x"] // -> 1
a[1] // -> 4
a[2]["1"] // -> 6
a[0].x // -> 1
```

### 4.4.2 **조건부 프로퍼티 접근**

- ES2020 에서 추가된 문법
    - **[Optional chaining](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Optional_chaining)**
    - 객체 속성이나 함수 호출시 값이 **null, undefined** 일 경우 TypeError 에러 발생을 방지하기 위해 사용
- 접근 문법
    - expression?.identifier
    - expression?.[identifier]

```jsx
let a = {b: {}}
a.b.c?.d // -> undefined
a.b.c.d // -> TypeError
```

### 4.5 호출 표현식

- 함수나 메서드를 호출(실행) 하는 문법
- 실행(평가) 순서
    - **함수 표현식의 값이 함수가 아닐 경우 TypeError 에러 발생**
    1. 함수 표현식
        1. return 문을 사용하여 값을 반환하는 것
    2. 인자 표현식 → 인자 값 리스트 생성

```jsx
f(0) // f는 함수 표현식이고 0은 인자 표현식
Math.max(x,y,z) // Math.max는 함수이고 x,y,z 는 인자
a.sort() // a.sort는 함수 이고 인자는 없습니다.
```

- 조건부 호출
    - Optional chaining 을 사용하면 값이 존제할떄만 호출되어 에러 방지

```jsx
function (x, log) {
	log?.(x)
	return x * x
}
```

### 4.6 객체 생성 표현식

- 객체를 생성하고 함수(생성자) 를 호출해 앞에 new 키워드를 붙여 객체 프로퍼티를 초기화
- 전달할 인자가 없다면빈 괄호는 생략할수있다.

```jsx
new Object()
new Point(2,3)
new Date
```

### 4.7 연산자

> 💡 MDN 문서 참고

- [MDN 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Expressions_and_Operators)

- **연산자 우선순위**
    - () 괄호를 사용하여 괄호 안에 있는 대상의 연산을 우선적으로 실행 할 수 있다.

    ```jsx
    1 + 2 * 3 // -> 7
    (1 + 2) * 3 // -> 9
    ```

## 4.8  **산술 표현식**

### 4.8.1 **+ 연산자**

- 문자면 병합,숫자면 덧셈 실행
- 피연산자의 타입이 다를 경우 우선적으로 문자열 병합 진행
- boolean 값이라면 ture : 1 , false: 0 으로변환하여 진행
- null 은  0 으로 변환
- undefined는 NaN

```jsx
1 + 1 // -> 2
"hello" + "world" // -> "hello world"
"1" + "2" // -> 12
"1" + 2 // -> 12
true + ture // -> 2
2 + null // -> 2
2 + undefined // -> Nan
```

### 4.8.2 **증감 연산자**

- 값을 피연산자로 받아 하나의 숫자값을 반환
    - 연산자 뒤에 ++ (접미사) 이 붙으면 증가하기 전의 값을 반환
    - 연산자 앞에 ++ (접두사) 이 붙으면 증가한 후의 값을 반환
    - 연산자 뒤에 -- (접미사) 이 붙으면 감소하기 전의 값을 반환
    - 연산자 앞에 -- (접두사) 이 붙으면 감소한 후의 값을 반환

```jsx
const i = 1;

console.log(i++) // 1
console.log(++i) // 2
console.log(i--) // 1
console.log(--i) // 0
```

### 4.8.3 **비트 연산자**

> ❓ 이건 잘 모르겠음 추가로 공부 필요


## 4.9 관계 표현식

> 💡 두 값이 사이의 관계(동등하다, ~보다 작다, ~의 프로퍼티)를 나타낸다.
- ture 또는 false 인 boolean 값을 반환

### 4.9.1 일치와 불일치 연산자

- 두 값의 일치 여부를 판단 (true, false 반환)
- **== , !=** (동등연산자)
    - 값을 비교할떄 타입 변환을 허용 (타입 비교 X)
    - 값이 일치 할 경우

```jsx
1 == 1 // true
1 == "1" // true
```

- **=== , !==** (일치 연산자)
    - 값과 타입 일치 할 경우
    - 두 값이 모두 null 또는 undefined 인 경우 같은 값
    - 두 값중 하나라도 NaN 이면 다른 값
    - 0 과 -0 도 같은 값

```jsx
1 === 1 // true
1 === "1" // false
0 === -0 // true
1 === "one" //false
```

### 4.9.2 **비교 연산자**

- 두 값의 비교 값을 true 또는 false 반환
- 피연산자의 순서 (숫자 또는 알파벳)를 비교
- 피연산자중 하나가 객체로 평가되면 기본 값으로 변환
    - valueOf() 이후 실패 시 toString() 으로 변환
- 문자열 일 경우 알파벳 순서로 변경
    - 16비트 유니코드값 순서 기준
- NaN 이 존재 할 경우 false 반환

- 종류
    1. **<** (미만)
    2. **>** (초과)
    3. **<=** (이하)
    4. **>=** (이상)

```jsx
11 < 3 // -> false : 숫자 비교
"11" < "3" // -> true : 문자열 비교
"11" < 3 // false : 숫자 비교 ("11" 은 11로 변환)
"one" < 3 // -> false: 숫자 비교 ("one"는 NaN 으로 변환)
```

### 4.9.3 in 연산자


> - 왼쪽 피연산자가 문자열, 심볼, 문자열 로 변환 될 수 있는 값이라고 예상
> - 오른쪽 피연산자는 객체라고 예상


- 왼쪽 피연산자가 오른쪽 객체의 프로퍼티 이름일 경우 true 반환

```jsx
let point = {x: 1, y: 2}
"x" in point // -> true : 프로포티 존재
"z" in point // -> false : 프로퍼티 없음
"toString" in point // -> true : toString 메서드를 상속 받음

let data = [7,8,9]
"0" in data // -> true : 배열에 인덱스(0) 존재
1 in data // -> true : 배열에 인덱스(1) 존재 (1은 "1"로 변환)
3 in data // -> false: 배열에 인덱스 없음
```

### 4.9.4 instanceof 연산자

> - 왼쪽 피연산자는 객체 라고 예상
> - 오른쪽 피연산자는 객체의 클래스 라고 예상

- 왼쪽에 있는 객체가 오른쪽에 있는 클래스의 인스턴스 라면 true 반환

```jsx
let d = new Date();
d instanceof Date // -> true : d는 Date()를 통해 생성
d instanceof Object // -> true : 객체는 모두 Object의 인스턴스
d instanceof Number // -> false : d는 Number 객체가 아님

let a = [1,2,3]
a instanceof Array // -> true : a 는 배열
a instanceof Object // -> true : 배열은 모두 객체
a instanceof RegExp // -> false : 배열은 정규 표현식이 아님
```

## 4.12 논리 표현식 (eval())

> - 동적으로 문자열을 자바스크립트 코드로 해석하고 평가해서 소스코드로 바꾸는기능이다.
> - 보안 문제로 eval() 은 정말 필요한게 아니면 안쓰는게 좋다

- 직접적으로 eval 을 사용 할 경우 eval 은 전역 변수에 접근한다.
- 변수에 할당하여 eval 을 간접적으로 사용할 경우 해당하는 로컬 변수에 사용된다.
- 스트릭트 모드 에서는 eval을 예약어처럼 사용 가능하다.
    - 새 값으로 변경하거나 다시 선언 할 수 없다.

## 4.13 기타 연산자

### 4.13.1 조건 연산자 (?:)

- 삼항 연사자 (?:)
    - 첫번째가 피연산자 - 조건 (boolean)
    - 두번째 피연산자 - ? 이후 내용 (true)
    - 세번째 피연산자 - : 이후 내용 (false)
- if문과 동일하지만 상황에따라 더 간결하게 표현 가능하다.

```jsx
// if 로 표현
let gretting = "hello"
if (userName) {
	gretting += userName
} else {
	gretting += "three"
}

// 삼항 연사자 (?:) 로 표현
gretting = "hello" + (userName ? userName : "three")
```

### 4.13.2 null 병합 연산자 (??)

- 왼쪽 피연산자가 null 이나 undefined가 아니면 그 값을 반환한다.
- && , || 와는 다르게 0, false 로 그대로 반환한다.

```jsx
let options = {timeout: 0, title: "", verbos: false, n: null}
options.timeout ?? 1000 // -> 0:
options.title ?? "Undefiend" // -> ""
options.verbose ?? true // -> false
options.quiet -> false // -> false : 정의된 값이 없음
options.n ?? 10 // ->10 : n 은 null 이므로 10 반환
```

### 4.13.3 typeof 연산자

- typeof 는 피연산자의 타입을 나타낸다.
- bigInt 는 bitInt 로 표현 된다.
- 함수가 아닌 객체 전체는 “object“ 로 표현 된다.

```jsx
typeof undefined // -> "undefined"
typeof null // -> "object" : null 도 숫자로 표기
typeof true // -> "boolean" : false 도 boolean 표기
typeof NaN // -> "number" : NaN 도 숫자로 표기
typeof 12 // -> "number"
typeof BitInt(전체) // -> bigInt ('bigInt' 로 표기)
typeof "hello" // -> "string"
typeof symbol() // -> "symbol"
typeof () => {} // "function"
```

### 4.13.4 delete 연산자

- 피연산자로 지정된 객체 프로퍼티나 배열 요소를 삭제한다.

```jsx
let foo = {
	x: 1,
	y: 2
}
delete foo.x // foo에서 x 객체를 삭제
"x" in foo // -> false z: x 는 존재하지않음

let bar = [1,2,3]
delete a[2] // 배열의 2번 인덱스 삭제
2 in a // -> false : 2번 인덱스 삭제하여 존재하지 않음
bar.length // -> 3 : 배열 길이는 처음과 같이 유지됨
```

### 4.13.5 await 연산자

- ES2017 에서 비동기 프로그래밍을 더 자연스럽게 사용하게 위해 도입
- 비동기 연산을 나타내는 promise 객체를 피연산자로 예상하고 동작
- async 함수와 같이 사용해야함

### 4.13.16 void 연산자

- 단항 형상자이며 피연산자 타입을 가리지 않는다.
- 피연산자를 평가 후 undefined를 반환
- 아무것도 반환하지 않는 함수를 나타내는대 주로 사용

---

> 이 외에도 다른 심화된 내용이 더 있지만 작성하면 좋겠다 하는것들만 작성함

- 비트연산자 추가 공부 필요!!
