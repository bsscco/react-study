### create-react-app
- 뭐지?
	- 페북에서 만든 React프로젝트 생성 도구
	
- 설치
	- ```npm install -g create-react-app```
	
- 프로젝트 생성
	- ```create-react-app redux-example```
	- ```npm install -save redux react-redux```

- 아톰 에디터 패키지 설치
	- 기존 jshint는 옵션 설정 같은 것, 새로운 문법 같은 것을 아직 제대로 지원하지 않는다.
	- create-react-app을 통해 만든 프로젝트는 eslint가 적용되어있으므로 아톰 에디터에서도 lint를 보려면 eslint 패키지를 설치해준다.
	![eslint-package](https://github.com/bsscco/react-study/blob/master/inflearn/redux/02-eshint-packages.png)	
	- react 패키지도 깔아주면 좋다.
	![eslint-package](https://github.com/bsscco/react-study/blob/master/inflearn/redux/02-react-package.png	)
	- 패키지 Setting에서 ```Enabled For All Javascript Files```를 활성화해주어야 .jsx 파일 말고도 .js 파일도 문법 지원을 받을 수 있다.
