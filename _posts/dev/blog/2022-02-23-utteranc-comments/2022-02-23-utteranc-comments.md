---
layout: post
title: Jekyll | utterances comments 연결하기
date: 2022-02-23 16:00:00 +09:00
modified: 
category: blog
tags: [jekyll]
image: "/assets/img/jekyll_logo.png"
cover: "../puzzle.jpg"
---

### 1. 추가 이유

블로그 포스트 내용에 대해 대화를 나눌 수 있는 기능이 필요했다.<br>

### 2. 추가 내용

![after](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/blog/2022-02-23-utteranc-comments/after.png?raw=true)

### 3. 추가 방법

##### 1) install ['utterances'](https://github.com/apps/utterances)
   
##### 2) github과 연동
   utterances를 연결하고자 하는 레파지토리 위치 지정<br>
   ![configuration](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/blog/2022-02-23-utteranc-comments/configuration.png?raw=true)<br>

##### 3) blog post <-> issue mapping
   blog 내용과 issue를 무엇을 기준으로 연결 할 것인지 정하는 설정이다.<br>
   3번째 옵션인 page title을 선택하면 issue 창에서 한눈에 알아보기는 쉽겠지만 title이 변경되는 경우 문제가 될 수 있다.<br>
   1번째 옵션인 pathname을 선택하면 issue창에서 path가 길게 나열되어 한눈에 알아보기는 어렵겠지만 title이 변경되어도 path만 여전하다면 문제 없다.<br>
   여러 옵션 중 잘 읽어보고 선택하는 것이 중요하다.<br>
   ![mapping](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/blog/2022-02-23-utteranc-comments/mapping.png?raw=true)<br>

##### 4) issue label
   issue label은 옵션으로 설정하지 않아도 된다.<br>
   다른 issue들과 구분하기 쉽게 필자는 '💬 comments'로 설정했다.<br>

##### 5) theme
   원하는 테마 색을 선택해서 설정<br>

위 설정을 모두 끝내면 블로그에 추가할 수 있는 script가 생성된다.<br>
![script](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/blog/2022-02-23-utteranc-comments/script.png?raw=true)<br>

이 코드를 'comments.html' 파일에 저장하고<br>
'post.html' 하단에 comment.html을 추가하면 끝!!<br>

    
    

---
**참고 자료**<br>
- [https://utteranc.es/](https://utteranc.es/) <br>