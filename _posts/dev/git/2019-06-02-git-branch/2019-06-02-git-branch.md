---
layout: post
title: git branch
date: 2019-06-02 00:00:12 +09:00
modified: 
category: git
tags: [git]
image: "/assets/img/git_icon.png"
cover: 
---

>실습 환경: Mac OS & zsh with oh-my-zsh

### branch 란?<br>

이름에서 알 수 있듯이 가지치기를 하는 것을 말합니다.
branch를 여러 개 생성해 작업을 독립적으로 진행할 수 있습니다. 
필요 시 merge를 통해 하나로 합칠 수 있습니다.

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_1.png?raw=true">
<figcaption>출처: https://geeks.uniplaces.com/mastering-branches-in-git-f20cb2d0c51f</figcaption>
</figure>

### git branch
현재 생성된 branch 종류를 확인할 수 있습니다.<br>

추가로 생성한 branch 가 아직 없으므로 master branch 하나만 존재합니다. <br>
<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_2.png?raw=true">
</figure>

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_3.png?raw=true">
</figure>

### git branch <생성할 branch 이름> 
hotfix1 이라는 이름의 새로운 branch를 만들어 봅시다.

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_4.png?raw=true">
</figure>

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_5.png?raw=true">
</figure>

### git checkout <방문할 branch>
현재 master branch에 있다는것을 알 수 있습니다.

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_6.png?raw=true">
</figure>

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_7.png?raw=true">
</figure>

git checkout hotfix1 명령을 통해 hotfix1 branch 로 이동해 봅시다!

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_8.png?raw=true">
</figure>

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_9.png?raw=true">
</figure>

hotfix1 branch 에 와 있고 status는 branch를 생성 할 당시 상태와 동일합니다.

### horfix1 branch 에 들어와서 파일을 변경 한 후 master branch 와 비교해 봅시다.
#### 1. new1.py 파일을 아래와 같이 수정하겠습니다. 
<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_10.png?raw=true">
</figure>

#### 2. new1.py 파일을 add & commit 하겠습니다.
<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_11.png?raw=true">
</figure>

#### 3. git log 를 살펴봅시다.
- log에 기록 된것을 확인 할 수 있습니다. 
- HEAD 가 hotfix1을 가리키고 있습니다. 
- master 는 이전 commit 에 머물러 있고 새로 생성된 commit 은 hotfix1에 있습니다.
<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_12.png?raw=true">
</figure>

#### 4. master branch 에 가서 확인해봅시다. 
<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_13.png?raw=true">
</figure>

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_14.png?raw=true">
</figure>

<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_15.png?raw=true">
</figure>

- HEAD 가 master를 가리키고 있습니다. 
- master branch의 log 에는 hotfix1 에서 commit 했던 내용이 적혀있지 않습니다. 

#### 5. master branch 에 있는 new1.py / hotfix1 branch 에 있는 new1.py 파일을 비교해봅시다.
각각의 branch 가 독립적으로 진행되고 있다는 것을 확인 할 수 있습니다.<br>

<master branch - new.py>
<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_16.png?raw=true">
</figure>

<hotfix1 branch - new1.py>
<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_17.png?raw=true">
</figure>

### git checkout -b <생성할 branch 이름>
branch 를 새로 만들고 이동까지 하는 명령어 입니다. <br>
hotfix2 라는 이름의 branch를 새로 만들고 이동해 봅시다. 
<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_18.png?raw=true">
</figure>

### git branch -d <삭제 할 branch 이름> / git branch -D <삭제 할 branch 이름>
branch 를 삭제할 때 사용됩니다. <br>
hotfix2 branch 를 삭제해 봅시다.
<figure>
<img src="https://github.com/krispediadot/krispediadot.github.io/blob/master/_posts/dev/git/2019-06-02-git-branch/git_branch_19.png?raw=true">
</figure>
