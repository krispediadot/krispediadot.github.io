---
layout: post
title: git revert
date: 2019-06-02 00:00:11 +09:00
modified: 
category: [posts, tools]
tags: [git]
image: "/assets/img/git_icon.png"
cover: 
---

>실습 환경: Mac OS & zsh with oh-my-zsh

### git reset 과 비슷한듯 다른 git revert! <br>

git reset은 이전의 상태로 돌리는 것이라면 <br>
git revert는 이전 상태를 변경시키는 것입니다. <br>

git reset
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_1.png?raw=true)

git revert
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_2.png?raw=true)

현재 git log 상황
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_3.png?raw=true)


### 실습을 위해 commit 을 추가하겠습니다.
#### gito2.py 파일 생성
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_4.png?raw=true)
#### add & commit
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_5.png?raw=true)
#### gito2.py 파일 추가 수정
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_6.png?raw=true)
#### add & commit
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_7.png?raw=true)
#### 현재 git log 실행 결과
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_8.png?raw=true)

현재 HEAD 는 마지막 commit에 있습니다. 

### git revert <해당 위치>
  gito1.py 을 추가한 두번째 commit을 변경해 보겠습니다. 
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_9.png?raw=true)

  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_10.png?raw=true)

  commit message 작성
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_11.png?raw=true)

  revert 완료!
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_12.png?raw=true)

  git revert 7a557 후 git log 실행 결과
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_13.png?raw=true)

  git revert 7a557 후 파일 list
  ![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-revert/git_revert_14.png?raw=true)

