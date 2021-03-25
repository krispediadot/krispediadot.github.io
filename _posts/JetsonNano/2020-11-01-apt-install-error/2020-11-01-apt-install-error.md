---
layout: post
title: Jetson Nano | apt install 명령어 오류
date: 2020-11-01 11:00:00 +09:00
modified: 
category: jetson nano
tags: [ubuntu18.04]
image: "/assets/img/nvidia_logo.jpg"
cover: "../puzzle.jpg"
---

### apt install 명령어 오류 해결

```
sudo apt install ~~
```

위 멸령어로 설치하려 할때 아래와 같은 오류가 날 때가 있다.  

`E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)`  
`E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?`  


해결 방법은 다음과 같다.  

```
sudo killall apt apt-get
sudo rm /var/lib/apt/lists/lock 
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock*
sudo dpkg --configure -a
sudo apt update
```