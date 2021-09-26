---
title: "[Ubuntu] 네트워크 드라이버 문제 해결"
date: 2021-09-26
categories:
  - troubleshooting
tags:
  - ubuntu
  - network
---

Ubuntu server 설치 후 네트워크 인식이 되지 않을 때 수동으로 랜카드 드라이버를 잡아주는 방법


## Network driver 준비

메인보드의 모델명이나 `lspci` 명령어를 통해 이더넷 컨트롤러를 알아냈다면, 해당 버전의 드라이버를 검색하여 설치한다.

예를 들어 MSI MAG B550M에서는 **Realtek R8125**을 사용하고 있어 다음 [링크](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software)에서 리눅스용 `2.5G Ethernet LINUX driver r8125 for kernel up to 5.6` 을 다운로드 받는다.

## 네트워크 연결 없이 dependancies 설치

드라이버 설치에 필요한 패키지(`make`)가 ubuntu server에 없을 수 있는 경우가 있다. 기본적으로 설치하는 `sudo apt-get install build-essential` 설치가
네트워크 연결이 되어있지 않기 때문에 드라이버 파일과 마찬가지로 직접 usb와 같은 외장 디스크를 통해 옮겨주어야 한다.

[Ubuntu 외장 usb 마운트 방법](http://localhost:4000/code/ubuntu-commands/#%EC%99%B8%EC%9E%A5-usb-%EB%A7%88%EC%9A%B4%ED%8A%B8)

ubuntu server에서 필요한 패키지 설치 파일들을 얻는 방법은 다음과 같다.


```bash
# Offline PC (e.g., ubuntu server)
sudo apt-get -qq --print-uris install build-essential | cut -d\' -f 2 > urls.txt

# Online PC (최신 URL이 아닐 경우, 필수 패키지가 다운되지 않을 수 있어, Failed 결과를 확인할 것)
wget -c -i urls.txt

# Offline PC
sudo dpkg -i *.deb
```

## Network controller interface name 확인

* option 1 : 드라이버 설치 후 `ip a` 명령어를 통해 확인
* option 2 : `lspci | grep -i Ethernet` 명령어를 통해 나온 콜론 앞의 숮자 가 enp 뒤에 붙고 뒤의 숫자가 p 뒤에 붙는다.
  * `01:06.0 Ethernet controller: Red Hat, Inc. Virtio network device (rev 01)` -> `enp1p6`
  * `2a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller (rev 04)` -> `enp42s0`


## Netplan 수정 후 반영

1. `/etc/netplan/00-installer-config.yaml`을 수정한다. 이때 **자신의 인터페이스 네임을 적는다.**
```yaml
# 동적 ip 할당
network:
ethernets:
  enp1s0:
    addresses: []
    dhcp4: true
version: 2
```
```yaml
# 고정 ip 할당
network:
  ethernets:
    enp1s0:
      addresses: [192.168.0.125/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [8.8.8.8]
      dhcp4: no
      optional: true
  version: 2
```

2. `sudo netplan apply` 명령어를 입력한다.
