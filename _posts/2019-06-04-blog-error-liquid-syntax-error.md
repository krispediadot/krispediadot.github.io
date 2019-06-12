---
layout: post
title: "[Blog] Error - Liquid Syntax Error"
comments: true
description: "blog"
tag : [Blog]
---

`jekyll 3.8.5 | Error:  Liquid syntax error (line 10): Variable '{ {1,0}' was not properly terminated with regexp: /\}\}`  


이런 오류가 나면 괄호 두개를 연달아 써서 나는 오류이니<br>
1.`**{ { } }**` 이런 방식으로 띄워주거나 <br>
2.`**{\{}\}**` 이렇게 나눠주면 됨.<br> 