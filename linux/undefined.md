# 시간 설정

HW 시간과 SW 시간으로 구분할 수 있음

OS 시간(SW 시간)은 재부팅 시 CMOS의 시간(HW 시간)을 가져옴

## 1. Linux 시간 설정

### 1.1. timedatectl

#### 1.1.1 시간 확인

```shell
$ timedatectl
```

* Local time: 현재 시간&#x20;
* Universal time: UTC 국제 표준시&#x20;
* RTC time: 하드웨어 시간
* Time zone: 타임존&#x20;
* NTP enabled: NTP 활성화 여부&#x20;
* NTP synchronized: NTP 동기화 여부&#x20;
* RTC in local TZ: 하드웨어 시간을 로컬 시간으로 동기화할지 여부 &#x20;

#### 1.1.2. timezone 설정&#x20;

timezone 목록 보기

```shell
$ timedatectl list-timezones | grep -i seoul
```

timezone 변경

```shell
$ timedatectl set-timezone Asia/Seoul
```

## 2. HW 시간 설정

### 2.1. hwcolck

#### 2.1.1 시간 확인&#x20;

```shell
$ hwclock
```

#### 2.1.2. SW 시간 -> HW 시간으로 동기화&#x20;

```shell
$ hwcolck -w
```

#### 2.1.3. HW 시간 -> SW 시간으로 동기화&#x20;

```shell
$ hwcolck -s
```

> 동기화가 안되는 경우 NTP 동기화 해제&#x20;
>
> ```shell
> $ timedatectl set-ntp false
> ```
