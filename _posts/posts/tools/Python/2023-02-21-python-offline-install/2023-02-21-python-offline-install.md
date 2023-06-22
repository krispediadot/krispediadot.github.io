---
layout: post
title: Python | Offline 환경에서 설치하기
date: 2023-02-21 22:00:00 +09:00
modified: 
category: [posts, tools]
tags: [install]
image: "/assets/img/python_logo.png"
cover: ""
---

### 1. python 다운로드

[공식 홈페이지](https://www.python.org/downloads/) 에 들어가서 설치한다.

.tgz 파일의 압축을 풀고 python을 아래 경로에 위치에 이동시킨다.

```jsx
C:₩Users₩~~USERNAME~~₩AppData₩Local₩Programs₩Python
```

예를 들어, python3.9를 다운 받았다면 python.exe 경로는 아래와 같다.

```jsx
C:₩Users₩~~USERNAME~~₩AppData₩Local₩Programs₩Python₩Python39₩python.exe
```

### 2. 환경변수 path 설정

cmd에서 python을 실행하기 전에 환경변수를 지정해주어야 한다.

환경변수는 python.exe 경로를 미리 시스템에게 알려주어 실행시 매번 python.exe 경로를 찾아 들어가야하는 수고로움을 덜어주는 역할을 한다.

환경변수 설정은 아래 경로에서 할 수 있다.

```jsx
 windows설정 > 시스템 > 정보 > 고급 시스템 설정 > 시스템 속성 > 고급 > 환경변수
```

환경변수는 각 사용자별 변수, 시스템 변수 2가지가 있고 필요에 따라 둘 중 하나를 선택하면 된다.

가상환경을 만들고 가상환경 내에서도 python을 실행시킬 예정이므로 시스템 변수에 path를 추가한다.

시스템 변수 아래 path를 클릭하고 편집을 누르면 환경 변수 편집 이라는 새 창이 팝업된다. 

새로 만들기 버튼을 클릭하고 추가하고자 하는 python의 경로를 축가하고 확인 버튼을 누르면 끝!

### 3. 설치 확인

cmd 창을 열어서 python을 부르면 환경변수에 추가한 python.exe가 실행된다.

이제 python이 설치되었다. 

그러나,

python의 다양한 기능들을 수행하려면 필요한 라이브러리를 다운받아야한다. 

오프라인 환경에서의 라이브러리 설치 방법은 다음 포스트에서 이어 설명할 예정이다.
