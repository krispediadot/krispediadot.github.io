---
layout: post
title: git commit+
date: 2019-06-02 00:00:05 +09:00
modified: 
category: [tools, git]
tags: [git]
image: 
cover: 
---

>실습 환경: Mac OS & zsh with oh-my-zsh

### git commit 하고나면 어떤 변화가 있는지 알아봅시다. 

- **.git 폴더 내부 objects**<br>

**[commit 하기 전]**

add만 되어있는 상태 

![git+ commit 1](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit/git+_commit_1.jpg)
<br>
![git+ commit 2](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit/git+_commit_2.jpg)
<br><br>
**[commit 하기 전]**
<br><br>
![git+ commit 3](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit/git+_commit_3.jpg)
<br>
![git+ commit 4](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit/git+_commit_4.jpg)
<br><br>
b3, f8 폴더와 해쉬값이 생성됩니다. <br>
<br>
git log로 확인해보면 
<br>
![git+ commit 5](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit/git+_commit_5.jpg)
<br>
![git+ commit 6](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit/git+_commit_6.jpg)
<br><br>
commit한 내용의 해쉬가 b3f4b1656--- 인것을 알 수 있습니다. <br>
<br>
b3 폴더내의 파일 이름을 살펴보면 f4b1656--- 인것으로 보아 이어보면 b3f4b1656---으로 commit한 해쉬값과 동일합니다. <br>
<br>
b3 폴더가 커밋한 내용을 담고있는 해쉬 값을 저장하고 있다는 것을 알 수 있습니다. <br>

- **.git 폴더 내부 COMMIT_EDITMSG**<br>
objects 폴더의 변화와 함께 commit_deitmsg 파일이 생성됩니다. 
<br><br>
![git+ commit 7](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit/git+_commit_7.jpg)
<br><br>
파일에는 commit시 작성했던 commit message가 저장되어 있습니다. 
<br><br>
![git+ commit 8](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit/git+_commit_8.jpg)
<br>
![git+ commit 9](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit/git+_commit_9.jpg)