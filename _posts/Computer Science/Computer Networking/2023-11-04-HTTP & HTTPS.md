---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Computer Network]
tags: [CS, computer network]
render_with_liquid: true
comments: true
---
# HTTP & HTTPS

## HTTP

> 인터넷 상에서 클라이언트와 서버가 자원을 주고 받을 때 쓰는 통신 규약
> 
- 일반적인 텍스트 교환 프로토콜
- 보안 이슈란 치명적인 문제가 존재
    - 도청이 가능
    - 다른 사람으로 위장 가능
    - 변조가 가능

## HTTPS

> 인터넷 상에서 정보를 암호화하는 SSL 프로토콜을 사용해 클라이언트와 서버가 자원을 주고 받을 때 쓰는 통신 규약 (SSL, TSL)
> 
- 일반적으로 공개키 + 대칭키 방식으로 보안 연결을 설정한다.

### SSL의  HandShake

![Untitled]({{ site.baseurl }}{{ page.url }}/HTTP%20&%20HTTPS%209ea4328ea3924bf7a2f2e170d46e8060/Untitled.png)

1. 서버에게 `client hello` 와 함께 암호화에 필요한 정보(암호 알고리즘, 압축 방식 ,랜덤 데이터)를 함께 보낸다.
2. 서버는 클라이언트에게 `server hello` 와 함께 정보에 대한 응답과 CA 인증서를 보낸다.
    1. ca : 믿을 수 있는 민간 인증서 
3. 클라이언트는 CA가 믿을 수 있는지 체크하고 랜덤 난수 바이트를 생성( 서버와 클라이 언트가 함께 생성한)하여 공개키(CA에 있는)로 암호화 한 뒤에 서버에게 보낸다.  → 추후 대칭키로 사용 예정
4. 서버는 자신의 비밀 키로 복호화 한 뒤에 대칭키를 알아낸다.
5. 서로의 대칭키로 통신한다.
6. 세션 종료시에 대칭키는 서로 폐기 한다.