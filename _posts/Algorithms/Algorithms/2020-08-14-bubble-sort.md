---
layout: post
title: "[Algorithm] Bubble Sort(버블 정렬) "
categories: algorithms
tag : [Sort]
---

### 1. 버블 정렬 알고리즘 
---
기본적인 정렬 알고리즘 중 하나이다. 

### 2. 버블 정렬 동작 방법
--- 

### 3. 시간복잡도
---
O(n²)

### 4. 구현 
---
- Pseudo Code
```
buble sort(A[], n){
    for i n-1->2
        for j 0->i-1
            if A[j] > A[j+1]이면 
                A[i], A[i+1] swap
}
```

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
void swap(int *a, int *b){
    int temp = *a;
    *a = *b;
    *b = temp;
}
void bubbleSort(int arr[], int n){
    for(int i=n-1; i>0; i--){
        for(int j=0; j<n-1; j++){
            if(arr[j]>arr[j+1])
                swap(&arr[j], &arr[j+1]);
        }
    }
}
```
</div>
</details>