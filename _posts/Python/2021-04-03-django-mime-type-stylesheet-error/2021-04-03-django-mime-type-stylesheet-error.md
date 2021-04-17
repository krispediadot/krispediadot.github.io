---
layout: post
title: Django | Refused to apply style from '<URL>' because its MIME type
date: 2021-04-03 14:00:00 +09:00
modified: 
category: python
tags: [django]
image: "/assets/img/python_logo.png"
cover: ""
---

### 1. 오류 내용
```
Refused to apply style from '<URL>' because its MIME type ('text/html') is not a supported stylesheet MIME type, and strict MIME checking is enabled.
```

Django의 url을 설정하다가 이런 에러가 발생했다.<br>

```python
# 변경 전
path('base',views.base, name='base')

# 변경 후
path('base/<str:id>/',views.base, name='base')
```

### 2. 해결 방법
<br>
stylesheet 파일의 위치 앞에 `/`를 추가한다.<br>
<br>
```python
# 변경 전
<link rel="stylesheet" href="static/css/shared/style.css">

# 변경 후
<link rel="stylesheet" href="/static/css/shared/style.css">
```