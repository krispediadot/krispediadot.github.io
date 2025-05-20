---
lang: kr
layout: post
title: GCP Professional Machine Leaning Engineer Certificate
date: 2024-11-26 18:00:00 +09:00
modified: 
category: [Reviews, Certificates]
tags: 
image: 
cover: 
---

21년 구글 머신러닝 부트캠프 활동으로 취득했던 Tensorflow 자격증이 곧 만료된다는 이메일을 받고 자격증 갱신을 시도했다. 그러나, Tensorflow 자격증이 2024년 5월을 끝으로 Closed 되었다는 슬픈 소식을 알게 되었다. 

이참에 새로운 자격증에 도전하기로 마음먹고 그동안 미뤄왔던 Google Cloud Professional ML Engineer 자격증을 취득했다.

자격증 시험을 준비하며 여러 자료를 보고 도움을 받았고 이 글이 자격증을 준비하는 누군가에게 도움이 되었으면 하는 마음에 2024.10. 업데이트 이후 PMLE 자격증 취득 과정과 경험을 공유하려 한다.

### 1. 시험 정보

- 시험 주요 내용 6가지
1. Architect low-code AI solutions
2. Collaborate within and across teams to manage data and models
3. Scale prototypes into ML models
4. Serve and scale models
5. Automate and orchestrate ML pipelines
6. Monitor AI solutions
- 시험 시간: 2시간
- 시험 비용: $200(온라인 시험 기준 실제 $120 결제)
- 언어: 영어
- 문제 수: 50-60 문제
- 문제 유형: 다지선다형
- 시험 방식: on-site 또는 online
- 재시험 가능 횟수: 3회

PMLE 시험은 Google Cloud 환경에서 ML engineer로서 시험 주요 내용 6가지 영역의 업무를 수행할 수 있는 지식이 있는지를 확인하는 시험이다. 상황을 주고 요구사항에 알맞은 선택지를 고르는 문제가 주로 나온다. 

<mark>알아두어야 할 사항은 2024.10.01. 기준으로 시험이 업데이트되었다는 점이다.</mark>

