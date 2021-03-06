### URL 라우팅
- app.METHOD(PATH, HANDLER)
	- METHDO
		- get
			- 클라이언트로부터 데이터를 요청받을 때 이쪽으로 들어온다.
		- post
			- 클라이언트로부터 새로운 데이터 추가를 요청받을 때 이쪽으로 들어온다.
		- delete
			- 클라이언트로부터 데이터 삭제를 요청받을 때 이쪽으로 들어온다.
		- put
			- 클라이언트로부터 데이터 수정을 요청받을 때 이쪽으로 들어온다.
	- PATH
		- URL이 http://ohou.se/cards/feed?order=recent라면 /cards/feed 부분이 PATH
	- HANDLER
		- 받은 요청을 처리하는 핸들러
- 예제 코드
	```javascript
	app.get('/user/:id', function(req, res){
		res.send('Received a GET request, param:' + req.params.id); // 일반 텍스트 형태로 응답한다.
	});

	app.post('/user', function(req, res) {
		res.json({success: true}); // json형태로 응답한다.
	});

	app.put('/user', function(req, res) {
		res.status(400).json({message: 'Hey, You. Bad Request!'}); // 상태코드와 함께 json형태로 응답한다.
	});

	app.delete('/user', function(req, res) {
		res.send('Received a DELETE request');
	});

	```
- API 테스팅 도구
	- 크롭 확장 프로그램 postman을 설치
	
### 라우팅 코드 모듈화 하기
- 프로젝트 루트에서 routes 디렉토리를 만듭니다.
- routes 디렉토리에서 user.js 파일을 만듭니다.
	```javascript
	var express = require('express');
	var router = express.Router();

	router.get('/:id', function(req, res){ // app.get에서 router.get으로, /user/:id에서 /:id로 변경했다.
		res.send('Received a GET request, param:' + req.params.id);
	});

	router.post('/', function(req, res) { // app.post에서 router.post로, /user에서 /로 변경했다.
		res.json({success: true});
	});

	router.put('/', function(req, res) {
		res.status(400).json({message: 'Hey, You. Bad Request!'});
	});

	router.delete('/', function(req, res) {
		res.send('Received a DELETE request');
	});
	```
- main.js에서 user.js를 불러와서 app에 연결한다.
	```javascript
	var user = require('./routes/user');

	app.use('/user', user);
	```

