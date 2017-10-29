JSX 소개
==========
## 시작
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

-------
JSX에 표현식 포함하기
-----------
-------
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

---------
JSX는 곧 표현식
----------
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

---------
JSX로 속성 지정하기
----------
-------
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
------------

JSX에서 Children 지정하기
-------------
------------

태그의 속성이 없을경우 XML처럼 ```/>```로 바로 닫을 수 있습니다.<br>
```JSX
const element = <img src={user.avatarUrl} />;
```
JSX 태그는 하위 태그도 포함할 수 있습니다.<br>
```JSX
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```
-----------

JSX 인젝션 방어
-------------
---------
사용자가 입력한 값을 JSX 변수에 넣으면 인젝션으로부터 안전합니다.
```JSX
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
```
기본적으로 React DOM은 랜더링하기전에 JSX의 변수들을 모두 이스케이프 처리합니다.<br>
그래서 코드에서 명시적으로 작성되지 않은 내용은 절때 삽입할 수 없습니다.<br>
그리고 랜더링되는 모든것은 랜더링하기 전에 텍스트로 변환됩니다.<br>
이렇게 한다면 [XSS 공격(스크립트 공격)](https://en.wikipedia.org/wiki/Cross-site_scripting) 에 대비할 수 있습니다.

----------
JSX는 곧 객체
----------
--------

Babel이 JSX를 컴파일 할때 ```React.createElement()``` 를 호출합니다.<br>
그래서 이 두가지 코드는 똑같습니다.<br>
```JSX
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```
```JSX
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
```React.createElement()``` 에서 버그를 잡아주는 몇가지 코드가 더 있긴 하지만 기본적으론 이런 객체를 생성합니다.<br>

```JSX
// Note: this structure is simplified
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world'
  }
};
```

이런 객체를 *"React elements"* 라고 부릅니다.<br>
화면에 표시될 내용에 대한 설명이라고 볼수도 있겠습니다.<br>
React는 객체를 읽고 그 객체를 사용해서 DOM을 구성하고 최신 상태로 유지합니다.<br>
