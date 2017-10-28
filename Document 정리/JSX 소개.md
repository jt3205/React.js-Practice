JSX 소개
==========
1. 시작
--------
이런방식의 변수선언를 생각해봅시다.
```JSX
const element = <h1>Hello, world!</h1>;
```
신기하게 생긴 이 코드는 문자열도 HTML도 ~~이도저도~~ 아닙니다.<br>
JSX라는 *JavaScript의 확장 버전* 입니다.<br>
React와 함께 UI를 표현하는데 사용합니다.<br>
<br>
JSX는 React의 요소를 생성합니다.<br>
다음 챕터에서는 DOM에 랜더링하는 방법을 다룰것입니다.<br>
이번엔 JSX의 기본적인 문법들을 살펴볼것입니다.<br>
2. JSX에 표현식 포함하기
-----------
[자바 스크립트 표현식](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Expressions)을 중괄호로 묶어 JSX에 삽입 할 수 있습니다.<br>
예를들어 이런식으로 사용할 수 있습니다.
```JSX
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
);
```
[CodePen](http://codepen.io/gaearon/pen/PGEjdG?editors=0010)에서 사용해보십시오.<br>
<br>
가독성을 위해 JSX를 여러 줄로 나누었습니다.<br>
꼭 그래야 하는 것은 아니지만 [자동 세미콜론 삽입](http://stackoverflow.com/q/2846283)의 함정을 피하기 위해 괄호로 묶는 것이 좋습니다.<br>

2. JSX는 곧 표현식
----------
컴파일이 끝나면 JSX 표현식이 일반 JavaScript가 됩니다.<br>
따라서, JSX를 ```if```명령문과 ```for```루프 안에서 사용할 수 있고, 변수에 할당하고, 인자값으로 받아서 함수에서 반환 할 수도 있습니다.<br>
```JSX
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```
3. JSX로 속성 지정하기
따옴표를 사용하여 문자열 리터럴을 속성으로 지정할 수 있습니다.
```JSX
const element = <div tabIndex="0"></div>;
```
중괄호를 사용하여 속성에 JavaScript 표현식을 포함시킬 수도 있습니다.
```JSX
const element = <img src={user.avatarUrl}></img>;
```
속성에 JavaScript 표현식을 포함 할 때 *중괄호를 따옴표로 묶으면 안됩니다.*<br>
표현식을 문자열로 인식 할 수도 있습니다.<br>
>주의 :
JSX는 HTML보다 자바 스크립트에 가깝기 때문에 React DOM은 camelCase 규칙을 사용합니다.

#### 작성중....
