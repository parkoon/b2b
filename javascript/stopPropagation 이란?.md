# `stopPropagation` 이란

> 이벤트 버블링, 캡처링과 같은 이벤트 전파를 막는다.

### `preventDefault` 와 구분하여 알고 있기!

`preventDefault` 는 태그가 가지고 있는 기본 동작을 막는다.

```javascript
const a = document.getElementById("a");
a.addEventListener("click", (e) => {
  e.preventDefault();
  alert("clicked!");
});
```

위 코드를 실행하면 `a` 태그의 `href` 속성이 중단되고 `alert` 이 실행된다.
