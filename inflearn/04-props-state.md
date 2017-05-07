### props
- Immutable data
- 사용. Parent 컴포넌트에서 Child 컴포넌트로 전달
	- ```<MyComponent name="Hi">```
	- ```this.props.name```
	- ```this.props.children```
- 기본값 설정
	```javascript
	MyComponent.defaultProps = {
		name: "default value"
	};
	```
- Type 검증
	```javascript
	MyComponent.propTypes = {
		name: React.PropTypes.string.isRequired
	};
	```
	- 오랜 된 코드를 다시 보거나 다른 사람이 이 코드를 봤을 때 이해하기 쉽도록, 유지보수를 위해 사용한다.

### state
- Mutable data
- 초기화
	```javascript
	constructor() {
		this.state = {
			name: "deafult name"
		};
	}
	```
- 사용
	- ```this.state.name```
- 갱신
	```javascript
	this.setState({
		name: "new name"
	});
	```
- 주의 
	- this.state = 는 절대 사용하지 말 것.
	

