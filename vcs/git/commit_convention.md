# Commit convention

## 커밋 메시지 구조

```
<type>[optional scope]: <description>
<BLANK LINE>
[optional body]
<BLANK LINE>
[optional footer(s)]
```

### Type

```
feat: 새로운 기능에 대한 커밋
fix: 버그 수정에 대한 커밋
build: 빌드 관련 파일 수정에 대한 커밋
ci: CI관련 설정 수정에 대한 커밋
docs: 문서 수정에 대한 커밋
style: 스타일 (코드 형식, 포멧 등: 비즈니스 로직에 변경 없는 경우)
refactor:  코드 리팩토링에 대한 커밋
test: 테스트 (테스트 코드 추가, 수정, 삭제: 비즈니스 로직에 변경 없는 경우)
chore: 그 외 자잘한 수정에 대한 커밋
```

### Subject

* 제목은 50자를 넘기지 않고, 마침표를 붙이지 않기
* 제목에는 commit 타입을 함께 작성
* 과거 시제를 사용하지 않고 명령조로 작성
* 제목과 본문은 한 줄 띄워 분리
* 제목의 첫 글자는 반드시 대문자
* 제목이나 본문에 이슈 번호(가 있다면) 붙이기

### Body

* 선택 사항이기에 모든 commit에 본문 내용을 작성할 필요는 없음
* 한 줄에 72자를 넘기면 안 됨
* 어떻게(How)보다 무엇을, 왜(What, Why)에 맞춰 작성
* 설명뿐만 아니라, commit의 이유를 작성할 때에도 사용

### Footer

* 선택 사항이므로 모든 commit에 꼬리말을 작성할 필요는 없음
* Issue tracker ID를 작성할 때 사용
* Issue tracker 키워드 외 See also 등

#### [키워드를 사용하여 pull request를 이슈에 연결](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)

Pull request의 설명이나 커밋 메시지에서 지원되는 키워드를 사용하여 풀 요청을 문제에 연결할 수 있습니다 (pull request는 기본 분기에 있어야 함을 참고).

* close
* closes
* closed
* fix
* fixes
* fixed
* resolve
* resolves
* resolved

## Example

```
feat: Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789
```

## Reference

* [Github commit 메세지 규칙](https://junhyunny.github.io/information/github/git-commit-message-rule/)
