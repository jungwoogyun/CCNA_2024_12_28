# DYNAMIC ROUTING PROTOCOL


상세 이동
---
|-|-|
|-|-|
|IGP PROTOCOL|[바로가기](./DOCUMENT/01)|
|EGP PROTOCOL|[바로가기](./DOCUMENT/02)|

---
#
---

AS(AUTONOMUS SYSTEM)
---
> AS란 <br>
---
```
자치시스템
동일한 라우팅 정책으로 하나의 관리자에 의하여 운영되는 네트워크, 즉 한 회사나 단체에서 관리하는 라우터 집단
각각 AS영역은 고유식별번호를 가진다(0-65535)
```

![imgipasSys10](https://github.com/MY-ALL-LECTURE/CCNA/assets/84259104/0df3f790-538c-484b-8467-024467e2108b)
 
> AS번호 장점
---
```
인터넷상에서 독립적인 네트워크를 식별
외부 네트워크와의 경로를 교환
고유한 라우팅 정책을 구현
```

> ASBR이란
---

```
AS Boundary Router
AS 가장자리에서 다른 AS를 연결할 때 사용되는 라우터<br>
자신의 AS와 인접한 다른 AS에 대한 정보를 가지며 자신을 경유하는 라우터에 외부 AS에 대한 정보를 제공 

```


---
#
---

IGP/BGP
---
![350_1](https://github.com/MY-ALL-LECTURE/CCNA/assets/84259104/3c677f4f-a92c-4ecb-a9c9-43956c464310)


> IGP <br>
```
IGP (Interior Gateway Protocol 또는 Intra-domain Routing Protocol)
자치시스템 내부에서 만 이루어지는 라우팅 프로토콜 (Routing Protocol)
```

> BGP <br>
```
1. BGP (Border Gateway Protocol)

  ㅇ 자치시스템 (AS) 상호 간에 적용되는 라우팅 프로토콜 (Inter-Domain Routing Protocol)
     - 즉, 독립 운용되는 대규모 네트워크 (AS) 간에, 네트워크 정보를 교환하기 위해 주로 사용됨
```

