---
layout: post
title: Github | SSH port 22 연결 오류 
date: 2024-03-04 12:00:00 +09:00
modified: 
category: [posts, errors]
tags: [github]
image: "/assets/img/github.png"
cover: "../puzzle.jpg"
---

### 1. 오류 내용

오랜만에 git pull을 하려 하니 오류가 발생했다. 

```
ssh: connect to host github.com port 22: Operation timed out
```



### 2. 해결 방법

기본 22 포트로 접속하지 않고 443 포트로 접속하도록 변경

~./ssh/config 파일 내용 수정
```
HOST github
    HostName ssh.github.com
    Port 443
    User git
    IdentityFile ~./ssh/파일
```


---
**참고 자료**<br>
[stackoverflow](https://stackoverflow.com/questions/15589682/how-to-fix-ssh-connect-to-host-github-com-port-22-connection-timed-out-for-g) <br>
