---
layout: post
title: "[Blog] Naver에 블로그 검색어 노출시키기"
categories: Blog
tag : [Blog]
---


Jekyll로 생서한 블로그는 수동으로 검색엔진에 노출될 수 있게 해 줘야 합니다. <br>

작성한 포스트들의 조회수를 높이기 위해! 네이버에서 검색될 수 있게 노출시켜봅시다.<br>

## 1.네이버 웹마스터에 들어가서 시작해 봅시다.<br>
[https://webmastertool.naver.com](https://webmastertool.naver.com)

#### 1- 로그인 해서 웹마스터에 들어옵니다.<br>
![google webmaster 1](https://krispedia.github.io/assets/images/naver_webmaster_1.jpg)<br>

#### 2- 블로그 주소를 추가합니다.<br>
![google webmaster 2](https://krispedia.github.io/assets/images/naver_webmaster_2.jpg)<br>

## 2.블로그 주인임을 인증해봅시다.<br>

#### 1- HTML파일을 다운 받습니다.<br>
![google webmaster 4](https://krispedia.github.io/assets/images/naver_webmaster_4.jpg)<br>
![google webmaster 5](https://krispedia.github.io/assets/images/naver_webmaster_5.jpg)<br>

#### 2- HTML파일을 루트 위치에 넣고 git add & push 합니다.<br>
![google webmaster 6](https://krispedia.github.io/assets/images/naver_webmaster_6.jpg)<br>

#### 3- 그 후 화면으로 돌아와 확인 버튼을 누릅니다.<br>

**확인 누른 후**
![google webmaster 3](https://krispedia.github.io/assets/images/naver_webmaster_3.jpg)<br>

## 3.이제 네이버에서 블로그 내용을 읽어갈 수 있게 설정합시다.<br>

#### 1- sitemap.xml 파일올리기<br>
블로그의 sitemap.xml 파일의 위치를 올려주면 됩니다.<br>

![google webmaster 7](https://krispedia.github.io/assets/images/naver_webmaster_7.jpg)<br>
![google webmaster 8](https://krispedia.github.io/assets/images/naver_webmaster_8.jpg)<br>

#### 2- robot.txt 파일 만들기<br>
![google webmaster 11](https://krispedia.github.io/assets/images/naver_webmaster_11.jpg)<br>

![google webmaster 12](https://krispedia.github.io/assets/images/naver_webmaster_12.jpg)<br>

robot.txt에 가서 간단 생성을 참고해 robot.txt 파일을 만듭니다.<br>
![google webmaster 13](https://krispedia.github.io/assets/images/naver_webmaster_13.jpg)<br>

#### 4- robot.txt 파일 추가하기<br>
생성한 robot.txt 파일을 루트 위치에 넣어줍니다.<br>
![google webmaster 14](https://krispedia.github.io/assets/images/naver_webmaster_14.jpg)<br>

그 후 `git add & push`로 적용시킵니다.<br>

#### 5- RSS 제출을 위해 feed.xml 파일 올리기<br>
![google webmaster 9](https://krispedia.github.io/assets/images/naver_webmaster_9.jpg)<br>
![google webmaster 10](https://krispedia.github.io/assets/images/naver_webmaster_10.jpg)<br>


이상 등록이 완료 되었습니다.<br>


**1일 후 수집 현황**
![google webmaster 15](https://krispedia.github.io/assets/images/naver_webmaster_15.jpg)<br>