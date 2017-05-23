# react-redux

### 소개
- View layer binding을 지원해준다.

### 사용법
- 앱 루트 컴포넌트를 ```<Provider>``` 컴포넌트로 감싼다.
	- 이렇게 하면 모든 하위 컴포넌트에서 this.props.dispatch로 dispatch를 호출할 수 있다.
- Smart 컴포넌트에서는 connect()를 호출해서 스토어와 컴포넌트를 바인딩한다.
	- 이렇게 하면 Smart 컴포넌트는 this.props.로 액션 생성자 함수와 상태를 불러올 수 있다.
	```javascript
	const mapStateToProps = (state) => { // 스토어의 state를 인자로 받아와서 this.props의 속성으로 바인딩
			return {
					number: state.counter.number,
					color: state.ui.color
			};
	};

	const mapDispatchToProps = (dispatch) => { // 스토어의 dispatch를 인자로 받아와서 액션 생성자 함수 호출 부분을 더 짧게 바인딩 한다. 
			//return bindActionCreators(actions, dispatch);
			return {
					handleIncrement: () => { dispatch(actions.increment())},
					handleDecrement: () => { dispatch(actions.decrement())},
					handleSetColor: (color) => { dispatch(actions.setColor(color))}
			};
	};

	export default connect(mapStateToProps, mapDispatchToProps)(Counter);
  ```
  
