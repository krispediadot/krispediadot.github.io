---
layout: post
title: "[Under The Sea] 1. Data Preperation"
categories: underthesea
tag : []
---

### 1. 데이터 수집
---

#### 1- QUT Fish dataset 
--- 
468종의 3960개의 이미지를 가진 데이터셋<br>
- cropped<br>
![cropped 1](https://krispedia.github.io/assets/images/qut_data_cropped.jpg)<br>

- raw_images<br>
![raw image 1](https://krispedia.github.io/assets/images/qut_data_raw.jpg)<br>

cropped/raw_images 두가지 버전을 중 지느러미 전체를 포함시키기 위해 raw_images 사용.<br> 
raw_images에 검은색으로 패딩을 통해 균일한 크기의 이미지로 재가공함.<br>

- resized_images<br>
![resized image 1](https://krispedia.github.io/assets/images/qut_data_resized.jpg)<br>

###### 장점:
많은 종의 어류 데이터를 가지고 있음<br>
파일 이름으로 종을 분류할 수 있어 레이블 데이터가 따로 필요하지 않음<br>

###### 단점:
한 종마다 10개 내외의 데이터가 있으며 일부는 3개의 데이터가 있는 경우도 있음 <br>
이미지가 아닌 그림 데이터도 포함되어 있음<br>

#### 2- 교내 수산과학대학의 데이터<br>
--- 
교내 수산과학대학의 한 연구실에서 보유하고 있는 데이터<br>

###### 장점:
한 종의 어류를 여러 각도로 찍어놓음<br>

###### 단점:
기밀 데이터이다보니 데이터를 공유할 수 없음<br>
허가 받은 사람만 데이터에 접근할 수 있으며 학습에 사용할 수 있음<br>

#### 3- 웹 크롤링을 통한 데이터 수집 
--- 
Python을 활용해 google image를 웹크롤링 한 데이터.<br>

###### 장점: 
원하는 수만큼 데이터를 모을 수 있음<br>

###### 단점:
데이터의 품질이 떨어져 데이터를 걸러낼 필요가 있음<br>

### 2. annotation 파일 생성
---
Mask RCNN 모델에서 학습을 시키기 위해 annotation 파일이 필요<br>
전체 데이터 중 일부만 annotation 파일 생성<br>
[VGG Image Annotator(VIA)](https://www.robots.ox.ac.uk/~vgg/software/via/) 를 사용해 annotation 파일 생성<br>

- polygon 형태의 annotation<br>
![vgg annotation 1](https://krispedia.github.io/assets/images/underthesea_vgg_img.jpg)<br>

- 생성된 annotation.json<br>
![vgg annotation 2](https://krispedia.github.io/assets/images/underthesea_vgg_ann.jpg)<br>

