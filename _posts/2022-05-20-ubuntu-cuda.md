---
title: "Ubuntu 20.04 - Nvidia Driver 설치"
date: 2022-05-20
categories:
  - utils
tags:
  - ubuntu
  - tensorflow
---

최신 Nvidia Driver 설치 및 tensorflow 2.7.0 환경 준비


## 최신 Nvidia Driver 설치
```
sudo apt install ubuntu-drivers-common
sudo ubuntu-drivers autoinstall
```

### 설치 후 gnome 제거
```
sudo apt-get remove gnome-*
sudo apt-get remove ubuntu-desktop --purge
```

## Tensorflow 환경 준비

### 테스트된 빌드 구성 (tensorflow compatibility table)

[https://www.tensorflow.org/install/source#tested_build_configurations](https://www.tensorflow.org/install/source#tested_build_configurations)

> 2022.05.20. 기준 tensorflow 2.7.0 환경 준비 (CUDA 11.2, cuDNN 8.1)

### CUDA 설치

[https://developer.nvidia.com/cuda-toolkit-archive](https://developer.nvidia.com/cuda-toolkit-archive)

> CUDA Toolkit 11.2.2 (March 2021) 선택

```
export PATH=/usr/local/cuda/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
```

### cuDNN 설치

[https://developer.nvidia.com/rdp/cudnn-archive](https://developer.nvidia.com/rdp/cudnn-archive)


> Download cuDNN v8.1.1 (Feburary 26th, 2021), for CUDA 11.0,11.1 and 11.2 선택


```
sudo cp cuda/include/cudnn*.h /usr/local/cuda/include
sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda/lib64
sudo chmod a+r /usr/local/cuda/include/cudnn*.h /usr/local/cuda/lib64/libcudnn*
```
