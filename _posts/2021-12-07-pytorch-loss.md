---
title: "[PyTorch] Loss object 정리"
date: 2021-12-07
categories:
  - pytorch
tags:
  - pytorch
  - loss
---

PyTorch에서 사용하는 loss obejct에 대한 cheat sheet



안녕하세요. 이번 글은 GAN 모델에 대한 reconstruction loss를 작성하던 중, 파이토치의 loss object에 대해 정리할 필요가 있을 것 같아 작성하게 되었습니다. 나중에 VAE에 대한 loss도 포스팅으로 남기면 좋을 것 같네요.

### MSE Loss

Logistic regression에서 처음 접할 수 있었던 손실 함수입니다.

먼저 logistic regression 예제를 하나 살펴보겠습니다.

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0, 10, 100) + np.random.normal(0, 1, (100))
y = np.linspace(0, 10, 100) + np.random.normal(10, 1, (100))

plt.scatter(x, y)
plt.show()
```

<img src="https://user-images.githubusercontent.com/29935117/145578332-36fc76b4-69c9-4523-aefb-f8d7fb68e384.png" width=500px/>
