---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Operating System]
tags: [CS, OS]
render_with_liquid: true
comments: true
---
# Interrupt

> 프로그램을 실행하는 도중에 예기치 않은 상황 발생시 현재 실행 중인 작업을 즉시 중단하고 발생된 상황에 대한 우선처리가 필요함을 CPU에게 알리는 것
> 

→ *급한 불부터 끄자 !*

### 인터럽트는 2가지로 나뉜다.

1. **외부 인터럽트**
    - 전원 이상, 외부 신호, 입출력으로 발생
2. **내부 인터럽트**
    - 잘못된 명령이나 데이터 (0으로 나누니, 오버플로우) 시에 발생
    - 명령의 요청에 의한 발생 (프로그램을 실행 시킬 때, 시분할 처리를 위한 자원 할당 동작)

## Interrupt 발생 처리 과정

1. 프로그램 실행 중 interrupt 발생
2. 처리 중이던 프로그램을 잠시 멈추고 PCB에 저장 한 뒤 interrupt 서비스 루틴으로 간다. (Context Swithcing)
    1. 만약 interrupt가 없었더라면 할일을 체크해주는 폴링을 계속 해야한다.
3. interrupt 루틴을 처리하고 다음 업무를 처리한다.

interrupt는 발생시기를 예측하기 힘든 경우에 컨트롤러가 가장 빠르게 업무를 처리 할 수 있는 방식