HelloWorld!
=============
시작
---------
--------
React를 해보는 가장 쉬운 방법은 [CodePen](http://codepen.io/gaearon/pen/ZpvBNJ?editors=0010)을 사용하는 것입니다.<br>
아무것도 설치할 필요 없이 그냥 예제를 따라가기만 하면 됩니다.<br>
가장 간단한 예제를 보겠습니다
```JSX
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```
root라는 id의 DOM객체에 Hello, world! 를 랜더링합니다.<br>
다음 몇 파트 동안은 점차적으로 React를 사용하는 방법을 소개할 것입니다.<br>
잘 사용할 수 있게 된다면 작은 단위에 컴포넌트들로 복잡한 앱을 만들 수 있습니다.<br>

------------------
### 자바스크립트에 대하여
---------------
React는 JavaScript 라이브러리이기 때문에 JavaScript에 대한 기본지식이 필요합니다.<br>
아직 JavaScript를 잘 다루지 못한다면 [JavaScript를 더 공부](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)하는게 좋을것입니다.<br>
<br>
예제들에서는 ES6 문법을 사용하기 때문에 [화살표 함수](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions), [클래스](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes), [템플릿 리터럴](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Template_literals), [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let), [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)에 익숙해지는것이 좋습니다.<br>
그리고 [Babel REPL](http://babeljs.io/repl/#?babili=false&evaluate=true&lineWrap=false&presets=es2015%2Creact&experimental=false&loose=false&spec=false&code=const%20element%20%3D%20%3Ch1%3EHello%2C%20world!%3C%2Fh1%3E%3B%0Aconst%20container%20%3D%20document.getElementById('root')%3B%0AReactDOM.render(element%2C%20container)%3B%0A)을 사용해서 ES6문법이 컴파일되는것을 확인할 수 있습니다.
