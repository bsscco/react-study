# Javascript

## 간단 소개
- Java-like 문법

## 개념
- Number
- String
	- string.length
- Math.random()
- typeof
- == 그리고 ===
- prompt()
- false
	- ''
	- undefined
	- null
	- NaN
	- 0
	- []
	- {}
- document.write()
- function
	- function foo() {}
	- var foo = function() {}
	- 객체로서의 함수
	- 비동기 처리 시 콜백으로서의 함수
- [] Array
	- array.length
	- array.push()
	- array.concat()
	- array.unshift()
	- array.shift()
	- array.splice()
	- array.pop()
	- array.sort()
	- array.reverse()
	- for(idx in array)
- {} Object(=Dictionary)
	- obj['property']
	- obj.property
	- for(key in obj)
- 모듈화
	- 관심사의 분리
	- 코드 재활용
	- 브라우저 캐시
- 호스트 환경이란
- 라이브러리
- 튜토리얼
	- 문법에 대한 설명
- 레퍼런스
	- 문법 사전
- 정규표현식
	- 컴파일 : 검출을 원하는 패턴을 만드는 일
	- pattern = /\d*/
	- pattern = new RegExp('\d*')
	- pattern.exec('123-456')
	- pattern.test('123-456')
	- '123-456'.match(/\d*/)
	- '123-456'.replace(/\d*/, '999') : only first match element
- var
	- 전역변수가 있음 -> 함수 안에서 var와 함께 선언 -> 지역변수
	- 전역변수가 있음 -> 함수 안에서 var 없이 선언 -> 전역변수
	- 전역변수가 없음 -> 함수 안에서 var와 함께 선언 -> 지역변수
	- 전역변수가 없음 -> 함수 안에서 var 없이 선언 -> 전역변수
	- 변수를 선언할 땐 되도록 var를 붙여야 전역변수와의 충돌을 예방할 수 있다.
- 클로저
	- 내부함수에서 외부함수의 지역변수를 사용할 수 있다.
- function
	- arguments
		- 함수에 실제로 들어온 모든 인자의 정보
		- function.length : 함수에서 정의된 인자수
	- fuction.apply(context, arg1, arg2, ...)
		- context의 속성으로 function을 지정해서 호출한 뒤에 속성에서 fuction을 제거한다.
	- function.call(arg1, arg2, ...)
		- function()과 같다.
- 객체
	- property
	- method
	- 생성자 함수
		```
		function Person(name) {
			this.name = name;
			this.instroduce = function() {
				return 'My name is ' + this.name;		
			}
		}
		var person = new Person('수키')
		```
		
- window
	- 전역객체
	- 전역객체의 이름과 프로퍼티, 메소드들은 호스트환경에 따라서 다르다.

- this
	- 이 함수를 감싸는 객체를 가리킨다.
	- apply(context)를 통해 들어왔다면 context를 가리킨다.
- prototype
	- 생성자 함수 간 상속을 위해 사용한다.
	- Sub.prototype = new Super()
- 내장 객체(=내장 생성자 함수)
	- Object
		- Object객체를 확장(prototype.contain = ....)하면 모든 객체를 확장할 수 있다.
	- Function
	- Array
	- String
	- Boolean
	- Number
	- Math
	- Date
	- RegExp
- primitive type
	- 원시 타입은 확장할 수도, 속성을 추가할 수도 없다.
	- number
	- string
	- boolean
	- null
	- undefined
- wrapper 객체
	- String
	- Number
	- Boolean
	
## 재진입하기
https://developer.mozilla.org/ko/docs/A_re-introduction_to_JavaScript


# TicTacToe 주요 설명

## React 개념

### props
- 바뀌지 않는 상수 속성
- 부모 컴포넌트에서 -> 자식 컴포넌트로 전달한다.
- props로 컴포넌트가 셋팅되도록 만들면 컴포넌트의 재활용도가 높아지며, 자식 컴포넌트 간에 데이터를 싱크 시킬 수 있다.

### state
- 바뀌는 상태 속성
- 컴포넌트 안에 캡슐화 되어있어서 부모 컴포넌트가 접근할 수 없다.
- state 변경 시 immutable이 좋은 이유
  1. 상태를 복사해서 변경하기 때문에 추적이 가능한 구조를 만들 수 있다.
  2. 상태 복사본과 원본의 변경점만 비교하기 때문에 어떤 부분만 렌더링 할지 효율적으로 결정할 수 있다.
  
