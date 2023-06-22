---
layout: post
title: Python | tensorflow import시 Could not find the DLL(s) 'msvcp140_1.dll' 에러
date: 2023-04-13 14:00:00 +09:00
modified: 
category: [posts, errors]
tags: [install]
image: "/assets/img/python_logo.png"
cover: ""
---

### 1. 오류 내용

```
ImportError: Could not find the DLL(s) 'msvcp140_1.dll'. TensorFlow requires that these DLLs be installed in 
a directory that is named in your %PATH% environment variable. You may install these DLLs by downloading "Microsoft C++ Redistributable for Visual Studio 2015, 2017 and 2019" for your platform from this URL: https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads
```

### 2. 해결 방법

우선 오류가 발생한 원인은 2023.3.Github에서 RSA SSH Host key를 업데이트 했기 때문이다. 

ssh key를 ed25519로 다시 생성해서 연결하는 방법으로 해결했다.

##### 1) msvcp140_1.dll 다운로드

online 환경에서 msvcp140_1.dll 파일을 다운로드 받는다.<br>

##### 2) msvcp140_1.dll 파일 추가

C:\Windows\System32 <br>
또는<br>
C:\Windows\SysWOW64 <br>

위치에 msvcp140_1.dll 파일을 추가한다.<br>

##### 3) vc_redist 설치 및 실행

오류 메세지에서 안내한 내용대로 [https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) 위치에서 환경에 알맞은 vc_redist 다운받고 실행한다.

**그럼 끝!**

---
**참고 자료**<br>
[https://stackoverflow.com/questions/60157335/cant-pip-install-tensorflow-msvcp140-1-dll-missing](https://stackoverflow.com/questions/60157335/cant-pip-install-tensorflow-msvcp140-1-dll-missing) <br>
