### Node.js
- Node는 웹서버가 아님.
- 웹브라우저가 아닌 환경에서도 JS를 돌릴 수 있게 해주는 JS 런타임 환경

### Express.js
- 웹서버를 돌리기 위해선 JS 코드를 직접 짜야 한다.
- 웹서버 코드를 가지고 있는 라이브러리가 Express

### Express 준비
- 터미널에서 프로젝트 루트로 이동한 다음, 아래와 같이 입력한다.
	```cli
	npm init
	npm install --save express
	```

### Express 실행
- 프로젝트 루트에 main.js 파일을 만든다.
	```javascript
	var express = require('express');
	var app = express();

	app.get('/', function(req, res) {
		res.send('Hello World');
	});

	app.listen(3000, function(){
		console.log('Example App is listening on port 3000');
	});
	```
- 터미널에서 프로젝트 루트 위치로 이동한 다음, ```node main.js```를 입력한다.




