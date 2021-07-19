---
layout: post
title: Python | UnboundLocalError 
date: 2021-03-29 23:00:00 +09:00
modified: 
category: python
tags: [scope]
image: "/assets/img/python_logo.png"
cover: ""
---

### 1. 오류 내용
```
UnboundLocalError: local variable 'time' referenced before assignment
```

아래와 같이 `time` 모듈을 가져오고 class 내부에서 사용하려 하니 오류가 났다.<br>
`time`을 지역변수로 인식하는 것이 문제였다.<br>

```python
import time

class A:
    def do_something():
        date = time.strftime("%Y-%m-%d", time.localtime(time.time()))
```

### 2. 해결 방법
<br>
`time`을 전역변수로 받으면 된다.<br>
<br>
```python
import time

class A:
    def do_something():
        global time
        date = time.strftime("%Y-%m-%d", time.localtime(time.time()))
```