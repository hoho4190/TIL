# Branch 보호 규칙

`GitHub Repository > Settings > Code and automation > Branches`에서 규칙을 추가할 수 있음

`main` 브런치에 아래와 같이 설정하면 좋음


- [X] Require a pull request before merging
  - [X] Require approvals
  > 보호되고 있는 브런치에 직접 push 할 수 없음
  > > 병합 전에 필요한 승인 인원을 설정할 수 있음

- [X] Require status checks to pass before merging
  - [X] Require branches to be up to date before merging
    - PR 테스트가 반드시 보호된 브랜치의 최신 상태를 포함하고 있어야 함
    - 필수적으로 상태 확인이 필요한 작업 선택 가능
  > 병합하기 전에 status checks가 이상이 없어야 병합 가능
  > > PR 테스트가 반드시 보호된 브랜치의 최신 상태를 포함하고 있어야 함. 필수적으로 상태 확인이 필요한 작업 선택
  
- [X] Do not allow bypassing the above settings
  > 관리자도 이 규칙을 적용
