# Local commit 취소

```bash
$ git commit -m "Something terribly misguided" # (0: Your Accident)
$ git reset HEAD~                              # (1)
[ edit files as necessary ]                    # (2)
$ git add .                                    # (3)
$ git commit -c ORIG_HEAD                      # (4)
```

#### 1. Undo

Git Reset은 실행 취소를 담당하는 명령입니다. 작업 트리 (디스크에 파일의 상태)를 그대로 두면서 마지막 커밋을 취소합니다. 다시 커밋하기 전에 다시 추가해야합니다.

#### 2. 수정

잘못된 working tree 파일들을 수정

#### 3. 스테이징

Git 새로운 커밋에 포함시키려는 모든 것을 추가하십시오.

#### 4. 커밋

기존 커밋 메시지를 재사용하면서 변경 사항을 커밋하십시오. `reset`은 이전 헤드를 `.git/orig_head`로 복사했습니다.&#x20;

`commit` 명령어에 `-c ORIG_HEAD` 옵션 사용 시 편집기를 열며, 처음에는 이전 커밋의 로그 메시지를 포함하여 편집 할 수 있습니다. 메시지를 편집 할 필요가 없으면 `-C` 옵션을 사용할 수 있습니다.

> [https://stackoverflow.com/questions/927358/how-do-i-undo-the-most-recent-local-commits-in-git](https://stackoverflow.com/questions/927358/how-do-i-undo-the-most-recent-local-commits-in-git)
