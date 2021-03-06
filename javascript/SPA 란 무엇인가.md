# SPA 란 무엇인가

> Single Page Application, 클라이언트 사이드 렌더링 웹사이트

SPA 는 클라이언트 사이드 렌더링을 한다. 브라우저는 초기 페이지 (index.html) 과 앱이 필요한 스크립트, 스타일시트를 받는다. 싱글 페이지의 특 장점으로, 페이지 이동할 때 HTML5 History API 를 이용하기 때문에 새로고침이 발생하지 않는다.

이에 따른 장점으로는

- 페이지 이동할 때 깜빡임이 없다.
- 페이지가 살아있는 느낌이 든다.
- 이미지와 같은 요소들을 페이지마다 요청할 필요가 없기 때문에 HTTP 요청이 줄어든다.

단점으로는

- 서버사이드 렌더링보다 많은 스크립트를 불러오기 때문에 초기 로딩이 무거워진다. 이 부분은 코드 스플릿팅을 이용해 해결할 수 있다.
- 빈 페이지를 전달하기 때문에 SEO 가 필요한 사이트에 적합하지 않다. 사실 지금까지 만들었던 웹앱중 SEO 가 절실히 필요한 서비스를 만들어보지 못했다. 그래도 필요하다면 그 페이지를 서버사이드 렌더링으로 구현하던가 Prerender와 같은 서비스를 이용하면 된다.
