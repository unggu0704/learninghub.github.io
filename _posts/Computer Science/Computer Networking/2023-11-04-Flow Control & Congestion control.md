---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Computer Network]
tags: [CS, computer network]
render_with_liquid: true
comments: true
---
# Flow Control & Congestion control

## Flow Control

> 송신 측과 수신측의 데이터처리 속도를 해결하기 위한 기법
> 

→ 수신측이 더 빠르면 별 문제가 되지 않는다… 하지만 송신측이 더 빠르다면?

### Stop and Wait

- 전송한 패킷의 응답을 받아야만 그 다음 패킷을 전송
- 송신- > wait → ACK 수신 → 다음 송신

### Sliding Window

- 여러 데이터 패킷을 동시에 전송한다. (window의 사이즈 만큼)
- window의 크기는 3-way-handShaking 때 정하고 추후게 혼잡도에 따라 서로 조절한다.
- 송신 윈도우, 수신 윈도우가 존재
    - 송신 윈도우 : ACK 수신 안받고도 연속적으로 전송할 수 있는 데이터 양
    - 수신 윈도우 : 수신자가 버퍼 overflow가 일어나지 않는 선에서 한번에 받을 수 있는 데이터 양
- **GO Back N**
    - 만약 윈도우 사이즈 내에서 송신한 프레임 중 하나라도 NAK 응답이 온다면 N 번부터 다시 재전송 하는 방식
- **선택적 재전송 방식**
    - 오류가 발생한 프레임만 선택적으로 재전송

## Congestion Control

- 수신자가 과부하 → 데이터 NAK 정보 수신 → 데이터 재전송등으로 더욱 혼잡
- 송신 측에서 보내는 데이터 속도를 강제로 줄이는 방식으로 회피

### Slow Start

- 처음에는 window를 낮게 설정 하지만 점차 지수 함수 꼴로 window 사이즈를 키운다.
    - 단! 이번 Congestion 발생 전까지만.
    - 만약 그 중 Congestion 발생시 바로 1로 떨어트린다.
    - 이를 통해 네트워크의 상태를 인지 가능

### Fast Recovery

- 혼잡 상태가 될 시에 바로 window size를 1로 설정하지 않고 반으로 줄인 뒤에 선형 증가