---
description: 함수 vs 화살표 함수
---

# Normal function vs Arrow Function





```typescript
class App extends Component<AppProps, AppState> {
  constructor(props) {
    super(props);
    this.state = {
      name: 'React'
    };
    this.hello = this.hello.bind(this);
  }

  hello(){
    alert(this.state.name)
  }


  render() {
    return (
      <div onClick={this.hello}>
          hello worlld 
      </div>
    );
  }
}
```

리액트에서 클래스형 컴포넌트로 구현할 때, 우리는 메소드에 bind를 항상 시켜줘야 했다.

```typescript
this.hello = this.hello.bind(this);
```

위 처럼 bind를 해주지 않으면, 정상적으로 this가 class의 인스턴스를 가르키고 있지 않아. 원하는 결과를 받을 수 없게 된다.

```text
Cannot read property 'state' of undefined
```

이런 식으로 state를 찾을 수 없다고 에러 메시지를 띄우게 된다. 그래서 우리는 bind를 항상 해주었다. 그러다 arrow function이 나오면서 편해졌다. 왜냐면 불편한 bind를 안해줘도 되기 때문이다.

```typescript
class App extends Component<AppProps, AppState> {
  constructor(props) {
    super(props);
    this.state = {
      name: 'React'
    };
    // this.hello = this.hello.bind(this);
  }

  hello(){
    alert(this.state.name)
  }

  helloWorld = () => {
    alert(this.state.name)
  }

  render() {
    return (
      <div onClick={this.helloWorld}>
          hello worlld 
      </div>
    );
  }
}
```

helloWorld 메소드는 정상적으로 `React` 알트창을 띄우는 것을 알 수 있다.

`그러면 Arrow Function면 쓰면 되겠네??`

아직 섣부르게 판단하면 안된다. 앞으로 이어지는 내용에서 차이점에 대해서 설명할 것이다.

1. this bind
2. arrow function
3. autobind decorator

