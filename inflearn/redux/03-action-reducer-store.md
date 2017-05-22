# 구성 요소

### Action
- 작업에 대한 정보 객체
- Actions
- ActionCreators

### Reducer
- 변화를 일으키는 순수함수(비동기 같은 비순수 기능이 없는)
- 항상 같은 인수는 같은 결과를 반환해야 한다.
- 이전 상태를 변경하는 것이 아니라 새로운 상태를 반환해야 한다.
- 리듀서 파일엔 그 리듀서가 처리하는 상태의 기본값을 가지고 있기 때문에 상태 트리의 각 부분이 이곳 리듀서 파일에 정의된다고 볼 수 있다.
- Root Reducer
- Sub Reducers
	
### Store
- 앱의 현재 상태를 지니고 있음.
- dispatch()
- getState()
- subscribe()

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
	
- 흐름
	- View component에서 이벤트 발생 -> 
	- Controller component는 Action creator로 Action을 생성해서 Store로 전달 -> 
	- Store는 적절한 Reducer를 찾아 Action을 전달 -> 
	- Reducer는 수정된 새 State를 반환 -> 
	- Store는 기존 State를 새 State로 변경하고 관련 View component를 re-rendering


- 참고
	- aaa 디렉토리에 index.js를 만들고 그 파일 안에 bbb를 export로 정의했다면 ```import bbb from './aaa'```와 같이 bbb에 접근할 수 있다. ```import bbb from './aaa/index'```로 하지 않아도 된다는 뜻.
	
### react-redux
- View layer binding을 지원해준다.
- 앱 루트 컴포넌트를 ```<Provider>``` 컴포넌트로 감싼다.
