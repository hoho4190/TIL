# 특정 commit과 history 내역을 삭제
- reset --mixed 옵션을 이용하여 현재 working directory를 유지한 채 특정 커밋으로 이동
- 특정 커밋 이후의 커밋들은 사라짐
- push -f 옵션으로 푸시
```bash
# 특정 커밋으로 리셋
$ git reset --mixed REVISION_NUMBER

# 커밋 후 푸시
$ git push -f
```

## Reference
- [★ reset 자세히 알아보기](https://antilog.tistory.com/29?category=734368)
- [[초보용] Git 되돌리기( Reset, Revert )](https://www.devpools.kr/2017/02/05/%EC%B4%88%EB%B3%B4%EC%9A%A9-git-%EB%90%98%EB%8F%8C%EB%A6%AC%EA%B8%B0-reset-revert/)
- [깃허브에서 특정 commit 과 history내역을 삭제할수 있나요?](https://okky.kr/article/374790)