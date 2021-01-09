---
description: 'http://bugtype-kr.gitbook.io/javascript-advanced'
---

# Javascript 고급



자바스크립트가 어떤식으로 동작하는지 알아보면서, 앞으로 최적화된 코드를 작성을 해보자.

내부적인 동작원리를 알면, **코드 하나에 담긴 여러가지 의미를 알게된다.**  


```javascript
// Case1
const hello = function(message) { console.log(message)}

// Case 2 ( class에서는 성능 이슈가 있다. )
const hello2 = (message) => console.log(message)
```

{% hint style="warning" %}
ES6문법부터는 Arrow Function인 Case 2 로 많이 사용할 것이다. 하지만, 단순하게 편리하다고 생각하면 안된다. Class에서 Arrow Function은 성능저하를 발생시킨다. 
{% endhint %}





### 목차



