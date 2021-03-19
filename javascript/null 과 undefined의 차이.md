# null과 undefined의 차이는?

> `null` 은 명시적인 값이고, `undefined` 는 값이 아닌 할당되지 않은 상태를 의미한다.

```javascript
let foo;
console.log(foo);
console.log(foo == null); // true
console.log(foo === null); // false
```

`undefined` 는 `null` 과 동일하게 `falsy` 한 값이므로, `==` 가 아닌 `===` 로 `undefined` 임을 확인 해야한다.

> 💡TIP, 사용하지 않는 변수는 `null` 로 설정해두자.
