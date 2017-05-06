# [part1.](https://www.codecademy.com/articles/react-setup-i)
- Babel
	- Babel이란?
		- JSX를 Javascript로 컴파일 하는 Javascript 컴파일러이다. ```transformation```들 중 하나다. (npm 모듈)
	- Babel 설치하기
		- ```Babel```의 npm 모듈 이름은 ```babel-core```
		- react, react-dom과 달리 ```npm install --save-dev babel-core```로 설치한다. -dev옵션이 포함되는 것이 비교되는 점이다. production에서는 이 변형이 필요하지 않기 때문이다.
		- 설치되어야 할 2가지 모듈이 더 있다. ```babel-loader```와 ```babel-preset-react```이다. ```babel-loader```는 아래에서 설명할 Webpack에 ```Babel```을 올리기 위한 모듈이다. ```babel-preset-react```는 ```Babel```에서 React 프리셋을 사용하게 하기 위한 모듈이다.
	- Babel 설정하기
		- Babel configuration 파일(```.babelrc```)을 프로젝트 루트디렉토리에 작성해야 한다. 내용은 ```{presets: ["react"]}```을 넣는다.
	
- Webpack
	- Webpack이란?
		- JSX to Javascript는 React에서 수행되는 많은 ```transformation```들 중 하나다. 이 변형들을 옳바른 순서에 맞게 수행시킬 수 있는 ```transformation manage```가 필요한데, 대표적인 도구가 ```Webpack```이다. (npm 모듈)
	- Webpack 설치하기
		- Babel과 같이 development 모드에서만 동작해야 하므로 ```npm install --save-dev webpack```으로 설치한다.
		- 설치되어야 할 2가지 추가 모듈이 더 있다. ```webpack-dev-server```와 ```html-webpack-plugin```이다.
	- Webpack 설정하기
		- ```webpack.config.js``` 파일을 프로젝트 루트디렉토리에 작성해야 한다.
		- 우선 변형해야 하는 js파일을 명시해야 하는데, outermost에 있는 React 컴포넌트를 사용하는 js파일이 해당된다. outermost 컴포넌트 아래에 있는 모든 컴포넌트들은 자동으로 변형 대상에 포함된다.
		```javascript 
		module.exports = {
			entry: __dirname + '/app/index.js'	
		};
		```
		```Node.js```에서 __dirname이란 현재 실행 중인 파일을 의미한다.
		- 다음으로 로더 목록을 명시한다. 로더마다 객체{}로 표현할 수 있고, 각 객체{}에는 몇가지 속성이 들어간다. test는 영향받을 대상을 가리킨다. include/exclude는 포함시키거나 제외시킬 대상을 가리킨다. loader는 사용할 ```transformation``` 로더를 가리킨다. output은 변형된 js코드를 어디에 담을지를 가리킨다.
		```javascript
		module.exports = {
			entry: __dirname + '/app/index.js',
			loaders: [
				{
					test: /\.js$/, // 모든 js파일이 영향을 받도록 한다.
					exclude: /node_modules/, // 많은 js파일을 포함하는 node_modules 디렉토리는 제외한다.
					loader: 'babel-loader', // babel-loader를 사용한다.
					output: {
						filename: 'tansformed.js',
						path: __dirname + '/build'
					}
				}
			]
		}
		```
		

[part2.](https://www.codecademy.com/articles/react-setup-ii)
[part3.](https://www.codecademy.com/articles/react-setup-iii)
[part4.](https://www.codecademy.com/articles/react-setup-iv)
[part5.](https://www.codecademy.com/articles/react-setup-v)
