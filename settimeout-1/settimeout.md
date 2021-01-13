# setTimeout



{% embed url="https://javascript.info/event-loop\#use-case-1-splitting-cpu-hungry-tasks" %}

#### 정리

1. 무거운 작업은 나눠서 처리 할 수 있다.
   1. promise로 해도 되지 않나?
2. 브라우저에서 먼저 렌더링된 후 비동기적으로 처리 가능하다
3. settimout을 0으로 해도 **최소 4ms**가 지나야 호출된다.
4. queueMicrotask가 있지만, IE엣서 지원 안한다.

* [https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/queueMicrotask](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/queueMicrotask)



간단한 sleep 코드

```javascript
const sleep = (delay) => new Promise((resolve) => setTimeout(resolve, delay));
```



분산 작업하기. 대충 만들었는데 의외로 잘된다.

```javascript
const sleep = (delay) => new Promise((resolve) => setTimeout(resolve, delay));

// dealy 10ms
// start 시작 0
// end 끝 1000
// n n개씩 처리하기
// callback : (index) => void
async function divideProcess(delay,start,end,n,callback){

    let i = start;
    while(i<end+1){
        for(let k = 0; k < n+1;k++){
          if(i>=end+1) break;
          callback(i++);
        }
        await sleep(delay)
    }
}
divideProcess(100,50,100,4,console.log)

let i = 0;
while(i<10000){
    console.log(i++)
}
```





