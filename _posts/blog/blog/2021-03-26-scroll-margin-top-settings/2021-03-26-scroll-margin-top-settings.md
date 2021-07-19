---
layout: post
title: Jekyll | CSS scroll-margin-top 설정
date: 2021-03-26 3:00:00 +09:00
modified: 
category: blog
tags: [jekyll, css]
image: "/assets/img/jekyll_logo.png"
cover: "../puzzle.jpg"
---

### 1. 설정 전

포스팅 할때 index를 사용해서 특정 header로 바로 이동할 수 있도록 설정 했으나<br>
이동하면 header의 제목이 navigation bar에 가려서 보이지 않았다.<br>

![scroll_margin_top_before](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/Blog/2021-03-26-scroll-margin-top-settings/scroll_margin_top_before.gif)

원하는 위치에는 가지만 뭔가 아쉬운 느낌🤔<br>

### 2. 설정 후
![scroll_margin_top_after](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/Blog/2021-03-26-scroll-margin-top-settings/scroll_margin_top_after.gif)

### 3. 설정 방법
1. **headings의 css가 설정 되어 있는 위치 찾기**<br>
<br>
[klisé theme](https://github.com/piharpi/jekyll-klise)의 경우 `_sass/klise/_base.scss`<br>
<br>
1. **headings의 css 설정 부분에 `scroll-margin-top:` 추가(또는 변경)**<br>
<br>
**[ 추가(또는 변경) 전 ]**<br>
```scss
// Headings
h1,
h2,
h3,
h4,
h5,
h6 {
  color: $black;
  font-weight: $bold-weight;
  & + ul,
  & + ol {
    margin-top: 10px;
  }
}
```
<br>
**[ 추가(또는 변경) 후 ]**<br>
```scss
// Headings
h1,
h2,
h3,
h4,
h5,
h6 {
  color: $black;
  font-weight: $bold-weight;
  & + ul,
  & + ol {
    margin-top: 10px;
  }
  scroll-margin-top: 65px;
}
```


