---
description: Linux에서 SW 패키지 설치를 간편하게 할 수 있도록 도와주는 명령어 인터페이스
---

# Package manager

패키지 관리자는 SW 응용 프로그램을 검색, 다운로드, 설치, 제거 및 업데이를 도와 줌&#x20;

## 대표적인 패키지 관리자

### Debian

**APT (Advanced Packaging Tool)**

```shell
# 패키지 저장소를 통해 업데이트 파일이 있는지 확인
$ apt update

# 패키지를 새로운 파일로 업데이트
$ apt upgrade
```

### Redhat

#### **YUM (Yellowdog Updater, Modified)**

```shell
# 패키지 업데이트 여부 확인 후 새로운 파일로 업데이트
$ yum update

# 패키지 업데이트 여부 확인 후 새로운 파일로 업데이트
# 더 이상 사용되지 않는 관련된 파일이나 패키지 삭제 
# yum update --obsoletes와 동일 
$ yum upgrade
```

