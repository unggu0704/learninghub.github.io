---
author: "unggu"
date: 2023-09-23 12:17:32 +0800
categories: [Study, Algorithm]
tags: [Algorithm, graph]
render_with_liquid: true
comments: true
---
# Kruskal & Prim

## MST

> **신장 트리 (Spanning Tree)**
> 
- 무방향 그래프
- $G(V, E)$ 에서 싸이클이 형성되지 않으면서 모든 정점 V를 연결한 그래프
- 노드가 N 개이면 간선의 개수는 N-1이면서 싸이클은 없음
- 이런 연결에 있어 가장 낮은 가중치를 가지는 것을 **MST(최소 신장트리)** 라고 한다.

## Kruskal (크루스칼)

> $O(ElogE)$
> 
- 최소 신장 트리를 구하는 알고리즘
- greedy 하다.
- **Union-Find** 알고리즘을 활용

### 동작 방식

> 1.  간선을 오름차순으로 정렬한다.
2.  가중치가 가장 작은 간선을 선택한다.
3.  정점의 연결은 *union-find* 를 사용한다.
4.  싸이클이 형성될거 같다면 스킵한다.
> 

## Prim (프림)

> $O(ElogV)$
> 
- 최소 신장 트리를 구하는 알고리즘
- 트리 집합의 단계적인 확장
- 다익스트라 알고리즘과 비슷함
- Priority Queue를 이용한 최소 힙으로 구현

### 동작 방식

> 1.  임의의 정점으로부터 시작한다.
2.  정점으로부터 연결될 수 있는 가장 적은 정점을 연결 
3.  열결된 집합 내에서 연결 될 수 있는 가장 적은 가중치를 확장 
4.  더이상 연결 될 때 없을때 까지 반복
> 

## 둘의 차이

- Prim : 정점 위주, Kruskal : 간선 위주
- kruskal → 매번 싸이클 체크를 해줘야함
- prim → 최소 거리 정점을 찾는 부분에서 자료구조 영향이 큼

### 간선의 개수가 작다면 Kruskal을 간선의 개수가 많다면 Prim을 사용하자.

---

[BOJ_행성터널_P5](https://www.notion.so/BOJ_-_P5-d84cd22ef58246c4a0da8fab9bf46177?pvs=21)


[BOJ_17472_다리만들기2](https://www.notion.so/BOJ_17472_-2-6700e0fb5a154df797886d2cdf8f5a1a?pvs=21)