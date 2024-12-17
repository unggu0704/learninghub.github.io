---
author: "unggu"
date: 2023-09-23 12:17:32 +0800
categories: [Study, Algorithm]
tags: [Algorithm, graph]
render_with_liquid: true
comments: true
---
# 그래프

## 그래프의 구성

- **정점** : 그래프의 구성요소로 하나의 연결점
- **간선** : 두 정점을 연결하는 선
- **차수** : 정점에 연결된 간선의 수

**그래프란 정점들의 집합과 이들을 연결하는 간선들의 집합니다!**

### 그래프의 종류

- 무향 그래프
- 유향 그래프
- 가중치 그래프
- 싸이클 없는 방향 그래프

![Untitled]({{ site.baseurl }}{{ page.url }}/graphimg/Untitled.png)

- 완전 그래프
- 부분 그래프
- 트리

## 그래프의 표현

### 인접 행렬

- 두 정점을 연결하는 간선의 유무를 행렬로 표현
- V x V의 정방 행렬

![Untitled]({{ site.baseurl }}{{ page.url }}/graphimg/Untitled%201.png)

**장단점**

- 메모리를 조금 더 사용한다.
- 두 정점이 연결되었는지 확인하는 속도가 빠르다

### 인접 리스트

- 각 정점에 대한 인접 정점을 순차적 표현
- 연결 리스트를 활용한다.

![Untitled]({{ site.baseurl }}{{ page.url }}/graphimg/Untitled%202.png)

**장단점**

- 메모리의 효율성
- 두 정점의 연결을 확인하는데 시간이 걸린다.

### 간선 리스트

- 두 정점에 대한 간선 그 자체를 객체로 표현
- 시작과 끝의 정보를 나타낸다

![Untitled]({{ site.baseurl }}{{ page.url }}/graphimg/Untitled%203.png)

- 모든 간선 탐색에 유리
- 특정 노드에 연결된 간선을 알아보기위해 모든 간선을 탐색해야한다.
