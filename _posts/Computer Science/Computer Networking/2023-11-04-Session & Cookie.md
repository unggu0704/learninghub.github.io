---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Computer Network]
tags: [CS, computer network]
render_with_liquid: true
comments: true
---
# Session & Cookie

- 이들을 사용하는 이유는?
    - HTTP 프로토콜은 **Connectionless 프로토콜** 이다.
    - 즉 Request(요청)을 하고 그에 대한 Response(응답)을 하고 연결을 헤제한다.
    - 물론 1.1 버전부터는 request를 재활용 하기도 한다.
    - 어쨌든 서버와 클라이언트 간의 관계가 1회용이라면 매번 인증에 대한 비용이 증가한다.
- cookie & session으로 해결하자.

## Cookie

- HTTP 의 일종
- Server가 Client의 컴퓨터에 저장하는 작은 기록정보 파일
    - 언제든지 필요하다면 참조 가능
- 이름, 값, 만료일(저장기간), 경로 정보로 구성
- Clinet - Server 연결시에 Server가 Client에게 HTTP 화면을 보내면서 Cookie를 Client에게 저장한다.
- 추후 Server에게 요청 할 때 Cookie와 함께 제공

### 사용 예시

- 오늘 이창을 다시 보지 않기
- 아이디와 비밀번호를 저장하기

## Session

- Client - Server의 연결을 하나의 상태로 보고 그것을 지속적으로 연결 시키는 것
- Cookie와 달리 Server 측에 저장한다.
    - Client에게 있는 것이 아니기에 보안성으로 우수함
- 각 Client에게 SessionID를 부여
- 추후 Cookie 에 SSEID를 함께 전송하여 Server는 이를 바탕으로 처리한다.

## Cookie VS Session

- Cookie는 Client에게 Session은 Server에게
- Cookie는 브라우저가 종료 되도 유지 될 수 있지만 Session을 브라우저가 종료되는 즉시 사라진다.
- Cookie는 속도가 빠르지만 보안성이 낮고 Session은 속도는 느리지만 보안성이 높다.
-