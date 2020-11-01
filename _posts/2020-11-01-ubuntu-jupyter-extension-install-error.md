---
layout: post
title: "[Ubuntu 18.04] jupyter extension 설치 오류 "
categories: 
tag : []
---

```
sudo jupyter labextension install @jupyter-widgets/jupyterlab-manager
```

위 명령어를 실행하는데 아래 오류가 났다.  

`UnicodeDecodeError: 'ascii' codec can't decode byte 0xf0 in position 23: ordinal not in range(128)`

해결 방법  

```
npm config set unicode false
```