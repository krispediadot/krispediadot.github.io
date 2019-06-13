---
layout: post
title: "[Algorithms] Markov Chain "
comments: true
description: "markov chain"
tag : [Algorithms]
---

마르코프 체인의 주요 특징은 **마르코프 성질**을 가진다는 것이다.<br

## 마르코프 성질이란 무엇인가?<br>
> 마르코프 성질이란 다음 상태로 넘어갈 때 오직 직전 상태의 값**만** 고려한다는 것이다.

이러한 특징은 모델링을 단순화 시킨다.<br>

## 마르코프 체인이란 무엇인가?<br>
> 마르코프 체인이란 마르코프 성질을 지닌 이산 확률 과정이다.

즉, 마르코프 체인이란 마르코프 성질을 만족하는 상태값의 연속이다.<br>

## 마르코프 모델이란 무엇인가?<br>
> 마르코프 모델은 마르코프 성질을 만족한다는 가정하에 만든 확률적 모델이다.

#### 마르코프 모델<br>
1단계. 각 상태를 정의한다.<br>
2단계. 각 상태에서 다른 상태로 넘어가는 **상태 전이 확률**을 정의한다.<br>

3단계. 각 상태와 상태 전이 확률을 정리해 상태 전이도/상태 전이 확률표를 그린다.<br>
4단계. 확률을 계산해본다.(각 상태가 전이 될 때 직전의 상태**만** 고려한다는 점을 명심!)<br>



---

#### 
>Certain Factors Affecting Telegraph Speed by H.NYQUIST

#### 정보의 크기(?) H = S*N
>Transmission of Information by R.V.I HARTLEY

#### 마르코프 모델을 기초로 삼아 의사소통을 생각하는  방법
>A Mathematical Theory of Communication by C.E.SHANNON

#### 압축
>A Method for the Construction of Minimum-Redundancy Codes by DAVID A.HUFFMAN 

**참고 자료:**
[https://ko.khanacademy.org/computing/computer-science/informationtheory#moderninfotheory](https://ko.khanacademy.org/computing/computer-science/informationtheory#moderninfotheory)