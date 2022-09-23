# OpenJDK

## 1. OpenJDK 설치

### apt

#### 패키지 목록 확인

```shell
$ apt search openjdk
```

#### 패키지 설치

```shell
$ sudo apt install openjdk-8-jdk
```

### yum

#### 패키지 목록 확인

```shell
$ yum list java*jdk-devel
```

#### 패키지 설치

```shell
$ sudo yum install java-1.8.0-openjdk-devel.x86_64
```

### 확인

```shell
$ javac -version
```

## 2. 환경 변수 설정

### 2.1. JDK 설치 경로 확인&#x20;

```
$ sudo update-alternatives --config java
```

### 2.2. profile 파일 수정

`/etc/profile` 파일에 `JAVA_HOME` 환경 변수 추가해야 함

```shell
$ sudo vi /etc/profile

...
JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"
```

> `/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java`일 경우 `/usr/lib/jvm/java-8-openjdk-amd64` 까지

### 2.3. profile 적용

```shell
$ source /etc/profile
```

## 3. 확인

```shell
$ echo $JAVA_HOME
```
