---
layout: post
title: Jekyll | toc(table of contents) 추가
date: 2022-07-09 20:00:00 +09:00
modified: 
category: blog
tags: [jekyll]
image: "/assets/img/jekyll_logo.png"
cover: "../puzzle.jpg"
---

### 1. 추가 이유

포스팅 내용을 한눈에 보고 이동할 수 있는 기능이 필요했다.<br>

### 2. 추가 내용

![after](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/blog/2022-07-09-toc-right-sidebar/toc_right_sidebar_result.png?raw=true)<br>

### 3. 추가 방법

찾아본 결과 jekyll에서 toc을 추가하는 데 2가지 방법이 있었다. <br>
- 방법 1. `jekyll-toc` plugin ([toshimaru/jekyll-toc](https://github.com/toshimaru/jekyll-toc) 사용)<br>
- 방법 2. `toc.html` 파일 추가 ([allejo/jekyll-toc](https://github.com/allejo/jekyll-toc) 사용)<br>

방법 1을 먼저 시도해 보았으나, plugin 설치와 적용 만으로는 기능이 반영되지 않았다.<br> 
현재 블로그의 코드를 살펴보고 일부를 수정해야 했다.<br>
코드를 수정해야 하는 거라면, 조금 더 맞춤형으로 만들어야 겠다고 생각이 들어서 방법 2를 선택했다. 

##### 1) toc.html 파일 다운 및 추가

[https://github.com/allejo/jekyll-toc/blob/master/_includes/toc.html](https://github.com/allejo/jekyll-toc/blob/master/_includes/toc.html)에 가서 `toc.html` 파일을 다운 받는다.<br>

다운로드가 완료되면 _includes 폴더 아래에 toc.html을 추가한다.<br>
   
##### 2) _layouts/post.html 수정

`toc.html`을 `post.html` 코드 사이에 넣어준다.<br>

코드의 위치는 sidebar를 불러오는 곳 아래로 정했다.<br>
코드의 위치는  `post.html` 코드 구성에 따라 달라질 수 있다.<br>
<mark>(`%` 앞에 있는 `/`는 실제 코드엔 들어가지 않는다. 포스팅할 때 만 추가함.)</mark>

```html
<div class="toc" id="toc">
   {/% include toc.html html=content %}
</div>
```

toc에 들어갈 내용을 추출하는 script 코드를 `_layouts/post.html` 파일에 추가한다.<br>

아래 코드는 [다른 블로거님](https://velog.io/@outstandingboy/Github-%EB%B8%94%EB%A1%9C%EA%B7%B8-%ED%8F%AC%EC%8A%A4%ED%8A%B8%EC%97%90-%EC%8A%A4%ED%81%AC%EB%A1%A4%EC%97%90-%EB%94%B0%EB%A5%B8-%EB%AA%A9%EC%B0%A8Table-of-Contents-TOC%EB%A5%BC-%EB%9D%84%EC%9A%B0%EB%8A%94-ScrollSpy-%EA%B8%B0%EB%8A%A5-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0)의 코드 중 필요한 부분만 추출한 것이다. 

```html
<script>
  function getTOCNodes(master) {
    var nodes = Array.prototype.slice.call(master.getElementsByTagName("*"), 0);
    var tocNodes = nodes.filter(function(elem) {
        return elem.tagName == "A";
    });
    return tocNodes;
  }
  function getHeaderNodes(master) {
    var nodes = Array.prototype.slice.call(master.getElementsByTagName("*"), 0);
    var headerNodes = nodes.filter(function(elem) {
        return elem.tagName == "H1" || elem.tagName == "H2" || elem.tagName == "H3" || elem.tagName == "H4" || elem.tagName == "H5" || elem.tagName == "H6";
    });
    return headerNodes;
  }

  var title = document.getElementsByClassName("post-title")[0];
  var titleY = window.pageYOffset + title.getBoundingClientRect().top;

  var article = document.getElementsByClassName("post-article")[0];
  var articleY = window.pageYOffset + article.getBoundingClientRect().top;

  var toc = document.getElementsByClassName("toc")[0];

  var headerNodes = getHeaderNodes(article);
  var tocNodes = getTOCNodes(toc);

  var before = undefined;

</script>
```

##### 3) _sass 내부 css 추가

포스트의 위에서 30%, 오른쪽에서 20% 위치에 고정되고<br>
포스트 내용이 나오는 블럭 오른쪽에 위치하도록 코드를 작성했다.<br>
아래 코드는 jekyll의 어떤 템플릿을 사용하는 지에 따라 다시 작성해야 할 수도 있다.<br>

```css
.toc {
  top: 30vh;
  position: fixed;
  left: 80vw;
  width: 300px;
  color: $dark-gray;
  overflow-y: auto;
  overflow-x: hidden;
  padding-left: 10px;
  padding-right: 10px;
  padding-top: 10px;
  padding-bottom: 10px;
  font-size: 15px;
  border-left: 2px solid #e0d9e7;

  @include media-query($on-tablet) {
    display: none;
  }

  span {
    font-size: 18px;
  }

  a.toc-active {
    font-weight: bold; 
    transition: all 0.125s ease-in 0s; 
    font-size: 0.75rem;
    color: #9075aa;
  }

  ul {
    list-style-type: none;
    margin-bottom: 0.1rem;
    padding-left: 0rem;
    li {
      padding-left: .5rem;
    }
  }

  a {
      color: $dark-gray;
      text-decoration: none;
  }

  a:hover {
     color:$dark-black;
  }
}
```

---
**참고 자료**<br>
- [[Github] 블로그 포스트에 스크롤에 따른 목차(Table of Contents, TOC)를 띄우는 ScrollSpy 기능 구현하기 포스트](https://velog.io/@outstandingboy/Github-%EB%B8%94%EB%A1%9C%EA%B7%B8-%ED%8F%AC%EC%8A%A4%ED%8A%B8%EC%97%90-%EC%8A%A4%ED%81%AC%EB%A1%A4%EC%97%90-%EB%94%B0%EB%A5%B8-%EB%AA%A9%EC%B0%A8Table-of-Contents-TOC%EB%A5%BC-%EB%9D%84%EC%9A%B0%EB%8A%94-ScrollSpy-%EA%B8%B0%EB%8A%A5-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0) <br>