### 핫로딩으로 수정된 코드를 바로 서버에 갱신하기
- 설치 ```npm install -g nodemon```
- 실행 ```nodemon main.js```

### 정적 파일에 접근할 수 있게 하기
- ```app.use('/', express.static('public'));```
- localhost:3000을 요청하면 public/index.html을 보내준다.
- localhost:3000/about.html을 요청하면 public/about.html을 보내준다.

### 팁
- ```app.get('/', ...```과 ```app.use('/', express.static(...``` 중 어느 게 더 우선권을 가질까?
	- 먼저 호출된 쪽이 더 우선권을 가짐.
