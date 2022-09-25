# Branch 보호 규칙

`GitHub Repository > Settings > Code and automation > Branches`에서 규칙을 추가할 수 있음

* [x] Require a pull request before merging
  * [x] Require approvals
* [x] Require status checks to pass before merging
  * [x] Require branches to be up to date before merging
* [x] Do not allow bypassing the above settings

`main` 브런치에 위와 같이 설정하면 좋음

* Require a pull request before merging: 보호되고 있는 브런치에 직접 push 할 수 없음
  * Require approvals: 병합 전에 필요한 승인 인원을 설정할 수 있음
* Require status checks to pass before merging: 병합하기 전에 status checks가 이상이 없어야 병합 가능
  * Require branches to be up to date before merging
    * PR 테스트가 반드시 보호된 브랜치의 최신 상태를 포함하고 있어야 함
    * 필수적으로 상태 확인이 필요한 작업 선택 가능
* Do not allow bypassing the above settings: 관리자도 이 규칙을 적용

