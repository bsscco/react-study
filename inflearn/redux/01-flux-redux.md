# Flux와 Redux

### React Flux
- 추상적인 개념
- [Flux 로의 카툰안내서](http://bestalign.github.io/2015/10/06/cartoon-guide-to-flux/)
- Actions, ActionCreators, Dispatcher, Stores, Views
- 이벤트 발생 ->
	- 뷰가 액션 생성자에게 액션을 요청 -> 
	- 액션 생성자는 새 액션을 디스패처로 전달 -> 
	- 디스패처는 적절한 스토어로 액션을 전달 -> 
	- 스토어는 액션에 대응하는 상태를 수정 -> 
	- 스토어는 수정된 상태와 관련된 뷰에게 수정된 상태를 떤져줌. -> 
	- 뷰는 받은 상태를 참조하여 렌더링

### React Redux
- Flux의 구현체 중 하나
- [Redux로의 카툰안내서](http://bestalign.github.io/2015/10/26/cartoon-intro-to-redux/)
- 원칙
	- 오직 하나의 상태 트리. App의 모든 상태는 하나의 스토어에 담겨있다.
	- 상태를 변경하기 위해선 무조건 액션을 스토어에 dispatch 해야 한다.
	- 액션을 처리하는 순수함수 리듀서는 DB, 네트워크 접근 같은 비동기 처리 없이 항상 같은 인수로 같은 결과를 반환하는 함수여야 한다.
- Actions, ActionCreators, Store, Reducers, Views
- 이벤트 발생 -> 
	- 뷰가 액션 생성자에게 액션을 요청 -> 
	- 액션 생성자는 새 액션을 스토어로 전달 -> 
	- 스토어는 모든 리듀서에게 액션을 전달 -> 
	- 액션을 처리할 수 있는 리듀서가 액션에 대응하는 새 상태를 반환 -> 
	- 스토어는 반환된 상태를 기존 상태와 바꿔치기 -> 
	- 스토어는 수정된 상태와 관련된 뷰에게 수정된 상태를 떤져줌. -> 
	- 뷰는 받은 상태를 참조하여 렌더링

