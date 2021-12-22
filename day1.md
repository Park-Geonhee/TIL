# Git & Github

1. Git
   - 분산 버전 관리 프로그램
   - 개인 컴퓨터(인터넷 연결 없이 가능)
2. Github
   - 분산 버전 관리 프로그램
   - 인터넷 연결 필요
   - 일종의 포트폴리오 역할도 가능

# CLI

1. CLI란?
   - Command Line Interface
   - 터미널을 통해 사용자와 컴퓨터가 상호 작용하는 방식
2. GUI 와 비교
   - GUI : Graphic User Interface
   - 그래픽을 통해 사용자와 컴퓨터가 상호 작용하는 방식
   - 
3. 명령어
   - touch : 파일을 생성
   - mkdir : 폴더를 생성(make directory)
   - ls : 현재 작업중인 디렉토리의 폴더/파일목록을 보여줌(list segments)
   - mv : 폴더/파일을 다른 폴더 내로 이동하거나 이름을 변경(move)
   - cd : 디렉토리를 변경하는 명령어(change directory)
   - rm : 폴더/파일을 지우는 명령어(remove)

# VS Code

Visual Studio Code 를 설치하고, 기본 터미널을 `powershell > Git Bash` 로 변경하였다.



# 마크다운

문서를 정리할 때 쓸 수 있는 마크다운 기능등을 연습해 본다.

# 제목1

## 제목2

### 제목3

#### 제목4

##### 제목5

###### 제목6



목록

순서가 없는 목록

- 목록1
- 목록2
- 목록3
- 과일
  - 수박
  - 참외

`-, *, +` 다 가능(편한거쓰기)

순서가 있는 목록

1. 목록1
2. 목록2
3. 목록3
4. 과일
   1. 바나나
   2. 참외

---

강조(스타일링)

1. 기울임(이탤릭체) : *글자* , _글자_ 

2. 굵게(볼드체) : **글자** , __글자__
3. 취소선 : ~~글자~~

---

코드 블록

인라인 코드(=한줄)

파이썬에는 `print("Hello World!")` 라고 쓸 수 있습니다.



블록 코드(=여러줄)

```python
for i in range(1,101):
	print(i)
```

---

수평선

`-, *, _` 3번 연속 작성

---

***

___

text 원문 보기 : `ctrl`+`/` 키 동시 입력

---

표(table)

| 동물   | 다리개수 | 종     |
| ------ | -------- | ------ |
| 사자   | 4개      | 포유류 |
| 원숭이 | 2개      | 포유류 |
| 앵무새 | 2개      | 조류   |

---

문자열 이스케이프

\'print()` >> \ 사용



# Git 활용하기

1. Git 을 이용한 버전관리 작성자 등록(최초 1번)
   - `git config --global user.name (name)` 
   - `git config --global user.email (email)`
   - `git config --global --list` : 버전 확인
2. 어떤 폴더를 Git으로 버전 관리를 하겠다
   - `git init`
3. Working Directory -> Staging Area
   - `git add a.txt`
4. Staging Area -> Commits(버전)
   - `git commit -m "first commit"`
