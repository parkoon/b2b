# document 의 load 이벤트와 DOMContentLoaded 차이점

> 리소스까지 모두 로딩되었는가? DOM 트리만 로드되었는가?

`DOMContentLoaded` 는 HTML 이 모두 로드되고, DOM 트리가 완성되었을 때 발생한다. 외부 리소스 (스타일시트, 이미지 등)가 완전한 로딩은 기다리지 않는다.

반면에, `window` 의 `load` 이벤트는 리소스까지 모두 로딩되었을 때 발생한다.

HTML 이 모두 로드되고, DOM 트리가 완성되었지만, 외부 리소스(img etc) 가 아직 로드되어지지 않았을 때
load - 브라우저에 모든 리소스(img, style, script, etc) 가 로드되었을 때
