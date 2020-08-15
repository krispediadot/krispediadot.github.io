---
layout: post
title: "[Algorithm] Merge Sort(합병 정렬) "
categories: algorithms
tag : [Sort]
---

### 1. 합병 정렬 알고리즘 
---
분할 정복법을 사용한 정렬 방법이다.  

### 2. 합병 정렬 동작 방법
--- 

### 3. 시간복잡도
---
O(nlogn)

### 4. 구현 
---
- Pseudo Code
```
mergeSort(A[], p, r){
    if p<r then{
        q <- (p+q)/2
        mergeSort(A, p, q)
        mergeSort(A, q+1, r)
        merge(A, p, q, r)
    }
}
merge(A[], p, q, r){
    정렬된 배열 A[p~q], A[q+1~r]를 합쳐 
    A[p~r] 배열 만들기 
}
```

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
void merge(int arr[], int begin, int q, int end){
    int a[end];
    int i=begin, j=q+1, k=begin;

    while(i<=q && j<=end){
        if(arr[i]<=arr[j])
            a[k++] = arr[i++];
        else
            a[k++] = arr[j++];
    }
    int tmp = i>q? j:i;
    while(k<=end)
        a[k++] = arr[tmp++];
    for(int i=begin; i<=end; i++)
        arr[i] = a[i];
}
void mergeSort(int arr[], int begin, int end){
    if(begin < end){
        int q = (begin+end)/2;
        mergeSort(arr, begin, q);
        mergeSort(arr, q+1, end);
        merge(arr, begin, q, end);
    }
}
```
</div>
</details>