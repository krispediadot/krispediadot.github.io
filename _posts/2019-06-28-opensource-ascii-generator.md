---
layout: post
title: "[Opensource] Ascii-generator"
categories: Side_Projects
tag : [Opensource]
---

 흥미로운 git 프로젝트를 찾아보다가 이미지를 아스키 문자로 표현해주는 프로젝트가 있어서 실행시켜 보려 합니다. <br>
(아래에서 진행하는 순서는 github.com에 올라와있는 다른 프로젝트를 실행하는데 적용할 수 있습니다.)<br>

프로젝트 링크: 
[https://github.com/vietnguyen91/ASCII-generator](https://github.com/vietnguyen91/ASCII-generator)<br>

## 0.먼저 Requirements를 맞춰 줍니다.<br>

---

**반!드!시! 아래 조건을 설치한 후 다음으로 넘어가야 합니다!**<br>

- Python3.6<br>
- cv2<br>
- PIL<br>
- numpy<br>


## 1.git clone을 해서 프로젝트를 내려 받습니다. <br>

---

#### 1- 프로젝트 첫 페이지에 있는 clone or download 버튼을 눌러 ssh 값을 가져옵니다.<br>
![git clone 1](https://krispedia.github.io/assets/images/ascii_generator_1.jpg)<br>

#### 2- 그 후 내려 받을 위치에 와서 git clone을 적고 방금 가져온 ssh 값을 넣습니다. <br>

(아래의 사진은 제가 실행한 사진입니다. 저기에 `git@open` 부분이 가져온 ssh 값과 다릅니다. 제가 `github.com`을 `open`이라는 값으로 미리 지정해놓아서 입니다. `github.com`을 사용하시면 됩니다.)<br>
![git clone 2](https://krispedia.github.io/assets/images/ascii_generator_2.jpg)<br>

## 2.이제 실행시켜보겠습니다. <br>

---

#### 1- img2img.py를 실행시켜보겠습니다.<br>
![git clone 3](https://krispedia.github.io/assets/images/ascii_generator_3.jpg)<br>

#### 2- 결과값을 확인해보겠습니다.<br>
![git clone 4](https://krispedia.github.io/assets/images/ascii_generator_4.jpg)<br>

**설명에 나온 결과와 똑같이 나옵니다!**<br>

#### 3- 입력 이미지를 바꿔 보겠습니다.<br>
![git clone 5](https://krispedia.github.io/assets/images/ascii_generator_5.jpg)<br>

#### 결과<br>
- input<br>
![git clone 6](https://krispedia.github.io/assets/images/ascii_generator_6.jpg)<br>
- output<br>
![git clone 7](https://krispedia.github.io/assets/images/ascii_generator_7.jpg)<br>