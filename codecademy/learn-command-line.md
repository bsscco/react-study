# Navigation

# Manipulation 
- ```li -l``` column 설명 왼쪽부터
	- 접근 권한
	- hard link 개수
	- 소유자
	- 그룹
	- 크기
	- 마지막 수정 날짜
	- 파일(디렉토리)명
	
- ```cp * dest-path```
	- 디렉토리를 제외하고 파일들만 dest-path로 복사한다.

- ```cp m*.txt dest-path```
	- m으로 시작하면서 .txt로 끝나는 모든 파일들만 dest-path로 복사한다.
	
# Redirection
- ```echo```는 string 입력값을 standard input으로 받아들여 standard output으로
	- ```echo "Hello"``` 
	
- ```>```는 왼쪽 대상의 출력 스트림 방향을 오른쪽 대상으로
	- ```cat hello.txt > hi.txt```
	
- ```>>```는 왼쪽 대상의 출력 스트림 방향을 오른쪽 대상으로 (append모드)
	- ```cat hello.txt >> hi.txt```
	
- ```<```는 왼쪽 대상의 입력 스트림 방향을 오른쪽 대상으로
	- ```cat < hello.txt```
	
- ```cat```는 파일을 출력

- ```|```는 왼쪽 명령어의 출력을 오른쪽 명령어의 입력으로 넣어준다.
	- ```cat volcanoes.txt | wc | cat > islands.txt```는 cat --> wc --> cat --> > 으로 넘어간다.
	
- 기타 명령어	
	- ```sort```는 파일 내용을 정렬해서 standard output
	- ```uniq```는 파일 내용 중 중복 line 제거해서 standard output
	- ```grep```은 파일 내용 중 포함하는 line들을 standard output
		- ```-i``` 옵션은 대소문자를 구별하지 않게
		- ```-R``` 옵션은 Recursive. 디렉토리 안에 있는 모든 파일을 대상으로 검색해서 해당하는 파일들만 standard output
		- ```-Rl``` 옵션은 ```-R```에서 파일 이름만 stadard output
	- ```sed```는 파일 내용 중 일치하는 단어를 replace하고 해당하는 line들만 standard output
		- ```sed 's/snow/rain/'```은 해당하는 line 마다 처음 snow만 rain으로 replace
		- ```sed 's/snow/rain/g'```는 모든 snow를 rain으로 replace
		
# Environmemt
- 환경설정 수정하기
	 - ```vi ~/.bash_profile```로 수정하기. ```.bash_profile``` 파일은 환경설정을 저장하는 파일이다.
	 - ```source ~/.bash_profile```로 현재 세션에 변겨사항 바로 갱신하기 ```source``` 명령어는 현재 세션에 변경사항을 바로 갱신시킨다.
	 - 환경 설정 바꿔보기
	 ```cli
	 # in ~/.bash_profile
	 alias pd="pwd"
	 alias hy="history" # history 명령어를 hy로 쓸 수 있게
	 export USER="Jane Doe" # 환경변수 $USER를 정의(소문자로 이름지어도 대문자로만 사용할 수 있음)
	 export PS1=">> " # 미리 정의된 환경변수. 프롬프트 표시를 기존 $에서 >>으로 변경한다.
	 # 그 외에도 HOME, PATH 등의 미리 정의된 환경변수가 있음. PATH는 콜론(;)으로 나누어진 디렉토리들의 목록이 들어있다.
	 ```

- 기타 명령어
	- ```history```는 명령어 실행 기록을 보여준다.
	- ```env```는 환경변수들을 보여준다.

# [명령어 모음](https://www.codecademy.com/articles/command-line-commands)
