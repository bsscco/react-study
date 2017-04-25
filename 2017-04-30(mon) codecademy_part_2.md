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
- React에서는 style 이름도 camelCase로 생각해야 한다. 

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
