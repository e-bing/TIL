# JavaScript

### **변수 선언**

✔ `var`

- 함수 스코프를 가지며, 블록 스코프는 지원하지 않는다.
- 같은 이름으로 중복 선언이 가능하다.
- 값의 재할당이 가능하다.
- 호이스팅 시 undefined로 초기화되어 선언 이전에도 접근할 수 있다.
- 복잡한 코드에서 예기치 않은 동작을 유발할 수 있어 ES6 이후에는 잘 사용하지 않는다.
- 전역 객체의 프로퍼티가 된다.

✔ `let`

- 블록 스코프를 가지며, 선언된 블록 내부에서만 유효하다.
- 중복 선언은 불가능하지만, 값의 재할당이 가능하다.
- 호이스팅이 발생하지만, 선언 이전에 접근하면 에러가 발생한다.
- 일반적으로 값이 변할 수 있는 변수에 사용한다.

✔ `const`

- 블록 스코프를 가지며, 선언된 블록 내부에서만 유효하다.
- 중복 선언과 값의 재할당 모두 불가능하다.
- 선언과 동시에 반드시 초기화해야 한다.
- 호이스팅이 발생하지만, 선언 이전에 접근하면 에러가 발생한다.
- 값이 변하지 않는 상수나 참조 변경이 필요 없는 객체에 사용한다.

✔ 전역 객체

- JavaScript의 전역 객체란 브라우저에서는 window, Node.js에서는 global를 말한다.

- `var` 로 선언한 전역 변수는 JavaScript의 전역 객체 속성(property)로 자동 등록된다.

