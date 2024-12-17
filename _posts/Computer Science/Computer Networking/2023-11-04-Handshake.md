---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Computer Network]
tags: [CS, computer network]
render_with_liquid: true
comments: true
---
# Handshake

> 연결을 성립하고 해제하는 과정을 말한다.
> 

## 3 Way HandShake

- **TCP**는 정확한 전송을 보장해야한다.
- 논리적 접속을 성립 하기 위해 **3 Way HandShake**

![Untitled]({{ site.baseurl }}{{ page.url }}/Handshake%20b408cc9a699342bc9386a7ae04b383e1/Untitled.png)

1. Client가 서버에게 SYN : x 를 보낸다.
2. Server는 SYN : x 를 받고 ACK : x + 1 로 대답하면서 SYN : y도 보낸다.
3. Client는 ACK : x + 1와 SYN : y를 받은 뒤 ACK : y + 1에 자신의 다음 정보인 SYN : x + 1를 보낸다…
    
    → ***piggybacking* 방식** : 전송할 데이터가 있는 경우에 제어프레임을 별도로 사용하는 것이 아닌 기존 확인에 덧붙인다.
    

### 왜 이런 방법을 취했을까?

- **2 way handshake** 는 Obsolete에 너무나 취약함!
    - 네트워크 상을 떠돌아디는 packet이 늦게 도착하거나..
    - 변조된 패킷이던가…
- 그렇기에 *ACK* 에도 대답을 하는게 핵심!

## 4 Way Handshake

- 통신이 해제 될때 사용되는 방식

![Untitled]({{ site.baseurl }}{{ page.url }}/Handshake%20b408cc9a699342bc9386a7ae04b383e1/Untitled%201.png)

1. Client는 FIN 플래그를 보낸다.
2. Server는 FIN 을 받고 FIN에 대한 ACK를 보낸다.
3. 데이터를 모두 보내고 나도 종료한다는 FIN을 보낸다.
4. Client는 FIN을 받고 FIN에 대한 ACK를 보낸다. 
5. 서버는 FIN → ACK를 받고 서야 Socket을 닫는다.
6. Client는 기다리고 있다가 TIME_WAIT이 끝나면 Socket을 닫는다.