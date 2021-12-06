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

