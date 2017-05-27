### Express에서 미들웨어의 의미
- HTTP요청 -> **미들웨어** -> URL 라우팅 -> HTTP응답

### 미들웨어 만들어서 적용해보기
- 미들웨어 만들기
	```javascript
	myLoggerMiddleware = function(req, res, next) {
		console.log(req.url); // URL 라우팅 전에 항상 이 메소드가 호출된다.
		next(); // 반드시 next()를 호출해줘야 다음 작업(URL 라우팅)이 진행된다.
	};

	app.use(myLoggerMiddleware);
	```
	
- 주의사항
	- 라우팅 코드를 use 하기 전에 미들웨어를 use해야 모든 라우팅에 대해 미들웨어가 잘 동작한다.
	```javascript
	app.use(myLoggerMiddleware); // 미들웨어 먼저 use
	app.use('/user', user); 
	```

### 이미 만들어져 있는 미들웨어 사용해보기
- 설치
	```cli
	npm install --save morgan body-parser
	```
- morgan
	- 로깅 미들웨어 사용하기
	```javascript
	var morgan = require('morgan');
	app.use(moragan('dev'));
	```
	
- body-parser
	- json형태의 데이터를 파싱하는 미들웨어 사용하기
	```javascript
	var bodyParser = require('body-parser');
	app.use(bodyParser.json());
	```

- 팁
	- 미들웨어 설명이 나와있는 github 페이지 바로가기
	```cli
	npm repo morgan
	npm repo body-parser
	```
