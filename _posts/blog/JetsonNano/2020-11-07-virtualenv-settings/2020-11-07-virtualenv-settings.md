---
layout: post
title: Jetson Nano | virtualenv & virtuelenvwrapper 설정
date: 2020-11-07 11:00:00 +09:00
modified: 
category: jetson nano
tags: [ubuntu18.04, virtualenv]
image: "/assets/img/nvidia_logo.jpg"
cover: "../puzzle.jpg"
---

### 1. 설치
---
```
pip install virtualenv
pip install virtualenvwrapper
```

### 2. 설정

zsh를 사용중이므로 .zshrc 파일에 아래 설정 내용을 추가(다른 커널을 사용한다면 해당 커널에 맞는 파일을 수정)

---
```
export WORKON_HOME=~/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON="$(which python3)"
export VIRTUALENVWRAPPER_VIRTUALENV=/usr/local/bin/virtualenv
source /usr/local/bin/virtualenvwrapper.sh
```

### 3. 사용  
---
`mkvirtualenv 이름 --python=python3`: 가상 환경 생성  
`workon 이름`: 가상 환경 실행  
`deactivate`: 가상 환경 빠져나오기  
`rmvirtualenv 이름`: 가상 환경 삭제  
