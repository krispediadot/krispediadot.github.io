---
layout: post
title: "[Git] git commit --amend란?"
comments: true
description: "git commit --amend"
tag : [Git]
---
<div class="divider"></div>
_/-- 실습 환경: Mac OS & zsh with oh-my-zsh --/_
<div class="divider"></div>

### git commit --amend를 살펴봅시다! <br>

 git commit --amend 멍령을 통해 마지막 commit을 수정, 변경 할 수 있습니다. <br>

  - 현재 `git log`<br>
   ![git commit amend 1](https://krispedia.github.io/assets/images/git_commit_amend_1.jpg)

#### 1. 실습을 위해 새로운 파일을 수정해봅시다. <br>

  **gito1.py 파일을 수정하겠습니다.**<br>

  - 수정 전 gito1.py<br>
  ![git commit amend 2](https://krispedia.github.io/assets/images/git_commit_amend_2.jpg)

  - 수정 후 gito1.py<br>
  ![git commit amend 3](https://krispedia.github.io/assets/images/git_commit_amend_3.jpg)

  - add<br>
  ![git commit amend 4](https://krispedia.github.io/assets/images/git_commit_amend_4.jpg)

  - `git commit --amend`<br>
  ![git commit amend 5](https://krispedia.github.io/assets/images/git_commit_amend_5.jpg)

  - commit message 작성
  ![git commit amend 6](https://krispedia.github.io/assets/images/git_commit_amend_6.jpg)

  - 완료!
  ![git commit amend 7](https://krispedia.github.io/assets/images/git_commit_amend_7.jpg)

  - git commit --amend 후 git log 실행 결과
  ![git commit amend 8](https://krispedia.github.io/assets/images/git_commit_amend_8.jpg)

    - 7a557--으로 시작되던 마지막 commit 해시값이 다른 값으로 변경되었다. 
    - add gito1.py였던 마지막 commit message가 update gito1.py로 변경되었다.