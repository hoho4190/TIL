# 이전 commit 메시지 수정

## 아직 커밋이 local 에 있을 때
### 가장 최근의 commit 수정
```bash
$ git commit --amend -m "바꿀 메시지"

# or 편집기에서 메시지 수정 후 저장
$ git commit --amend
```

### 더 오래된 commit 수정 or 한 번에 여러 commit 수정
```bash
# 로그 보기 - 어떤 커밋을 수정할지 확인
$ git log

# -i 옵션은 대화형으로 수행
# HEAD~3은 최근 3개 커밋 불러옴
$ git rebase -i HEAD~3
```
1. 편집기에서 수정하고 싶은 커밋 옆의 `pick`이라는 문구를 `reword`로 바꿔 주고 저장
2. `reword`로 바꾼 커밋들이 순서대로 편집기로 열림
3. 메시지를 수정하고 저장

## 이미 커밋을 push 해 remote 에 올린 상황일 때
local에 있을 때와 똑같이 수정 후 강제로 `push`해야 함
```bash
$ git push -f
```