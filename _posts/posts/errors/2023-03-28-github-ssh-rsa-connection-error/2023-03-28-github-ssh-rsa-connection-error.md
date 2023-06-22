---
layout: post
title: Github | SSH RSA KEY 사용 중 발생한 오류 
date: 2023-03-28 13:00:00 +09:00
modified: 
category: [posts, errors]
tags: [github]
image: "/assets/img/github.png"
cover: "../puzzle.jpg"
---

### 1. 오류 내용

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
SHA256:uNiVztksCsDhcc0u9e8BujQXVUpKZIDTMczCvj3tD2s.
Please contact your system administrator.
Add correct host key in ~/.ssh/known_hosts to get rid of this message.
Host key for github.com has changed and you have requested strict checking.
Host key verification failed.
```

### 2. 해결 방법

우선 오류가 발생한 원인은 2023.3.Github에서 RSA SSH Host key를 업데이트 했기 때문이다. 

ssh key를 ed25519로 다시 생성해서 연결하는 방법으로 해결했다.

##### 1) SSH KEY 재생성
```
ssh-keygen -t ed25519 -C "example@mail.com"
```

##### 2) ~./ssh/config 파일 내용 수정
```
HOST github
    HostName github.com
    IdentityFile ~./ssh/새로 생성한 파일
```


---
**참고 자료**<br>
[https://github.blog/2023-03-23-we-updated-our-rsa-ssh-host-key/](https://github.blog/2023-03-23-we-updated-our-rsa-ssh-host-key/) <br>
