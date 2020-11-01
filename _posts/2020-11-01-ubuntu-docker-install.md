---
layout: post
title: "[Ubuntu 18.04] docker 설치 "
categories: 
tag : []
---

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

아래 명령어로 설치 완료!  

```
sudo snap install docker
```