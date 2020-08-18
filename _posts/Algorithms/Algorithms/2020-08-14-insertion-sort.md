---
layout: post
title: "[Algorithm] Insertion Sort(삽입 정렬) "
categories: algorithms
tag : [Sort]
---

### 1. 삽입 정렬 알고리즘 
---
기본적인 정렬 알고리즘 중 하나이다. 

### 2. 삽입 정렬 동작 방법
--- 

### 3. 시간복잡도
---
O(n²)

### 4. 구현 
---
- Pseudo Code
```
buble sort(A[], n){
    for i 1->n-1
        target = A[i]
        j = i-1
        while j>=0 & A[j]>target
            A[j+1] = A[j]
            j = j-1
        A[j+1] = target
}
```

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
void insertionSort(int arr[], int n){
    for(int i=1; i<n; i++){
        int target = arr[i];
        int j = i-1;
        while(j>=0 && arr[j]>target){
            arr[j+1] = arr[j];
            j--;
        }
        arr[j+1] = target;
    }
}
```
</div>
</details>

<div class="divider"></div>
**[참고 자료]**
- [Introduction to Algorithms, Third Edition](https://en.wikipedia.org/wiki/Introduction_to_Algorithms)
- [권오흠 교수님의 알고리즘 강의](https://www.youtube.com/watch?v=i4ZDgJS0_yM&list=PL52K_8WQO5oUuH06MLOrah4h05TZ4n38l&index=34)