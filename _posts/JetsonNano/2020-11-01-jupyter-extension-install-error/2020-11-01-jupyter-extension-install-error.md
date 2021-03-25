---
layout: post
title: Jetson Nano | jupyter extension 설치 오류
date: 2020-11-01 11:00:00 +09:00
modified: 
category: jetson nano
tags: [ubuntu18.04, jupyter]
image: "/assets/img/nvidia_logo.jpg"
cover: "../puzzle.jpg"
---

### 1. 오류 내용
```
sudo jupyter labextension install @jupyter-widgets/jupyterlab-manager
```

위 명령어를 실행하는데 아래 오류가 났다.  

`UnicodeDecodeError: 'ascii' codec can't decode byte 0xf0 in position 23: ordinal not in range(128)`

### 2. 해결 방법  
```
npm config set unicode false
```