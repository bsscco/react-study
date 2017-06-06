### 초기 프로젝트 클론
```cli
git clone https://github.com/velopert/react-codelab-project.git
cd react-codelab-project #프로젝트로 이동
git branch -r #원격 브랜치 목록 보기
git checkout step00 #첫번재 브랜치로 전환
```

### 프로젝트 라이브러리 설치
```cli
npm install #프로젝트에 필요한 클라이언트쪽 npm 모듈들을 설치합니다. (babel-core, babel-loader, babel-preset-es2015, babel-preset-react, react, react-dom, react-hot-loader, webpack, webpack-dev-server)

npm install --save express body-parser #서버쪽 npm 모듈들을 설치합니다.
```
- 로컬 라이브러리 목록(in package.json)
  ```javascript
  ...
  "dependencies": {
      "body-parser": "^1.17.2",
      "express": "^4.15.3",
      "react": "^15.2.1",
      "react-dom": "^15.2.1"
    },
  "devDependencies": {
    "babel-core": "^6.9.1",
    "babel-loader": "^6.2.4",
    "babel-preset-es2015": "^6.9.0",
    "babel-preset-react": "^6.5.0",
    "react-hot-loader": "^1.3.0",
    "webpack": "^1.13.1",
    "webpack-dev-server": "^1.14.1"
  }
  ...
  ```

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
```
