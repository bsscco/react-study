# create-react-app
### 소개
- 이 도구는 뭐지?
	- 페북에서 만든 React프로젝트 생성 도구

### 프로젝트 셋팅
- 도구 설치
	- ```npm install -g create-react-app```
	
- 프로젝트 생성 및 의존성 설치
	- ```create-react-app redux-example```
	- ```npm install -save redux react-redux```
	
- 의존성 라이브러리 설명
	- ```redux``` : Redux 본체
	- ```react-redux``` : ```redux```만으로도 Redux 기능을 사용할 수 있지만, 뷰 레이어 바인딩을 위해서 ```react-redux```를 설치한다.

- 아톰 에디터 패키지 설치
	- 기존 jshint는 옵션 설정 같은 것, 새로운 문법 같은 것을 아직 제대로 지원하지 않는다.
	- create-react-app을 통해 만든 프로젝트는 eslint가 적용되어있으므로 아톰 에디터에서도 lint를 보려면 linter-eslint 패키지를 설치해준다.
	- 이제 jshint는 꺼준다.
	- Lint Javascript on the fly, using ESLint
	![eslint-package](https://github.com/bsscco/react-study/blob/master/inflearn/redux/02-eshint-packages.png)	
	- react 패키지도 깔아주면 좋다.
	- React.js(JSX) language support, indentation, snippets, auto completion, reformatting
	![react-package](https://github.com/bsscco/react-study/blob/master/inflearn/redux/02-react-package.png	)
	- 패키지 Setting에서 ```Enabled For All Javascript Files```를 활성화해주어야 .jsx 파일 말고도 .js 파일도 문법 지원을 받을 수 있다.
	![react-package-settings](https://github.com/bsscco/react-study/blob/master/inflearn/redux/02-react-package-settings.png)

- 아톰 에디터 스니펫 설정
	- [동영상에서 쓰인 스니펫 코드](https://gist.github.com/velopert/8f22cf0830e65f6de8ae99808c5b92f5)
	- Atom-Snippets 메뉴를 클릭해서 스니펫 코드를 넣고 저장한다.
	
- [Airbnb의 React 컨벤션 가이드 한글](https://github.com/apple77y/javascript/tree/master/react)

### 구조 셋팅
- 
