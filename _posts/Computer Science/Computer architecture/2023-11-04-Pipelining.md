---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Computer Architecture]
tags: [CS, computer architecture]
render_with_liquid: true
comments: true
---
# Pipelining

- 일반적으로 cpu는 병렬로 작업을 처리한다.
- 해야할 일을 pipeline에 담아 순서대로 처리하는 방식
- 하지만 이러한 방식은 가장 오래 걸리는 시간이 전체 작업량에 큰 영향을 끼친다

### RISC - V의 pipeline 용어

- IF STAGE (명령어 fetch)
- ID STAGE (명령어 해석)
- EX STAGE (ALU 사용)
- MEM STAGE(load 사용)
- WB STAGE(ALU 결과 값을 목적 R에 작성)

## 구조적 해저드(Structural Hazard)

- 이러한 병렬 처리에 있어 자원 사용에 있어 충돌 할 경우
- I1 에서 data fetch를 위해 M3 을 참조할때 I3 도 instruction fetch를 위해 M3 참조
    
    ![스크린샷 2023-12-04 오후 1.36.00.png]({{ site.baseurl }}{{ page.url }}/Pipelining%2027d2a927612b4bed8bde90447bf7d58f/1.png)
    

### 해결법

- stall :  잠깐 쉬기 → 다른 메모리가 참조 할떄까지
- hardward resource 추가

## 데이터 해저드(Data Hazard)

- 만약 ADD 2 + 3이 끝나고 다른 데이터가 이걸 참조해야하는데 해당 연산이 아직 끝나기전에 다른 연산에서 사용할려고 가져가버린다면?
    - 두개의 인접 명령에 의존성이 있을때
        
        ![스크린샷 2023-12-04 오후 1.39.13.png]({{ site.baseurl }}{{ page.url }}/Pipelining%2027d2a927612b4bed8bde90447bf7d58f/2.png)
        

### 해결법

- bubble (많은 stall) ← clock 손해
    
    ![스크린샷 2023-12-04 오후 1.39.27.png]({{ site.baseurl }}{{ page.url }}/Pipelining%2027d2a927612b4bed8bde90447bf7d58f/3.png)
    
- Forwarding
    
    ![스크린샷 2023-12-04 오후 1.40.34.png]({{ site.baseurl }}{{ page.url }}/Pipelining%2027d2a927612b4bed8bde90447bf7d58f/4.png)
    
    - ALU에서 나온 값을 산지 직송으로 보낸다.
    - 조금더 clock에서 이점을 가질수도…?
- bublle + fowarding
    
    ![스크린샷 2023-12-04 오후 1.41.49.png]({{ site.baseurl }}{{ page.url }}/Pipelining%2027d2a927612b4bed8bde90447bf7d58f/5.png)
    

## Control Hazard

- 분기 명령어(IF) 등으로 인해 명령어를 건더 뛰어 버리면 그동안의 연산은 낭비
    
    ![스크린샷 2023-12-04 오후 1.43.04.png]({{ site.baseurl }}{{ page.url }}/Pipelining%2027d2a927612b4bed8bde90447bf7d58f/6.png)
    

### 컨트롤 해저드 해결책

- **Stall**
    - 분기 결과가 나올떄 까지 계속 기다릴것
        
        ![스크린샷 2023-12-04 오후 1.43.47.png]({{ site.baseurl }}{{ page.url }}/Pipelining%2027d2a927612b4bed8bde90447bf7d58f/7.png)
        
- **optimized branch procession**
    - branch 유무를 최대한 빠르게 탐색
    - MeM stage → ID stage에서 브랜치 유무 빠르게 탐색
    - 구조에서 XOR 과 OR 게이트를 추가해 빠르게 알아보자!
        
        ![스크린샷 2023-12-04 오후 1.46.09.png]({{ site.baseurl }}{{ page.url }}/Pipelining%2027d2a927612b4bed8bde90447bf7d58f/8.png)
        
    
    - 극한의 이득충 방식
- **branch prediction**
    - 결과를 예측하자
    - static한 방식도 존재하지만 dynamic방식도 좋다
        
        ![Untitled]({{ site.baseurl }}{{ page.url }}/Pipelining%2027d2a927612b4bed8bde90447bf7d58f/Untitled.png)
        
        - 2번 not taken이였으면 3번째는 not taken으로 변경