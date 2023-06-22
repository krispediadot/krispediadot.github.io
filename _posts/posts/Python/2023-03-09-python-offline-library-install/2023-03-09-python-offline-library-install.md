---
layout: post
title: Python | Offline 환경에서 라이브러리 설치하기
date: 2023-03-09 19:00:00 +09:00
modified: 
category: python
tags: [install]
image: "/assets/img/python_logo.png"
cover: ""
---

### 1. python 라이브러리 다운로드

[공식 홈페이지](https://pypi.org/) 에 들어가서 필요한 라이브러리를 다운받는다.

Offline 환경에서 설치할 예정이므로

built distributions 중 시스템에 알맞은 .whl 파일을 다운받는다. 


### 2. 가상환경 설정 및 실행

파이썬 라이브러리의 경우 개발하다보면 버전이 맞지 않아서 문제가 생기는 경우가 있다. 

따라서, 가상환경을 설정해서 각 task에 필요한 라이브러리를 따로 관리하는 것이 효율적이다. 

우선, 가상환경을 생성한다. 

```
python -m venv [가상환경이름]
```

가상환경을 실행시킨다.
(실행 경로는 설치된 위치에 따라 다를 수 있으며 편의를 위해 추가적인 도구를 사용할 수도 있다.)

```
cd [가상환경이름]/Scripts
activate
```

### 3. 라이브러리 설치하기

필요한 라이브러리 .whl 파일을 가상환경 아래 하나의 폴더를 만들어 관리하면 편리하다. 

가상환경을 실행하고 .whl 파일이 있는 위치로 이동한다. 

그 후, 아래 명령어를 사용해섯 라이브러리를 설치한다. 

```
python -m pip install --no-index --find-links="./" [설치하려는 라이브러리 파일명.whl]
```

### **의존성 있는 라이브러리 설치 시

다른 라이브러리와 의존성을 가지고 있는 라이브러리를 설치한다면

아래 명령어로 한번에 여러 .whl 파일을 다운받아서 한번에 설치하면된다.

```
python -m pip download [라이브러리명]
python -m pip install --no-index --find-links="./" [설치하려는 라이브러리 파일명.whl]
```

