# VNet & VPN

## VNet

- Azure의 다양한 리소스와 통신이 가능하다.  (이를 위해선 VPN이 필요)
- 확장, 격리 등 인프라의 이점을 활용 가능
- 서브넷 정의 가능
    - 웹 서버를 위한 서브넷(**WebSubnet**)
    - 데이터베이스를 위한 서브넷(**DBSubnet**)
    - 이 둘은 하나의 VNet안에서 서로간에 통신이 가능하다.
    - DBSubnet은 오직 WebSubnet으로만 오는 통신을 수용한다. (다른 외부 통신은 허용하지 않는다.)
    - WebSubnet은 인터넷 트래픽을 제어 작업

## VPN

### site to site VPN

- Azure의 VNet을 활용해 외부 온프레미스 환경과 통신될 때 사용될 수 있음
    - 기존의 VNet에 VPN 게이트웨이 설정
- Azure Database의 내용을 백업할 필요가 있을때 온프레미스의 백업 서버가 주기적으로 Azure 데이터 베이스에 접속한다.

### point to site VPN

- 직원들은 언제나 회사 노트북에 VPN 클라이언트를 설치해 Azure 클라우드 접속 가능
- 재택근무가 가능하다.
