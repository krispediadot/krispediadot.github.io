---
layout: post
title: Python | matplot 그래프에 한글 적용하기
date: 2020-06-03 11:58:47 +09:00
modified: 
category: python
tags: [matplot]
image: "/assets/img/python_logo.png"
cover: ""
---

#### 실행전 
![matplot korean before](https://github.com/krispediadot/krispediadot.github.io/tree/master/_posts/python/2019-07-09-matplot-korean/matplot_korean_before.jpg)

```python
import matplotlib.pyplot as plt
%matplotlib inline 

plt.rc('font', family = 'AppleGothic')
plt.rcParams['axes.unicode_minus']=False
```

#### 실행후
![matplot korean after](https://github.com/krispediadot/krispediadot.github.io/tree/master/_posts/python/2019-07-09-matplot-korean/matplot_korean_after.jpg)