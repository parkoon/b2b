# CORS 가 무엇이고 어떻게 해결할 수 있을까요

> Cross Origin Resource Origin, 타 도메인간 자원을 공유하자

브라우저의 보안상 이슈로, 대부분의 브라우저에서는 다른 도메인에서 리소스 요청을 제한한다.

어떻게 해결할 수 있을까? 🤔

1. 동일한 origin 에서 요청을 한다.
2. JSONP (JSON-padding) 을 이용한다.
3. 서버쪽에서 HTTP 응답 헤더에, Access-Control-Allow-Origin : \* 혹은 Access-Control-Allow-Origin: 허용할 도메인을 설정해준다.
4. 서버쪽에서 해결할 수 없는 상황이라면, 프록시 서버를 이용한다.
