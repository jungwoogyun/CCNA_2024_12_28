# STATIC ROUTING

라우팅 프로토콜
---
>라우팅 프로토콜이란 <br>
```
  ㅇ `라우터 간에 라우팅 정보의 교환` 및 `라우팅테이블의 유지관리`를
     동적으로 수행하는 프로토콜
```
>라우팅 프로토콜의 필요 기능 및 요소  <br>
```
  ①  라우팅 수행 프로세스
     - 라우팅 정보를 주고받기 위한 프로세스
     - 최적 경로 계산 및 이를 라우팅 테이블에 기록하는 프로세스
     - 토폴로지 변화를 감지하고 이를 자동으로 학습 반영하는 프로세스

  ②  라우팅 테이블의 갱신관리
     - 최적 경로 결정을 위한 알고리즘 및 프로세스들을 적용

  ③  라우팅 알고리즘
     - 최적 경로 산출을 하여가며 라우팅 테이블의 갱신,유지관리

  ④  라우팅 프로토콜 메세지
     - 라우팅 정보를 라우터들 간에 운반,전달,교환 등 
```

> 라우팅 프로토콜의 구분<br>
```
  ㅇ 알고리즘 또는 라우터끼리 공유하는 정보(Distance Vector, Link State)에 따라
     - Distance Vector Routing Protocol
       . RIP,  IGRP,  EIGRP
     - Link State Routing Protocol
       . OSPF,  IS-IS

  ㅇ AS 내부간(Intra-domain), 외부간(Inter-domain) 구분방식에 따라
     - AS 내부 라우터 간 : IGP
      . RIP,  OSPF,  IS-IS
     - AS 외부 라우터 상호간 : EGP
       . EGP,  BGP,  IDRP

  ㅇ 업체 종속적인 라우팅 프로토콜
     - IGRP, EIGRP (시스코社)

  ㅇ Classful 및 Classless 구분에 따라
     - Classful Routing
       . RIP v1,  IGRP
     - Classless Routing
       . RIP v2,  EIGRP,  OSPF,  BGP
```

> 라우팅 프로토콜의 성능 비교

![20240530172423](https://github.com/MY-ALL-LECTURE/CCNA/assets/84259104/b3c15eb0-1966-4fd0-b0f9-5ab951702443)


> 라우티 메트릭<br>
```
  ㅇ RIP         :  Hop Count (홉 카운트)
  ㅇ OSPF        :  Link Cost (링크 비용) 
     - 링크 대역폭,전송속도에 기초하여 계산되고, 16 비트 Metric 값(1~65,535)으로 표현
  ㅇ IGRP, EIGRP :  Bandwidth,Delay,Load,Reliability,MTU를 조합하여 계산한 Cost가 가장 낮은 경로
  ㅇ BGP         :  속성(Attribute)이라고 하는 네트워크 도달성(Reachability) 정보
     - BGP Path Attribute : Next_Hop, Weight, Local Preference, AS_path, Origin type, MED 등
```

---
#
---

정적인 라우팅 (Static Routing)
---
> 정의<br>

```
  ㅇ 네트워크 관리자가 패킷의 경로를 수동으로 구성하는 라우팅 방식
     - 네트워크 환경 변화와는 무관하게 항상 같은 경로로 만 라우팅 경로의 설정 및 유지
        . 고정적이므로, 만약 토폴로지 변화 때, 수동으로 직접 작업해야 함
```

> 특징<br>
```
  ㅇ 관리자가 라우팅 테이블을 직접 구축
     - 트래픽 패턴이 예측가능하고 정적인 구조를 갖는 네트워크에서 효과적으로 동작하지만,
     - 네크워크 변경에 따른 대응에 다소 어려움 (주로 회선교환 등에 쓰임)

  ㅇ 멀리에 있는 라우터까지의 경로를 일일이 수작업으로 경로를 구성
     - 과거, SNA 및 X.25는 이 관리방식을 따르고 있음

  ㅇ 유연성이 없어, 혼잡에 즉각적인 대응에 취약함
```

> 설정<br>
```

  ㅇ 정적 경로는 라우터에서 관리자가 일부러 수동으로 설정하는 경로를 말함 

  ㅇ 라우터끼리 알아서 동적으로 경로를 구성하는 것이 여러모로 편리하고 안정하나,
     다음과 같이 정적인 경로의 설정이 일부러 필요한 경우도 있음

     - Default Route 설정시
        . 외부로 나가는 통로를 하나 만 설정할 경우에 사용
     - 라우터 내의 Null Interface에 대한 경로 설정시
        . 바람직하지 않은 트래픽을 필터링 할 경우에 주로 사용
     - Stub Network에 대한 경로 설정시 등
        . 내외부 통로가 하나 밖에 없는 끝단 네트워크
```

> 명령어<br>
```
  ㅇ 시스코社 라우터에서 Static Route를 설정하는 명령어 例

     - ip route  ①192.168.1.0  ②255.255.255.0  ③192.169.5.1
       ① 목적지 네트워크의 IP 주소
       ② 목적지 네트워크의 서브네트 마스크
       ③ 목적지로 향하는 바로 다음의 라우터 IP 주소 (Next Hop)
```



---
#
---

