---
layout: post
title: Jetson Nano | ssh 연결 오류
date: 2021-05-11 16:00:00 +09:00
modified: 
category: errors
tags: [ssh]
image: "/assets/img/nvidia_logo.jpg"
cover: "../puzzle.jpg"
---

### 1. 오류 내용
---
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
Please contact your system administrator.
Add correct host key in /Users/sujinlee/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/sujinlee/.ssh/known_hosts:6
RSA host key for [연결할 IP]:포트번호 has changed and you have requested strict checking.
Host key verification failed.
```

### 2. 해결 방법

1단계. known_hosts 파일을 연다. <br>
2단계. `/Users/sujinlee/.ssh/known_hosts:6`를 통해 오류가 나는 위치를 파악한다.<br>
3단계. `:6`를 입력해 6번째 줄로 이동한다. <br>
4단계. `dd`를 입력해 6번째 줄을 제거한다. <br>
5단계. `:wq`를 입력해 저장한다. <br>

------
**참고자료**<br>
- [참고한 블로그](http://www.coolio.so/ssh-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EC%A0%91%EC%86%8D%EC%8B%9C-known_hosts-%EC%B6%A9%EB%8F%8C-%EC%97%90%EB%9F%AC-%EB%B0%9C%EC%83%9D%EC%8B%9C/)