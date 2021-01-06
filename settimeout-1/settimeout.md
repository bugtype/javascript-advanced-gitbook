# setTimeout



{% embed url="https://javascript.info/event-loop\#use-case-1-splitting-cpu-hungry-tasks" %}

#### 정리

1. 무거운 작업은 나눠서 처리 할 수 있다.
   1. promise로 해도 되지 않나?
2. 브라우저에서 먼저 렌더링된 후 비동기적으로 처리 가능하다
3. settimout을 0으로 해도 **최소 4ms**가 지나야 호출된다.
4. queueMicrotask가 있지만, IE엣서 지원 안한다.

* [https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/queueMicrotask](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/queueMicrotask)



```javascript
const sleep = (delay) => new Promise((resolve) => setTimeout(resolve, delay));
```







