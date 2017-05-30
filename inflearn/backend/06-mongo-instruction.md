### DB서버 실행
- 터미널에서 ```mongod``` 입력

### DB서버에 접속하기
- 새 터미널에서 ```mongo``` 입력

### DB 생성
- ```use mongodb-tutorial``` mongodb-turorial을 db라는 alias로 접근할 수 있게 함.
- ```show dbs``` db 목록에 아직 mongodb-tutorial db가 생성되어있지 않음을 확인하고,
- ```db.member.isert({'name': 'bsscco'});``` db에 document(JSON형태의 객체)를 넣으면 db가 생성됨.
- ```show dbs```를 다시 입력해보면 mongodb-tutorial이 생성되어있는 것을 확인할 수 있다.

### DB 제거
- ```db.dropDatabase()```

### collection 생성
- ```db.createCollection('member')``` 근데 collection을 미리 만들어둘 필요가 없음.
- ```db.member.isert(...``` 위에서 이렇게 document를 넣을 때 member collection이 같이 만들어지니까 이게 더 편리함.
- collection을 미리 만드는 이유는 ```db.createCollection(name, [option])```에서 option을 줄 수 있기 때문

### collection 보기
- ```show collections```

### collection 제거
- ```db.member.drop()```

### document 삽입
- ```db.member.insert({'name': 'bssscco'})```
- 여러 개 삽입 ```db.member.insert([{'name':'one'}, {'name':'two'}])```

### document 제거
- ```db.member.remove({'name': 'bsscco'})```
- 첫번째 인자 criteria에 만족하는 document가 여러 개일 때 하나만 제거하고 싶으면 ```db.member.remove({'name': 'bsscco'}, true)```를 실행한다. 두번 째 인자 justOne은 기본값이 false이다.

### document 보기
- ```db.member.find()```는 member collection의 모든 document를 찾아준다.
- ```db.member.find().pretty()```는 document 하나하나가 값이 많아서 보기 안 좋을 때 document마다 multi-line으로 보여준다.
- query를 주려면 ```db.member.find({'name': 'one'})```으로 입력한다.

- query에 비교 연산자 사용하기
	- ```db.number.find({'value', {$gt: 0, $lt:100, $nin: [12, 33]}})
- query 비교 연산자
	- $eq : 같다.
	- $neq : 같지 않다.
	- $gt : 크다.
	- $gte : 크거나 같다.
	- $lt : 작다.
	- $lte : 작거나 같다.
	- $in : 배열 속에 있다.
	- #nin : 배열 속에 없다.

- query에 논리 연산자 사용하기
	- ```db.post.find({$and: [{'title': 'good title'}, {'order', {$gt: 10}}]})
- query 논리 연산자
	- $and
	- $or
	- $not : 조건이 false이면 true, true이면 false
	- $nor : 모든 조건이 false일 때 true


### 
