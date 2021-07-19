---
layout: post
title: JavaScript | 정렬
date: 2021-04-19 10:00:00 +09:00
modified: 
category: javascript
tags: [javascript]
image: "/assets/img/javascript_logo.png"
cover: ""
---

### 1. 기능
javascript로 데이터를 정렬 할 때

### 2. 구현

```javascript
// p_data 가장 뒤 값을 기준으로 정렬할 때
const c_data = [{'name': 'AAVE', 'p_data': [-5.74]}, 
                   {'name': 'ADP', 'p_data': [0.18]}, 
                   {'name': 'AMO', 'p_data': [-42.87]}];
c_data.sort(function(a, b) {
  	const a_last = a.p_data.length - 1;
  	const b_last = b.p_data.length - 1;
	return b.p_data[b_last] - a.p_data[a_last];
});
console.log(c_data);

// p_data 가장 앞 데이터를 기준으로 정렬할 때
const d_data = [{'name': 'AAVE', 'p_data': [-5.74]}, 
                {'name': 'ADP', 'p_data': [0.18]}, 
                {'name': 'AMO', 'p_data': [-42.87]}];
d_data.sort(function(a, b) {
	return b.p_data - a.p_data;
});
console.log(d_data);
```
