### 검색에 필요한 것들
- ```newLlist = list.filter((item)=>true/*or false*/)```

### 수정에 필요한 것들
- 도구
	- immutable.js를 사용한다.
	- React에서는 immutable.js를 적용한 ```Immutable Helper```를 사용한다.
	- 또 다른 도구로는 ES7의 ```spread 문법```이 있다. 지금은 ```Immutable Helper```를 사용한다.

- 설치
```npm install --save react-addons-update```

- 불러오기
```import update from 'react-addons-update';```

- 사용하기
	- 추가하기
	```javascript
	this.setState({
		contactData: update(this.state.contactData, {$push: [ contact ]/*배열 형태로*/});
	});
  ```
	- 제거하기
	```javascript
	this.setState({
		contactData: update(this.state.contactData, {$splice: [ [this.state.selectedKey, 1] ]/*배열 형태로*/})
	});	
	```
	- 수정하기
	```javascript
	this.setState({
		contactData: update(this.state.contactData, 
			{
				[this.state.selectedKey]: {
					name: {$set: name},
					phoen: {$set: phone}
				}
			}
	});	
	```
  
  
