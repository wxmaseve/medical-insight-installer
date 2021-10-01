# medical-insight-installer

## 설치 usb 구성
```
usb
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
