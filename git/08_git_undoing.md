# git 추가 명령어

## undoing

### 1. WD 작업내용 복구

> 고양이가 작업 내용을 지웠다면

```bash
$ git status
On branch master
Changes not staged for commit:
  # WD => Staging area .. 
  (use "git add <file>..." to update what will be committed)
  # WD의 변경사항을 버리기 위해서는... 
  (use "git restore <file>..." to discard changes in working directory)
        modified:   3.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

```bash
$ git resotre 3.txt
$ git status
On branch master
nothing to commit, working tree clean
```

### 2. staging area 취소 (unstage)

```bash
$ touch 2.txt
$ git add .
$ git status
On branch master
Changes to be committed:
	# hint!
  (use "git restore --staged <file>..." to unstage)
        new file:   2.txt
```

```bash
$ git restore --staged 2.txt
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        2.txt

nothing added to commit but untracked files present (use "git add" to track)
```

3. commit 메시지 변경

> 주의: commit 메시지를 변경하면 해시값이 바뀌므로 공개된 저장소에 push가 된 경우 절대 변경 금지

```bash
$ git commit -m 'Add 3.txt'
[master 851bb18] Add 3.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 2.txt
```

```bash
$ git commit --amend
```

- commit 메시지를 편집할 수 있는 창이 뜸.
  - vim 편집기
  - `i` 키를 눌러 편집모드로 전환해 내용을 수정
  - `esc`+`:wq` 로 나오기

```bash
$ git commit --amend
[master e4ff93e] Add 2.txt
 Date: Wed Dec 23 17:16:11 2020 +0900
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 2.txt
```

## revert vs reset

```bash
$ git log --oneline
e4ff93e (HEAD -> master) Add 2.txt
739161d 개발완료
2c827ac ==
a522d2e Add 2.txt
ce72fc0 Add 1.txt
```

### 1.  revert

```bash
$ git revert e4ff93e
Removing 2.txt
[master 1f5a2ce] Revert "Add 2.txt"
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 2.txt
 
$ git log --oneline
# revert 커밋 발생!!
1f5a2ce (HEAD -> master) Revert "Add 2.txt"
e4ff93e Add 2.txt
739161d 개발완료
2c827ac ==
a522d2e Add 2.txt
ce72fc0 Add 1.txt
```

### 2. reset

```bash
$ git reset --hard 739161d
HEAD is now at 739161d 개발완료

$ git log --oneline
739161d (HEAD -> master) 개발완료
2c827ac ==
a522d2e Add 2.txt
ce72fc0 Add 1.txt
```

- option
  - `--mixed`: 기본 옵션. 해당 commit 이후 변경사항을 staging area 에 보관
  - `--hard`: 해당 커밋 이후 내용을 모두 삭제
    - 이 명령어를 사용할 때 주의. 모든 작업 내용이 사라짐
  - `--sort`: 해당 커밋 이후 변경사항 및 working directory 보관