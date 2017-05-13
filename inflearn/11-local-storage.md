### localStorage
- 뭐니?
	- HTML5부터 지원하는 로컬 저장소, 쿠키랑 비슷하지만 쿠키보다 많은 데이터를 저장할 수 있음.
	- 도메인별로 로컬 저장소를 갖는다.

- 주의사항
	- 텍스트 형태로만 저장할 수 있기 때문에 객체를 저장할 땐 JSON.stringify()로 저장하고, 불러올 땐 JSON.parse()로 불러와야 한다.
	
- 사용하기
	```javascript
	componentWillMount(){
		const contactData = localStorage.contactData;
		if(contactData) {
			this.setState({
				contactData: JSON.parse(contactData)
			});
		}
	}

	componentDidUpdate(prevProps, prevState) {
		if(JSON.stringify(prevState.contactData) != JSON.stringify(this.state.contactData)) {
			localStorage.contactData = JSON.stringify(this.state.contactData);
		}
	}
	```
	- localStorage.clear();
