### 불필요한 렌더링을 막는 방법
```javascript
shouldComponentUpdate(nextProps, nextState){
    	return (JSON.stringify(nextProps) != JSON.stringify(this.props));
    } 
```
[출처](https://velopert.com/1015https://velopert.com/1015)<br>
<br>

### props와 state가 바꼈을 때 라이프사이클
pros가 바꼈을 때 <br>
componentWillReceiveProps -> shouldComponentUpdate -> componentWillUpdate -> render -> componentDidUpdate <br>
<br>
state가 바꼈을 때 <br>
shouldComponentUpdate -> componentWillUpdate -> render -> componentDidUpdate<br>
[출처](https://velopert.com/1130)