[공식 사이트](https://cloud.google.com/learn/certification/guides/machine-learning-engineer)에 따르면 generative AI 관련 내용이 포함되었다고 한다. 
>What's new:\
The upcoming version of the Professional Machine Learning Engineer exam launching on October 1 will cover tasks related to generative AI, including building AI solutions using Model Garden and Vertex AI Agent Builder, and evaluating generative AI solutions.

그 외에도 시험 주요 내용의 영역별 문제 비중이 조금 달라졌다. 

업데이트 관련 내용 및 시험에 대한 자세한 사항은 [공식 사이트](https://cloud.google.com/learn/certification/guides/machine-learning-engineer)에서 확인할 수 있다. 

### 2. 시험 준비

- 참고 자료: 
  - [Machine Learning Engineer Learning Path](https://www.cloudskillsboost.google/paths/17)
  - [Dump 문제](https://www.examtopics.com/exams/google/professional-machine-learning-engineer/)
- 준비 기간: 약 2주

최단기간 자격증 취득을 목표로 기본적인 ML 지식이 있는 상태에서 약 2주간 퇴근 후 준비했다.

[공식 사이트](https://cloud.google.com/learn/certification/guides/machine-learning-engineer) exam guide에 나와 있는 주요 시험 내용 6가지 영역에 대한 설명을 기준으로 GCP 전반적인 개념을 정리하려 노력했다.
PMLE 자격증이 2024.10. 업데이트가 되면서 Architecting Low-Code ML Solutions, Serving and Scaling Models, Automating and Orchestrating ML Pipelines 파트의 비중이 조금씩 늘었다고 한다. 
이에 맞춰, Dump 문제들은 Discussion을 포함해 한번 정독하고 Vertex AI, BigQuery ML, Auto ML, Kubeflow, TFX를 중점적으로 살펴봤다.

ML 기본 지식이 있고 GCP에 대한 기본적인 이해가 있다면 충분히 문제를 풀 수 있었다.

### 3. 시험 신청

시험 신청 방식이 certmetrics에 접속한 후 webassessor에 들어가야 하는 복잡한 구조였다. 

1. certmetrics 계정 생성

[자격증 사이트](https://cloud.google.com/learn/certification/machine-learning-engineer/)에 접속 후 Register 버튼을 누르면 certmetrics에 사이트로 들어가게 된다. 

![GCP_PMLE1](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/reviews/certificates/2024-11-26-GCP-professional-ml-engineer/GCP_PMLE1.png)

위 화면에서 `NEW CANDIDATE REGISTER`를 눌러 계정을 생성한다. 

2. webassessor 시험 일정 예약

![GCP_PMLE2](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/reviews/certificates/2024-11-26-GCP-professional-ml-engineer/GCP_PMLE2.png)

![GCP_PMLE3](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/reviews/certificates/2024-11-26-GCP-professional-ml-engineer/GCP_PMLE3.png)

![GCP_PMLE4](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/reviews/certificates/2024-11-26-GCP-professional-ml-engineer/GCP_PMLE4.png)

한국어는 선택지에 없으니 Google Cloud Certified - Professional Machine Learning Engineer(English)를 선택한다.
Remote로 시험을 선택하고 Buy Now를 클릭하면 시간을 선택하는 창이 뜬다. 

![GCP_PMLE5](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/reviews/certificates/2024-11-26-GCP-professional-ml-engineer/GCP_PMLE5.png)

15분 단위로 선택할 수 있었다. 
시험 후기 부분에서 한 번 더 이야기 하겠지만 실제 시험 시간 2시간 외 신분 확인 및 주변 환경 세팅 시간을 감안해서 여유 있는 시간대에 시험을 치르는 걸 추천한다!

![GCP_PMLE6](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/reviews/certificates/2024-11-26-GCP-professional-ml-engineer/GCP_PMLE6.png)

설명에는 $200로 적혀있었지만 결제 단계에서는 $120를 지불하면 시험 예약 끝!!

### 4. 시험 후기

온라인으로 시험을 보기 위해 secure browser를 설치해야 하고 사전에 점검받아야 할 사항들이 있었다.

시험 예약 시간 전에 webassessor 내 활성화된 Launch 버튼을 누르고 실제 시험에 들어가기 전 신분 확인 및 시험을 치르는 장소 주변 환경을 확인하는 과정이 있었다.

1. 본인 인증(정면 사진) 
2. 여권 확인 
3. 주변 환경 확인 \
채팅으로 요청하는 지시에 따라 카메라를 통해 주변 환경 확인을 받았다. 노트북에 내장된 카메라를 사용하다 보니 노트북을 들고 화면을 비춰야 하는 불편함이 있었다.
그리고 책상 위에 모니터 및 책이 꽂혀있는 환경에서 시험을 보려 했으나 책상 위 물건을 치울 수 없다면 장소를 이동하라는 지시에 테이블 위에 아무것도 없는 장소로 이동해서 다시 주변 환경을 확인하는 과정을 진행했다. 이 과정에서 시간이 20분 이상 소요되었다. 실제 시험 시간 2시간 외 시간이 더 걸릴 수 있으니 시간적 여유가 필수다!

위 과정을 거치고 나면 시험이 시작되고 한 문제씩 보여주는 웹 화면 환경에서 시험을 봤다. 시험을 보는 동안 웹캠을 통해 감독받았고 남아있는 시간, 선택하지 않은 문제 그리고 나중에 다시 확인할 문제는 체크해 두고 다시 확인할 수 있었다. 총 50문제를 한 번 쭉 풀고 애매했던 문제는 다시 확인한 후 시험 종료 1분 전에 최종 제출을 했다.

전체 50문제 중 Dump와 동일하게 나온 문제는 10개 미만이었다. 개인적으로는 Dump 문제를 살펴볼 때 Discussion을 읽으며 정리해 뒀던 지식이 많은 도움이 되었다.

### 5. 시험 결과

PASS 🎉

최종 제출을 하고 나면 화면에서 바로 PASS 인지 결과를 확인할 수 있었고 하루 뒤 credly에 자격증이 발급되었다는 메일을 받았다. credly에서 `Download Certificate` 누르면 PDF 자격증을 받을 수 있다. 

![GCP_PMLE7](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/reviews/certificates/2024-11-26-GCP-professional-ml-engineer/GCP_PMLE7.png)

자격증을 취득하고 나면 Google Cloud에서 주는 Merchandise를 받을 수 있다. 
certmetrics에 접속해서 BENEFITS > My Benefits에 가서 Merchandise를 선택하면 끝!!

![GCP_PMLE8](https://raw.githubusercontent.com/krispediadot/krispediadot.github.io/master/_posts/reviews/certificates/2024-11-26-GCP-professional-ml-engineer/GCP_PMLE8.png)