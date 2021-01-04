# 내부 동작 원리



1. V8에는 Event loop가 없다.
   1. nodeJs나 브라우져에서 관리한다.
2. Event Loop는 여러개의 Queue로 이루어져있다.
   1. Timer  \(setTimeOut, setInterval \)
   2. I/O callback
   3. idle \( 매 Tick 마다 실행 \)
   4. poll \( 새로운 커넥션, 데이터 등\)
   5. check \( setImmediate \)
   6. close \( socket\)

```javascript
setTimeout(() => {
    console.log('setTimeout')
}, 0);
setImmediate(() =>{
    console.log('setImmediate')
})
setTimeout(() => {
    console.log('setTimeout')
}, 0);

// 1번
// setTimeout
// setImmediate
// setTimeout

// 2번
// setImmediate
// setTimeout
// setTimeout
```

1번과 2번 어떤 것이 맞을 거 같은가???





#### 정답은 **둘다**이다. EventLoop의 타이밍에 맞게 출력된다.

* EventLoop가**i/O callback Queeue** 전에 있으면 setTimeout이 먼저 실행되고, **i/O callback Queeue** 을 막 지난 상태면, **Check Queue**가 실행되기에 setImmediate가 먼저 실행된다.







{% embed url="https://sjh836.tistory.com/149" %}



{% embed url="https://psyhm.tistory.com/9" %}

[https://evan-moon.github.io/2019/08/01/nodejs-event-loop-workflow/](https://evan-moon.github.io/2019/08/01/nodejs-event-loop-workflow/)

