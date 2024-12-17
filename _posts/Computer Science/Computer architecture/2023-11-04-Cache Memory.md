---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Computer Architecture]
tags: [CS, computer architecture]
render_with_liquid: true
comments: true
---



# Cache Memory

> 병목을 줄이자!
> 

- 데이터를 저장하는 공간의 속도와 용량은 반비례 구조이다..
- 메모리는 계층적으로 사옹되어야한다.
- 가장 빠른 저장공간인 Cache를 사용!
- 자주 사용하는 데이터를 Cache에 저장!
- 일반적으로 CPU는 2~3개의 cahce 메모리를 사용
    - L1, L2 ,L3 라고 불림

### L1, L2 ,L3

- 일반적으로 다중 CPU 환경일 경우 L1 Cache의 경우는 별도로 사용함
- L1 Cache가 128kb라면?
    - 64kb는 명령어를 처리하기 전 명령어를 임시 저장
    - 나머지 64kb는 명령어를 실행 후 에 임시 저장
- I - Cache , D - Cache
- L2, L3는 공유 캐시이다.
    - L2 : CPU와 RAM 사이의 어딘가…
    - L3 : 메인보드

### Cache 메모리의 작동원리

- **시간 지역성**
    - 한번 참조된 데이터는 또 참조 된다.
- **공간 지역성**
    - 한번 참조된 데이터의 근처에는 또 다시 사용된다.

## Cache의 적중

### Cache Hit

- Cache에 원하는 데이터가 있을때

### Cach Miss

- **Cold Miss**
    - 한번도 요청 한적 없는 메모리 주소라서  miss
- **Conflict Miss**
    - A와 B 모두 저장 해야하는데 서로 같은 캐시 메모리 주소에 할당 된 경우
- **Capacity Miss**
    - 캐시 메모리의 공간이 부족해서 나는 문제

## Cahce의 구조 및 작동 방식

### Direct Mapped Cache

![Untitled]({{ site.baseurl }}{{ page.url }}/Cache%20Memory%20cbcac5e48adb4ca7bc4afcc5aa4f561f/Untitled.png)

- 각 메모리의 위치가 캐시 내의 정확히 한곳만을 가리침 ( Many to One )
    - *001*의 주소는 모두 *001* cache에 매핑
    - *001*이 인덱스 필드 나머지 주소를 태그 필드라고 한다.
    - 만약 *001 라면 이건 000*01*인가? 010*01*인가?*
    - 태그 필드를 확인!
- **Conflict Miss** 가 발생하는 것이 치명적 단점

### **Fully Associative Cache**

- 그냥 무지성 캐시 메모리 저장
- 저장은 간단 찾는게 문제…

### **Set Associative Cache**

- Direct + Fully 방식
- Direct에 비해 검색 속도는 느리지만, 저장이 빠르고 Fully에 비해 저장이 느린 대신 검색이 빠른 중간형

### Valid Bit

- cache는 추가적으로 유효 비트라는 것을 운영한다.
- 이것이 정말 쓸모 있는 data인지 아닌지
- 단순히 초기화 하는것보단 이게 효율적!