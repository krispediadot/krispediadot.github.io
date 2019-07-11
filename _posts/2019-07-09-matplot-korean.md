---
layout: post
title: "[Python] matplot 그래프에 한글 적용하기"
categories: Pyhton
tag : [matplot]
---

#### 실행전 
![matplot korean before](https://krispedia.github.io/assets/images/matplot_korean_before.jpg)

```Python
import matplotlib.pyplot as plt
%matplotlib inline 

plt.rc('font', family = 'AppleGothic')
plt.rcParams['axes.unicode_minus']=False
```

#### 실행후
![matplot korean after](https://krispedia.github.io/assets/images/matplot_korean_after.jpg)