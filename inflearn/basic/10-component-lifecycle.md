### Mounting
- constructor()
	- 딱 한 번만 호출
	- state를 설정
- componentWillMount()
	- 딱 한 번만 호출
	- 아직 mount 안 되었기 때문에 DOM 처리 불가
- render()
- componentDidMount()
	- 딱 한 번만 호출
	- 다른 자바스크립트를 연동할 수 있음
	- DOM 처리 가능
	
### Updating
- Mounting 메소드들이 호출될 땐 Updating 메소드들이 호출되지 않는다.
- componentWillReceiveProps(nextProps)
	- props를 받을 때 호출
	- props에 따라 state를 업데이트해야 할 때 유용
	- setState()를 호출해도 됨.
- shouldComponentUpdate(nextProps, nextState)
	- 업데이트를 허락할지 결정
	- stringify()를 쓰면 여러 field를 편하게 비교할 수 있다.
- componentWillUpdate(nextProps, nextState)
	- setState()를 호출하면 무한 루프에 빠짐.
- render()
- componentDidUpdate(prevProps, prevState)
	- setState()를 호출하면 무한 루프에 빠짐.

### Unmounting
- componentWillUnmount()
