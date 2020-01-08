---
layout: post
title: "[MongoDB] homebrew 사용하지 않고 설치 및 설정하기"
categories: db
tag : [MongoDB]
---

homebrew 업데이트를 하면서 문제가 생겼고 `brew install mongodb`를 할 수 없어 homebrew 없이 MongoDB를 설치하게 되었다.  

#### 1. MongoDB 다운받기
---
[https://www.mongodb.com/download-center/community](https://www.mongodb.com/download-center/community) 에서 MongoDB를 다운 받는다.  

#### 2. 압축 풀고 위치 지정하기
---
###### 1- 다운로드 한 위치로 간다.  
```
cd Download
```
###### 2- 압축을 푼다.(다운받은 버전에 따라 그리고 환경에 따라 파일 명이 다르니 확인!!)  
```
tar mongodb-macos-x86_64-4.2.2.tar
```

###### 3- 압축을 푼 파일을 `/usr/local/mongodb/`위치로 옮긴다.  
```
sudo mv mongodb-macos-x86_64-4.2.2 /usr/local/mongodb
```

###### 4- `/usr/local/` 위치로 가서 MongoDB가 쌓일 데이터 공간을 만들어 준다.
```
cd ~/usr/local/
sudo mkdir -p /data/db
```  

###### 5- 사용하고 있는 사용자가 누구인지 확인한다.  
```
whoami
``` 

###### 6- 새로 만든 공간의 권한을 변경한다. 사용자 이름 사용!! (`whoami`결과)  
```
sudo chown 사용자이름 /data/db
```

#### 3. 쉘 설정하기
--- 
###### 1- zsh을 사용중이니 `.zshrc` 파일의 설정을 추가한다.   
```
vim ~/.zshrc
```  

###### 2- `.zshrc` 파일의 가장 아래에 다음 코드를 추가한다.   
```
export MONGO_PATH=/usr/local/mongodb
export PATH=$PATH:$MONGO_PATH/bin
```

###### 3- `.zshrc` 파일을 저장한 후 다음 명령어를 실행시킨다.  
```
source ~./zshrc
``` 

#### 4. 설치 완료 확인하기
--- 
```
mongod  
mongo
```  

