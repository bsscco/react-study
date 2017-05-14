### Action
- Action Creator
- Actions

### Reducer
- 이전 상태와 액션을 받아서 -> 새로운 상태를 반환하는 함수
- Reducer Root
- Reducers
	
### Store
- 앱의 현재 상태를 지니고 있음.

### 파일 구조
- src
	- actions
		- ActionTypes.js #action types
		- index.js #action creator
	- components
		- App.js #root component
		-	Counter.js #controller component
		-	Control.js #view component
		-	Value.js #view component
	- reducers
		- counter.js #reducer
		- ui.js #reducer
		- index.js #root reducer
	- index.js #store creator
	
- View component에서 이벤트 발생 -> Controller component는 Action creator로 Action을 생성해서 Store로 전달 -> Store는 적절한 Reducer를 찾아 Action을 전달 -> Reducer는 수정된 새 State를 반환 -> Store는 기존 State를 새 State로 변경하고 관련 View component를 re-rendering


### 기타 참고
- aaa 디렉토리에 index.js를 만들고 그 파일 안에 bbb를 export로 정의했다면 ```import bbb from './aaa'```와 같이 bbb에 접근할 수 있다. ```import bbb from './aaa/index'```로 하지 않아도 된다는 뜻.
