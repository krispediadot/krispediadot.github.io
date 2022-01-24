---
layout: post
title: git commit --amend
date: 2019-06-02 00:00:09 +09:00
modified: 
category: git
tags: [git]
image: "/assets/img/git_icon.png"
cover: 
---

>실습 환경: Mac OS & zsh with oh-my-zsh

### git commit --amend를 살펴봅시다! <br>

 git commit --amend 멍령을 통해 마지막 commit을 수정, 변경 할 수 있습니다. <br>

  - 현재 `git log`<br>
   ![git commit amend 1](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit--amend/git_commit_amend_1.jpg)

### 1. 실습을 위해 새로운 파일을 수정해봅시다. <br>
<br>
**gito1.py 파일을 수정하겠습니다.**<br>
<br>
- 수정 전 gito1.py<br>
![git commit amend 2](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit--amend/git_commit_amend_2.jpg)
<br>
- 수정 후 gito1.py<br>
![git commit amend 3](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit--amend/git_commit_amend_3.jpg)
<br>
- add<br>
<br>
![git commit amend 4](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit--amend/git_commit_amend_4.jpg)
<br><br>
- `git commit --amend`<br>
<br>
![git commit amend 5](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit--amend/git_commit_amend_5.jpg)
<br><br>
- commit message 작성<br>
![git commit amend 6](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit--amend/git_commit_amend_6.jpg)
<br>
- 완료!<br>
<br>
![git commit amend 7](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit--amend/git_commit_amend_7.jpg)
<br><br>
- git commit --amend 후 git log 실행 결과
![git commit amend 8](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/git/2019-06-02-git-commit--amend/git_commit_amend_8.jpg)
<br>
  * 7a557--으로 시작되던 마지막 commit 해시값이 다른 값으로 변경되었다. 
  * add gito1.py였던 마지막 commit message가 update gito1.py로 변경되었다.