# Redux Saga

> 액션을 모니터링하고 있다가 특정 액션이 발생하면 특정 작업을 한다.

### 여기서 말하는 특정 작업이라 함은

1. 일반 자바스크립트 실행
2. 액션 디스패치
3. 상태 접근
4. 1 ~ 3 조합으로 구현된 서비스 로직

### `redux-thunk` 와 차이점은

1.  클로저 패턴이 없어 코드가 간결하다.
2.  saga 에서 제공해주는 effect 로 비동기 처리를 간편하게 구현할 수 있다. (ex, `takeLatest` 로 마지막 액션만 받는다. `cancel` 을 이용해서 태스크를 취소한다.)

```typescript
import * as api from 'api';
import {loginRequest, loginSuccess, loginFailure} from './loginActions';

export const loginThunk =
  (name: string, password: string)=>
    (dispatch: Function)=>{
        dispatch(loginRequest());
        try{
          api.login(name, password);
        }
        catch(err){
          dispatch(loginFailure(err));
          return;
        }
        dispatch(loginSuccess();)
    };
```

```typescript
import * as api from "api";
import { take, call, put } from "redux-saga";
import { LoginRequestAction, loginSuccess, loginFailure } from "./loginActions";

function* loginSaga() {
  const action: LoginRequestAction = yield take("LOGIN_REQUEST");
  const { name, password } = action.payload;
  try {
    yield call(api.login, name, password);
  } catch (err) {
    yield put(loginFailure(err));
    return;
  }
  yield put(loginSuccess());
}
```

### 사가 이펙트

1. `take` : 액션이 `dispatch` 되면 제너레이터의 `next` 를 호출한다.
2. `takeEvery`: 들어오는 모든 액션에 대해서 특정 작업을 한다.
3. `takeLatest`: 기존에 진행 중이던 작업이 있다면 취소 처리하고 가장 마지막으로 실행된 작업만 수행한다.
4. `put` : `dispatch` 와 동일하다.
5. `call`: 함수의 첫 번째 파라미터는 함수, 나머지 파라미터는 해당 함수에 넣을 인수이다.
6. `fork`: 새로운 하위 saga 태스크를 생성한다.
7. `all` : 제너레이터 함수들이 병행적으로 동시에 실행되고, 전부 resolve될때까지 기다린다. `Promise.all` 과 비슷하다. (ex, `yield all([sampleSaga1(), sampleSaga2()])`)
8. `delay` : 일정 시간 후 `next` 호출하여 다음 단계의 함수를 실행한다.
9. `select` : state 에서 특정 상태를 가져올때 사용한다.

### 솔직히 리덕스 사가를 쓰면서,

컴포넌트의 서비스로직을 `saga` 에서 처리할 수 있어서, 코드 가독성에서는 최고였다. 하지만, 단순 API 호출에도 액션을 생성하고, 사가를 만드는 과정이 너무 과하단 생각이 들었다. (이건 사가 뿐만 아니라 리덕스의 문제이기도 하다. 이때 `swr` 과 같은 라이브러리를 이용!)
