# React 컴포넌트 프로그래밍 패턴 1
### Stateful 컴포넌트에서 Stateless 컴포넌트로 전달한다.
- Stateful : getInitialState()를 가지는 컴포넌트
- Stateless : getInitialState()를 가지지 않는 컴포넌트
- Stateful 컴포넌트는 Stateless 컴포넌트에게 state를 넘겨준다. 넘겨받은 state는 Stateless 컴포넌트에겐 props다.

### Automatic binding
- Automatic binding이 없으면?
```javascript
var Parent = React.createClass({
	getInitialState: fuction() {
		return {value:''};
	},
	handleChange: function(e) {
		thi.setState({ // 만약 React가 automatic binding을 지원하지 않는다면 this는 호출한 객체를 가리키므로 this는 Chlid를 가리켰을 것이다. 이것 매우 중요.
			value: 'new val'
		});
	},
	render: function() {
		return <Child onClick={this.handleClick} />;
	}
});
var Child = React.createClass({
	render: function() {
		return <button onClick={this.props.onClick}>button</button>;
	}
});

```

# React 컴포넌트에 Style 적용하기
### inline style 사용 예
- ```<MyComponent style={{backgroundColor: 'red'}}```
- 바깥쪽 {}는 javascript표현식을 사용하겠다는 의미이고, 안쪽 {}는 style값을 객체(dictionary or map)형태로 던지겠다는 의미이다.

### external style 사용 예
- in external styles.js File
- ```module.exports = {backgroundColor: 'red'};```

- in js File to use it
- ```var styles = require('./styles');```

### 주의사항
- React에서는 style 이름도 camelCase로 생각해야 한다. 객체이기 때문이다.

# React 컴포넌트 프로그래밍 패턴 2
### Presentational 컴포넌트로부터 Container(Controller) 컴포넌트를 분리하기
- Container(Controller) : Stateful과 같다. 또한 UI 컨트롤 로직을 갖는다.
- Presentational : Stateless와 같다. 또한 rendering에 대한 아주 단순한 로직만 갖는다.

# Stateless Functional 컴포넌트
### render 메소드만 가지는 컴포넌트(보통 stateless 컴포넌트)는 하나의 함수로 정의할 수 있다.
```javascript
var Friend = React.createClass({
  render: function () {
    return <img src='https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-octopus.jpg' />;
  }
});

// 위 아래 코드는 서로 같다.

function Friend() {
  return <img src='https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-octopus.jpg' />;
}

// props를 사용해야 하는 경우는 아래와 같다.
function Friend(props) {
  return <img src={props.src} />;
}
```

# PropTypes
### 무엇인가?
- 부모 컴포넌트로부터 내려받는 props의 각 프로퍼티에 대응하는 이름과 기대하는 타입을 모아놓은 객체
- ex
```javascript
var Book = React.createClass(
  propTypes: {
    title: React.PropTypes.string.isRequired,
    id: React.PropTypes.number
  },
  render: function(){
    return <h1>{this.props.id} {this.props.title}</h1>;
  }
);
```
### 주의사항
- 기대하는 타입이 아니거나 isRequired인데 값이 없으면 콘솔에 경고메시지가 뜬다.
- 15.5버전부터 이 기능이 라이브러로 빠짐.
- ```npm install --save prop-types```
- ```var PropTypes = require('prop-types');```

### Stateless Functional 컴포넌트에서 PropTypes 쓰기
```javascript
function Book(props) {
  return <h1>{this.props.id} {this.props.title}</h1>;
}
Book.propTypes = {
  title: React.PropTypes.string.isRequired,
  id: React.PropTypes.number
};
```

# React Forms
### Uncontrolled 컴포넌트에서 Controlled 컴포넌트로 만들기
- input 태크는 입력값이라는 상태를 갖고 있기 때문에 Uncontrolled 컴포넌트이다.
- input 태크에 value 속성을 넣어주면 스스로의 상태를 더 이상 사용하지 않기 때문에 Controlled 컴포넌트가 된다. 이러면 React-like가 된다.

# Lifecyle Methods
### 메소드 종류 
- Mounting
  - mount 메소드는 render 메소드가 처음 호출되는 전후에 딱 한 번만 호출된다.
  - *componentWillMount*
  - render
  - *componentDidMount*
		- AJAX API를 사용하거나 Timer를 사용하거나 외부 JS 라이브러리를 연결하는 코드를 넣기에 이곳이 적당하다.

- Updating
	- componenetWillReceiveProps(nextProps)
		- props의 값을 state에 반영할 수 있다. 
	- shouldComponentUpdate(nextProps, nextState)
		- 업데이트 가능 여부를 return값으로 결정
		- props나 state가 변하지 않는다면 업데이트 할 필요가 없다.
	- componentWillUpdate(nextProps, nextState)
		- window 같은 Non-react 컴포넌트와 인터렉션 할 때 필요할 때 이 메소드가 적당하다.
		- this.setState()를 사용하면 안 된다. 무한 콜백에 빠지기 때문이다.
	- render
	- comoponentDidUpdate(prevProps, prevState)
	
- Unmounting
	- componentWillUnmount(prevProps, prevState)
		- DOM에서 제거되기 전에 불려진다.
		- 컴포넌트에서 해제해야 할 것이 있다면 이 메소드에서 한다.
