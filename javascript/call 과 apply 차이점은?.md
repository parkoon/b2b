# `Function.prototype.call` 과 `Function.prototype.apply` 의 차이점은?

> 함수 호출로 `this` 지정하는 것은 같지만, 함수 파라미터를 전달하는 방식에 차이가 있다.

`call`, `apply` 호출 시 첫번째 인자로 객체를 보낸다. 이 객체가 `this` 와 연결된다. 두 번째 파라미터부터 함수의 파라미터를 전달하는데 다음과 같다.

```javascript
function add(a, b) {
  return a + b;
}

console.log(add.call({}, 1, 2)); // 3
console.log(add.apply({}, [1, 2])); // 3
```
