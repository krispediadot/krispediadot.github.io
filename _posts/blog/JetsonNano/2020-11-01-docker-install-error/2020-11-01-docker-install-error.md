---
layout: post
title: Jetson Nano | docker 설치 오류
date: 2020-11-01 11:00:00 +09:00
modified: 
category: jetson nano
tags: [ubuntu18.04, docker]
image: "/assets/img/nvidia_logo.jpg"
cover: "../puzzle.jpg"
---

### 1. 오류 내용
```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update
apt-cache policy docker-ce
```

위 명령어로 설치하려 했지만  

`Package 'docker-ce' has no installation candidate` 에러가 났다.  

### 2. 해결 방법  
```
sudo snap install docker
```