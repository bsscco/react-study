### props
- Immutable data
- Parent 컴포넌트에서 Child 컴포넌트로 전달
	- <MyComponent name="Hi">
	- this.props.name
	- this.props.children
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

### state
- Mutable data
- 
