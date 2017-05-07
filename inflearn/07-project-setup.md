### 프로젝트 생성 및 의존 모듈 설치
- 명령어
	```cli
	npm init
	npm install --save react react-dom
	npm install --save-dev babel-core babel-loader babel-preset-es2015 babel-preset-react
	npm install --save-dev webpack webpack-dev-server react-hot-loader
	```

- 모듈
	- webpack
		- require 지원, scss를 css로 변환, js코드를 하나의 파일로 합치기

	- webpack-dev-server
		- 테스트 서버 실행
		- hot-loader 지원
		
	- react-hot-loader
		- webpack-dev-server가 React 컴포넌트의 hot-loeading을 지원하지 않기 때문에 React 컴포넌트가 바뀌면 hot-loading 될 수 있도록 해주는 모듈
		
- project-root-dir/webpack.config.js
	```javascript
	var webpack = require('webpack');

	module.exports = {
		entry: './src/index.js', // entry에 있는 파일부터 시작해서 require를 통해 타고타고 들어가서 모든 파일들을 불러오는 시작경로

		output: {
			path: __dirname + '/public/', // 합쳐진 js들이 담긴 파일을 저장할 디렉토리(프로젝트-root/public/)
			filename: 'bundle.js' // 저장할 파일명
		},

		devServer: {
			hot: true, // hot loading 기능 켜기
			inline: true, // hot loading에 사용할 client를 bundle.js에 넣어준다. 뭔 뜻임..?
			host: '0.0.0.0',
			port: 4000, 
			contentBase: __dirname + '/public/'
		},

		module: {
			loaders: [
				{
					test: /\.js$/, // js로 변경할 대상 파일들
					loader: 'babel', // 사용할 로더
					exclude: /node_modules/, // node_modules 디렉토리는 js로만 이루어져있고 양이 많기 때문에 제외시킴.
					query: {
						cacheDirectory: true,
						presets: ['es2015', 'react'] // js로 변경할 대상들에 대한 프리셋
					}
				}
			]
		},

		plugins: [
			new webpack.HotModuleReplacementPlugin() // Hot loading 모듈
		]
	};
	```

- project-root-dir/.jshintrc
	- Atom 에디터에서 jshint 패키지를 사용할 때 es6 문법을 사용하면 에러가 나는 것을 방지하기 위함.
	```javascript
	{
		"esversion": 6
	}
	```

- project-root-dir/package.js
	```javascript
	"scripts" : {
		"dev-server": "webpack-dev-server" // webpack-dev-server를 직접 입력해서 실행하지 않는 이유는 만약, 프로젝트 루트 디렉토리가 아니라 src디렉토리 같은 곳에서 실행했을 때 이상하게 동작하기 떄문. 테스트 서버는 프로젝트 루트 디렉토리에서 실행되어야 webpack.config.js를 읽을 수 있다. 실행 스크립트로 테스트 서버를 실행하면 루트 디렉토리 기준으로 실행되기 때문에 정상 동작.
	}
	```
