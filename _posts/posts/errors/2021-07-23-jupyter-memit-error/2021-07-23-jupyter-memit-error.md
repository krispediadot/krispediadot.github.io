---
layout: post
title: jupyter | UsageError ~~ '%memit` not found.
date: 2021-07-23 13:00:00 +09:00
modified: 
category: [posts, errors]
tags: [profiler]
image: "/assets/img/python_logo.png"
cover: ""
---

### 1. 오류 내용

파이썬 코드를 프로파일링 하기 위해서 `%memit`을 사용하려다가 오류가 발생했다.<br>

```bash
UsageError: Line magic function `%memit` not found.
```

### 2. 해결 방법

가장 먼저 memory_profiler가 설치 되어있는지 확인한다.<br>

```bash
pip install memory_profiler
```

그 후, jupyter-notebook 또는 jupyter-lab 에서 사용하면 된다.<br>

```bash
%load_ext memory_profiler
%memit print("test")
```