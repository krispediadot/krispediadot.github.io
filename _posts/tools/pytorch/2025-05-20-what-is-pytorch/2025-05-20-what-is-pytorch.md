---
lang: kr
layout: post
title: What is Pytorch?
date: 2025-05-20 09:00:00 +09:00
modified: 
category: [Tools, Pytorch]
tags: 
image: 
cover: 
---

### 1. Pytorch란?

> PyTorch is an optimized tensor library for deep learning using GPUs and CPUs.

PyTorch 공식 document에 나와있는 설명에 따르면 PyTorch는 GPU와 CPU를 사용하는 머신러닝을 위해 최적화 된 tensor library이다. 



##### Tensor란?

> Tensors are a specialized data structure that are very similar to arrays and matrices. In PyTorch, we use tensors to encode the inputs and outputs of a model, as well as the model’s parameters.
> Tensors are similar to NumPy’s ndarrays, except that tensors can run on GPUs or other specialized hardware to accelerate computing.

Tensor는 배열 행렬과 비슷한 특별한 데이터 구조이고 PyTorch에서는 모델의 입력과 출력, 그리고 모델의 파라미터를 인코딩하기위해 사용한다. 

Tensor는 Numpy의 ndarray와 비슷하지만 ndarray와는 달리 GPU에서 연산이 가능하다는 점히 큰 차이점이다. 


**tensor library** 단어로 알 수 있듯 PyTorch는 tensor를 기반으로 하는 라이브러리이고 머신러닝에 필요한 데이터를 tensor로 구조화한다. 



---
- [PyTorch 공식 document](https://docs.pytorch.org/docs/stable/index.html)
- [PyTorch 공식 document - Tensor](https://docs.pytorch.org/tutorials/beginner/blitz/tensor_tutorial.html)
