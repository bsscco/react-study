# React 컴포넌트 프로그래밍 패턴 1
### Stateful 컴포넌트에서 Stateless 컴포넌트로 전달한다.
- Stateful : getInitialState()를 가지는 컴포넌트
- Stateless : getInitialState()를 가지지 않는 컴포넌트
- Stateful 컴포넌트는 Stateless 컴포넌트에게 state를 넘겨준다. 넘겨받은 state는 Stateless 컴포넌트에겐 props다.

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
### render 메소드만 가지는 컴포넌트(보통 stateless 컴포넌트)는 하나의 함수로 정의할 수 있습니다.
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
	- shouldComponentUpdate(nextProps, nextState)
		- 업데이트 가능 여부를 return값으로 결정
		- 
	- render
- Unmounting
