---
layout: post
title: "[Algorithm] Selection Sort(선택 정렬) "
categories: algorithms
tag : [Sort]
---

### 1. 선택 정렬 알고리즘 
---
기본적인 정렬 알고리즘 중 하나이다. 

### 2. 선택 정렬 동작 방법
--- 

### 3. 시간복잡도
---
O(n²)

### 4. 구현 
---
- Pseudo Code
```
selection sort(A[], n){
    for index n-1-> 2
        A[2~last] 에서 가장 큰 값 찾기
        A[index] 와 가장 큰값 swap
}
```

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
void selectionSort(int arr[], int n){
    for(int index=n-1; index>0; index--){
         int maxIndex = index;
         for(int i=0; i<index; i++){
             if(arr[i]>arr[maxIndex])
                 maxIndex = i;
         }
         swap(&arr[index], &arr[maxIndex]);
    }
}
```
</div>
</details>