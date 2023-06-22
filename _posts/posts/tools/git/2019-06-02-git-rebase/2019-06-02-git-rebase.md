---
layout: post
title: git rebase
date: 2019-06-02 00:00:15 +09:00
modified: 
category: [posts, tools]
tags: [git]
image: "/assets/img/git_icon.png"
cover: 
---

>실습 환경: Mac OS & zsh with oh-my-zsh

**이번 내용은 git merge-2 와 이어지는 내용입니다.**

### 이번엔 git rebase 를 살펴봅시다!
git rebase 를 이용해 merge 해보도록 하겠습니다.<br>
현재 branch 상황
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_1.png?raw=true)

목표 branch 상황
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_2.png?raw=true)

### hotfix2 merge 되돌리기
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_3.png?raw=true)

현재 branch 상황
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_4.png?raw=true)

### hotfix3 branch 변경 후 commit 하기
변경 전 new1.py
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_5.png?raw=true)

변경 후 new1.py
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_6.png?raw=true)

add & commit
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_7.png?raw=true)

hotfix3 branch 에서 git log --graph 실행 결과
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_8.png?raw=true)

new1.py 한 번 더 수정
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_9.png?raw=true)

add & commit
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_10.png?raw=true)

hotfix3 branch 에서 gitlog --graph 실행 결과
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_11.png?raw=true)

변경 전 master branch new1.py
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_12.png?raw=true)

변경 후 master branch new1.py
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_13.png?raw=true)

add & commit <br><br>
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_14.png?raw=true)

master branch 에서 git log 실행 결과
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_15.png?raw=true)

현재 branch 상황
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_16.png?raw=true)

원하는 branch 상황
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_17.png?raw=true)

### git rebase 사용
#### 1. git checkout hotfix3 & git rebase master
충돌 발생!! 
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_18.png?raw=true)

- 충돌이 발생합니다.
    hotfix3 branch 에서 변경한 new1.py 와 master branch 에서 변경한 new1.py 가 다르기 때문에 충돌이 발생합니다.

new1.py파일에 가서 충돌을 해결합시다.<br>
충돌 후 hotfix3 branch new1.py<br>
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_19.png?raw=true)

수정 후 hotfix3 branch new1.py
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_20.png?raw=true)

git add & git rebase --continue<br><br>
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_21.png?raw=true)

두번째 충돌 후 hotfix3 branch new1.py
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_22.png?raw=true)

수정 후 hotfix3 branch new1.py
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_23.png?raw=true)

new.1py 변경 확인
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_24.png?raw=true)

add & rebase --conitnue
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_25.png?raw=true)

hotfix3 branch 에서 git log 실행 결과
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_26.png?raw=true)

master branch 에서 git log 실행 결과
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_27.png?raw=true)

아직까지 merge 안됨!!

### git merge hotfix3 --no-ff
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_28.png?raw=true)

merge 할때 commit message 
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_29.png?raw=true)

merge 완료!
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_30.png?raw=true)

merge 후 master branch 에서 git log 실행 결과
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_31.png?raw=true)

현재 branch 상황
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_32.png?raw=true)

### git rebase -i <구역>

merge 후 commit message 를 합쳐줍니다. <br>
git rebase -i 하기 전 git log<br>
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_33.png?raw=true)

![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_34.png?raw=true)

pick = 남기기 / fixup = 버리기
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_35.png?raw=true)

수정 후 저장
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_36.png?raw=true)

완료!
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_37.png?raw=true)

git rebase -i HEAD~~ 실행 후 git log
![](https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-rebase/git_rebase_38.png?raw=true)

- fixup 한 "2nd update new1.py in hotfix3" 의 commit 이 사라진것을 확인할 수 있습니다. 