- 아래 코드에서 `foo` 가 window 객체의 프로퍼티가 되어, [`window.foo`](http://window.foo) 로도 접근 가능하다.
  
  ```jsx
  var foo = 123;
  console.log(window.foo); // 123 출력
  ```

✔ 호이스팅

- JavaScript에서 변수 선언이 코드 실행 전에 해당 스코프의 최상단으로 끌어올려진 것처럼 동작하는 현상을 말한다.
- JavaScript 엔진이 실행 전에 변수 선언을 미리 처리하기 때문에 이런 현상이 발생한다.
- let과 const는 호이스팅이 발생하지만, 선언 이전에 접근하면 TDZ(Temporal Dead Zone)에 머물러 ReferenceError가 발생한다.
- 함수 선언식은 호이스팅되어 선언 전에 호출해도 동작하지만, 함수 표현식은 호이스팅되지 않는다.

### **함수 선언**

✔ JavaScipt의 함수 선언

- 매개변수의 타입을 명시하지 않으므로, 함수 내에서 타입 체크가 필요할 수 있다.
- 코드 재사용, 가독성, 유지 보수성에 도움을 준다.

✔ 함수 선언식(Function Declaration)

- function 키워드를 사용해 함수 이름과 함께 선언한다.

- 전체 코드가 실행되기 전에 호이스팅되어, 선언 이전에 호출 가능하다.

- Function 객체의 모든 속성과 메서드를 가진다.

- 예시
  
  ```jsx
  function add(a, b) {
      return a + b;
  }
  ```

✔ 함수 표현식(Function Expression)

- 함수 자체를 변수에 할당하는 방식이다.

- 변수 선언만 호이스팅되고, 함수 자체는 실행 흐름이 해당 코드에 도달했을 때 생성되므로 선언 이전에는 사용할 수 없다.

- 예시
  
  ```jsx
  const add = function(a, b) {
      return a + b;
  }
  ```

✔ 화살표 함수(Arrow Function)

- ES6에서 도입된 새로운 함수 선언 방식이다.

- `function` 키워드 대신 `=>` 기호를 사용해 더 간결하게 함수를 작성할 수 있다.

- 익명 함수 형태로, 함수 표현식으로만 사용할 수 있으며 이름을 붙여 선언할 수 없다.

- 콜백 함수, 배열 메서드(map, filter 등), 간단한 연산 등에서 자주 활용된다.

- 예시
  
  ```jsx
  const add = (a, b) => a + b;
  const square = x => x * x;
  ```

### **배열**

- **forEach** 배열의 각 요소에 대한 함수를 실행한다. 반복문을 간결하게 대체한다.
  
  ```jsx
  arr.forEach(element => console.log(element));
  ```

- **map** 배열의 각 요소를 변환하여 새로운 배열을 만든다.
  
  ```jsx
  const squared = arr.map(num => num * num);
  ```

- **filter** 조건에 맞는 요소만 추려 새로운 배열로 반환한다.
  
  ```jsx
  const even = arr.filter(num => num % 2 === 0);
  ```
  
  ```jsx
  const numbers = [1, 2, 3, 4, 5];
  const evenNumbers = numbers.filter(num => num % 2 === 0); // [2, 4]const even = arr.filter(num => num % 2 === 0);
  ```

- **reduce** 배열을 누적하여 하나의 값으로 만든다. 합계, 곱, 객체 변환 등 다양하게 활용된다.
  
  ```jsx
  const sum = arr.reduce((acc, cur) => acc + cur, 0);
  ```

- **sort** 배열을 정렬한다. 숫자 정렬 시 비교 함수를 꼭 넣어야 한다.
  
  ```jsx
  arr.sort((a, b) -> a - b);
  ```

- **indexOf, includes** 특정 값의 위치나 존재 여부를 확인한다.
  
  ```jsx
  arr.indexOf(3); // 값이 없으면 -1 리턴
  arr.includes(3); // true/false 리턴
  ```

- **find, findIndex** 조건에 맞는 첫 번째 요소(또는 인덱스)를 반환한다.
  
  ```jsx
  arr.find();
  arr.findIndex();
  ```

- **every** 배열의 모든 요소가 조건을 만족하면 true, 그렇지 않으면 false를 반환한다.
  
  ```jsx
  const numbers = [2, 4, 6, 8];
  const allEven = numbers.every(num => num % 2 === 0); // true
  
  const mixed = [2, 3, 6, 8];
  const allEven2 = mixed.every(num => num % 2 === 0); // false
  ```

- **some** 배열의 요소 중 하나라도 조건을 만족하면 true, 그렇지 않으면 false를 반환한다.
  
  ```jsx
  const numbers = [1, 2, 3, 4, 5];
  const hasEven = numbers.some(num => num % 2 === 0); // true
  
  const allOdd = [1, 3, 5];
  const hasEven2 = allOdd.some(num => num % 2 === 0); // false
  ```

### **문자열 관련 함수**

- **split, join** 문자열을 배열로, 배열을 문자열로 변환한다.
  
  ```jsx
  'a, b, c'.split(','); // ['a', 'b', 'c'] 리턴
  ['a', 'b', 'c'].join('-'); // 'a-b-c' 리턴
  ```

- **length** 문자열의 길이를 반환한다.
  
  ```jsx
  const text = "Hello, Javascript!";
  console.log(text.length); // 18 리턴
  ```

- **trim()** 문자열 양쪽 끝의 공백을 제거한다.
  
  ```jsx
  const str = "   ABCDEFG   ";
  console.log(str.trim()); // "ABCDEFG"
  ```

- **split(separator)** seperator를 기준으로 문자열을 나누어 배열로 반환한다.
  
  ```jsx
  const fruits = "apple/banana/lemon";
  const fruitArr = fruits.split("/");
  console.log(fruitArr); // ["apple", "banana", "lemon"]
  ```

### **숫자 함수**

- **Math.max(), Math.min()** 최댓값, 최솟값을 구할 때 사용한다.
  
  ```jsx
  const arr = [1, 2, 3, 4, 5];
  const maxNum = Math.max(...arr); // 5
  const minNum = Math.min(...arr); // 1
  ```

- **Math.round()** 소수점 첫째 자리에서 반올림한 정수를 반환한다. (반올림)
  
  ```jsx
  const num = Math.round(4.7); // 5
  const num2 = Math.round(4.3); // 4
  ```

- **Math.ceil()** 소수점 이하는 올리고, 주어진 값보다 크거나 같은 가장 작은 정수를 반환한다. (올림)
  
  ```jsx
  const num = Math.round(4.7); // 5
  const num2 = Math.round(4.3); // 4
  ```

- **Math.floor()** 소수점 이하는 버리고, 주어진 값보다 작거나 같은 가장 큰 정수를 반환한다. (내림)
  
  ```jsx
  const num = Math.floor(4.7); // 4
  const num2 = Math.floor(-4.7); // -5
  ```

- **Math.round()** 소수점 첫째 자리에서 반올림한 정수를 반환한다.
  
  ```jsx
  const num = Math.round(4.7); // 5
  const num2 = Math.round(4.3); // 4
  ```

- **Math.trunc()** 소수점 이하를 단순히 버리고 정수 부분만 반환한다.
  
  ```jsx
  const num = Math.trunc(4.9); // 4
  const num2 = Math.trunc(-4.9); // -4
  ```

- **Math.sqrt(x)** x의 제곱근을 반환한다.
  
  ```jsx
  const result = Math.sqrt(9); // 3
  ```

- **Math.pow(x, y)** x의 y제곱 값을 반환한다.
  
  ```jsx
  const result = Math.pow(2, 3); // 8
  ```

- **Math.random()** 0 이상 1 미만의 난수를 반환한다.
  
  ```jsx
  const randomNum = Math.random(); // 예: 0.123456...
  ```

### **기타**

- **Set** 배열의 중복을 제거할 때 자주 사용한다.
  
  ```jsx
  const unique = [...new Set(arr)];
  ```

### **입력 값 읽어오기**

- **readline 사용**
  
  ```jsx
  const readline = require('readLine');
  
  const rl = readline.createInterface({
      input: process.stdin,
      output: process.stdout
  });
  
  // 입력받은 값 등을 저장할 변수 생성
  // let input;
  
  rl.on('line', (line) => {
      // 여기서 값 저장하거나 처리하면 될 듯
      // input = line;
      rl.close();
  });
  rl.on('close', () => {
      // 실행할 코드 입력
      // console.log(input);
      process.exit();
  })
  ```

- **readFileSync 간소화**
  
  ```jsx
  const input = require('fs').readFileSync(0).toString();
  ```
