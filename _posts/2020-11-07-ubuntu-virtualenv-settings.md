---
layout: post
title: "[Ubuntu 18.04] virtualenv & virtuelenvwrapper 설정 "
categories: 
tag : []
---

1. 설치
---
```
pip install virtualenv
pip install virtualenvwrapper
```

2. 설정
---
```
export WORKON_HOME=~/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON="$(which python3)"
export VIRTUALENVWRAPPER_VIRTUALENV=/usr/local/bin/virtualenv
source /usr/local/bin/virtualenvwrapper.sh
```

3. 사용  
---
`mkvirtualenv 이름 --python=python3`: 가상 환경 생성  
`workon 이름`: 가상 환경 실행  
`deactivate`: 가상 환경 빠져나오기  







`screen -S 세션이름`: 특정 세션이름으로 새로운 스크린 생성  
`screen -r 세션이름`: 특정 세션 attach  
`exit`: 해당 세션 제거
`Ctrl+a d`: 기본 스크린으로 이동  
