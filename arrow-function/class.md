# Class에서 사용하지마!!!



```javascript
class Test {
    hello() {}
    helloWorld = () => {}
}
const instance = new Test()
console.log(instance) //  Test {helloWorld: ƒ}
console.log(Test.prototype) // {constructor: ƒ, hello: ƒ}

```

Normal Function은 Test의 **Prototype**에 선언되어 있다.

Arrow Function은 Test의 Instance에 선언되어 있다.

#### 

#### 왜 Class 내에 Method를 선언 했는데 다르게 나올까??

일단 Javascript의 Class는 설탕 문법인 것을 모두가 알 것이다. Javascript에는 Class가 존재하지 않는다. prototype으로 흉내만 낸 것이다.

Class 문법을 ES5 문법으로 바꾸면 어떻게 변환되는지 보자.

```javascript
var Test = /** @class */ (function () {
    function Test() {
        this.helloWorld = function () { };
    }
    Test.prototype.hello = function () { };
    return Test;
}());
var instance = new Test();
console.log(instance); //  Test {helloWorld: ƒ}
console.log(Test.prototype); // {constructor: ƒ, hello: ƒ}
```

Class 내의 Arrow Function는 생성자 안으로 변환된다.

#### 그러면 arrow function 써도 상관없는 거야???

* Class 내의 Arrow Function는 생성자 안으로 변환된다고 하였다. prototype에 선언 되는 것이 아니다. 
* Javascript에서 Class의 상속은 prototype으로 한다. 그러므로 부모를 호출할 수 없으므로 super를 호출할 수 없다. 
* 그리고 Arrow function은 Class내에서 bind하는 것보다 느리다.



