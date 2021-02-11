---
layout: post
title: git commit+
date: 2021-02-08 00:00:05 +09:00
modified: 
category: git
tags: [git]
image: "/assets/img/git_icon.png"
cover: 
---

>실습 환경: Mac OS & zsh with oh-my-zsh

### git commit 하고나면 어떤 변화가 있는지 알아봅시다. 

- **.git 폴더 내부 objects**
    **[commit 하기 전]**

    add만 되어있는 상태 

    ![git+ commit 1](https://krispediadot.github.io/assets/images/git+_commit_1.jpg)

    ![git+ commit 2](https://krispediadot.github.io/assets/images/git+_commit_2.jpg)

    **[commit 하기 전]**

    ![git+ commit 3](https://krispediadot.github.io/assets/images/git+_commit_3.jpg)

    ![git+ commit 4](https://krispediadot.github.io/assets/images/git+_commit_4.jpg)

    b3, f8 폴더와 해쉬값이 생성됩니다. <br>

    git log로 확인해보면 

    ![git+ commit 5](https://krispediadot.github.io/assets/images/git+_commit_5.jpg)

    ![git+ commit 6](https://krispediadot.github.io/assets/images/git+_commit_6.jpg)

    commit한 내용의 해쉬가 b3f4b1656--- 인것을 알 수 있습니다. <br>

    b3 폴더내의 파일 이름을 살펴보면 f4b1656--- 인것으로 보아 이어보면 b3f4b1656---으로 commit한 해쉬값과 동일합니다. <br>

    b3 폴더가 커밋한 내용을 담고있는 해쉬 값을 저장하고 있다는 것을 알 수 있습니다. <br>


- **.git 폴더 내부 COMMIT_EDITMSG**
    objects 폴더의 변화와 함께 commit_deitmsg 파일이 생성됩니다. 

    ![git+ commit 7](https://krispediadot.github.io/assets/images/git+_commit_7.jpg)

    파일에는 commit시 작성했던 commit message가 저장되어 있습니다. 

    ![git+ commit 8](https://krispediadot.github.io/assets/images/git+_commit_8.jpg)

    ![git+ commit 9](https://krispediadot.github.io/assets/images/git+_commit_9.jpg)