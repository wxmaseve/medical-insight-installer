# medical-insight-installer

##### 현장 설치를 위해 USB 파일 기반으로 명령어를 나열한 임시 설치 스크립트

## 설치 usb 구성
```
usb
  |-- Ubuntu-Server 20.04.2 LTS amd64 설치 파일
  |
  |-- medical-insight
  |   |-- 1.network-driver
  |       |-- deb_files
  |       |-- r8125-9.005.06
  |   |-- 2.kubernetes
  |       |-- bin
  |       |-- knative-serving
  |       |-- kfserving
  |   |-- 3.aiip-runtime
  |       |-- airuntime-account
  |       |-- airuntime-config-server
  |       |-- airuntime-core
  |       |-- airuntime-gw
  |       |-- airuntime-history : 생략 가능
  |       |-- airuntime-ifservice
  |       |-- airuntime-monitoring : 생략 가능
  |       |-- airuntime-watcher
  |       |-- airuntime-web
  |       |-- config : 환경 변수 정의
  |       |-- serviced : 서비스 데몬 등록 파일
  |       |-- nginx.conf : nginx 설정 파일
  |       |-- createDB : DB 생성 스크립트
  |       |-- v1_airuntime_20210727_060001 : 초기 데이터 마이그레이션 스크립트
  |   |-- 4.test
  |       |-- 1.2.410.2000010.82.220.12100424023 : test sample data
  |-- installer
  |-- init
  |-- network-driver
```

## device 이름 확인
```
$ sudo fdisk -l

Device       Start       End   Sectors  Size Type
/dev/sda1   411648 250626047 250214400 31.8G Linux filesystem
```

## mount cmd
```
$ sudo mkdir -p /mnt/usb
$ sudo mount -t ntfs-3g /dev/sda1 /mnt/usb
```

## 설치
```
$ cd /mnt/usb/medical-insight
$ . installer
```
