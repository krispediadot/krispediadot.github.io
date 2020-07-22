---
layout: post
title: "[Datascience-Data] 정수(Integer)"
categories: data
tag : [data]
---

정수는 양의정수, 음의 정수 그리고 0으로 이루어진 수 체계로 영어로는 Integer라 불린다.  

### 정수가 컴퓨터에서는 어떻게 표현될까?
주로 `int`형으로 정수는 표현 된다.  
32비트 수 체계 기준 4바이트, 64비트 수 체계 기준 8바이트 의 공간을 차지한다.  

### 4바이트 or 8바이트는 어떤 순서로 메모리에 작성 될까?  
**용어  
MSB(Most Significant Byte): 최상위 바이트  
LSB(Least Significant Byte): 최하위 바이트  

메모리에 작성되는 순서에 따라 `Big Endian`과 `Little Endian`으로 나눌 수 있다. 
#### Big Endian  
MSD가 가장 앞쪽에 오는 저장 방법.  
네트워크로 데이터를 전송할 때에는 항상 Big Endian으로 전송해야 한다.  

#### Little Endian
LSB가 가장 앞쪽에 오는 저장 방법.  
네트워크로 데이터를 전송, 수신할때 Big Endian으로 변환해줘야 해서 번거롭지만 형변환시 유용함.  
예를들어, 32비트 변수를 16비트로 형변환 하면 앞의 두 바이트만 읽어주면 됨.  
