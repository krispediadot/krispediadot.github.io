---
layout: post
title: "[MongoDB] docker로 MongoDB 실행하기"
categories: database
tag : [MongoDB]
---

구글 클라우드를 썻으나 무료 체험이 거의 끝나가 로컬에서 잠시 사용해야 할것 같다.  

mongo 를 로컬 컴퓨터에 설치하기 싫으니 docker로 사용하기로  


#### 1. docker-compose.yml 작성  
[참고](http://junil-hwang.com/blog/docker-mongodb/)  
위 포스트를 참고했다.  
```yml
version: "3.2"      # version 정보를 작성합니다.

services:           # service 목록을 정의합니다.
  mongodb:          # service의 이름입니다.
    image: mongo    # 해당 service에서 사용할 image입니다.
    restart: always # container를 실행할 때 항상 이미 수행중이라면 재시작을 수행합니다.
    environment:    # 환경변수를 정의합니다.
      MONGO_INITDB_ROOT_USERNAME: **유저네임**
      MONGO_INITDB_ROOT_PASSWORD: **유저패스워드**
    volumes:        # container -> local로 mount할 수 있습니다.
      - type: bind 
        source: ./data/db # local 경로
        target: /data/db  # container 내부에서의 경로
    container_name: "mongodb" # container의 name을 정의합니다.
    ports:                # service port를 정의합니다.
      - "27017:27017"     # local:container

```

#### 2. docker 실행 
```
docker-compose up -d
```

#### 3. docker 실행되는 컨테이너 들어가서 설정
```
docker exec -it mongodb bash
```
```
mongo -u 유저네임 -p 유저패스워드
```

#### 4. NoSQL booster 연결
![connect](https://krispediadot.github.io/assets/images/mongodb_nosql_connect.png)


---
**참고자료**  
[https://dev.to/sonyarianto/how-to-spin-mongodb-server-with-docker-and-docker-compose-2lef](https://dev.to/sonyarianto/how-to-spin-mongodb-server-with-docker-and-docker-compose-2lef)

