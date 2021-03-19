# this 키워드의 동작원리

> `this` 가 어디서 어떻게 호출되냐에 따라 가리키는 것이 달라진다.

1. `new` 키워드로 함수를 실행했다면, 그 함수 안에서 `this` 는 새로운 객체를 가리킨다.
2. 단순히 함수를 호출한 경우, `this` 는 전역 객체를 가리킨다. 실행환경이 브라우저라면 `window`, 노드라면 `global` 이 된다. 만약 strict 모드라면 전역 객체가 아닌 `undefined` 가 된다.
3. 화살표 함수를 사용하면, 함수가 만들어진 시점에서 그 함수를 둘러싼 스코프의 `this`를 가리킨다.

   ```javascript
   const person = {
     age: 32,
     getPersonAge() {
       (() => {
         console.log(this.age); // 32
       })();
     },
     getGlobalAge() {
       (function () {
         console.log(this.age); // undefined
       })();
     },
   };
   ```

4. `apply`, `call`, `bind` 를 사용해 함수를 호출했다면, 호출 시 전달 된 객체가 `this` 가 된다.
5. 함수가 객체의 메소드로 호출됐다면, `this` 는 그 객체를 가리킨다. 단, 메소드는 화살표 함수가 아닌 일반 함수로 생성되어야 한다.
