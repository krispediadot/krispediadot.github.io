---
layout: post
title: Jekyll | bundle exec jekyll serve webrick (LoadError)
date: 2021-07-18 13:00:00 +09:00
modified: 
category: blog
tags: [jekyll]
image: "/assets/img/jekyll_logo.png"
cover: "../puzzle.jpg"
---

### 1. 오류 내용

```
              ------------------------------------------------
      Jekyll 4.2.0   Please append `--trace` to the `serve` command 
                     for any additional information or backtrace. 
                    ------------------------------------------------
/usr/local/lib/ruby/gems/3.0.0/gems/jekyll-4.2.0/lib/jekyll/commands/serve/servlet.rb:3:in `require': cannot load such file -- webrick (LoadError)
```

### 2. 해결 방법

아래 명령어로 `webrick`을 설치하고
```
bundle add webrick
```

```
bundle exec jekyll serve
```

위 명령어로 실행하면 된다. 

---
**참고 자료**<br>
[https://junho85.pe.kr/1850](https://junho85.pe.kr/1850) <br>