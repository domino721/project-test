# 원격저장소 push 시 오류

```bash
$ git push origin master
To https://github.com/Sekeun/bigdata.git
 ! [rejected]        master -> master (fetch first)
error: 레퍼런스를 'https://github.com/Sekeun/bigdata.git'에 푸시하는데 실패했습니다
# 거절됨(rejected)
# 원격 저장소의 작업(커밋)이 로컬에 있음
힌트: 리모트에 로컬에 없는 사항이 들어 있으므로 업데이트가
힌트: 거부되었습니다. 이 상황은 보통 또 다른 저장소에서 같은
힌트: 저장소로 푸시할 때 발생합니다.  푸시하기 전에
힌트: ('git pull ...' 등 명령으로) 리모트 변경 사항을 먼저
힌트: 포함해야 합니다.
힌트: 자세한 정보는 'git push --help'의 "Note about fast-forwards' 부분을
힌트: 참고하십시오.
```

- 원격 저장소와 로컬 저장소의 커밋 히스토리를 확인하고 아래의 명령어를 입력한다.

  ```bash
  $ git pull origin master
  warning: Pulling without specifying how to reconcile divergent branches is
  discouraged. You can squelch this message by running one of the following
  commands sometime before your next pull:
  
    git config pull.rebase false  # merge (the default strategy)
    git config pull.rebase true   # rebase
    git config pull.ff only       # fast-forward only
  
  You can replace "git config" with "git config --global" to set a default
  preference for all repositories. You can also pass --rebase, --no-rebase,
  or --ff-only on the command line to override the configured default per
  invocation.
  
  remote: Enumerating objects: 5, done.
  remote: Counting objects: 100% (5/5), done.
  remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
  오브젝트 묶음 푸는 중: 100% (3/3), 645 bytes | 215.00 KiB/s, 완료.
  https://github.com/Sekeun/bigdata URL에서
   * branch            master     -> FETCH_HEAD
     a6c9a52..9148ea3  master     -> origin/master
  Merge made by the 'recursive' strategy.
   README.md | 2 +-
  ```

  - vim 편집기 창이 popup 될 것.
    - `esc` + `:wq` + enter
      - w : write (저장)
      - q : quit (나가기)

- log를 확인한다.



- log를 확인한다.

```bash
$ git log --oneline
# vim 편집기가 뜬 이유 => 합쳐졌다는 사실을 커밋으로 남김

# 로컬 작업한 것

# 원격 저장소에서 작업한 것
```

- 다시 push를 한다.

```bash
$ git push origin master
```

- https://vim-adventures.com/