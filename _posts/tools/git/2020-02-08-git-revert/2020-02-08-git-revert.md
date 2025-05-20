---
layout: post
title: git revert
date: 2019-06-02 00:00:11 +09:00
modified: 
category: [Tools, Git]
tags: [git]
image: 
cover: 
---

>실습 환경: Mac OS & zsh with oh-my-zsh

### git reset 과 비슷한듯 다른 git revert! <br>

git reset은 이전의 상태로 돌리는 것이라면 <br>
git revert는 이전 상태를 변경시키는 것입니다. <br>

git reset
![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_1.png)

git revert
![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_2.png)

현재 git log 상황
![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_3.png)


### 실습을 위해 commit 을 추가하겠습니다.
#### gito2.py 파일 생성
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_4.png)
#### add & commit
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_5.png)
#### gito2.py 파일 추가 수정
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_6.png)
#### add & commit
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_7.png)
#### 현재 git log 실행 결과
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_8.png)

현재 HEAD 는 마지막 commit에 있습니다. 

### git revert <해당 위치>
  gito1.py 을 추가한 두번째 commit을 변경해 보겠습니다. 
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_9.png)

  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_10.png)

  commit message 작성
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_11.png)

  revert 완료!
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_12.png)

  git revert 7a557 후 git log 실행 결과
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_13.png)

  git revert 7a557 후 파일 list
  ![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/tools/git/2020-02-08-git-revert/git_revert_14.png)

