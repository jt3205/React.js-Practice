리액트란? / 설치
================
1. 리액트란?
---------
페이스북에서 개발한 유저 인터페이스 라이브러리입니다.<br>
개발자로 하여금 재사용 가능한 UI를 생성 할 수 있게 해줍니다.<br>
현재 페이스북, 인스타그램, 야후, 넷플릭스등의 큰 서비스들에서 사용되고 있습니다.<br>
이 라이브러리는 ***Virtual DOM*** 이라는 개넘을 통하여 뷰에서 *필요한 부분만 업데이트* 할 수 있게 해줍니다.<br>
React는 라이브러리이기 때문에 여러 프로젝트에 적용할 수 있으며 Angular.js등과 함께도 사용할 수 있습니다.
*********
2. 설치
----------
React를 간단하게만 사용해보고 싶다면 *[CodePen](https://codepen.io/gaearon/pen/rrpgNB?editors=0010)* 으로도 충분히 가능합니다.<br>
[React Create App](http://github.com/facebookincubator/create-react-app)은 React 단일 응용프로그램을 만들때 정말 유용합니다.<br>
좋은 개발 환경, 개발 경험, 최신 자바스크립트를 경험할 수 있습니다.<br>
Node.js의 버전은 6 이상이여야 합니다.<br>
```
npm install -g create-react-app
create-react-app my-app

cd my-app
npm start
```
npm 5.2.0 이상을 사용하고 있다면 대신 [npx](https://www.npmjs.com/package/npx)를 사용할수도 있습니다.
```
npx create-react-app my-app

cd my-app
npm start
```
Create React App은 백앤드, 데이터베이스를 처리하지 않습니다.<br>
프론트 엔드 빌드 파이프 라인을 생성하기 때문에 원하는 백엔드와 함께 사용할 수 있습니다.<br>
**babel**, **webpack** 같은 빌드 도구들을 사용 하지만, 제로 구성으로 작동합니다.<br>
즉 거의 아무런 설정을 하지 않고 사용이 가능합니다.<br>
<br>
실행할 준비가 되었다면 ```npm run build```을 실행함으로써 ```build```폴더에서 최적화 된 빌드를 생성할 수 있습니다.<br>
*****
3. 기존 어플리케이션에 추가
-----
앱을 처음부터 다시 설치해야하는 귀찮음따위는 없습니다.<br>
프로그램의 일부분에 React를 추가해서 작동을 확인할 수 있습니다.<br>
React는 빌드 파이프 라인 없이도 사용가능 하지만 생산성을 높히기 위해서 설정하는게 좋습니다<br>
요즘 대세 빌드 파이프라인은 이런것들이 있습니다.<br>
* **package manager** : [Yarn](https://yarnpkg.com/), [npm](https://www.npmjs.com/)
여러가지 다른 패키지를 쉽게 설치하고 업데이트 할 수 있습니다.

* **bundler** : [webpack](https://webpack.js.org/), [Browserify](http://browserify.org/)
코드를 모듈단위로 묶어서 로드 시간을 줄여줍니다.

* **compiler** : [Babel](http://babeljs.io/)
오래된 브라우저에서도 최신 JavaScript코드를 사용할 수 있습니다.

> 프로덕션 환경에서 React를 최적화시키기 위해서 프로덕션 빌드 프로세스 를 설정하는 것이 좋습니다 .

프론트엔드 의존성(dependencies)을 관리하기 위해서 [Yarn](https://yarnpkg.com/)이나 [npm](https://www.npmjs.com/)을 사용하는 것이 좋습니다.<br>
패키지 관리자를 처음 사용해 본다면 [Yarn의 도큐먼트](https://yarnpkg.com/en/docs/getting-started)를 참고하는것도 좋을겁니다.<br>
<br>
React with Yarn을 설치하려면 이걸 실행합니다.
```
yarn init
yarn add react react-dom
```
React with npm을 설치하려면 이걸 실행합니다.
```
npm init
npm install --save react react-dom
```

Yarn과 npm 모두 [npm 레지스트리](https://www.npmjs.com/) 에서 패키지를 다운로드합니다.

### ES6 및 JSX 사용
React with [Babel](http://babeljs.io/) 을 사용하면 JavaScript 코드에서 ES6 및 JSX를 사용할 수 있습니다.<br>
*ES6* 는 최신 자바스크립트 문법인데 코드가 간결하고 명확해 졌습니다.<br>
*JSX* 는 React에서 작동하는 JavaScript의 확장 기능입니다.<br>
<br>
Babel 설치 안내에서는 어떻게 다양한 빌드 환경에서 Babel을 사용할 수 있는지 설명합니다.<br>
.babelrc 에서 [babel-preset-react](http://babeljs.io/docs/plugins/preset-react/#basic-setup-with-the-cli-), [babel-preset-env](http://babeljs.io/docs/plugins/preset-env/)를 사용 가능하도록 설정 했는지 확인해야 합니다.

### Hello World (ES6 및 JSX 사용)
[webpack](https://webpack.js.org/) 또는 [Browserify](http://browserify.org/) 와 같은 bundler을 사용하여 모듈단위의 코드를 작성하여 작은 패키지로 묶어 로딩 시간을 최적화 할 수 있습니다.<br>
간단한 React 예제입니다.
```JavaScript
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```
이 코드는 id가 root인 DOM요소로 랜더링 되므로 HTML어딘가에 ```<div id="root"></div>```가 있어야 합니다.<br>
다른 자바스크립트 UI 라이브러리로 만든 기존 앱 DOM요소 내부에도 랜더링 시킬수 있습니다.<br>
~~이를테면 Angular.js라던가? 근데 Angular는 라이브러리가 아닌데...~~

### CDN 사용
npm을 사용하지 않는다면 CDN을 사용할 수 있습니다.
```HTML
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
```
위 버전은 개발용도로 사용하기 위한 패키지이기 때문에 서비스하기엔 적합하지 않습니다.<br>
최적화된 버전은 다음과 같습니다.
```html
<script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
```
버전을 바꾸고 싶다면 16을 원하는 버전으로 바꾸면 됩니다.<br>
