---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Operating System]
tags: [CS, OS]
render_with_liquid: true
comments: true
---
# Process & Thread

## Process VS Thread

**프로세스** : 프로그램을 메모리 상에서 실행중인 작업

**스레드** : 프로세스 안에서 실행되는 여러 흐름 단위

### 키워드

- **실행 단위** → cpu core에서 실행하는 하나의 단위로 프로세스 + 스레드 개념
- **프로세스** → 하나의 스레드만 가지고 있는 단일 스레드 프로세스
- **동시성** → 짧은 전환으로 여러가지 일을 동시에 처리하는 것처럼 보이는 것

> *프로세스는 최소 1개의 스레드를 소유한다. (메인 스레드 포함)
각 Thread는 부모 프로세스의 대부분을 공유한다. (각자 Stack만 가짐)*
> 

![Untitled]({{ site.baseurl }}{{ page.url }}Process%20&%20Thread%20d16147d99af34dda9b9523bc3b567ad3/Untitled.png)

- Code : 코드 자체를 구성하는 메모리 영역
- Data : 전역 변수… 배열.. 등등
- Heap : 동적 할당
- Stack : 지역 변수, 리턴 값 → 지역변수는 소멸하는 이유

**프로세스는 자신만의 고유 공간과 자원을 할당받아 사용**하는데 반해, **스레드는 다른 스레드와 공간, 자원을 공유하면서 사용**하는 차이가 존재함

---

## Multi-process VS Multi-thread

### Multi-Process

- 부모 process를 fork 해서 각각 독립된 저장 장소를 가지고 여러 작업을 처리함
- **Context Switching** 으로 인한 성능 저하 문제
- 안정성은 높다.. 각자 다른 저장소를 가지고 있기에

***Context Switching*이란?**

> 프로세스의 상태 정보를 저장하고 복원하는 일련의 과정
> 
> 
> 즉, 동작 중인 프로세스가 대기하면서 해당 프로세스의 상태를 보관하고, 대기하고 있던 다음 순번의 프로세스가 동작하면서 이전에 보관했던 프로세스 상태를 복구하는 과정을 말함
> 
> → 프로세스는 각 독립된 메모리 영역을 할당받아 사용되므로, 캐시 메모리 초기화와 같은 무거운 작업이 진행되었을 때 오버헤드가 발생할 문제가 존재함
> 

### Multi-Thread

- 여러 작업을 다수의 thread가 처리하는 것
    - 하지만 공유 메모리를 사용한다는 차이가 있다.
- 성능적으로 우수하다.
- 안정성 문제가 유발됨 → 임계 영역

---

### Multi Core

- 앞서 말한 건 SW의 분야
- **동시성** 과 **병렬성** 이 위와 조금 다름 → 실제로 둘 이상의 코어가 각각 실행한다.

### Process의 일반적인 구조

![Untitled]({{ site.baseurl }}{{ page.url }}Process%20&%20Thread%20d16147d99af34dda9b9523bc3b567ad3/Untitled%201.png)