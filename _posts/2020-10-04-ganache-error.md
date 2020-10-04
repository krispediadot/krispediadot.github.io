---
layout: post
title: "ganache node14 사용시 에러"
categories: 
tag : []
---

brew 로 node 14 설치하고 ganache-cli를 실행하려 하니 오류가 생겼다.  

```
Error: Callback was already called.
```

node 버전을 14->12로 변경해서 해결했음!  

```
brew unlink node
brew install node@12
brew link node@12
```


