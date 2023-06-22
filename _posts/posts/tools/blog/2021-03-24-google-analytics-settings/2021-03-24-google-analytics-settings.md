---
layout: post
title: Jekyll | google analytics 추가하기
date: 2021-03-24 11:00:00 +09:00
modified: 
category: [posts, tools]
tags: [jekyll]
image: "/assets/img/jekyll_logo.png"
cover: "../puzzle.jpg"
---

### 1. 변경 이유

Jekyll 블로그의 테마를 변경하고 나니 google analytics가 제대로 동작하지 않았다. <br>

`_config.yml` 파일에 `google_analytics:` 항목이 있어서 User ID 값만 넣었는데 어딘가 문제가 있는듯 했다. <br>

구조를 살펴보니 `footer.html` 에서 `assets/js/galite.js` 파일을 통해 google analytics를 사용하도록 연결되어 있어 보였다. <br>

google analytics를 `dafault.html`에서 추가하도록 변경 할 겸 아래와 같이 변경했다.<br>

### 2. 변경 내용

1. google analytics에서 제공하는 추적코드(`gtag.js`)를 `analytics.html` 파일에 추가
1. `default.html` 파일에 `analytics.html` 추가

### 3. 변경 방법

1. 추적 코드 추가<br>
google analytics의 `계정 관리 > 추적 정보 > 추적 코드`에서 `gtag.js` 코드를 확인할 수 있다. 이 코드에는 각 계정의 추적 ID 정보가 들어있으니 본인의 코드를 사용해야 한다.<br>
<br>이 코드를 `_include/analytics.html` 파일에 복사한다.<br>
1. 기본 파일에 analytics <br>
`default.html` 파일의 `</body>` 바로 직전에 `include analytics.html` 코드를 추가<br>   


이상 끝!!💡   
