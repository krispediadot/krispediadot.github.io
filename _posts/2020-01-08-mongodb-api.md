---
layout: post
title: "[MongoDB] DB에 저장된 데이터 Json 형식 api로 제공하기"
categories: db
tag : [MongoDB]
---

#### 1. Django 프로젝트 생성
프로젝트를 진행 할 폴더 만들기 
```
mkdir mongo_api
```
Django 프로젝트 생성하기  
```
django-admin startproject mongo_api
```

#### 2. MongoDB에 접속 할 수 있도록 `mongo`모듈을 만들기 
pymongo 가 필요하므로 없다면 아래 명령어로 설치 
```
pip install pymongo
```

**모듈의 위치 = mongo_api/mongo_api/mongo.py**  

모듈 작성  
```python 
from pymongo import MongoClient

class MongoDB():
    def __init__(self, server, dbName, collectionName):
        self.Client = MongoClient(server)
        self.Db = self.Client.get_database(dbName)
        self.Collection = self.Db.get_collection(collectionName)

if __name__ == "__main__":
    db = MongoDB('127.0.0.1', 'local','startup_log')
    for item in db.Collection.find({}):
        print(item['hostname'])
```

localhost서버의 local 데이터베이스의 startup_log 데이터로 테스트 한다.

```
python mongo.py
```

**DB에 들어있는 데이터가 제대로 출력 된다면 성공!**  

#### 3. mongo_api/mongp_api/views.py 파일 생성하기

```python
from django.http import JsonResponse

from . import mongo

DB = mongo.MongoDB('127.0.0.1', 'local','startup_log')

dbconnector = {'log': DB}

def startupLog(request, dbname):
    res = {}
    res['items'] = []
    db = dbconnector[dbname]
    res['itemLen'] = db.Collection.count_documents({})

    for item in db.Collection.find({}):
        each = {'hostname':'',
                'startTime':''}
        each['hostname'] = item['hostname']
        each['startTime'] = item['startTime']

        res['items'].append(each)
    
    return JsonResponse(res, safe=False)
```

#### 4. urls.py 파일 설정하기
```python
from django.contrib import admin
from django.urls import path

from . import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('<dbname>', views.startupLog)
]
```

#### 5. Django 실행하기 

mongo_api 폴더가 있는 동일한 위치에서 manage.py 파일 찾은 후 차례로 실행  

```
python manage.py migrate
python manage.py runserver
```

#### 6. 출력 확인하기 
![mongo_api](https://krispedia.github.io/assets/images/mongo_api.png)