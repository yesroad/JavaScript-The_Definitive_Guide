# 3장. 타입, 값, 변수

## 01. 숫자

- 숫자 리터럴안에 밑줄을 사용하여 읽기 쉽게 표현할수 있다.

    ```jsx
    1_000_000_000 // 밑줄은 천 단위 구분자로 사용
    0x89_AB_CD_EF // 바이트 구분자로 사용
    0b001_1101_0111; // 4비트 구분자로 사용
    0.123_456_789; // 소수점 아래 부분에도 사용 가능
    ```


### 1. 정수 리터럴

- 10진수 정수는 연속된 숫자로 표현한다.
- 2진수, 8진수, 16진수 값도 인식한다.
    - 2진수 - `0b` 또는 0B로 시작한다.
    - 8진수 - `0o` 또는 `0O`로 시작한다.
    - 16진수 - `0x` 또는 `0X`로 시작한다.

    ```jsx
    // 정수
    1, 3, 100000
    
    // 2진수
    ob10101 // => 21
    
    // 8진수
    0o377 // -> 255
    
    // 16진수
    oxff //=> 255
    0XBADCAFE // => 19539070
    ```


### 2. 부동 소수점 리터럴

- 소수점 리터럴은 **정수, 소수점, 소수점 아래** 부분을 순서대로 나열한다.
- 지수 표기법으로도 표현 가능하다.
    - 실수 다음에 e(E)를 쓰고 그 뒤에 선택적으로 + 또는 - 기호, 마지막으로 지수를 나타내는 정수를 쓴다.
    - 이 표기법은 10의 지수 승을 곱하는 방식으로 표현한다.

    ```jsx
    // 소수점
    3.14
    2345.6789
    .123
    
    // 지수 표기법
    6.02e23
    1.4738223Ee-32
    ```


### 3. 산술 연산자

> 📖 산술연산자에는 **덧셈(+)  뺄셈(-)  곱셈(*) 나누기(/)  나머지(%)** 등 이 있습니다.


1. **Math**
    - 해당 객체의 프로퍼티를 통하여 더 복잡한 수학 계산을 지원합니다.
    - 참고 링크 : [mdn Math](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math)
2. **Infinity**
    - 산술연산시 표현할 수 있는 가장 큰 숫자보다 큰 경우(오버플로) **Infinity**로 반환된다.
    - 산술연산시 표현할 수 있는 가장 큰 음수의 절대값 보다 큰 경우 **-Infinity**로 반환된다.

### 4. 이진 부동 수소점 숫자와 반올림 오류

---

- 실수를 다룰때 실세 숫자의 근삿값으로 표현될때가 자주 있습니다.

    ```jsx
    let x = .3 - .2;
    let y = .2 - .1;
    x === y // => false
    ```


### 5. BigInt로 임의 정확도를 부여한 정수

---

- BigInt는 ES2020에서 정의한 자바스크립트의 최신 기능 중 하나이다.
- 다른 프로그래밍 언어나 API와의 호환에 필요한 64비트 정수를 표현하기 위해 추가되었다.
- 타이밍 공격을 방지할 수 없으므로 암호화에는 사용할 수 없다.
- 산술 연산자 사용시 일반적인 피연산자와 BigInt 피연산자를 섞어쓸수없다.
- BigInt 리터럴은 연속된 숫자 다음에 `소문자n` 을 붙인 형식이다.

    ```jsx
    1234n // 정수 BigInt
    0b111111n // 이진 BigInt
    0o7777n // 8진 BigInt
    ```

## 텍스트
- 자바스크립트에서 텍스트를 표현하는 타입은 문자열이다.
- 문자열은 16비트 값이 순서에 따라 이어진 형태이며, 기본값이므로 불변이다.
- 각 값은 일반적으로 유니코드 문자이며 길이는 그 값에 포함된 16비트 값의 개수이다.

### 01. 문자열 리터럴
- 문자열을 사용할 때는 작은 따옴표(’’), 큰 따옴표(””), 백틱(``) 으로 표현한다.
- 백틱으로 감싼 문자열은 ES6 기능이며 템플릿 리터럴 이라고 부른다.
- '+' 연산자로 문자열을 합치는것이 가능하다.
  - ES5 부터는 역슬래시(\)를 사용하여 여러행으로 구분할 수 있다.
    ```javascript
    "" // 빈 문자열
    'test' // 문자열 test
    "test" // 문자열 test
    `test` // 문자열 test
      
    // 두 행을 한 행으로 표현
    'two\nlines'
    
    // 한 행을 세 행으로 나누어 표현
    "two\
    long\
    line"
    ```

### 02. 문자열 리터럴 안의 이스케이프 시퀀스
- 문자열 안에 역슬래시(\)를 사용하면 문자열에 표현할 수 없는 이스케이프 시퀸스 이다.

### 03. 문자열 다루기
- 자바스크립트에는 다양한 문자열 API가 존재한다.
  - 관련 링크 : mdn string
### 04. 패턴 매칭
- 문자열 내부의 패턴을 정의하고 매칭하는 정규표현식(RegExp) 이라는 데이터 타입이 있다.
  - 관련 링크 : mdn RegExp
