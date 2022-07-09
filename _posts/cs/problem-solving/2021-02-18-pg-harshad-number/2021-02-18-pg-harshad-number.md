---
layout: post
title: 프로그래머스. 하샤드 수 
date: 2021-02-18 19:00:00 +09:00
modified: 
category: problem solving
tags: [ps, c++]
image: "/assets/img/problem_solving_logo.png"
cover: "../puzzle.jpg"
---

### 문제 링크
[]()

### 나의 생각의 흐름
💡 [1차 시도 - 성공]<br>  

### 문제의 주요 내용 및 처리 방안
1. 자릿수 합 → 입력 수 10으로 나누며 더하기<br>
1. 입력 수가 자리수 합으로 나누어 떨어지면 true → (입력 수/자리수 합)의 나머지 0인지 확인<br>

### 코드 구현 
1. **입력 수 10으로 나누며 더하기**<br>
    입력 값을 tempx로 복사<br>
    그 이유는 이후 나머지 계산을 위해 원본 입력값이 필요하기 때문<br>
    ```c++
    int tempx = x;
    ```
    
    자리수 합 계산<br>
    ```c++
    int sum = 0;
    while (tempx > 0) {
        sum += (tempx % 10);
        tempx /= 10;
    }
    ```
    
1. **(입력 수/자리수 합)의 나머지 0인지 확인**<br>
    ```c++
    if (x % sum != 0) answer = false; 
    ```

### 전체 코드
```c++
#include <iostream>
#include <string>
#include <vector>

using namespace std;

bool solution(int x) {
    bool answer = true;

    int sum = 0;
    int tempx = x;
    while (tempx > 0) {
        sum += (tempx % 10);
        tempx /= 10;
    }
    if (x % sum != 0) answer = false; 

    return answer;
}
int main() {
    int x; cin >> x;
    cout >> boolalpha >> solution(x);
}
```
