---
layout: post
title: entropy & information gain
date: 2021-10-13 11:00:00 +09:00
modified: 
category: machine learning
tags: []
image: "/assets/img/avatar_code.png"
cover: "../puzzle.jpg"
---

### Question

엔트로피에 대해 설명해주세요. 가능하면 information gain에 대해서도요.

### 정보량

엔트로피를 이야기 하기 위해서는 정보량(Information)에 대해 알고 있어야한다.<br>

정보량은 일반적으로 Shannon entropy를 정의할 때 나오는 용어로 log2(가능한 경우의 수)로 정의되어 있다.<br>

확률이 적은 경우 많은 정보를 얻을 수 있고<br>
확률이 많을 수록 적은 정보를 얻을 수 있다.<br>

이러한 수식을 정리하면 log2(1/확률)로 나타낼 수 있고<br>
이는 -log2(확률)로 정리된다.<br>

이 정리된 수식은 Shannon entropy를 정의하는데 사용된다.<br>

### 엔트로피(Entropy)

엔트로피는 무질서를 나타내는 값이다.<br>

>열역학적 정의: 미시적 상태의 무질서한 정도로 볼 수 있다. 계(시스템)는 기를 쓰고 엔트로피가 증가하는 쪽으로, 즉 무질서해지는 쪽으로 변하려 한다.<br>
>정보이론적 정의: 한 메시지에 들어갈 수 있는 정보량[6]의 비트 수. 정보 이론의 창시자인 수학자 클로드 섀넌이 1948년 창안한 개념이다. 정보기술, 암호학, 데이터 압축 등의 중심이 되는 개념.<br>


### Shannon Entropy

Claud Shannon이라는 사람이 정의한 수식으로 한 번의 메세지를 통해 표현할 수 있는 정보의 양을 정의한 수식이라고 한다.<br>

Shnnon entropy는 밑이 2인 로그를 취하고 있을때는 `bit`라는 단위로 불린다.<br>
이 `bit`는 컴퓨터에서 주로 나오는 1bit와 동일한 단위이다.<br>

Shannon entropyd의 수식은<br>
h(x) = -sum(p(x)*log2(p(x)))이다.<br>

이산 확률 분포에서는 sigma가 사용되고<br>
연속 확률 분포에서는 ~~가 사용된다.<br>

### Cross Entropy

cross entropy는 p라는 분포와 q라 예측된 분포의 엔트로피 값이다.<br>

cross entropy의 수식은<br>
h(p,q) = -sum(p(x)*log2(q(x)))이다.<br>

여기서 -log2(q(x))는 예측된 분포의 정보량이라 할 수 있다.<br>

만약, q가 p분포를 정확히 예측한다면 cross entropy = Shannon entropy가 될것이다.<br>

### Kullback-Leibler Divergence

KL Divergence는 서로 다른 두 분포의 차이를 측정하는데 사용된다.<br>

KL Divergence의 수식은<br>
Dkl(p||q) = h(p,q) - h(p)이다.<br>

예측하는 문제를 푸는 경우 두 분포 사이의 차이를 줄이는 것이 목표이므로 KL Divergence 값을 줄여야 한다.<br>
이때 h(p)는 정해져있는 값, 즉 고정된 값이므로 KL Divergence를 줄이기 위해서는 h(p,q) 즉, cross entropy를 줄여야 한다.<br>

이러한 이유에서 분류 문제를 푸는 머신러닝 모델에 대해 cross entropy를 cost 함수로 정의하고 cross entropy를 줄이는 방향으로 모델을 학습한다.<br>

cross entropy를 줄이는 일은 KL Divergence를 줄이는 일과 동일하므로 예측값 q가 정답값 p와 동일해지도록 학습된다.<br>

### information gain

얻을 수 있는 정보량이라 정의할 수 있다.<br> 

주로 decision tree를 생성할 때 나오는 용어로 tree 생성을 위해 분기할 때 사용되는 지표이다.<br>

information gain의 수식은<br>
IG = entropy(parent node) - entropy(parent node, child node)이다.<br>

분기로 인해 줄일수 있는 불순도의 양을 의미한다.<br>

이러한 지표는 decision tree를 생성하는 알고리즘 중 ID3 알고리즘에서 사용된다.<br>

### information gain ration

information gain을 사용하는 ID3 알고리즘의 한계점은 4가지가 있다.<br>
1. 잘게 나뉘어져 전체 불순도가 높아지는 경우가 있다는 점
1. 연속값에는 사용할 수 없다는 점
1. 결측치가 있는 경우 적용할 수 없다는 점
1. 과적합되기 쉽다는 점

이러한 점을 보완해서 decision tree를 생성하는 C4.5 알고리즘이 나오게 되었고<br>
information gain ratio는 C4.5 알고리즘에서 사용된다.<br>

information gain ration의 수식은<br>
IGR = information gain(IG) / intrinsic vlaue(IV)<br>
IV = entropy(child node)<br>

잘게 나뉘어지는 경우에 가중치를 부여해 한계를 보완했다.<br>


----
**참고자료**:<br>
[https://namu.wiki/w/%EC%97%94%ED%8A%B8%EB%A1%9C%ED%94%BC](https://namu.wiki/w/%EC%97%94%ED%8A%B8%EB%A1%9C%ED%94%BC)<br>
[https://homes.cs.washington.edu/~shapiro/EE596/notes/InfoGain.pdf](https://homes.cs.washington.edu/~shapiro/EE596/notes/InfoGain.pdf)<br>
[https://tyami.github.io/machine%20learning/decision-tree-3-c4_5/](https://tyami.github.io/machine%20learning/decision-tree-3-c4_5/)<br>
[https://angeloyeo.github.io/2020/10/27/KL_divergence.html](https://angeloyeo.github.io/2020/10/27/KL_divergence.html)
