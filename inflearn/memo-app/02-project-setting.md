### 초기 프로젝트 클론하기
```cli
git clone https://github.com/velopert/react-codelab-project.git
cd react-codelab-project #프로젝트로 이동
git branch -r #원격 브랜치 목록 보기
git checkout step00 #첫번재 브랜치로 전환
```

### 프로젝트 내에 라이브러리 설치
```cli
npm install #프로젝트에 필요한 클라이언트쪽 npm 모듈들을 설치합니다. (babel-core, babel-loader, babel-preset-es2015, babel-preset-react, react, react-dom, react-hot-loader, webpack, webpack-dev-server)

npm install --save babel-polyfill #클라이언트쪽 모듈을 추가 설치합니다.

npm install --save-dev style-loader css-loader #개발서버쪽 모듈들을 설치합니다.

npm install --save express path body-parser morgan mongoose express-session bcryptjs axios react-addons-update react-router react-timeago redux react-redux redux-thunk react-addons-css-transition-group #개발+제품서버쪽 npm 모듈들을 설치합니다.
```
- 클라이언트쪽 모듈 목록
	- babel-core
		- jsx를 js로 변환해주는 transform 
	- babel-loader
		- babel을 webpack에 올려주는 로더
	- babel-preset-es2015
		- babel이 사용하는 es6 프리셋
	- babel-preset-react
		- babel이 사용하는 react 프리셋
	- react
		- react
	- react-dom
		- react가 dom을 사용할 수 있게 해줍니다.
	- react-hot-loader
		- react 코드가 수정되면 서버에 바로 갱신될 수 있게 해줍니다.
	- webpack
		- babel 같은 transform들을 한데 모아 동작시키고, 결과물을 하나의 js파일에 모아줍니다.
	- webpack-dev-server
		- webpack이 지원하는 개발용 서버
	- babel-polyfill
		- es6문법을 이전 버전으로 변환해줍니다.

- 개발서버쪽 모듈 목록
	- style-loader
		- css 파일들을 require로 불러올 수 있습니다.
	- css-loader
		- css 파일들을 require로 불러올 수 있습니다.
 
- 개발+제품서버쪽 모듈 목록
	- express
		- js 웹 서버
	- path
		- 경로 관련 유틸
	- morgan
		- HTTP 요청을 기록하는 **미들웨어**
	- body-parser
		- 요청을 JSON으로 파싱할 때 사용되는 **미들웨어**
	- mongoose
		- mongo db ORM 툴
	- express-session
		- express 세션 관련 **미들웨어**
	- bcryptjs
		- 비번 같은 데이터의 암호화를 위한 해쉬 모듈
  	- axios
		- HTTP 클라이언트
	- react-addons-update
		- immutable helper
	- react-router
		- 클라이언트쪽 라우터
	- react-timeago
		- 몇 시간(분) 전인지 계산해서 보여주는 리액트 컴포넌트
	- redux
		- redux
	- react-redux
		- 뷰 레이어 바인딩
	- redux-thunk
		- redux에서 비동기 처리를 가능하게 해주는 **미들웨어**
	- react-addons-css-transition-group
		- 트랜지션을 돕는 모듈
  
### 글로벌 라이브러리 설치
```cli
sudo npm install -g babel-cli nodemon cross-env
```
- babel-cli
	- 콘솔 환경에서 babel을 사용 할 수 있게 해줍니다.
- nodemon
	- 코드를 수정하면 실시간으로 갱신됩니다.
- cross-env
	- 윈도우 / 리눅스 / OSX 에서 환경변수값을 설정합니다.

### 서버 코드 작성
- project-root/main.js
	```javascript
  import WebpackDevServer from 'webpack-dev-server';
  import webpack from 'webpack';

  const devPort = 4000;

  /*
      Express Codes 
  */


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
  
### 명령어 스크립트 셋팅
- project-root/package.json
	```javascript
  "clean": "rm -rf build public/bundle.js",
  "build": "babel server --out-dir build --presets=es2015 && webpack",
  "start": "cross-env NODE_ENV=production node ./build/main.js",
  "development": "cross-env NODE_ENV=development nodemon --exec babel-node --presets=es2015 ./server/main.js --watch server"
	```
  
### 개발서버 설정 파일 셋팅
- project-root/webpack.dev.config.js
	```javascript
  var webpack = require('webpack');
  
  module.exports = {

      /* webpack-dev-server를 콘솔이 아닌 자바스크립트로 실행 할 땐, 
      HotReloadingModule 를 사용하기 위해선 dev-server 클라이언트와 
      핫 모듈을 따로 entry 에 넣어주어야 합니다. */

      entry: [
          './src/index.js',
          'webpack-dev-server/client?http://0.0.0.0:4000', // 개발서버의 포트가 이 부분에 입력되어야 제대로 작동합니다
          'webpack/hot/only-dev-server'
      ],

      output: {
          path: '/', // public 이 아니고 /, 이렇게 하면 파일을 메모리에 저장하고 사용합니다
          filename: 'bundle.js'
      },

      // 개발서버 설정입니다
      devServer: {
          hot: true,
          filename: 'bundle.js',
          publicPath: '/',
          historyApiFallback: true,
          contentBase: './public',
          /* 모든 요청을 프록시로 돌려서 express의 응답을 받아오며,
          bundle 파일의 경우엔 우선권을 가져서 devserver 의 스크립트를 사용하게 됩니다 */
          proxy: {
              "**": "http://localhost:3000" // express 서버주소
          },
          stats: {
            // 콘솔 로그를 최소화 합니다
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
  
### 제품 서버 설정 파일 셋팅
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
  
### 
