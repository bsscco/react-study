### ref
- 뭔가?
	- focus를 바꾸고 싶을 때 같은 경우(dom에 접근이 필요한 경우)에 사용한다.
	- ```<input ref={(ref)=>{this.myInput = ref}}```로 준비하고 ```this.nameInput.focus();``` 사용
	
- 주의사항
	- ref를 사용하지 않아도 되는 경우엔 사용하지 말아야 한다.
	- constructor(), render() 안에서는 ref를 사용할 수 없다.
