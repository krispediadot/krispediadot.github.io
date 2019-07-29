---
layout: post
title: "[Git] Gihub의 branch 가져오기"
categories: git
tag : [git, branch]
---

## Github에 올려놓은 프로젝트에 있는 branch 가져오기

프로젝트를 github에 올려놓은 상태에서 로컬에 있는 폴더를 지웠다. <br>

한참을 잊고 지내다 프로젝트 내용이 필요해 `git clone`으로 프로젝트를 내려받았는데 내 전용 branch가 받아지지 않는다. <br>

이런 경우 아래와 같이 하면 된다.<br>

#### 1- 먼저 프로젝트 내려받기 (`git clone`)
---
이렇게 내려받은 후 `git branch`명령으로 확인해보면 master branch만 보인다. <br>

![branch check](https://krispedia.github.io/assets/images/git_branch_check_after_clone.jpg)<br>

#### 2- `git branch -r` 과 `git branch -a` 확인
---
- `git branch -r`의 결과<br>
![branch -r check](https://krispedia.github.io/assets/images/git_branch_r_check.jpg)<br>

- `git branch -a`의 결과<br>
![branch -r check](https://krispedia.github.io/assets/images/git_branch_a_check.jpg)<br>

여기서 원격에 있는 branch를 확인할 수 있다. <br>


#### 3- `git checkout -t [brancch 위치]` 명령어로 branch 가져오기
---
나의 경우 **origin/sujin** branch를 가져오고 싶으므로 <br>
![branch checkout-t ](https://krispedia.github.io/assets/images/git_branch_checkout_t.jpg)<br>

#### 4- `git log` 로 해당 branch의 log 확인하기
---
![branch after checkout-t ](https://krispedia.github.io/assets/images/git_branch_after_checkout_t.jpg)<br>


성공적으로 가져와졌다. <br>
