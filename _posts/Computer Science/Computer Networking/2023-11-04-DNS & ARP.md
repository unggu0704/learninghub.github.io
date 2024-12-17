# DNS & ARP

- 일반적으로 통신을 하기 위해서는 IP, MAC 주소가 필요하다.
- IP : 네트워크 계층에서 논리 주소로써 네트워크를 찾아가는 용도
- MAC : 데이터 링크 계층에서 고정된 물리 주소

## DNS

우리가 일반적으로 사용하는 `[www.naver.com](http://www.naver.com)` 을 사용 (도메인 네임)

이것은 IP 주소를 대신해서 사용한다.

- `[www.naver.com](http://www.naver.com)` → IP 주소로 바꿔 주는것 **DNS**
- 도메인 네임 ↔ IP 주소를 대응하는 데이터 베이스
- DNS는 UDP 통신을 사용한다.
    - Request의 양이 작기에 UDP Request 사이즈에 딱 맞는다.
    - 3-way-handshake로 연결을 유지할 필요가 없다… (오버헤드)
    - 손실이 나더라도 Appliacation Layer에서 제어가 가능 → 원래 UDP의 손실 제어는 이렇게
- 53번 port 사용

## ARP

- IP 주소를 가져왔다.. 하지만 MAC 주소는?
- ARP 테이블을 활용해서 해당 MAC주소를 찾는다.
- 하지만… 모든 정보가 ARP 테이블에 없을 수도 있다.
    - BoradCasting을 활용해 ARP 요청을 모두 보낸다.
    - 응답하는 기기만 ARP 응답을 보내 ARP 테이블에 저장한다.
    - 하지만 MAC 주소는 영원하지 않다… 언젠가 바뀌기에 ARP 테이블도 주기적으로 데이터를 갱신