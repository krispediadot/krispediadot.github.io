---
layout: post
title: "[GCP] mongodb 서버 설정"
categories: mini-projects
tag : []
---

### 1. Google Cloud 인스턴스 생성
---
![](https://krispedia.github.io/assets/images/gcp_create_instance.gif)

### 2. Ubuntu Linux에 MongoDB 설치
---

[공식문서](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)에 적힌 대로 설치!

#### 2-1 MongoDB public GPG 키 가져오기  
```
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
```
OK 뜨면 성공.


#### 2-2 리스트 파일 생성  
```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
```
#### 2-3 로컬 패키지 reload 
```
sudo apt-get update
```
#### 2-4 MongoDB 설치  
```
sudo apt-get install -y mongodb-org
```
### 3.MongoDB 실행
---
```
sudo systemctl start mongod
```
#### 3-1 실행 확인  
```
sudo systemctl status mongod
```
실행 안되면 중지
```
sudo systemctl stop mongod
```
재실행
```
sudo systemctl restart mongod
```
### 4. Mongo Shell 사용
--- 
```
mongo
```
### 5. 사용자 추가
---
mongo shell 실행 후 

```
use admin

db.createUser({
    user: 'userName',
    pwd: 'userPassword',
    roles: [ "userAdminAnyDatabase",  "dbAdminAnyDatabase",  "readWriteAnyDatabase"]
})

```

### 6. 외부에서 접근 가능하도록 ip 설정
```
sudo vim /etc/mongod.conf
```

```
# network interfaces
net:
  port: 27017
  bindIp: 0.0.0.0

security:
  authorization: enabled
```

재시작
```
sudo systemctl restart mongodb
```

### 7. 방화벽 설정 변경
외부에서 GCP를 인스턴스를 포트에 접속하려면 방화벽 규칙을 설정해줘야함  

#### 7-1 이름 설정
![](https://krispedia.github.io/assets/images/firewall_name.jpg)
#### 7-2 트래픽 방향 설정
수신 / 송신 설정
![](https://krispedia.github.io/assets/images/firewall_traffic.jpg)
둘 다 필요할 경우 각각 만들어 줘야함  

#### 7-3 대상 지정
"네트워크의 모든 인스턴스" 로 변경
![](https://krispedia.github.io/assets/images/firewall_target.jpg)
#### 7-5 소스 IP 범위 지정 
![](https://krispedia.github.io/assets/images/firewall_ip.jpg)
#### 7-6 프로토콜과 포트 번호 지정
![](https://krispedia.github.io/assets/images/firewall_protocol_port.jpg)

### 8. 연결 확인
외부에서 DB 연결
![](https://krispedia.github.io/assets/images/mongodb_check.jpg)