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







