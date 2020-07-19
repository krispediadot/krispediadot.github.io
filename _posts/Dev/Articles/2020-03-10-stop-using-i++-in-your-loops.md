---
layout: post
title: "[Article] Stop Using i++ in Your Loops"
categories: articles
tag : [medium]
---

[원문](https://medium.com/better-programming/stop-using-i-in-your-loops-1f906520d548)

#### Q. i++ 보다 ++i를 쓰는게 더 나은 이유

A. i++를 사용하면 증가 되기 전 수를 기억하고 있어야함. 정수처럼 기본 자료형과 같이 사용하면 컴파일러가 알아서 최적화 하겠지만 사용자 정의 자료형을 사용할 경우 적절하게 최적화 하지 않을 수도 있음.  

