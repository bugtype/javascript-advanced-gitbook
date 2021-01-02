# Crypto

Nodejs는 Single Thread가 아니다.

**crypto.pbkdf2**는 별도의 쓰레드에서 작동한다.

```typescript
const crypto = require('crypto');

const startDate = Date.now();
crypto.pbkdf2('bugtype', 'javascript', 100000, 512, 'sha512', () => {
  console.log('JOB 1 : ', Date.now() - startDate);
});

crypto.pbkdf2('bugtype', 'javascript', 100000, 512, 'sha512', () => {
  console.log('JOB 2 : ', Date.now() - startDate);
});

crypto.pbkdf2('bugtype', 'javascript', 100000, 512, 'sha512', () => {
  console.log('JOB 3 : ', Date.now() - startDate);
});

crypto.pbkdf2('bugtype', 'javascript', 100000, 512, 'sha512', () => {
  console.log('JOB 4 : ', Date.now() - startDate);
});

crypto.pbkdf2('bugtype', 'javascript', 100000, 512, 'sha512', () => {
  console.log('JOB 5 : ', Date.now() - startDate);
});

crypto.pbkdf2('bugtype', 'javascript', 100000, 512, 'sha512', () => {
  console.log('JOB 6 : ', Date.now() - startDate);
});

crypto.pbkdf2('bugtype', 'javascript', 100000, 512, 'sha512', () => {
  console.log('JOB 7 : ', Date.now() - startDate);
});

crypto.pbkdf2('bugtype', 'javascript', 100000, 512, 'sha512', () => {
  console.log('JOB 8 : ', Date.now() - startDate);
});

crypto.pbkdf2('bugtype', 'javascript', 100000, 512, 'sha512', () => {
  console.log('JOB 9 : ', Date.now() - startDate);
});
// 결과 ( 필자는 쿼드코어 )
JOB 2 :  542
JOB 4 :  548
JOB 3 :  549
JOB 1 :  552
// 다음 작업
JOB 7 :  1077
JOB 5 :  1077
JOB 8 :  1077
JOB 6 :  1079
// 다음 작업
JOB 9 :  1584
```

필자는 **쿼드코어의 CPU**를 가지고 있다. 그래서 4개씩 작업이 된다.

**CPU당 하나의 Thread를 사용하기에 다음과 같은 시간**이 걸렸다.

그러면 Thread의 사이즈를 변경할 수 없을까?

```javascript
process.env.UV_THREADPOOL_SIZE = 8; //  제일 위에 선언
```

위와 같은 옵션을 줘서 바꿀 수 있다.

```javascript
JOB 1 :  1222
JOB 7 :  1245
JOB 2 :  1247
JOB 3 :  1253
JOB 6 :  1255
JOB 4 :  1262
JOB 8 :  1265
JOB 5 :  1270
// 다음 작업
JOB 9 :  1747
```

결과는 위와 같다. 근데 결과를 보면 알겠지만,  1~4번의 작업이 처음보다 **2배의 시간**이 걸렸다.

왜냐면 **하나의 CPU에서 2개의 Thread**가 동시에 작업을 하게 되는데 그래서 2배의 시간이 걸리게 된다. 그대신 **1~8번의 작업**은 동시에 끝나게 된다.





