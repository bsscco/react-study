### 서버쪽 파일구조
```
server
├── main.js
├── models
│   ├── account.js
│   └── memo.js
└── routes
    ├── account.js
    ├── index.js
    └── memo.js
```
- 디렉토리 models
	- mongoose의 데이터 모델들
- 디렉토리 routes
	- 앱의 API들

### 서버코드 수정
- project-root/server/main.js
	```javascript
	import express from 'express';
	import path from 'path';

	// 추가 시작
	import webpack from 'webpack';
	import WebpackDevServer from 'webpack-dev-server';

	import morgan from 'morgan'; // HTTP REQUEST LOGGER
	import bodyParser from 'body-parser'; // PARSE HTML BODY

	import mongoose from 'mongoose';
	import session from 'express-session';

	import api from './routes';
	// 추가 끝
	
	const app = express();
	const port = 3000;
	const devPort = 4000;

	// 추가 시작
	app.use(morgan('dev'));
	app.use(bodyParser.json());

	/* mongodb connection */
	const db = mongoose.connection;
	db.on('error', console.error);
	db.once('open', () => { console.log('Connected to mongodb server'); });
	// mongoose.connect('mongodb://username:password@host:port/database=');
	mongoose.connect('mongodb://localhost/codelab');

	/* use session */
	app.use(session({
			secret: 'CodeLab1$1$234',
			resave: false,
			saveUninitialized: true
	}));
	// 추가 끝

	app.use('/', express.static(path.join(__dirname, './../public')));

	// 수정 시작
	/* setup routers & static directory */
	app.use('/api', api);

	/* handle error */
	app.use(function(err, req, res, next) {
		console.error(err.stack);
		res.status(500).send('Something broke!');
	});
	// 수정 끝

	app.listen(port, () => {
			console.log('Express is listening on port', port);
	});

	if(process.env.NODE_ENV == 'development') {
			console.log('Server is running on development mode');
			const config = require('../webpack.dev.config');
			const compiler = webpack(config);
			const devServer = new WebpackDevServer(compiler, config.devServer);
			devServer.listen(
					devPort, () => {
							console.log('webpack-dev-server is listening on port', devPort);
					}
			);
	}
	```
- 미들웨어 morgan과 body-parser, express-session을 사용합니다.
- DB툴 mongoose를 사용합니다.

### API 코드
- project-root/server/routes/accounts.js
	```javascript
	import express from 'express';

	const router = express.Router();

	router.post('/signup', (req, res) => {
			/* to be implemented */
			res.json({ success: true });
	});

	router.post('/signin', (req, res) => {
			/* to be implemented */
			res.json({ success: true });
	});

	router.get('/getinfo', (req, res) => {
			res.json({ info: null });
	});

	router.post('/logout', (req, res) => {
			return res.json({ success: true });
	});

	export default router;
	```

