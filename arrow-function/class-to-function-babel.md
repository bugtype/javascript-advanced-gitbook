# Class To Function \( babel \)

![test&#xB294; A prototype &#xC5D0; &#xC815;&#xC758; / test2 - class A&#xC5D0; &#xC815;&#xC758;](../.gitbook/assets/image.png)



```typescript
class A{
    test(){}
    test2 = () => {}
}
```



```typescript
"use strict";
var A = /** @class */ (function () {
    function A() {
        this.test2 = function () { };
    }
    A.prototype.test = function () { };
    return A;
}());
```



class를 function으로 변환하면, method는 prototype에 선언된다.

하지만 arrow function은 보는 거와 같이 A 인스턴스에 선언 된다.

A 인스턴스를 100개 만든다면, prototype\(hidden class, shape\)가 공유되므로, 메모리를 새로 할당하지 않는다. 하지만 arrow function은 새로 할당하게 된다.



