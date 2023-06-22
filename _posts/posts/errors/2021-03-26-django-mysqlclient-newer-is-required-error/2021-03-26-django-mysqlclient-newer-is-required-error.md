---
layout: post
title: Django | mysqlclient newer is required 오류 
date: 2021-03-26 23:45:00 +09:00
modified: 
category: [posts, errors]
tags: [django]
image: "/assets/img/python_logo.png"
cover: ""
---

### 1. 오류 내용
```
django.core.exceptions.ImproperlyConfigured: mysqlclient 1.4.0 or newer is required; you have 0.10.1.
```

### 2. 해결 방법

virtualenv를 사용하고 있다면 해당 env의 `python3.x/django/db/backends/mysql/base.py` 파일의 아래부분을 수정하면 된다. <br>

**변경 전**<br>
```python
version = Database.version_info
if version < (1, 4, 0):
  raise ImproperlyConfigured('mysqlclient 1.4.0 or newer is required; you have %s.' % Database.__version__)
```
<br>
**변경 후**<br>
```python
version = Database.version_info
if version < (1, 4, 0):
  pass
```