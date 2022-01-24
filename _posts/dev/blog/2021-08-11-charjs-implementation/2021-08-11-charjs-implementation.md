---
layout: post
title: Jekyll | 누적 막대그래프 추가
date: 2021-08-11 23:00:00 +09:00
modified: 
category: blog
tags: [jekyll]
image: "/assets/img/jekyll_logo.png"
cover: "../puzzle.jpg"
---

### 1. 추가 이유

분야별 관심도 표현을 위해 `home`에 누적 막대 그래프를 추가하고 싶었다.<br>


### 2. 추가 내용

아래 그림에서의 빨간 부분을 추가하려 계획했고<br>

![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/blog/2021-08-11-charjs-implementation/plan.png)<br>

실제 추가한 모습은 아래와 같다.<br>

![](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/blog/blog/2021-08-11-charjs-implementation/result.png)

### 3. 추가 방법

1. html `canvas` 태그 추가<br>
    ```html
    <canvas id="canvas" height="50"></canvas>
    ```
1. script 작성<br>
    ```html
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.7.2/Chart.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datalabels@0.7.0"></script>
    <script>
        new Chart(document.getElementById("canvas"), {
        type: 'horizontalBar',
        data: {
                labels: ['CURRENT'],
                datasets: [{
                label: 'Algorithms',
                data: [30],
                borderColor: "rgba(209, 216, 224, 1)",
                backgroundColor: "rgba(209, 216, 224, 0.5)",
                },
                {
                label: 'Machine Learning',
                data: [40],
                borderColor: "rgba(75, 101, 132, 1)",
                backgroundColor: "rgba(75, 101, 132, 0.5)",
                },
                {
                label: 'Medical Data',
                data: [20],
                borderColor: "rgba(209, 216, 224, 1)",
                backgroundColor: "rgba(209, 216, 224, 0.5)",
                },
                {
                label: 'Etc',
                data: [10],
                borderColor: "rgba(75, 101, 132, 1)",
                backgroundColor: "rgba(75, 101, 132, 0.5)",
                }]
        },
        options: {
                title: { display: false,
                        text: 'In My Mind'
                },
                responsive: true,
                tooltips: {
                enabled: false
                },
                hover: {
                mode: 'nearest',
                intersect: true
                },
                legend: {
                display: true
                },
                scales: {
                xAxes: [{
                        display: false,
                        stacked: true,
                        barThickness: 6
                }],
                yAxes: [{
                        display: false,
                        stacked: true,
                        barThickness: 30
                }]
                },
                plugins: {
                datalabels: {
                color: 'black',
                font: {
                weight: 'bold'
                },
                formatter: function(value, context) {
                return Math.round(value) + '%';
                }
                }
                }
        }
        });

        </script>
    ```
    

---
**참고 자료**<br>
[https://www.chartjs.org/docs/3.0.2/samples/bar/stacked.html](https://www.chartjs.org/docs/3.0.2/samples/bar/stacked.html) <br>