---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Operating System]
tags: [CS, OS]
render_with_liquid: true
comments: true
---
# CPU Scheduling

### 스케줄링의 목표

- 오버헤드는 낮추고 사용률은 높이고 기아현상은 낮추고
- **Batch System** : 가능한 많은 일을 수행
- **Interactive System** : 빠른 응답시간, 적은 대기 시간
- **Real-time System** : deadLine 맞추기

프로세스의 상태 (실행을 위해 메모리에 올라온 상태) → PCB도 이때 생긴다.

> `New` → `Ready` → `waiting` → `Running` → `Terminated`
> 

![Untitled](CPU%20Scheduling%20dc2a1e24ac804113b8bcc3e85d784e7e/Untitled.png)

### dispatcher

- 프로세스 `p1` 이 실행중이다.
- `p2` 가 실행될 때, 자신의 pcb 영역에 pc를 저장
- `p2` 의 pcb를 가져와 실행

→ 둘이 가져와서 pcb에 저장 및 로드 하는 과정을 **Context Switching** !!! 아무것도 안한다.

### 프로세스의 상태 전이

- **승인(Admitted)** : 프로세스 생성이 가능하며 승인됨
- **스케줄러 디스패치** : `ready` 상태의 프로세스 중 하나를 선택 및 실행
- **인터럽트** : 예외, 입출력, 이벤트 등으로 현재 프로세를 `ready` 로 바꾸고 해당 작업 처리하러 가는것
- **입출력 대기** : 실행중인 프로세스가 입출력이나 이벤트를 처리 할 경우 입출력 끝날때까지 `wati` 상태

---

# CPU 스케줄링

## 비 선점 스케줄링(Non - preepmitive)

> *한 프로세스가 CPU를 할당 받아 실행 중이라면 다른 프로레스들이 CPU를 강제적으로 뺏을 수 없는 방식*
> 

### **FCFS**

- Queue에 도착한 순서대로 CPU 할당
- 실행 시간이 짧은데 뒤에 오면 괜히 많이 기다림

### SJF

- 처리 시간이 짧은 프로세스 부터 CPU에 할당
- 짧은 얘들은 매우 짧은 대기에 처리 가능하지만, 긴 얘들은 오래 기다려야함 (기아 현상)
- 현실적으로 처리 시간을 어케 알지

### HRN

- SJF를 개선
- 우선순위를 계산 (대기 시간 + 처리 시간) / 처리 시간
    - 오래 기다릴 수록 대기 시간이 높아지기에 조금 더 공평 할수도…?

## 선점 스케줄링(Preemptive)

> *CPU를 할당받아 실행 중이더라도 언제든지 뺏을 수 있음*
> 

### Round Robin

- 기본적으로 FCFS이지만 동일한 시간의 `Time Quantum` 만큼 CPU를 할당 받음
- `Time Quantum` 이 크면 FCFS와 동일 너무 작으면 Context Switching이 잦아져 오버헤드 증가

### SRT

- **SJF**의 선점형 방식
- 처리된 시간 만큼 작업의 처리 순서를 재계산
- 여전히 기아 현상은 지속됨

### Multi-Level Feedback Queue

- 우선 순위가 높은 Queue에 있는 프로세스가 먼저 실행됨
- 같은 우선순위에 대해서는 **Round Robin** 방식 이용
- 큐에 대한 `Time Quantum` 을 모두 처리하면 아래 단계의 큐로 이동됨
- 입출력 위주 작업에 우선권을 줌