---
title: "Artificial intelligence"
date: 2020-03-20
categories: study

---
#### ㅡ Artificial intelligence

![notion](https://img.shields.io/badge/notion-2020ver-purple?logo=notion)




### supervised learning vs unsupervised learning
## Table of Contents

- [What is Big Data?](#what_is_big_data?)
- [What is Machine Learning?](#what_is_machine_learning?)
  - [What is Data Mining](#what_is_data_mining)
- [Learning](#learning)
  - [supervised learning vs unsupervised learning](#supervised_learning_vs_unsupervised_learning)
  - [representation learning](#representation_learning)
- [Example](#example)
- [About](#about)

## What is Big Data?
빅 데이터란 기존 데이터베이스 관리도구의 능력을 넘어서는 대량의 정형 또는 심지어 데이터베이스 형태가 아닌 비정형의 데이터 집합조차 포함한 데이터로부터 가치를 추출하고 결과를 분석하는 기술

## What_is_Machine_Learning?
데이터 처리 방법론 = 머신러닝
기계 학습 또는 머신 러닝은 인공 지능의 한 분야로, 컴퓨터가 학습할 수 있도록 하는 알고리즘과 기술을 개발하는 분야를 말한다. 비정형데이터(이미지, 텍스트-e.g 뉴스, 블로그게시물)를 처리한다.
### What_is_Data_Mining?
데이터 마이닝 = 정형데이터(나이, 거주지역)
데이터 마이닝은 대규모로 저장된 데이터 안에서 체계적이고 자동적으로 통계적 규칙이나 패턴을 찾아 내는 것이다. 다른 말로는 KDD라고도 일컫는다.

## Learning 
### supervised_learning_vs_unsupervised_learning
supervised learning(지도 학습), 지도 데이터 = 학습된 데이터를 가지고 training 하고 testing 한다. 선형모델과 비선형모델이 있다.
unsupervised learning(비지도 학습), 이미지 보고 판단 e.g) 자동차인지 꽃인지 확인
데이터 생김에 따라서 그룹을 나눌 수 있다. 알고리즘으로 데이터를 나눌 수 있다.
K-means Clustering - 기준점으로 가까운점을 찾는다.
![](../../assets/images/study/kmeans.png)

디비스캔 = 기준 점들을 먼저 찾는것 보다, 임의의 데이터 포인트 시작해서 자기 가까운 점으로 세력 확장
![](../../assets/images/study/dbscan.png)
### representation_learning

딥러닝은 Representation Learning이라는 정의를 갖는다.
multiple level로 모델링 하는 것 = 다양한 층(layer)을 쌓아 각 층마다 데이터의 패턴을 학습시켜 각 층마다 학습시킨 패턴을 종합하는 과정

딥러닝이 두각되는 이유는 
- 기존의 인공신경망의 단점을 보완할 수 있는 알고리즘의 발전을 얘기 할 수 있고

- 학습시킬수 있는 충분한 데이터(빅데이터)

- GPU의 등장으로 빠른 연산을 가능하게 한것을 들 수 있다.

이에 따라서, 데이터 사이즈가 커짐에 따라서 의미있는 demension 의 뉴런 모델, 뉴런 네트워크 연구. 
뉴런 네트워크가 사진을 보면서 얼굴 경계선 찾을 수 있고, 얼굴안에 있는 눈,코,입 선으로 이루어졌다. 
뉴런네트워크 연구 = 좋은 모델이다. 다양한 것으로 표현되기 좋다. 계산하는데 오랜시간이 걸릴 수 있다. 하지만, 데이터 양이 많다. GPU 로 처리 할 수 있다.

## Example
왓슨, 알파고 같은 사례가 있다.
구글 듀플렉스 와 같은 경우

## About
Authored and maintained by **ingyu**

## Sources
[wiki]

[참고블로그1]

[wiki]: https://ko.wikipedia.org/wiki/
[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[code]: https://github.com/lllilllilllilili/hufs_projects/tree/master/MobileProgramming
[참고블로그1]: https://t-lab.tistory.com/1 