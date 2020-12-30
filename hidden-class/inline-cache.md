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

polymorphic

#### Megamorphic <a id="polymorphic-and-megamorphic-in-action"></a>



[http://www.egocube.pe.kr/lecture/content/html-javascript/202003240001](http://www.egocube.pe.kr/lecture/content/html-javascript/202003240001)

