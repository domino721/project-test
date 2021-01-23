# Git 기초 문법

> Git은 분산형 버전관리시스템(DVCS)이다.

---

## Git 사전 준비

0. (윈도우의 경우: git bash를 설치한다.)
1. 로컬 설정

```bash
$ git config --global user.name 'domino721'
$ git config --global user.email ' minho0893@gmail.com'
```

- 처음 git을 설치하면, commit을 하는 작성자(author)를 설정해야 한다.
- email 정보는 github에 등록된 email을 설정하는 것을 추천.
- 설정된 내용을 확인하기 위해서는 아래의 명령어를 입력한다

```bash
$ git config --global -l
user.name=domino721
user.email= minho0893@gmail.com

```

- 오프라인 강의장에서 하는 경우 반드시 체크



## 기초흐름

> 작업 => add => commit
>
> 작업이 끝나면, 커밋할 파일을 모아(add) 커밋한다.(버전을 기록한다.)

### 0.저장소 설정

```bash
$ git init
Initialized empty Git repository in C:/Users/user/.git/
```

- git 저장소로 활용하기 위해서는 위의 명령어를 활용한다.
  - .git 폴더가 생성
  - `git status`로 현재 작업중인 브랜치 확인 (master)

### 1.add

> 커밋을 위한 파일 목록(status)

```bash
$ git add .
$ git add a.txt
$ git add a.txt b.txt
$ git add md-images/
```

- 실습

```bash
$ touch text.txt
```

### 2.commit

> 버전을 기록(스냅샷)

```bash
$ git commit -m '커밋 메시지'
[master (root-commit) abdfedb] first_commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 text.txt
```

  - 커밋 메시지는 현재 작업의 내용을 알 수 있도록 명확하게 진행한다.

  - 커밋 이력을 확인하기 위해서는 아래의 명령어를 활용한다.

    ``` bash
    $ git log
    ```

    - 추가 옵션

``` bash
$ git log -l
$ git log --oneline

$ git log --oneline -l
```

### 3.상태확인

> git 저장소의 현재 상태는 status로 확인하는 습관을 가지자.

``` bash
$ git status
```