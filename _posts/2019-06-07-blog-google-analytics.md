---
layout: post
title: "[Blog] Google Analytics 추가하기"
comments: true
description: "blog"
tag : [Blog]
---

블로그의 방문자를 확인하고 방문 기록을 데이터로 남겨놓기 위해 구글에서 지원하는 google analytics를 추가해 봅시다.<br>

## 1.Google Analytics에 가입을 합니다.<br>

구글 아이디로 로그인 한 후 아래 링크에 들어가 가입해 봅시다.<br>
[https://analytics.google.com/analytics/web/](https://analytics.google.com/analytics/web/)<br>

#### 1- Sign in을 눌러 가입 페이지로 들어갑니다.<br>
![ga1](https://krispedia.github.io/assets/images/ga_1.jpg)<br>

#### 2- 필요한 부분을 채워 작성합니다<br>
![ga2](https://krispedia.github.io/assets/images/ga_2.jpg)<br>

#### 3- 작성 후 아래 `Get Track ID` 버튼을 누릅니다.<br>
버튼을 누르면 다음과 같은 창이 뜹니다. <br>

지역을 `South Korea` 로 맞춰 주고 그 다음 동의란에 체크합니다.<br>

![ga3](https://krispedia.github.io/assets/images/ga_3.jpg)<br>
![ga4](https://krispedia.github.io/assets/images/ga_4.jpg)<br>

#### 4- tracking ID가 생성 되었습니다! <br>
![ga5](https://krispedia.github.io/assets/images/ga_5.jpg)<br>

검은색으로 가려진 위쪽에 ID가 생성 되었고 <br>
아래쪽에 블로그에 추가할때 필요한 코드가 나옵니다.<br>

## 2.tracking ID를 config.yml 파일에 추가해 줍니다.<br>

![ga6](https://krispedia.github.io/assets/images/ga_6.jpg)<br>

이 블로그를 만들때 사용한 템플릿은 추가적인 파일을 설정해주지 않고 위 사진 처럼 confing.yml에만 ID를 추가해주면 됩니다.<br>

사용하는 템플릿에 따라 코드를 따로 추가해줘야하는 경우가 있습니다.<br>

**파일 변경 후 변경된 config.yml 파일을 `push`합니다.**<br>

## 3.Google Analytics가 잘 작동하는지 확인해 봅시다.<br>

![ga7](https://krispedia.github.io/assets/images/ga_7.jpg)<br>

![ga8](https://krispedia.github.io/assets/images/ga_8.jpg)<br>

모바일에서 블로그에 들어가본 결과 Real-time 으로 접속 위치와 무엇을 보고있는지 확인할 수 있습니다.<br>