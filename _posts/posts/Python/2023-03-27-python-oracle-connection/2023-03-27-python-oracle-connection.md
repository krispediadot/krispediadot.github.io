---
layout: post
title: Python | Oracle 데이터베이스 연결
date: 2023-03-27 19:00:00 +09:00
modified: 
category: [posts, tools]
tags: [database]
image: "/assets/img/python_logo.png"
cover: ""
---

### 1. cx_Oracle 다운로드

[공식 홈페이지](https://pypi.org/) 또는 pip를 사용해 cx_Oracle 라이브러리를 다운받는다.

### 2. Oracle Instant Client 설치

[Oracle 공식 홈페이지](https://www.oracle.com/kr/database/technologies/instant-client/downloads.html)에서 각자의 환경에 맞는 Oracle Instant Client를 설치한다.

### 3. cx_Oracle을 활용한 데이터베이스 연결 코드
- 방법 1

```python
import cx_Oracle
import os

LOCATION = "oracle instant client 경로"

os.environ["PATH"] = LOCATION + ";" + os.environ["PATH"]
conn = cx_Oracle.connect(USERNAME, PASSWORD, DATABASEINFO)
cursor = conn.cursor()

QUERY = ""
cursur.execute(QUERY)

for i in cursor:
    print(i)
```

- 방법 2

```python
import cx_Oracle
import os
import pandas as pd

LOCATION = "oracle instant client 경로"

os.environ["PATH"] = LOCATION + ";" + os.environ["PATH"]
conn = cx_Oracle.connect(USERNAME, PASSWORD, DATABASEINFO)

QUERY = ""

df_ora = pd.read_sql(QUERY, con = conn)
```

