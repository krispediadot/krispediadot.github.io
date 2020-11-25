---
layout: post
title: "[Blog] jekyll 블로그에 favicon 추가하기"
categories: blog
tag : [blog]
---

jekyll 로 github.io 블로그를 만들고 나면 탭에 표시되는 [favicon](https://ko.wikipedia.org/wiki/%ED%8C%8C%EB%B9%84%EC%BD%98)은 기본으로 설정되어있습니다.<br>

이것을 변경해봅시다.<br>

### 1. 이미지 선택 
---
![favicon_1](https://krispediadot.github.io/assets/images/favicon_1.jpg) 


### 2. favicon.ico 파일 생성
---
온라인 generator를 사용하거나<br> 
또는<br> 
이미지 편집으로(16x16/32x32 pixel) 직접 파일을 생성하면 됩니다. <br>

### 3. jekyll 디렉토리에 추가 
---
![favicon_2](https://krispediadot.github.io/assets/images/favicon_2.jpg) 


**이렇게만 추가한 경우 로컬에서는 탭에 이미지가 나왔지만 실제 블로그에는 적용되지 않았습니다.**<br>

**아래의 코드를 추가해 위 문제를 해결했습니다.**<br>

### 4. _layouts/default.html 파일에 코드 추가 
---
```
<!DOCTYPE html>
<html>
    <head>
	    <link rel="shortcut icon" type="image/x-icon" href="https://krispediadot.github.io/favicon.ico">
    </head>
    ~~~
</html>
```

파일 위치는 각자의 블로그에 따라 달라지니 그에 맞춰 변경해야합니다. <br>

### 5. 결과 확인 
---
![favicon_3](https://krispediadot.github.io/assets/images/favicon_3.jpg) 