### key
- React에 의해 다루어지는 특별한 프로퍼티
- props는 아님. this.props.key로 접근할 수 없다.
- 리스트 요소의 UI 갱신이 필요할 때 React는 key를 사용해 자식 컴포넌트들을 구별한다.
- key가 제거되면 컴포넌트도 제거되고, key가 생성되면 컴포넌트도 생성됩니다. key의 값을 바꾸면 컴포넌트는 새로운 상태로 재생성 된다.
- 만약 리스트에서 자식 컴포넌트들에게 key를 설정하지 않으면 React가 array index를 key로써 설정할 겁니다. 
	- array index를 사용하게 하는 것은 좋은 선택이 아닙니다. 리스트 내 아이템을 추가/제거/재정렬을 여러 번 하다보면 헷갈리기 때문입니다.(맞나?)
	- key는 글로벌하게 unique 할 필요는 없고, 형제 컴포넌트 간에만 unique 하면 됩니다.

## 게임 소개
- 플레이어 O, X가 번갈아가며 버튼을 오픈하는 게임
- 가로, 세로, 대각선을 먼저 오픈하는 플레이어가 승리

## 스탭
- [스타터 코드](https://codepen.io/gaearon/pen/JNYBEZ?editors=0010)
- JS파일만 봅시다.
- props
	- 부모 컴포넌트인 Board로부터 자식 컴포넌트인 Square들에게 속성을 부여해서 속성에 따라 다르게 보여지도록 해봅시다.
	- in Board class
	```javascript
	renderSquare(i) {
	    return <Square value={i}/>;
	  }
	```
	- in Square class
	```javascript
	render() {
	    return (
	      <button className="square">
		{this.props.value}
	      </button>
	    );
	  }
	```
	- 부모 컴포넌트는 자식 컴포넌트에게 속성을 부여할 수 있습니다.
	- 전달받은 속성은 자식 컴포넌트의 UI를 동적으로 만들어주는 역할을 합니다.
- state
	- Square를 클릭하면 X로 표시되도록 해봅시다.
	- in Square class
	```javascript
	  constructor(){
	    super();
	    this.state = {
	      value: null,
	    };
	  }
	  render() {
	    return (
	      <button className="square" onClick={() => this.setState({value:'X'})}>
		{this.state.value}
	      </button>
	    );
	  }
	```
	- this.state의 값(상태)들을 바꾸면 값들을 사용하는 부분들이 자동으로 갱신됩니다.
- props와 state 혼용
	- 이제 TicTacToe를 만들어봅시다.
	- 이전 스탭과 똑같이 Square를 클릭하면 X가 표시되도록 할 거지만 누가 플레이어인지, 게임의 위너가 누구인지 체크하는 로직과 관련 데이터를 9개의 Square가 각각 다 가지고 있을 필요는 없기 때문에 Square를 관리하는 Board에 넣습니다.
	- in Board class
	```javascript
	  constructor(){
	    super();
	    this.state = {
	      squares : Array(9).fill(null)
	    }
	  }
	  renderSquare(i) {
	    return <Square value={this.state.squares[i]} onClick={() => this.handleClick(i)} />;
	  }
	  handleClick(i) {
	    const squares = this.state.squares.slice();
	    squares[i] = 'X';
	    this.setState({squares: squares});
	  }
	```
	- in Square class
	```javascript
	  render() {
	    return (
	      <button className="square" onClick={() => this.props.onClick()}>
		{this.props.value}
	      </button>
	    );
	  }
	```
	- 이제 Square를 클릭했을 때 Board에서 Sqaure의 상태를 바꿉니다. Sqaure의 UI가 자동 갱신되는데, Board의 state값을 Square가 props로 내려받아 사용하기 때문입니다. this.state값이 바뀌면 이 값을 사용하는 모든 UI가 자동 갱신됩니다.
	- 다음으로 플레이어 턴을 바꾸는 코드를 추가합시다.
	- in Board class
	```javascript
  	  constructor(){
	    super();
	    this.state = {
	      squares : Array(9).fill(null),
	      xIsNext: true,
	    }
	  }
	  handleClick(i) {
	    const squares = this.state.squares.slice();
	    squares[i] = this.state.xIsNext ? 'X' : 'O';
	    this.setState({
	      squares: squares,
	      xIsNext: !this.state.xIsNext,
	    });
	  }
	```
	- 다음으로 위너를 체크하는 코드와 누군가 이기면 더 이상 Square를 오픈할 수 없도록 코드를 추가합시다.
	- in Board class
	```javascript
	  handleClick(i) {
	    const squares = this.state.squares.slice();
	    if (calculateWinner(squares) || squares[i]) {
	      return;
	    }
	    squares[i] = this.state.xIsNext ? 'X' : 'O';
	    this.setState({
	      squares: squares,
	      xIsNext: !this.state.xIsNext,
	    });
	  }
	  
  	  render() {
	    const winner = calculateWinner(this.state.squares);
	      let status;
	      if (winner) {
		status = 'Winner: ' + winner;
	      } else {
		status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
	      }
	    return (
	      <div>
		<div className="status">{status}</div>
		<div className="board-row">
		  {this.renderSquare(0)}
		  {this.renderSquare(1)}
		  {this.renderSquare(2)}
		</div>
		<div className="board-row">
		  {this.renderSquare(3)}
		  {this.renderSquare(4)}
		  {this.renderSquare(5)}
		</div>
		<div className="board-row">
		  {this.renderSquare(6)}
		  {this.renderSquare(7)}
		  {this.renderSquare(8)}
		</div>
	      </div>
	    );
	  }
	```
	- 마지막으로 게임 히스토리를 기억하도록 코드를 추가해봅시다.
	- Board의 상태를 히스토리로 관리할 것이기 때문에 모든 데이터를 Board의 부모 컴포넌트인 Game으로 올립니다.
	```javascript
	class Square extends React.Component {
	  render() {
	    return (
	      <button className="square" onClick={() => this.props.onClick()}>
		{this.props.value}
	      </button>
	    );
	  }
	}

	class Board extends React.Component {
	  renderSquare(i) {
	    return <Square key={i} value={this.props.squares[i]} onClick={()=>this.props.onClick(i)}/>;
	  }

	  render() {
	    return (
	      <div>
		<div className="board-row">
		  {this.renderSquare(0)}
		  {this.renderSquare(1)}
		  {this.renderSquare(2)}
		</div>
		<div className="board-row">
		  {this.renderSquare(3)}
		  {this.renderSquare(4)}
		  {this.renderSquare(5)}
		</div>
		<div className="board-row">
		  {this.renderSquare(6)}
		  {this.renderSquare(7)}
		  {this.renderSquare(8)}
		</div>
	      </div>
	    );
	  }
	}

	class Game extends React.Component {
	  constructor() {
	    super();
	    this.state = {
	      stepNumber: 0,
	      history: [{
		squares: Array(9).fill(null)
	      }],
	      xIsNext: true,
	    };
	  }
	  handleClick(i) {
	    const history = this.state.history.slice(0, this.state.stepNumber + 1);
	    const current = history[this.state.stepNumber];
	    const squares = current.squares.slice();
	    if (calculateWinner(squares) || squares[i]) {
	      return;
	    }
	    squares[i] = this.state.xIsNext ? 'X' : 'O';
	    this.setState({
	      stepNumber: this.state.stepNumber + 1,
	      history: history.concat([{
		squares: squares
	      }]),
	      xIsNext: !this.state.xIsNext,
	    });
	  }
	  jumpTo(step) {
	    this.setState({
	      stepNumber: step,
	      xIsNext: (step % 2) ? false : true,
	    });
	  }
	  render() {
	    const history = this.state.history;
	    const current = history[this.state.stepNumber];
	    const winner = calculateWinner(current.squares);

	    let status;
	    if (winner) {
	      status = 'Winner: ' + winner;
	    } else {
	      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
	    }

	    const moves = history.map((step, move) => {
	      const desc = move ? 'Move #' + move : 'Game start';
	      return (
		<li>
		  <a href="#" key={move} onClick={() => this.jumpTo(move)}>{desc}</a>
		</li>
	      );
	    });

	    return (
	      <div className="game">
		<div className="game-board">
		  <Board
		      squares={current.squares}
		      onClick={(i) => this.handleClick(i)}
		    />
		</div>
		<div className="game-info">
		  <div>{status}</div>
		  <ol>{moves}</ol>
		</div>
	      </div>
	    );
	  }
	}
	```
	

## 튜토리얼을 마치고 느낀 점
- UI 상태 갱신이 자동화 되어있어서 사고가 단순해지고 UI 제작이 매우 쉽다.
