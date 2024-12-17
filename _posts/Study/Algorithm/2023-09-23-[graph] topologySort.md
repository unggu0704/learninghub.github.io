---
author: "unggu"
date: 2023-09-23 12:17:32 +0800
categories: [Study, Algorithm]
tags: [Algorithm, graph]
render_with_liquid: true
comments: true
---
# 위상정렬

## **Topological Sorting**

- 순서가 정해져있는 작업을 수행할 때 필요한 알고리즘
- 방향성에 거스르지 않도록 정렬하는 알고리즘

## 진입 차수와 진출차수

### 진입 차수

- 특정한 노드로 들어오는 간선의 개수

### 진출 차수

- 특정한 노드에서 나가는 간선의 개수

![Untitled]({{ site.baseurl }}{{ page.url }}/topologyimg/Untitled.png)

## 위상 정렬 동작 과정

> 사이클이 없는 방향 그래프(DAG)

1. 진입 차수가 0인 노드를 큐에 넣는다. (어떤 노드부터 시작하던지 상관없다.)
2. 큐가 빌 때까지 아래 과정을 반복
   1. `dequeue` 된 원소의 진출 차수(나가는 간선)을 그래프에서 제거
   2. 진입 차수(들어오는 간선)이 0이 된 노드를 큐에 삽입

**노드가 큐에 들어온 순서가 위상 정렬 수행 결과**

**[Step 1]**

![Untitled]({{ site.baseurl }}{{ page.url }}/topologyimg/Untitled%201.png)

1번 노드를 꺼낸다.

1번 노드와 연결된 간선을 모두 제거

2번 노드와 5번 노드의 진입하수가 0

**[Step 2]**

![Untitled]({{ site.baseurl }}{{ page.url }}/topologyimg/Untitled%202.png)

2번 노드와 5번 노드중 하나를 꺼내서

2번 노드의 진출 차수를 없애면저 진입 차수를 모두 없앤다.

**[Step 3]**

![Untitled]({{ site.baseurl }}{{ page.url }}/topologyimg/Untitled%203.png)

5번 노드를 꺼내면서 간선을 마찬가지로 제거한다.

계속해서 큐에 노드를 넣으면서 진행한다.

**[Step 4]**

![Untitled]({{ site.baseurl }}{{ page.url }}/topologyimg/Untitled%204.png)

3번 노드 꺼내서 제거하지만 진입차수가 0이 되는 노드가 존재하지 않는다.
