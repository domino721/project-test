# Git 기초 문법

> Git은 분산형 버전관리시스템(DVCS)이다.

---

## Git 사전 준비

0. (윈도우의 경우: git bash를 설치한다.)
1. 로컬 설정

```bash
$ git config --global user.name 'Sekeun'
$ git config --global user.email 'dhtprms9090@gmail.com'
```

- 처음 git을 설치하면, commit을 하는 작성자(author)를 설정해야 한다.
- email 정보는 github에 등록된 email을 설정하는 것을 추천.
- 설정된 내용을 확인하기 위해서는 아래의 명령어를 입력한다.

```bash
$ git config --global -l
user.name=Sekeun
user.email=dhtprms9090@gmail.com
```

- 오프라인 강의장에서 하는 경우 반드시 체크



## 기초흐름

> 작업 => add => commit
>
> 작업이 끝나면, 커밋할 파일을 모아(add) 커밋한다.(버전을 기록한다.)

### 0.  저장소 설정

```bash
$ git init
/Users/sekeun/Desktop/정리/.git/ 안의 빈 깃 저장소를 다시 초기화했습니다
```

- git 저장소로 활용하기 위해서는 위의 명령어를 활용한다.
  - .git 폴더가 생성
  - (master) 로 현재 작업중인 브랜치 확인

### 1.  add

> 커밋을 위한 파일 목록(staging area)

```bash
$ git add .						# 현재 디렉토리
$ git add a.txt				# 특정 파일
$ git add a.txt b.txt # 여러 파일
$ git add md-images/ 	# 특정 폴더
```

* 실습

```bash
$ touch text.text
```

- add 전 모습

```bash
$ git status
현재 브랜치 master

아직 커밋이 없습니다
# 트래킹이 되지 않는 파일 : WD O
추적하지 않는 파일:
	# git add 명령어를 사용!
	# 커밋이 될 것에 포함시키기 위하여.
  (커밋할 사항에 포함하려면 "git add <파일>..."을 사용하십시오)
	text.txt
# 맨 마지막 줄: 총 정리
# nothing added to commit / 커밋하기 위해 추가된 것 x: staging area X
# untracked files present : WD O
커밋할 사항을 추가하지 않았지만 추적하지 않는 파일이 있습니다 (추적하려면 "git
add"를 사용하십시오)
```

- add 후 모습

```bash
$ git add.
$ git status
현재 브랜치 master

아직 커밋이 없습니다
# 커밋이 될 변경사항 : SA O
커밋할 변경 사항:
  (스테이지 해제하려면 "git rm --cached <파일>..."을 사용하십시오)
# 새 파일: test.txt
	새 파일:       text.txt
```

### 2.  commit

> 버전을 기록 (스냅샷)

```bash
$ git commit -m '커밋 메시지'
[master (최상위-커밋) b172e72] 커밋 메시지
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 text.txt
```

- 커밋 메시지는 현재 작업의 내용을 알 수 있도록 명확하게 작성한다.

- 커밋 이력을 확인하기 위해서는 아래의 명령어를 활용한다.

  ```bash
  $ git log
  commit b172e72536267013e71597edbd482ecad5aadd49 (HEAD -> master)
  Author: Sekeun <dhtprms9090@gmail.com>
  Date:   Tue Dec 22 14:36:23 2020 +0900
  
      커밋 메시지
  ```

  - 추가 옵션

```bash
$ git log -l
$ git log --oneline
b172e72 (HEAD -> master) 커밋 메시지
$ git log --oneline -l
```

### 3. 상태확인

> git 저장소의 현재 상태는 status로 확인하는 습관을 가지자.

```bash
$ git status
현재 브랜치 master
커밋할 사항 없음, 작업 폴더 깨끗함
```
