---
title: "[잡담] 라벨 임베딩에 대한 생각"
date: 2022-02-01
categories:
  - 잡담
tags:
  - 잡담
---

Classifier의 마지막 fully-connected layer의 weight에 대해서





안녕하세요. onnoo입니다.

최근 자연어 컨퍼런스 쪽 논문 리스트를 살펴보면, 분류 문제의 label 표현 방법에서 one-hot과 같은 hard label이 아닌 여러 클래스에 걸친 soft label을 이용한 연구들이 몇몇 있었습니다.

문장에 대한 감정 분류를 예로 들면, 한 문장 안에 포함된 감정은 '화남' 하나만으로 구성되지 않을 수 있습니다.

하지만 지도 학습 과정에서 '화남'이라는 hard label만 학습하지 않고, '기쁨' 또는 '슬픔'과 같은 soft label을 고려하여 학습에 이용할 수 있다는 아이디어입니다.





이러한 생각 중에, "어, 그렇다면 one-hot label에 대한 embedding을 학습할 수 없을까?"라는 생각을 했습니다.

다시 말해서 label을 learnable parameter로 두어 representation learning을 할 수 있다면, 모델의 최종 아웃풋 벡터에 곱하여 스코어를 구할 수 있다고 생각을 했습니다.

나름 재미있어 보인다 생각하던 차에, classifier가 생각나 해당 포스트를 남기게 되었습니다.





우리는 자연스럽게 분류 문제에서 classifier를 구성할 때, 마지막 dense layer의 out_feature 수를 label class 개수만큼 지정합니다.

이후에 softmax와 같은 activation을 통과시켜 각 라벨에 해당하는 확률을 산출하죠.

제가 앞서 생각하던 각 label에 대한 embedding이 classifier의 마지막 fully-connected layer의 weights 안에서 학습이 되고 있었습니다.



<img src="https://user-images.githubusercontent.com/29935117/152016223-77eac25f-5e06-41f7-96e7-3d707c2594d3.png" />



마지막 레이어의 연산을 간단하게 나타낸 그림입니다. 결국 각 클래스에 대해 학습된 embedding과 내적하여 유사도를 나타낼 수 있습니다.

평소에는 생각하지 않고 사용해왔던 classifier의 마지막 부분에 대한 생각이었습니다.

감사합니다.
