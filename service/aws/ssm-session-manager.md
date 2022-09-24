---
description: AWS SSM, CloudWatch, S3를 이용하여 서버에 접속하고 세션 기록, 로그를 저장
---

# SSM Session manager를 통해 서버 접속

SSH Key 없이 서버 접속 가능, SSH port 관리 필요 없음

Private subnet이어도 bastion host 없이 서버 접속 가능

## 1. EC2 Instance 설정

SSM Agent가 설치되어 있어야 하지만 EC2 Instance에는 기본적으로 설치되어 있음

### 1.1. [SSM Agent 상태 확인 및 에이전트 시작](https://docs.aws.amazon.com/ko\_kr/systems-manager/latest/userguide/ssm-agent-status-and-restart.html)

## 2. IAM 설정

### 2.1. IAM 역할 생성

IAM > 엑세스 관리 > 역할 > 역할 만들기

* 신뢰할 수 있는 엔터티 유형: AWS 서비스
* 사용 사례: EC2
* 권한 정책:
  * AmazonSSMManagedInstanceCore
  * CloudWatchAgentServerPolicy
  * AmazonS3FullAccess
* 역할 이름: \[EC2 Instance 이름]-iam-role

### 2.2. EC2 Instance에 IAM 역할 추가

EC2 > 인스턴스 > 상단 작업 > 보안 > IAM 역할 수정

* [2.1. 단계](ssm-session-manager.md#2.1.-iam)에서 만든 IAM 역할 선택

## 3. CloudWatch 설정

### 3.1. 로그 그룹 추가

CloudWatch > 로그 > 로그 그룹 > 로그 그룹 생성

* 로그 그룹 이름: \[EC2 인스턴스 이름]-session-manager
* 보존 설정: 각자 설정

## 4. S3 설정

### 4.1. 버킷 생성

S3 > 버킷 > 버킷 만들기

* 이름: \[인스턴스 이름]-ssm
* 리전: ap-northeast-2(서울)
* 객체 소유권: ACL 비활성화됨(권장)
* 이 버킷의 퍼블릭 액세스 차단 설정: 모든 퍼블릭 액세스 차단
* 버킷 버전 관리: 비활성화
* 기본 암호화: 비활성화

### 4.2. 버킷에 수명 주기 규칙 생성

S3 > 버킷 > \[버킷 선택] > 관리: 수명 주기 규칙 생성

* 수명 주기 규칙 이름: session-manager-lifecycle
* 규칙 범위 선택 - 하나 이상의 필터를 사용하여 이 규칙의 범위 제한
* 접두사: session-manager/
* 수명 주기 규칙 작업(각자 설정)
  * 객체의 현재 버전 만료 - 객체 생성 후 경과 일수: 30

## 5. Session manager 설정

### 5.1. Session manager 설정

SSM > 노드 관리 > 세션 관리자 > 기본 설정

* General preferences
  * Idle session timeout: 20 minutes
  * Enable maximum session duration: X
  * KEnable KMS encryption: X
  * Linux 인스턴스에 대해 Run As 지원 활성화
    * Operating system user name: \[EC2 instance user name]
      * ex) ec2-user
  * CloudWatch logging
    * CloudWatch logging: Enable
    * Choose your preferred logging option: Stream session logs (Recommended)
    * Enforce encryption - Allow only encrypted CloudWatch log groups: X
    * [3.1. 단계](ssm-session-manager.md#3.1.)에서 생성한 CloudWatch 로그 그룹 추가
  * S3 logging
    * Send session logs to S3: Enable
    * Enforce encryption - Allow only encrypted S3 buckets: X
    * 4.1. 단계에서 생성한 S3 버킷 선택
    * S3 키 접두사: session-manager
    *   Linux shell profile:

        ```bash
        $ cd
        $ source ./.bash_profile
        $ user=$(whoami)
        $ echo "Welcome $user"'!'
        ```

## 6. SSM으로 서버 접속하기

SSM으로 서버에 접속하기 위해서는 아래 2가지가 설치되어 있어야 함

1. AWS CLI
2. Session Manager plugin

### 6.1. [AWS CLI 설치 및 설정](cli.md)

### 6.2. Session Manager plugin 설치

[AWS CLI용 Session Manager 플러그인 설치](https://docs.aws.amazon.com/ko\_kr/systems-manager/latest/userguide/session-manager-working-with-install-plugin.html) 참고

### 6.3. 서버 접속

```shell
$ aws ssm start-session --target "[EC2 Instance ID]"
```
