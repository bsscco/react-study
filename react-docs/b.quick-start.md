# Create new app

### 설치
```
npm install -g create-react-app
create-react-app my-app

cd my-app
npm start
```

### 설치 후
```
Success! Created my-app at /Users/bsscco/my-app
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!
```

# 시작 전

- 자바스크립트 리마인드
	https://developer.mozilla.org/ko/docs/A_re-introduction_to_JavaScript

- ES6(ECMAScript2015) 문법을 사용한다.
	Babel이 ES6 미만을 지원하는 곳에서도 돌아가게끔 만들어준다.

# 닥스

### JSX에 대해서
- Javascript의 확장 문법이다.
- HTML-like 문법
- JSX 안에서 Javascript를 사용하려면 {}로 감싼다.
- JSX를 감싸는 ()를 다른 라인으로 나누길 추천한다. [ASI의 부작용을 피하기 위함](http://doyouwannabuildservice.blogspot.kr/2016/08/blog-post.html)
- JSX는 Bebel 컴파일 후에 순수 Javascript로 바뀌기 때문에 Javascript 어디에서나 JSX를 사용해도 문제가 없다.
- JSX 태그 안에 있는 속성에 값을 넣을 때 '' 아니면 {}를 사용해야 한다. ''와 {}를 함께 사용하면 안 된다.
- JSX는 컴파일 후 Javascript가 되기 때문에 속성명이 camelCase다.
- JSX 안의 값은 모두 String으로 변환되기 때문에 유저인풋에 의한 값이 JSX에 들어가도 Injection어택이 예방된다.
- 사용하는 에디터에서 Babel Syntax스키마를 찾는 것을 권한다. 그러면 ES6와 JSX에 하이라이트가 생길 것이다.

### 엘리먼트에 대해서
- React 엘리먼트는 DOM 객체와 달리 순수 Javascript 객체이기 때문에 생성비용이 싸다.
- React 엘리먼트의 속성이나 자식 엘리먼트를 변경하기 위해선 오직 ReactDOM.render()를 다시 호출하는 수밖에 없다. React 엘리먼트는 영화의 한 프레임과 같기 때문이다. immutable이다.
- 하지만 대부분의 React app에선 ReactDOM.render()를 한 번만 호출한다. 그게 가능한 이유는 이후 배울 stateful compoments가 있기 때문이다.
