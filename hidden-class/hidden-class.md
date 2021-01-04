# Hidden Class

{% embed url="https://mathiasbynens.be/notes/shapes-ics" %}

**Shape = Hidden Class**

ShapleTable



```javascript
var a = {} // Shape 1
a.x = 100; // Shape 2
a.y = 200; // Shape 3

console.log(a.x);
```

\*\*\*\*

1. a객체에 접근한다.
2. a객체의 shape에 접근한다.
3. a객체의 shape에서 x를 찾는다.
4. **Shape 3** 에서 전환 체인을 통해서 **Shape**를 찾는다.
5. a객체의 shape에서 x에 있는 offset을 찾는다.
6. a객체에서 해당 offset 위치로 가서 값을 가져온다.

\*\*\*\*

\*\*\*\*

\*\*\*\*

속도 영향. 

\*\*\*\*[**https://medium.com/@bmeurer/surprising-polymorphism-in-react-applications-63015b50abc**](https://medium.com/@bmeurer/surprising-polymorphism-in-react-applications-63015b50abc)\*\*\*\*

