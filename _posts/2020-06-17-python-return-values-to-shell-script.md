---
layout: post
title: "[Shell Script] Python 리턴 값을 쉘 스크립트로 전달하기"
categories: 
tag : []
---

코드의 자동화를 위해 크론탭 등의 설정을 하다보니 쉘 스크립트 공부가 필요함을 느끼고 있다.  

mongodb의 백업을 위해 스크립트를 작성하던 도중 파이썬 코드로 확인한 변수 값을 쉘 스크립트로 전달하는 코드가 필요했고 일단 방법을 모르니 구글신에게 한글로 '파이썬 리턴값을 쉘 스크립트로 전달' 이라는 키워드로 찾아봤지만 원하는 답을 찾을 수 없었다. 그래서 영어로 검색해 여러 stackoverflow 글들을 참고해 아래와 같은 코드를 작성했다.  

_쉘 스크립트를 기초부터 공부한게 아니라 아래의 코드가 잘못된 부분이 있을 수 있고 더 효율적인 방법이 있을 수 있으니 이 글을 보시는 분께서 더 좋은 방법이 있으시다면 알려주시면 감사하갰습니다._

### 1. 원하는 값을 가져오는 python 코드 작성
---
파이썬 코드를 통해 얻고자 하는 값은 mongodb의 db 이름과 collection 이름이었다.  

따라서 pymongo의 MongoClient를 사용해 아래와 같은 코드를 작성했다.  

```python
# dbNames.py

import sys

from pymongo import MongoClient
mongo = MongoClient(host=서버 이름,
                     port=27017, 
                     username=사용자 ID, 
                     password=사용자 비밀번호,
                    authSource="admin")

dbNames = mongo.list_database_names()

if sys.argv[1] == 'dbNames':
  for each in dbNames:
    print(each)

elif sys.argv[1] == 'collectionNames':
  collectionNames = mongo[sys.argv[2]].list_collection_names()
  for each in collectionNames:
    print(each)
```

db이름을 가져오는 일과 collection이름을 가져오는 일, 2가지 일을 argvs 값에 따라 선택할 수 있게 한 코드이다.  

```
python3 dbNames.py dbNames
``` 

위 명령어로 실행시키면 해당 mongodb에 존재하는 모든 db 이름들이 한 줄에 하나씩 출력된다.  

```
python3 dbNames.py collectionNames [db이름]
``` 

위 명령어를 실행시키면 db이름에 들어있는 collection 이름들이 한 줄에 하나씩 출력된다.  

이렇게 출력되는 값을 쉘 스크립트에 전달해보자!!  

### 2. 리턴 값을 전달 받을 쉘 스크립트 작성
---
쉘 스크립트에서 db 이름과 collection 이름을 받아 해당 collection의 백업 파일을 만드는 일을 하길 원한다.  

따라서 코드 안에 필요한 요소와 기능이 아래 4가지이다.   
1. 백업 파일 이름을 만들 때 필요한 시간
2. db 이름
3. db에 있는 collection 이름  
4. mongodb 해당 collection 백업

이렇게 정하고 아래 코드를 작성했다.  

```bash
# backup.sh
#!/bin/bash

# 1. 백업 파일 이름을 만들 때 필요한 시간
echo "sync date and clock from time server"
rdate -s time.bora.net && clock -w
dat=`date +%Y-%m-%d_%H%M`

# 2. db 이름
# argv[1] = dbNames 로 db 이름 받아옴 
DBNames=$(python3 dbNames.py dbNames)
#echo $DBNames

for db in $DBNames;
do
  # admin 내용은 제외
  if [ $db = "admin" -o $db = "local" ]; then
    echo 'admin contents'
  # admin 내용 아닌건 백업
  else
    # 3. db에 있는 collection 이름
    echo 'DB Name ===' $db
    # argv[1] = collectionNames, argv[2] = db이름으로 해당 db에 있는 collection 이름 가져옴. 
    COLLECTIONNames=$(python3 dbNames.py collectionNames $db)
    for collection in $COLLECTIONNames;
    do 
      # 4. mongodb 해당 collection 백업
      echo $collction
      mongodump --archive=/저장위치/[${db}]_${collection}_${dat}.gz --gzip --authenticationDatabase admin --username 사용자 이름 --password 사용자 비밀번호 --db $db --collection $collection
    done    
  fi
done
```

코드를 작성하고 

```
chmod +x backup.sh
/bin/bash backup.sh 
```

권한을 설정하고 쉘 스크립트를 실행하면 db 내 collection 하나씩 백업 파일이 생성되는 것을 확인 할 수 있다.  

위 코드에 조건을 추가하면 원하는 db만 또는 원하는 collection만 백업 파일을 생성하게 할 수 있을 것이다.  


-----
다른 방법으로는 python의 sys모듈을 사용하는 방법도 있다.  
정확한 내용은 구글신에게 물어보면 답을 해 주실것임.  