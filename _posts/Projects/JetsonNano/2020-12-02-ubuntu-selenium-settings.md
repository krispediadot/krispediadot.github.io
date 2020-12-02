---
layout: post
title: "[Ubuntu 18.04] python selenium 사용을 위한 준비 "
categories: jetsonnano
tag : []
---

### 1. chromium-driver 설치
---
```
sudo apt-get install chromium-chromedriver
```

selenium을 사용하기 위해서는 드라이버가 필요하므로 <br>
위 명령어로 드라이버를 설치한다. <br>

설치된 드라이버의 버전을 확인한다. <br>
![driver_version_1] (https://krispediadot.github.io/assets/images/driver_version_1.jpg)

### 2. chromium-broswer 버전 업데이트
---

기존에 설치되어있는 chromium의 버전을 확인한 결과 78.0.3904.108 이었으므로 업그레이드가 필요했다. <br>

```
apt search chromium-brower
```
위 명령어를 실행한 결과 설치할 패키지를 찾을 수 있었다.<br>
![driver_version_2] (https://krispediadot.github.io/assets/images/driver_version_2.jpg)

```
sudo apt-get install chromium-browser
```
위 명령어를 실행해 설치했다. <br>

설치 후 버전 확인<br>
![driver_version_3] (https://krispediadot.github.io/assets/images/driver_version_3.jpg)

### 3. 사용  
---
![selenium_1] (https://krispediadot.github.io/assets/images/selenium_1.jpg)


<div class="divider"></div>
**[참고 자료]**
- [참고1](https://medium.com/dropout-analytics/selenium-webdriver-on-jetson-nano-4e38cca8e61d)