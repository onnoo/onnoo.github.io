---
title: "Ubuntu 명령어"
date: 2021-09-23
last_modified_at: 2021-10-07
categories:
  - code
tags:
  - ubuntu
  - environment
---

자주 사용하는 ubuntu 명령어

### SSH 키 추가

```bash
# client
ssh-keygen -t rsa
ls -al ~/.ssh
scp ~/.ssh/id_rsa.pub <username>@<host>:id_rsa.pub

# client (simple)
ssh-copy-id -i ~/.ssh/id_rsa.pub <username>@<host>

# server
mkdir ~/.ssh
sudo chmod 700 ~/.ssh
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys

```

### 사용자 추가

```bash
sudo adduser <username>
sudo usermod -aG sudo <username>

# docker 그룹 추가
cat /etc/group
sudo usermod -aG docker <username>
```

### 포트 허용

```bash
sudo iptables -i input 1 -p tcp --dport <port> -j ACCEPT
```

### 외장 USB 마운트

```bash
# create directory to be mounted
mkdir ~/usb
# check usb device name (e.g., sdc1)
lsblk

# mount usb (option 1)
sudo mount /dev/sdc1 ~/usb
# mount usb (option 2)
# sudo mount -t vfat /dev/sdc1 ~/usb

# unmount usb
sudo umount /dev/sdc1
```

### 폴더 용량 확인

```bash
# mounted disk
df -h

# current working space
du -sh ./*
```

