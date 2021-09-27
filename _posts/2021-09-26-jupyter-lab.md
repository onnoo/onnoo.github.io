---
title: "[Python] jupyter lab 환경 설정"
date: 2021-09-26
categories:
  - python
tags:
  - jupyter-lab
  - environment
---

jupyter lab 외부 접속 허용 및 테마 적용

### 설치

`pip install jupyterlab jupyterlab_darkside_ui`

### config 파일 추가

`jupyter lab --generate-config`

### 패스워드 암호화

```python
from notebook.auth import passwd
passwd(algorithm='sha256')
# output
# Enter password: 
# Verify password: 
# 'sha256:...'
```

### config 파일 수정

```py
c.ServerApp.allow_origin = '*'
c.ServerApp.ip = '0.0.0.0'
c.ServerApp.open_browser = False
c.ServerApp.password = u'sha256:...'
c.ServerApp.port = 8888
c.ServerApp.root_dir = ''
```

> 혹시 ubuntu에서 포트가 막혀있다면 : [ubuntu 포트 허용](http://127.0.0.1:4000/code/ubuntu-commands/#%ED%8F%AC%ED%8A%B8-%ED%97%88%EC%9A%A9)
