# Inline Cache



```javascript
function test(){
	const a = { name: 'a' }
	const b = { name: 'b' }
	const c = { name: 'c' }
	const d = { name: 'd' }
	const e = { name: 'e' }
  const arr = [a,b,c,d,e]
  const getName = (obj) => obj.name;
  for (var i = 0; i < 1000; i++) {
      getName(arr[i & arr.length-1]);
  }
}
test()
```

```javascript
function test(){
	const a = { name: 'a', address: 'a' }
	const b = { name: 'b', go: 'b' }
	const c = { name: 'c', apple: 'pie' }
	const d = { name: 'd', phone: 'number' }
	const e = { name: 'e' }
  const arr = [a,b,c,d,e]
  const getName = (obj) => obj.name;
  for (var i = 0; i < 1000; i++) {
      getName(arr[i & arr.length-1]);
  }
}
test()
```

![](../.gitbook/assets/screen-shot-2020-12-16-at-9.35.19-pm%20%281%29.png)

그림에서 보는 거와 같이 **23퍼**나 느리다

---



인라인 캐싱의 상태

* UNINITIALIZED\(0\)
* PREMONOMORPHIC\(1\) - 1번째 접근
* MONOMORPHIC\(1\) - 2번째 접근
* **3번째 접근 \(cache hit\)**
* POLYMORPHIC\(P\) - 다른 Shape\(Hidden Class\)가 접근할 경우. 4개까지 가능.
* MEGAMORPHIC\(N\) - 최대 4개 캐시 가능.



[http://www.egocube.pe.kr/lecture/content/html-javascript/202003240001](http://www.egocube.pe.kr/lecture/content/html-javascript/202003240001)

