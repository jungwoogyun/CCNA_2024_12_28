# STP

```
1. 스패닝 트리 프로토콜 (STP, Spanning Tree Protocol)

  ㅇ 브리지/스위치로 연결 구성된 네트워크들에서, 
     - Physical Loop (끊임없이 계속되는 루프 순환)를 발견,방지,제거하는 프로토콜

  ㅇ 기반 알고리즘
     - Spanning Tree 형태의 토폴로지를 만드는 알고리즘에 기초함

  ㅇ 동작 방식
     - 연결 브리지 간에 BPDU를 교환하며, 이를통한 정보로부터 브리지 루프를 차단시킴

  ㅇ 관련표준 : IEEE 802.1D "Media Access Control (MAC) Bridges"


2. STP 필요성

  ㅇ 이중화 설계로 중복성 높도록 (Redundant Link 존재) 설계된 네트워크에서,
     발생 가능한 안좋은 상황 셋(3)
     - 브로드캐스트 스톰 : 동일 링크에서 동일 유형의 포워딩이 되풀이됨 
     - MAC 주소 테이블 불안정 : 동일 source MAC 주소를 갖는 MAC 프레임이 다른 포트들로부터 수신됨
     - 다중 프레임 수신 : 동일 MAC 프레임의 여러 복사본이 난무함


3. STP 동작 

  ㅇ BPDU 교환
     - 모든 브리지는, 정기적으로,
        . BPDU이라는 특수 목적의 프레임(Spanning-Tree 관련 정보)을 송출 및 수신하게됨 (2초 마다)
     - BPDU에 담겨지는 주요 정보 : 브리지 ID, 경로 비용, 포트 정보 등
        . 이 정보를 토대로 루트 브리지 선출 및 브리지 루프 차단(포트 차단,포트 블로킹)하게 됨

  ㅇ 브리지 루프 차단
     - 각 브리지에서 루트 브리지로 가는 각 경로의 경로 비용을 계산하여,
     - 경로 비용이 가장 낮은 경로 만 유지하고, 다른 경로는 중단(블록킹)시킴
        . 주로, 루핑 포트 중 하나를 차단시키는 방식으로 운용됨


4. STP에서, 선출 및 차단 과정

  ㅇ 1 단계  :  루트 브리지 선출
     - 가장 낮은 BID 값을 갖는 브리지를 루트 브리지로 선출         

  ㅇ 2 단계  :  루트 포트 결정
     - 루트 브리지까지의 최단 경로비용을 계산하여, 
       Non-Root 브리지 마다 하나의 루트 포트를 결정

  ㅇ 3 단계  :  지정 포트 결정
     - 세그먼트당 하나의 Designated 포트를 결정

  ㅇ 4 단계  :  비지정 포트 봉쇄
     - 결국, 루트포트도 지정포트도 아닌 포트틀 비지정포트로 정하여 최종적으로 차단


5. STP에서, 상태 구분

  ㅇ Disabled (안정)
     - 초기화, 비활성 

  ㅇ Listening (과도기)
     - 포워딩 안함
     - MAC 주소 학습 안함
     - BPDU 수신 및 송신 허용

  ㅇ Learning (과도기)
     - 포워딩 안함
     - 수신 프레임의 MAC 주소 학습 함
     - BPDU 수신 만 허용 

  ㅇ Forwarding (안정)
     - 포워딩 함 
     - 수신 프레임의 MAC 주소 학습 함
     - BPDU 수신 및 송신 허용 

  ㅇ Blocking (안정)
     - 포워딩 안함
     - MAC 주소 학습 안함
     - BPDU 수신 만 허용 


6. STP의 개선

  ㅇ CST (Common Spanning Tree)
     - 모든 VLAN에 공통된 Spanning Tree를 만듬

  ㅇ PVST (Per VLAN Spanning Tree)
     - 각 VLAN 마다 별도 다른 Spanning Tree를 만듬
     - 시스코社 고유의 프로토콜


7. STP의 고속화

  ㅇ 802.1w RSTP (Rapid Spanning Tree Protocol)
     - 토폴로지 변화에 신속한 대응을 위해 차단에서 전달 상태로의 수렴시간 단축

  ㅇ 802.1w PVRST+ (Per VLAN Rapid Spanning Tree Protocol Plus)
     - 각 VLAN 당 하나의 RSTP를 구체화

  ㅇ 이더채널 (EtherChannel)
     - 물리적 이더넷 채널을 여럿을 묶어 하나의 논리적인 대역폭으로 서비스 제공
```
