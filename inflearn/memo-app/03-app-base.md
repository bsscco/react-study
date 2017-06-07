### 서버코드 작성
- project-root/server/main.js
	```javascript
	import express from 'express';
	import path from 'path';

	import webpack from 'webpack';
	import WebpackDevServer from 'webpack-dev-server';

	const app = express();
	const port = 3000;
	const devPort = 4000;

	app.use('/', express.static(path.join(__dirname, './../public')));

	app.get('/hello', (req, res) => {
			return res.send('Hello CodeLab');
	});

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
- express()와 path, webpack(), WebpackDevServer를 불러와 사용합니다.
- 개발서버와 제품서버의 코드가 함께 있습니다.

### 개발서버 설정파일 작성
- project-root/webpack.dev.config.js
	```javascript
	var webpack = require('webpack');

	module.exports = {

			entry: [
					'./src/index.js',
					'webpack-dev-server/client?http://0.0.0.0:4000',
					'webpack/hot/only-dev-server'
			],

			output: {
					path: '/',
					filename: 'bundle.js'
			},

			devServer: {
					hot: true,
					filename: 'bundle.js',
					publicPath: '/',
					historyApiFallback: true,
					contentBase: './public',
					proxy: {
							"**": "http://localhost:3000"
					},
					stats: {
						// Config for minimal console.log mess.
						assets: false,
						colors: true,
						version: false,
						hash: false,
						timings: false,
						chunks: false,
						chunkModules: false
					}
			},


			plugins: [
					new webpack.optimize.OccurenceOrderPlugin(),
					new webpack.HotModuleReplacementPlugin(),
					new webpack.NoErrorsPlugin()
			],

			module: {
					loaders: [
							{
									test: /\.js$/,
									loaders: ['react-hot', 'babel?' + JSON.stringify({
											cacheDirectory: true,
											presets: ['es2015', 'react']
									})],
									exclude: /node_modules/,
							}
					]
			}


	};
	```
- entry
	- 응?
- output
	- 응?
- proxy
	- 응?
	
### 제품서버 설정파일 작성
- project-root/webpack.config.js
	```javascript
	module.exports = {
			entry: './src/index.js',

			output: {
					path: __dirname + '/public/',
					filename: 'bundle.js'
			},

			module: {
					loaders: [
							{
									test: /\.js$/,
									loaders: ['babel?' + JSON.stringify({
											cacheDirectory: true,
											presets: ['es2015', 'react']
									})],
									exclude: /node_modules/,
							}
					]
			}
	};
	```
- 개발환경에서의 bundle.js와 제품환경에서의 bundle.js가 다르기 때문에 설정파일을 따로 구성한다고 합니다.

### 서버 실행해보기
- 제품서버 실행
	- ```npm run start```
- 개발서버 실행
	- ```npm run development```
