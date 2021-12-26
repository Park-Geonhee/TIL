# Git 특강 2일차

## .gitignore

### .gitignore 이란?
- 특정 파일 혹은 폴더에 대해 git이 버전 관리를 하지 못하도록 함
- 다음과 같은 내용을 `.gitignore`에 작성
  - 민감한 정보
  - OS에서 활용되는 파일
  - IDE(통합 개발 환경) 혹은 Text editor 등에서 활용되는 파일
  - 개발 언어 혹은 프레임워크에서 사용되는 파일

### .gitignore 작성시 주의사항
- 반드시 이름을 `.gitignore` 로 작성. 앞의 점(.)은 숨김파일을 의미
- `.gitignore` 파일은 `.git` 폴더와 동일한 위치에 생성
- 제외하고 싶은 파일은 반드시 `git add` 전에 `.gitignore`에 작성

### .gitignore 쉽게 작성하기
- `https://gitignore.ie/` 에서 현재 개발환경을 체크하면 `.gitignore` 파일들을 정리해 줌

### .gitignore 패턴 예시

- 확장자가 txt인 파일 무시 : `*.txt`
- 느낌표를 사용할 경우 무시되지 않음 : `!test.txt`
- 현재 디렉토리에 있는 TODO 파일만을 무시, 다른 디렉토리의 TODO는 무시하지 않음 : `/TODO`
- bulid 디렉토리에 있는 모든 파일은 무시 : `bulid/`
- folder 디렉토리 아래의 모든 .pdf 파일을 무시 : `folder/**/*.pdf`

## 원격저장소 Github

### git clone
- 원격 저장소의 커밋 내역을 모두 가져와 로컬 저장소를 생성
- `git clone` 은 내 컴퓨터에 저장소가 없을 때 최초 사용
- `git clone <원격 저장소 주소>` 의 형태로 작성

### git pull
- 원격 저장소의 변경 사항을 가져와서 로컬 저장소를 업데이트
- 원격 저장소와 로컬 저장소의 내용이 완전히 일치하면 변화 없음
- `git pull <저장소 이름> <브랜치 이름>` 의 형태로 작성

