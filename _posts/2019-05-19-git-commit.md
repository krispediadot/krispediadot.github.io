---
layout: post
title: "[Git] git commit"
comments: false
description: "git commit"
tag : [Git]
---
<div class="divider"></div>
_/-- 실습 환경: Mac OS & zsh with oh-my-zsh --/
<div class="divider"></div>

### git commit에 대해 알아봅시다. 

#### 1. git commit <br>

  폴더 내 파일이 모두 add 되어 있습니다.<br>

  ![git commit 1](https://krispedia.github.io/assets/images/git_commit_1.jpg)

  지역 저장소에 올리기 위해 commit을 해 봅시다. <br>
  commit을 하기 전에 git log를 한번 확인해 볼까요?!

  ![git commit 2](https://krispedia.github.io/assets/images/git_commit_2.jpg)

  아직 commit을 한 것이 없다고 알려줍니다. <br>

  이제 commit을 해 봅시다!

  ![git commit 3](https://krispedia.github.io/assets/images/git_commit_3.jpg)

  git commit을 하면 위와 같이 나옵니다. <br>

  보라빛 글씨에 commit을 할 파일을 보여줍니다.<br>
  폴더에서 add한 3개의 파일이 보입니다. <br>
  commit이 무슨 내용인지 이후에 알아보기 위해 commit message 를 작성합니다. <br>

(1).키보드 i = insert mode<br>
(2).메세지 작성(ex. add new files)<br>
(3).esc키 + :wq 로 저장합니다. <br>

  ![git commit 4](https://krispedia.github.io/assets/images/git_commit_4.jpg)

  ![git commit 5](https://krispedia.github.io/assets/images/git_commit_5.jpg)

  enter를 누르는 동시에 <br>

  _[master (root-commit) 9ce965d] add new files_<br>
  _3 files changed, 3 insertions(+)_<br>
  _create mode 100644 new1.py_<br>
  _create mode 100644 new2.txt_<br>
  _create mode 100644 newfile.txt_<br>

  3개의 파일이 바꼈고 3개가 추가되었다는 말과 하께 파일의 이름이 터미널에 나옵니다. <br>

  **그리고 master 글자 옆 빨간 x가 초록 체크로 변경된 것을 확인할 수 있습니다.**

  (oh-my-zsh에서 실습 하는 것이므로 환경에 따라 보여지는 실행 결과가 다를 수 있습니다.)

  이제 commit이 완료 되었습니다!!!

  commit 기록을 확인하기 위해 `git log`로 가 봅니다. 

  ![git commit 6](https://krispedia.github.io/assets/images/git_commit_6.jpg)

  ![git commit 7](https://krispedia.github.io/assets/images/git_commit_7.jpg)

  commit 옆에 sha로 해슁된 값이 들어가있고 <br>
  commit 한 사람의 정보<br>
  commit 한 시간<br>
  commit message 가 나옵니다.<br>

  '키보드 q'를 눌러 log 에서 나옵니다. <br>

  **commit 메세지를 작성하는 또다른 방법이 있습니다.**


#### 2. commit -m "~commit message~" <br>

  **commit 명령어와 메세지를 쓰는 일을 한번에 하는 아주 유용한 방법입니다.** <br>

  실습을 하기 위해 기존 파일을 변경하고 add 하겠습니다.<br>

  new2.txt 파일에 내용을 변경하겠습니다. <br>

  ![git commit 8](https://krispedia.github.io/assets/images/git_commit_8.jpg)

  ![git commit 9](https://krispedia.github.io/assets/images/git_commit_9.jpg)

  상태를 확인해 보면 new2.txt 파일이 modified 되었다고 합니다. <br>

  _use "git add ..." to update what will be committed_<br>
  업데이트 commit 하기 위해 추가하려면 git add 

  _use "git checkout --..." to discard changes in working directory:_<br>
  업데이트 commit 안하려면 git checkout<br>

  `git add` 하겠습니다. 

  ![git commit 10](https://krispedia.github.io/assets/images/git_commit_10.jpg)

  이전과는 다른 방법으로 commit을 하고 메세지를 작성하겠습니다. <br>

  ![git commit 11](https://krispedia.github.io/assets/images/git_commit_11.jpg)

  ![git commit 12](https://krispedia.github.io/assets/images/git_commit_12.jpg)

  commit 이 완료되었습니다!!<br>

  git log로 확인해봅시다.

  ![git commit 13](https://krispedia.github.io/assets/images/git_commit_13.jpg)

  이상으로 git add 한 파일 목록들을 commit 하는 방법에 대해 알아보았습니다. <br>

<div class="divider"></div>

#### **git commit 조금 더 알아보기**<br>

[[Git+] git commit](https://krispedia.github.io/git+-commit)