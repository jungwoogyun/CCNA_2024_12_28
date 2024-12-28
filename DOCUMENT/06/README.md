# ARP

ARP 기본
---
> ARP(Address Resolution Protocol) 프로토콜이란<br>
```
OSI 7 Layer에서 Layer 3에 위치한 프로토콜이며, MAC 주소와 IP 주소를 서로 연결하는 용도로 사용한다.
LAN 환경에서는 MAC 주소를 기반으로 통신하기 때문에 ARP는 IP 주소를 기반으로 MAC 주소를 알아오는 역할
``` 

> 네트워크 모델 확인<br>

<img width=400px src="https://github.com/MY-ALL-LECTURE/CCNA/assets/84259104/47b73ea2-aaae-4145-a8a6-e9cf896e70a6" />

> ARP 동작방식<br>
```
ARP 요청
  만일 이전에 전혀 통신한 경험이 없는 LAN의 라우터에 외부로부터 data packet이
  전달되어 목적지 호스트를 찾을때, - 라우터가 최초로 하는 일은 ARP Request packet(ARP 요청 패킷)을 LAN의
  전체 노드에 송출함 (브로드캐스트) - APP 요청 메세지에는 송신자 자신의 MAC 주소 및 IP 주소, 목적지 IP 주소를 채
  우지만, 목적지의 MAC 주소는 0 으로 채워넣음
ARP 응답
  ARP 요청 패킷에 포함된 IP 주소와 일치하는 Host는 자신의 IP 주소 및 물리주소
  를 채워놓은 ARP Reply packet(ARP 응답패킷)을 해당 라우터에게 송출함으로써,
  물리 주소 및 IP 주소 상호간의 관련     정보를 얻게됨 (유니캐스트)
```
> ARP 캐시<br>
```
ARP 캐쉬를 최신으로 유지
  - 각 노드(node)는 ARP의 효율적 수행을 위해 ARP 캐쉬를 최신으로 유지하는 일이 필수
  - 캐쉬의 각 항목은 새로이 생긴 후로 20분이 지나면 자동적으로 소멸 (RFC 1122)
  - 따라서, 자주 사용되는 곳은 ARP cache를 통해 즉각적으로 조회가 가능

ARP 트래픽 경감
  - 만약 ARP cache에 조회되는 자료가 없는 경우에만 ARP request packet 을 송출하게 되어 전체적으로
    LAN 트래픽을 경감시킴

ARP 캐쉬 확인 명령어
  - arp -a : 주요 표시 내용(IP 주소 또는 호스트 이름,물리 주소,유형:동적,정적)
```
