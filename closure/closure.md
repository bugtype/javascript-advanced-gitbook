# Closure



“A closure is the combination of a function and the lexical environment within which that function was declared.”

"클로저는 함수가 선언되었을 때의 렉시컬 환경과의 조합이다"

클로저에 대해 MDN은 위와 같이 정의 되어 있다.

무슨 말인지 이해가 되는가??? 필자는 아무리 생각해도 이해가 안된다.

그러면 이렇게 이해 하는 것이 어떤가?

`내부함수가 외부변수를 참조하는 것을 말한다.`

조금은 와닿는가?? 한번 아래 예제 코드를 보고 한번 이해해보자.

```typescript
function Outer(){
    const str = 'hello'
    function Inner(){
        console.log(str)
    }
    Inner()
}
Outer() // hello
```

위에 코드를 보면 알겠지만, Outer안에 있는 **Inner 메소드**가 Outer의 변수를 호출하고 있다. 이제 감이 좀 잡히지 않는가???

더 자세한 내용은 맨 아래 레퍼런스를 참고 하자.! 😅

#### Next\) Closure는 Memory Leak을 발생시킨다 ?!

내부함수가 외부변수를 잡고 있기 때문에 GC가 해당 변수를 처리하지 못한다. ~~Javascript에서는 해당 문법이 없다~~. \( Swift에서는 `weak self`를 사용을 해서 작업을 했었다.\) 그러면 Javascript GC에서 어떻게 메모리를 잡고 있는지. 어떻게 해결해야 하는지 다음편에서 보도록 하자.!

**다시 찾아보니 javascript에도 weak ref가 있긴하다. 다만 IE, safari에서 지원하지 않는다..**

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/WeakRef](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakRef)





**참고**

* [https://poiemaweb.com/js-closure](https://poiemaweb.com/js-closure) \( 필자 글보다 매우 잘 설명 되어 있다.\)

