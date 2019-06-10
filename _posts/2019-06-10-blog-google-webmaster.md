---
layout: post
title: "[Blog] Google에 블로그 검색어 노출시키기"
comments: true
description: "blog"
tag : [Blog]
---

Jekyll로 생서한 블로그는 수동으로 검색엔진에 노출될 수 있게 해 줘야 합니다. <br>

작성한 포스트들의 조회수를 높이기 위해! 구글에서 검색될 수 있게 노출시켜봅시다.<br>

## 1.구글 웹마스터에 들어가서 시작해봅시다. <br>

#### 1- 구글 아이디로 로그인을 하고 시작하기 버튼을 누릅니다.<br>
![google webmaster 1](https://krispedia.github.io/assets/images/google_webmaster_1.jpg)<br>

#### 2- URL prefix에 블로그 주소를 넣습니다. <br>
![google webmaster 2](https://krispedia.github.io/assets/images/google_webmaster_2.jpg)<br>

만약 기존 관리하는 페이지가 있고 추가로 넣고 싶으시다면 아래와 같이 하면 됩니다.<br>

![google webmaster 3](https://krispedia.github.io/assets/images/google_webmaster_3.jpg)<br>

![google webmaster 4](https://krispedia.github.io/assets/images/google_webmaster_4.jpg)<br>

**`continue` 버튼을 누르고 나면 아래와 같은 창이 뜹니다.** <br>
![google webmaster 5](https://krispedia.github.io/assets/images/google_webmaster_5.jpg)<br>

**`GO TO PROPERTY` 버튼을 누르면 속성 추가가 완료 됩니다**<br>
![google webmaster 6](https://krispedia.github.io/assets/images/google_webmaster_6.jpg)<br>

## 2.이제 추가한 블로그가 본인의 블로그가 맞다는 것을 인증해봅시다.<br>

#### 1- settings에 들어갑니다.<br>
![google webmaster 7](https://krispedia.github.io/assets/images/google_webmaster_7.jpg)<br>

#### 2- Ownership verification에 들어갑니다.(인증을 완료하기 전에는 체크 표시가 나오지 않습니다.)<br>
![google webmaster 8](https://krispedia.github.io/assets/images/google_webmaster_8.jpg)<br>

#### 3- HTML file을 클릭해 다운 받습니다.<br>
![google webmaster 9](https://krispedia.github.io/assets/images/google_webmaster_9.jpg)<br>

파일의 내용은 아래와 비슷할 것입니다.<br>
![google webmaster 10](https://krispedia.github.io/assets/images/google_webmaster_10.jpg)<br>

![google webmaster 11](https://krispedia.github.io/assets/images/google_webmaster_11.jpg)<br>

#### 4- 이 파일을 blog에 추가해 줍니다. <br>
추가할 위치는 `https://krispedia.github.io/google2cc~~~.html` 입니다.<br>
![google webmaster 12](https://krispedia.github.io/assets/images/google_webmaster_12.jpg)<br>

추가 한후 적용하기 위해 `git add & push`를 해 줍니다.<br>

#### 5- 그 후 webmaster에 들어가 확인하면 인증 완료!!<br>
![google webmaster 13](https://krispedia.github.io/assets/images/google_webmaster_13.jpg)<br>

## 3.이제 블로그의 내용을 구글이 가져갈 수 있도록 sitemap을 추가해봅시다.<br>

#### 1- 먼저 블로그의 sitemap의 위치를 확인합니다.<br>
![google webmaster 15](https://krispedia.github.io/assets/images/google_webmaster_15.jpg)<br>

제 블로그의 sitemap은 `_site` 디렉토리 안에 들어있습니다.<br>

#### 2- sitemaps 에 들어갑니다.<br>
![google webmaster 14](https://krispedia.github.io/assets/images/google_webmaster_14.jpg)<br>


#### 3- sitemap의 위치를 적어줍니다.<br>
![google webmaster 16](https://krispedia.github.io/assets/images/google_webmaster_16.jpg)<br>

#### 4- `SUBMIT` 버튼을 눌러 확인합니다.<br>
![google webmaster 17](https://krispedia.github.io/assets/images/google_webmaster_17.jpg)<br>

**정상적으로 등록이 완료 되었습니다!!**<br>

---
완료되고 구글에서 검색이 가능해지는데 까지 시간이 좀 걸리는듯 합니다.<br>

등록후 바로 확인하면 검색이 안 될 수 있습니다.<br>

**등록한 후 2일 후 확인해 본 결과!**<br>

![google webmaster 18](https://krispedia.github.io/assets/images/google_webmaster_18.jpg)<br>

