---
layout: post
title: Django | MySQLdb 오류 
date: 2021-03-26 23:45:00 +09:00
modified: 
category: errors
tags: [django]
image: "/assets/img/python_logo.png"
cover: ""
---

### 1. 오류 내용
```
import MySQLdb as Database
ModuleNotFoundError: No module named 'MySQLdb'
```

### 2. 해결 방법

virtualenv를 사용하고 있다면 해당 env의 `python3.x/django/db/backends/mysql/base.py` 파일의 아래부분을 수정하면 된다. <br>

**변경 전**<br>
```python
try:
  import MySQLdb as Database
except ImportError as err:
  raise ImproperlyConfigured(
    'Error loading MySQLdb module.\n'
    'Did you install mysqlclient?'
  ) from err
```
<br>
**변경 후**<br>
```python
try:
  import pymysql as Database
  Database.install_as_MySQLdb()
except ImportError as err:
  raise ImproperlyConfigured(
    'Error loading MySQLdb module.\n'
    'Did you install mysqlclient?'
  ) from err
```