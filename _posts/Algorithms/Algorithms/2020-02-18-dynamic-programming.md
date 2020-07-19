---
layout: post
title: "[Algorithms] Dynamic Programming"
categories: algo
tag : [algorithms]
---

### Dynamic Programming 이란?  
---

부분 문제가 서로 중복 될 때 부분 문제의 해를 결함해 문제를 해결하는 방법  

### Divide & Conquer vs Dynamic Programming  
--- 
Divide & Conquer은 서로 겹치지 않는 부분 문제로 분할하고 해당 부분을 재귀적으로 해결한 후 결과를 결합해 문제를 해결하는 반면, Dynamic Programming은 부분 문제가 다시 자신의 부분 문제를 공유할때 미리 풀어놓은 부분 문제를 활용해 문제를 해결한다.  

일반적으로 최적화 문제에 Dynamic Programming을 사용한다.  

### Dynamic Programming 개발 단계
--- 
1단계. 최적해의 구조 특징을 찾는다  
2단계. 최적해의 값을 재귀적으로 정의한다  
3단계. 최적해의 값을 일반적으로 bottom-up 방법으로 계산한다  
4단계. 계산된 정보들로 최적해를 구성한다  


### Dynamic Programming 이 사용 되는 곳
---

<div class="divider"></div>
**[참고자료]**

- school of ai로 유명한 **Siraj Raval** 의 설명:  
[https://www.youtube.com/watch?v=DiAtV7SneRE](https://www.youtube.com/watch?v=DiAtV7SneRE)