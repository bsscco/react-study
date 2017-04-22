### 시작부터 칭찬을 늘어놓는다.
- 매우 빠르다.
- 모듈화가 잘 된다.
- 큰 앱도 잘 돌아간다.

# JSX
### 문법상의 주의사항

- class속성은 className으로 써야 한다.
	- 이유
		- JSX가 Javascript로 변환될 때 각 태그는 객체로 만들어지는데, Javascript에선 class가 예약어이기 때문이다.

- ```<br>```태그와 같이 셀프 클로징은 쓸 수 없다. 항상 ```<br />```로 써주어야 한다.

- JSX표현식 {}에 제어문, 반복문을 쓸 수 없다. 
	- 이유
		- JSX가 Javascript로 변환될 때 각 태그는 객체로 만들어지는데, 객체생성자의 인자가 될 수 있는 것은 값이나 표현식(expression)이기 때문이다. if문, for문 같은 제어문, 반복문은 들어갈 수 없다.
	- 해결방법
		1. JSX 범위 밖에서 제어문으로 조건에 따라 JSX를 생성한다.
		2. JSX표현식 {}에서 제어문 대신 삼항 연산자를 쓴다.
		3. JSX표현식 {}에서 제어문 대신 && 연산자를 쓴다.	
		4. JSX표현식 {}에서 반복문 대신 map(function(item, idx){}) 메소드를 쓴다.
		
- JSX 안에 list가 있을 경우 어떤 조건을 만족하면 반드시 항목마다 key속성을 설정해주어야 한다.
	- 아래 조건 중 하나라도 만족하면 key값이 필요하다.
		- 각 항목이 체크되어있는지 여부를 기억해야 할 경우
		- 각 항목의 순서가 다음 렌더링 시에 바뀌는 경우
	- key의 값
		- 항목 간 key속성의 값은 서로 unique 해야 하먀, sibling 항목 간에만 unique 하면 된다.

# Component
### 무엇인가?
- 하나의 작업을 책임지는 재사용 가능한 작은 코드 덩어리. 보통 HTML 태그를 그리는 작업을 한다.

### 컴포넌트 만들 준비를 하자.
- ```var React = require('react');```
	- React는 리액트를 사용하기 위한 메소드들을 담고 있는 객체이다.
- ```var ReactDOM = require('react-dom');```
	- ReactDOM은 DOM과 상호작용한다.
	
### 컴포넌트 만들기
- React.createElement()와 React.createClass()의 차이
	- HTML 태그 하나를 만다는 것 / React 컴포넌트를 만드는 것

- React.createClass() 주의사항
	- 생성된 클래스를 받는 변수의 이름은 대문자로 시작해야 한다.
	- 오직 하나의 인자만 받는데 그것은 Javascript 객체여야 한다. 
	```javascript
	var NavBar = Rreact.createClass({
		render: function () {
			return <h1>Hello world</h1>;
		}
	})
	```
	
### 컴포넌트 모듈화하기
- 다른 js파일에 작성해서 require로 불러오자.
	- in NavBar.js
	```javascript
	var NavBar = React.createClass(...);
	module.exports = NavBar;
	```
	- in NavBarContainer.js
	```javascript
	Var NavBar = require('./NavBar.js'.NavBar);
	```
	
# props
### 무엇인가?
- 컴포넌트의 정보를 고정하는 객체
- 부모 컴포넌트로부터 전달받는다.

### 컴포넌트에 속성 넘기기
- ```<MyComponent foo="bar" />```

- 왜 속성을 넘기나요?
	- 컴포넌트 객체마다 UI를 다르게 만들 수 있다. 컴포넌트 안에 고정된 값을 담아놓으면 컴포넌트 객체들은 모두 같은 UI를 가진다. 부모 컴포넌트로부터 속성을 넘겨받아 사용하면 속성에 따라 다른 UI를 가지게 할 수 있다.

- props 네이밍 컨벤션
	- 이벤트 핸들러는 handle*EventType*으로 짓는다. ex) handleClick, handleKeyPress
	- prop은 on*EventType*으로 짓는다. ex) onClick, onPress
- defalt props
	```javascript
	getDefaultProps: function () {
	    return{
	      text: 'I am a text prop's default value'
	    };
	},
	```

- this.props.children
	- 현재 컴포넌트의 오프닝, 클로징 태그 사이에 있는 모든 태그들이 들어있다.	
	
# state
### 무엇인가?
- props와 달리 부모 컴포넌트로부터 전달받지 않는다.

### 상태값 초기화
```javascript
getInitialState: function () {
    return { mood: 'I am a mood state's initial value' };
  },
```

### 상태값 변경하기
- ```this.setState({})```
- ```setState()``` 호출 후에는 바로 render()가 호출된다고 생각하자. 만약 render() 안에서 setState()를 호출하면 무한 루프가 돌 것이다.

