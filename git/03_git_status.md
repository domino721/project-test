# git status

```bash
$ git status
```

- working directory에서 파일의 상태
  - `untracked`: 깃이 관리하고 있지 않은 파일 (커밋에 들어간 적 없음)
    - 파일 생성 (new file)
  - `tracked`: 이전 커밋에 포함된 적 있는 파일
    - `modified`
      - `modified` / `deleted`
    - `unmodified`
      - 수정 X => git status에 등장하지 안ㄴㅎ음