# IGP

---
# DISTANCE VECTOR
---

RIP
---
|-|
|-|
|[참고](https://haekt-log.tistory.com/68)|

> RIP
```
Distance Vector Routing Protocol (거리와 방향을 보고 라우팅을 한다.)
Metric : Hop Count (라우터 개수), 15대까지
소규모 네트워크에 사용
Multicast Address : 224.0.0.9 (D Class)
정보 교환(광고)을 30초마다
수렴 시간 늦다.

- 동작 방식.
1> Update Packet 교환(30초마다)
2> RIP Database에 업데이트 정보 저장
# show ip rip database
3> Routing Tab
le Update
# show ip route
- 명령어
[R1]
router rip
version 2
network 1.0.0.0
network 192.168.10.0
no auto-summary

[R2]
router rip
version 2 
network 1.0.0.0
network 192.168.20.0
no auto-summary

```
---
# LINK STATE
---
|-|
|-|
|[참고](https://blog.naver.com/luexr/222460005000)|

> OSPF(Open Shortest Path First)
```
Link-State Routing Protocol(링크 상태 정보)
Metric : 10^8 / 실제대역폭(속도) = Cost
Serial : 10^8 / 1,544,000bps =  64(Cost)
FastEthernet : 10^8 / 100,000,000bps = 1(Cost)
GigaEthernet : 10^8 / 1,000,000,000bps = 0.1 => 1(Cost)

Multicast : 224.0.0.5(DR) & 224.0.0.6(DROther)
AD(관리자 거리값) : 110
변화가 있을 경우에만 정보 교환
(수렴 시간이 빠르고, 쓸데 없는 트래픽이 적다.)
대규모 네트워크에서 사용(Area 단위)

* 동작 방식
1> Hello Packet : Neighbor 성립
# show ip ospf neighbor
2> LSA(Link-State Advertise) 정보 교환
3> LSDB(Link-State Database) 정보 저장
# show ip ospf database
4> SPF(Dijkstra) 알고리즘 경로 계산
5> LSDB(Link-State Update) 정보 갱신 = SPFT(Shortest Path First Tree)
6> Routing Table Update
# show ip route

```

---
# DISTANCE VECTOR +  LINK STATE
---
|-|
|-|
|[참고](https://m.blog.naver.com/luexr/222441096481)|

>EIGRP
```
Distance Vector(RIPv2) + Link-State(OSPFv2) = Hybrid Routing Protocol
중규모 네트워크에 사용
Metric : K 상수
Bandwidth : 속도(대역폭)(Serial : 1544kbps, FastEthernet : 100Mbps)
Load : 부하(1/255)
Delay : 지연(Serial : 20000, FastEthernet : 100)
Reliability : 신뢰도(255/255)
MTU : 최대 전송 단위(1500byte)
(K1, K3 ★)
10^10 / 제일느린대역폭 값 = A
+
모든 Delay 값 / 10 = B
(A + B) * 256 = K 값(EIGRP Metric 값)
AD : 90
Multicast Address : 224.0.0.9
변화 시 에만 정보 교환(수렴 시간이 빠름.)

- 동작 방식
1> Hello Packet : Neighbor 성립
# show ip eigrp neighbors
2> Update Packet 
3> EIGRP Topology 에 저장
# show ip eigrp topology
4> Dual 알고리즘 : 경로 계산
5> 라우팅 테이블 업데이트
# show ip route

- 명령어
* 첫 번째 방법
router eigrp AS번호 ( 1 - 65535 )
eigrp router-id ?
network 자신에게붙어있는네트워크주소
no auto-summary

* 두 번째 방법
router eigrp AS번호 ( 1 - 65535 )
eigrp router-id ?
network 자신에게붙어있는네트워크주소 와일드카드마스크주소
no auto-summary
```




