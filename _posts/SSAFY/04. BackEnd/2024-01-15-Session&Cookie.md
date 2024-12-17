---
author: "unggu"
date: 2024-01-11 12:17:32 +0800
categories: [SSAFY, BackEnd]
tags: [SSAFY, BackEnd, JDBC, Servlet, JSP, Session, Cookie]
render_with_liquid: true
comments: true
image:
  path: https://www.ssafy.com/swp/images/sns_img.png
---


# Session & Cookie

- Http Protocol의 특징
  - clinet가 server에 요청
  - server는 요청에 대한 처리 후 client에 응답
  - 응갑의 연결을 헤제한다.
    - 지속적인 연결로 자원낭비를 줄이기 위해 연결을 해제
    - 그러나 일반적으로 server와 연결 상태를 유지해야할 필요가 있을 수 있음
    - 일반적인 HttpSession의 단점을 보완하기 위해 사용됨

## Cookie

- **서버**에서 사용자의 **하드웨어**에 저장하는 정보 파일
- 서버 측에서 request Header에 넣어 자동으로 서버에 전송
- _key_ 와 _value_ 로 이루어져 있음
- browser마다 저장되는 쿠키가 다르다.
- 쿠키는 **이름, 값, 유효기간, 도메인, 경로**로 구성되어 있다.

### 쿠키의 사용 목적

- **세션 관리** : 사용자의 정보나 장바구니 같은 서버도 알아야할 정보 저장
  - ID 저장 (자동 로그인)
  - 쇼핑몰 장바구니 기능
- **개인화** : 사용자마다 다른 웹 페이지 구성
  - 일주일간 다시 보지 않기
  - 맞춤형 광고
- **트래킹** : 사용자를 추적

### Cookie의 동작 순서

1. Cline가 페이지를 요청
2. WAS는 Cookie를 생성
3. HTTP Header에 Cookie를 넣어 응답
4. 추후 클라이언트는 서버에 요청 할 때 Cookie를 함께 전송한다.
5. Broswer가 종료되어도 쿠키의 만료 기간이 남아 있다면 Client는 계속해서 보관한다.
6. 추후 해당 사이트 재 방문시 쿠키 사용

### Cookie의 특징

- 이름, 값, 만료일, 경로 정보로 구성
- 클라이언트는 총 300개의 쿠키, 도메인당 20개의 쿠키
- 쿠키는 4KB가 최대이다.

## Session

- 방문자가 웹 서버에 접속해 있는 상태를 하나의 단위로 보고 그것을 세션이라 한다.
- WAS의 메모리에 Object 형태로 저장
- 저장소가 허가하는 용량 까지 제한 없이 저장 가능
- 일반적으로 site내 화면이 이동해도 로그인 정보가 풀리지 않고 유지되는 것

### Session의 동작 순서

- 클라이언트가 페이지를 요청
- 서버는 접근한 클라이언트의 Request-Header 필드인 Cookie를 확인하여, 클라이언트가 해당 session-id를 보냈는지 확인
- 서버는 session-id를 쿠키를 사용해 서버에 저장
- 클라리언트 재 접속시 이 쿠키를 이용하여 session-id 값을 서버에 전달

### session의 특징

- 웹 서버에 사용자의 상태를 유지하기 위한 정보를 저장
- 웹 서버에 저장되는 쿠키 (= 세션 쿠키)
- 브라우저를 닫거나 서버에서 세션을 삭제 했을 때만 삭제가 되므로 쿠키보다 보안이 좋다.
  - 중요한 정보는 서버만 가지고 있다. 세션은 서버가 가진다.
- 각 클라이언트 고유 Session ID를 부여
- Session ID

## Session vs Cookie 정리

![Untitled]({{ site.baseurl }}{{ page.url }}/resources/Session%20&%20Cookie%20b7baa7aab0a04efbad69bd089fa05b5b/Untitled.png)
