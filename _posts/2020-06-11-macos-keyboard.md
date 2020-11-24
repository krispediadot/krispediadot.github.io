---
layout: post
title: "[MacOS] Windows용 키보드 MacOS에서 사용하기"
categories: 
tag : []
---

최근 기계식 키보드에 관심을 가지면서 MacOS 전용으로 나온 기계식 키보드가 정말 얼마 없다는 것을 알게 되었다. 기계식이 아닌 일반적으로 많이 사용하는 멤브레인 방식의 키보드도 MacOS 전용으로 나온것이 많이 없지만 기계식으로는 더 없다💧

찾아본 결과로는 맥북에서 사용할 수 있는 기계식 키보드로는 킥스타터 $1,000 달성으로 유명한 '[키크론](http://keychron.kr/)'에서 나오는 제품과 '[바밀로](http://funkeys.co.kr/)' 제품이 있었다. (이보다 더 있을 수도)

'키크론 k2' 제품을 구매하고 싶지만 방향키 배열이 불편할 것 같아 보이고 곧 새로 나올 '키크론 k8' 제품을 보니 딱 원하는 키 배열이라 좀 더 기다릴 것이다.

그동안 '레오포드 FC750R' 키보드를 사용하려고 중고로 구매했다.
'레오포드 FC750R' 제품의 설명서에는 MacOS는 지원하지 않는다고 적혀있다. 

![macos not supported](https://krispediadot.github.io/assets/images/macos_not_supported.jpg)

키보드 키 역시 MacOS용 command 등등의 키들이 없다. 

하지만 간단한 설정으로 Windows용으로 나온 키보드를 MacOS에서 기본 내장키보드처럼 사용할 수 있다.  

아래의 내용은 https://cornswrold.tistory.com/305 포스트를 참고했다.  

### 1. System Preference -> Keyboard
---
키보드 설정에 들어간다.

![keyboard](https://krispediadot.github.io/assets/images/systempreference_keyword.jpg)

### 2. Modifier Keys...
---
키 설정에 들어간다. 

![modifier keys](https://krispediadot.github.io/assets/images/modifier_keys.jpg)

### 3. select keyboard -> HID Keyboard
---
Apple Internal Keyboard 에서 HID Keyboard로 변경한다.

![select keyboard](https://krispediadot.github.io/assets/images/select_keyboard.jpg)

![HID Keyboard](https://krispediadot.github.io/assets/images/hid_keyboard.jpg)

### 4. Option Key, Command Key 설정 변경
---
아래와 같이 2개 키의 설정을 변경한 후 `OK` 버튼을 누른다. 

![option command key](https://krispediadot.github.io/assets/images/option_comment_key.jpg)

### 5. (옵션) 키보드의 키를 변경한다.
---
command 키캡이 없으니 Windows 키로 대체  
option 키가 따로 없으니 Alt 키로 대체  

![change keys](https://krispediadot.github.io/assets/images/change_keys.jpg)

이렇게 설정을 하면 최대한 Windows용 키보드를 MacOS 기본 내장 키보드와 비슷하게 사용할 수 있다. 그리고 기본 내장된 키보드에는 변경사항의 영향이 없다.

이상 끝!!


위의 방법으로 변경해서 사용하는 것도 나쁘진 않지만
이런 수고로움 없이 키보드를 사용할 수 있게 MacOS용 키보드가 많아지면 좋겠다. 

