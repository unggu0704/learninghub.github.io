---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Operating System]
tags: [CS, OS]
render_with_liquid: true
comments: true
---
# Page Replacement Algorithm

> Main / Virtual Memory에서 hit 하지 못하고 페이지 폴트 발생시 가득 차 있을 때 어떤 process를 swap out할 것인지를 결정하는 문제
> 

- Main / Virtual Memory는 필요한 페이지만 메모리에 적재하고 사용하지 않은 부분은 그대로 둔다.
- 사용이 다 되었지만 자리만 차지하고 있는 페이지는 out 하는게 좋다.
- 그리고 필요한 것은 in!
    - 근데… 어떤 페이지를 out 해야하는가?
    - 최소한으로 fault가 발생하지 않도록 골라보자’

### 1. FIFO 알고리즘

- 가장 오래 있는 놈이 나간다.
- First - In - First - Out
- 초기화 코드에서 특출난 방법
    - 최초로 프로세스 실행될 때만 시키는 역할 → 초기화 코드
    
    ![Untitled]({{ site.baseurl }}{{ page.url }}Page%20Replacement%20Algorithm%20634b62471ad24186888ef41cea009f29/Untitled.png)
    

### 2. OPT 알고리즘

- 앞으로 가장 안쓸 놈을 골라서 내보낸다.
- 근데 어떻게 미래를 예측하지…

![Untitled]({{ site.baseurl }}{{ page.url }}Page%20Replacement%20Algorithm%20634b62471ad24186888ef41cea009f29/Untitled%201.png)

### 3. LRU 알고리즘

- 최근에 가장 사용하지 않은 페이지를 내보낸다.
- 가장 실용적임

![Untitled]({{ site.baseurl }}{{ page.url }}Page%20Replacement%20Algorithm%20634b62471ad24186888ef41cea009f29/Untitled%202.png)

### 4. LFU

- 참조 횟수가 가장 적은 페이지를 교체
- 횟수가 같다면 가장 오랫동안 사용되지 않은 페이지를 교체

### 5. NUR

- LRU와 비슷하지만 최근에 사용되지 않은 페이지를 교체 ‘
- 두개의 참조 / 변형 비트를 활용
    - 참조 : 페이지 호출 시에 1, 호출 되지 않았을때 0
    - 변형 : 페이지 내용 변경시 1, 변경 아닐시에 0

### 교체 방식

- Global 교체
    
    > 메모리 상의 모든 프로세스 페이지에 대해 교체하는 방식
    > 
- Local 교체
    
    > 메모리 상의 자기 프로세스 페이지에서만 교체하는 방식
    > 

다중 프로그래밍 환경에서 메인 메모리에는 다양한 프로레스가 올라온다. 

그렇기에 다양한 프로세스의 다양한 메모리가 올라오는데… 이것들을 모두 한번에 생각할지 아니면 따로 생각할지의 차이

→ 전체로 하는게 효율적이다.