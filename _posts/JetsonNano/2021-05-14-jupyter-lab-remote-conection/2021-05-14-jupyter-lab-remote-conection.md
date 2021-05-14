---
layout: post
title: Jetson Nano | jupyter lab 원격 접속 설정
date: 2021-05-14 16:00:00 +09:00
modified: 
category: jetson nano
tags: [jupyter]
image: "/assets/img/nvidia_logo.jpg"
cover: "../puzzle.jpg"
---

### 1. 설정 파일 생성
---

```
jupyter-lab --generate-config
```

### 2. 설정 파일 확인
---

```
vim /root/.jupyter/jupyter_lab_config.py
```

### 3. 설정 파일 수정
---

```python
c.ServerApp.allow_remote_access = True
c.ServerApp.allow_root = True

c.ServerApp.ip = '0.0.0.0' # 모든 ip 접속 가능
```

------
**참고자료**<br>
- [참고한 블로그](https://dydwnsekd.tistory.com/18)