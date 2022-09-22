# CLI

## 1. \[CLI 설치]\([https://aws.amazon.com/ko/cli/](https://aws.amazon.com/ko/cli/))

{% embed url="https://aws.amazon.com/ko/cli/" %}

### 1.1. macOS

<pre class="language-shell"><code class="lang-shell"><strong>$ brew install aws</strong></code></pre>

### 1.2. Windows

msi 파일 다운로드하여 설치

### 1.3. 설치 확인

```shell
$ which aws

$ aws --version
```

## 2. CLI로 접속할 IAM 설정

### 2.1. CLI용 관리자 생성

IAM > 엑세스 관리 > 사용자 > 사용자 추가

* 사용자 이름: \[계정]-admin
* 액세스 키 – 프로그래밍 방식 액세스
* 기존 정책 직접 연결 - AdministratorAccess 추가

## 3. AWS CLI 설정

### 3.1. 설정

default 설정

```shell
$ aws configure

AWS Access Key ID [None]: XXX
AWS Secret Access Key [None]: XXX
Default region name [None]: ap-northeast-2
Default output format [None]: json
```

profile 설정

```shell
$ aws configure --profile PROFILE_NAME
```

### 3.2. 설정 확인

default 설정 확인

```shell
$ aws configure list
```

profile 목록 확인

```shell
$ aws configure list-profiles
```

### 3.3. Default 설정 변경

```
# linux
$ export AWS_DEFAULT_PROFILE=testUser

# windows
$ set AWS_DEFAULT_PROFILE=testUser
```

### 3.4. 사용 예시

```shell
# default 설정 예시
$ aws s3 ls

# profile 설정 예
aws s3 ls --profile PROFILE_NAME
```
