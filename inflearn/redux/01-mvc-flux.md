### MVC
- 관심사의 분리
- Actions, Controllers, Models, Views
- Action -> Controller updates Model -> Controller notifies View. -> View updates itself with Model. -> Action be emitted in View

### Flux
- 추상적인 개념
- Actions, Dispatcher, Stores, Views
- Action -> Dispatcher dispatches Action to one of the appropriate Stores.-> Store updates Model -> Store notifies View -> View updates itself with State that received from Store. -> Action be emited in View
- [Flux 로의 카툰안내서](http://bestalign.github.io/2015/10/06/cartoon-guide-to-flux/)

### Redux
- flux의 구현체 중 하나
- 원칙
	- Single Store. App의 모든 State는 하나의 store에 담겨있습니다.
	- State를 변경하기 위해선 무조건 Action을 dispatch 해야 합니다.
	- Reducer(Action을 처리하는 순수함수)는 DB, 네트워크 접근 같은 비동기 처리 없이 항상 같은 인수로 같은 결과를 반환하는 함수여야 한다.
- [Redux로의 카툰안내서](http://bestalign.github.io/2015/10/26/cartoon-intro-to-redux/)
