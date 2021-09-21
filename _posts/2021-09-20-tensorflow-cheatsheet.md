---
title: "Tensorflow 환경 설정"
date: 2021-09-20T14:15:00-01:00
categories:
  - code
tags:
  - tensorflow
  - environment
---

자주 사용하는 tensorflow 환경 설정

```python
import os, sys

# 주피터 노트북 파이썬 모듈 경로 설정
dir2 = os.path.abspath('')
dir1 = os.path.dirname(dir2)
if not dir1 in sys.path: sys.path.append(dir1)

# GPU 지정 환경변수
os.environ['CUDA_VISIBLE_DEVICES'] = '1'

# 텐서플로우 memory growth
import tensorflow as tf

gpus = tf.config.experimental.list_physical_devices('GPU')
tf.config.experimental.set_memory_growth(gpus[0], True)
```
