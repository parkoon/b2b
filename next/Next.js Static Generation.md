# Next.js Static Generation

## `getStaticProps`

정적 페이지 생성을 지원하며, 빌드 타임에만 한 번 실행된다.

### 언제 사용하면 좋을까?

- 사용자의 요청마다 데이터를 fetch 할 필요가 없는 페이지
- SEO 가 필요한 페이지

## `getStaticPaths`

`getStaticProps` 와 비슷하다. 차이점으로는 `getStaticPaths` 는 Dynamic route 를 사용할 때 쓰인다.

`pages/posts/[id].js` 가 있다는 가정하에 `getStaticPaths` 를 어떻게 사용하는지 알아보자.

```javascript
export async function getStaticPaths() {
  return {
    paths: [
        { params: { id: '1' } },
        { params: { id: '2' } }
    ],
    fallback: true or false
  };
}
```

> 💡 주의 ! `getStaticProps` 와 함께 사용해야한다!

위와 같이 `paths` 를 입력하면 `build` 시점에서 `posts/1.html`, `posts/2.html` 을 생성한다.

`fallback` 이 `false` 일 경우, `paths` 로 전달한 `id` 값 이외에 페이지를 접근하면 404 페이지를 렌더링한다.

`fallback` 의 값이 `true` 로 설정하면 `getStaticProps` 의 동작이 달라진다. 404 페이지를 보여주는 것이 아닌 빌드 시점에서만 실행되던 `getStaticProps` 를 호출한다.

### `fallback: true` 는 언제 사용하면 좋을까?

데이터에 따라 정적인 페이지를 많이 만들어야 할 때 사용하면 좋다. 모든 페이지를 빌드시에 만든다고하면, 하루 종일 빌드해야 하는 상황이 나온다. 따라서, 몇 중요한 페이지만 보여주고 나머지는 `fallback: true` 로 처리하자.

## `getServerSideProps`

각 요청 마다 서버사이드에서 미리 렌더링을 한다.

```javascript
export async function getServerSideProps(context) {
  return {
    props: {},
  };
}
```

## 참고

- https://yceffort.kr/2020/03/nextjs-02-data-fetching
