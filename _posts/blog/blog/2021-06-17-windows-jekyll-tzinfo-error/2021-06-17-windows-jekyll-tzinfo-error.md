---
layout: post
title: Jekyll | windows jekyll tzinfo 오류
date: 2021-06-17 13:00:00 +09:00
modified: 
category: blog
tags: [jekyll]
image: "/assets/img/jekyll_logo.png"
cover: "../puzzle.jpg"
---

### intro

연구소 내 windows 컴퓨터를 사용하다보니 mac을 사용할 때는 나타나지 않는 오류가 생겼다. <br>
(컴퓨터 공학 공부를 mac으로 해온 나에겐 windows는 생소하고 혼란스러운 공간이다.)<br>

### 1. 오류 내용

잘 정리되어있는 블로그[1]를 보고 jekyll을 설치하고<br>
`bundler install` 명령을 실행하고 난 후 <br>
`bundle exec jekyll serve`를 하니 문제가 생겼다.<br>

```
 Dependency Error: Yikes! It looks like you don't have tzinfo or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. If you've run Jekyll with `bundle exec`, ensure that you have included the tzinfo gem in your Gemfile as well. The full error message from Ruby is: 'cannot load such file -- tzinfo' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/!
```

검색해서 찾아보니 windows에는 루비 인터프리터가 IANA 타임존 정보를 처리하는데 필요한 정보 원천이 없어서, 환경변수인 TZ를 사용한다고 한다.[2] [3] <br>


### 2. 해결 방법

github.io 블로그 디렉토리 내 **Gemfile**을 열어서 아래 내용을 추가했다. <br>

```
# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo'
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```

---
**참고 자료**<br>
[1](https://shryu8902.github.io/_posts/2018-06-22-jekyll-on-windows/) <br>
[2](https://jennysgap.tistory.com/entry/Github-Pages-04-%ED%83%80%EC%9E%84%EC%A1%B4-%EA%B4%80%EB%A6%AC) <br>
[3](https://jekyllrb.com/docs/installation/windows/) <br>