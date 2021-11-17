# medical-insight-installer

##### 현장 설치를 위해 USB 파일 기반으로 명령어를 나열한 임시 설치 스크립트
##### 대략 20분 소요

## 설치 usb 구성
```
usb
  |-- Ubuntu-Server 20.04.3 LTS amd64 설치 파일
  |
  |-- medical-insight
  |
  |   |-- medical-insight : 메인 쉘
  |
  |   |-- script : 설치 스크립트
  |       |-- install : 설치 메인 스크립트
  |       |-- file-handler-offline : 로컬 파일로 설치하기 위한 리눅스 패키지, 도커 이미지 파일들
  |       |-- init : no passwd 설정
  |       |-- network-driver
  |       |-- restart_k8s : minikube 클러스터 재생성
  |       |-- restart_model : AI모델 삭제 후 재배포
  |   |-- network-driver
  |       |-- deb_files : 네트워크 드라이버 설치를 위한 리눅스 패키지 파일
  |       |-- r8125-9.005.06 : 네트워크 드라이버
  |           |-- autorun.sh : 설치쉘
  |   |-- kubernetes
  |       |-- bin
  |       |-- knative-serving
  |           |-- serving-crds.yaml
  |           |-- serving-core.yaml
  |           |-- net-certmanager-release.yaml
  |           |-- net-istio-release.yaml
  |       |-- cert-manager.yaml
  |       |-- kfserving.yaml
  |   |-- aiip-runtime
  |       |-- airuntime-account
  |           |-- bin
  |           |-- logs
  |       |-- airuntime-config-server
  |       |-- airuntime-core
  |       |-- airuntime-gw
  |       |-- airuntime-history : 생략 가능
  |       |-- airuntime-ifservice
  |       |-- airuntime-monitoring : 생략 가능
  |       |-- airuntime-watcher
  |       |-- airuntime-web : 생략 가능
  |       |-- config : 환경 변수 정의
  |       |-- serviced : 서비스 데몬 등록 파일
  |       |-- nginx.conf : nginx 설정 파일
  |       |-- createDB : DB 생성 스크립트
  |       |-- v1_airuntime_20210727_060001 : 초기 데이터 마이그레이션 스크립트
  |   |-- test
  |       |-- 1.2.410.2000010.82.220.12100424023 : test sample data
```

## 설치

##### 1. usb device 이름 확인
```
$ sudo fdisk -l

Device       Start       End   Sectors  Size Type
/dev/sda1   411648 250626047 250214400 31.8G Linux filesystem
```

##### 2. USB 마운트
```
$ sudo mkdir -p /mnt/usb
$ sudo mount -t ntfs-3g /dev/sda1 /mnt/usb
```

##### 3. 설치 스크립트 실행
```
$ cd /mnt/usb/medical-insight
$ ./medical-insight install
```

## 장비 재부팅, K8S 장애 상황시 클러스터 재생성
```
$ cd ~
$ ./medical-insight restart-k8s
```

## 모델 재배포
```
$ cd ~
$ ./medical-insight restart-model
```

## 설치 테스트
##### VM 환경 : Hyper-V on Windows 11 Pro
##### OS : Ubuntu-Server 20.04.3 LTS amd64
##### Device : mount CIFS Windows Share in Linux

