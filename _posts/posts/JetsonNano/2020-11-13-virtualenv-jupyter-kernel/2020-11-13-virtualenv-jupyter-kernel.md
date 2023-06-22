---
layout: post
title: Jetson Nano | jupyter virtualenv 커널 추가
date: 2020-11-07 11:00:00 +09:00
modified: 
category: jetson nano
tags: [ubuntu18.04, virtualenv, jupyter]
image: "/assets/img/nvidia_logo.jpg"
cover: "../puzzle.jpg"
---

### 1. 가상환경 실행
---
```
workon [가상환경 이름]
```

### 2. 설치
---
```
pip install ipykernel
```

### 3. 사용  
---
`python -m ipykernel install --user --name=[가상환경 이름]`: 커널 추가  
`sudo jupyter kernelspec uninstall [가상환경 이름]`: 커널 삭제 


<div class="divider"></div>
**[참고 자료]**
- [참고1](https://medium.com/@kwoncharles/jupyter-notebook-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EA%B0%80%EC%83%81%ED%99%98%EA%B2%BD-kernel-%EC%B6%94%EA%B0%80-%EC%A0%9C%EA%B1%B0-mac-67ee72088784)