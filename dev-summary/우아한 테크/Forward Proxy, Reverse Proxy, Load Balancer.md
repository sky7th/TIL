## Forward Proxy, Reverse Proxy, Load Balancer
### Proxy Server
- 대신 처리하는 서버
- 클라이언트와 서버간의 중계서버로, 통신을 대리 수행하는 서버
- 캐시/보안/트래픽 분산 등 여러 장점을 가질 수 있음

### Forward Proxy
- 클라이언트와 인터넷 사이에 위치
- 일반적으로 말하는 Proxy
  - 인터넷 속도를 향상 시키기 위해..
  - 외국에서 접속하는 것처럼 테스트하기 위해..
  - IP추적을 방지하기 위해..
- 특징
  - 캐싱
    - 전송 시간 절약
    - 불필요한 외부 전송 X
    - 외부 요청 감소: 네트워크 병목 현상 방지
  - 익명성: 클라이언트가 보낸 요청을 감춤
    - Server가 응답 받은 요청을 누가 보냈는지 알지 못하게 함
    - Server가 받은 요청 IP = Proxy IP

### Reverse Proxy
- 인터넷과 서버 사이에 위치
- 특징
  - 캐싱
    - 클라이언트가 요청한 내용을 캐싱 (Forward와 동일)
  - 보안
    - 서버 정보를 클라이언트로부터 숨김
    - Client는 Reverse Proxy를 실제 서버라고 생각하여 요청
    - 실제 서버의 IP가 노출되지 않음
  - Load Balancing
    - 부하 분산(요청을 나눠줌)
    - 부하분산: 해야할 작업을 나누어 서버의 부하를 분산시키는 것

### Load Balancing
- 여러 대의 서버가 분산(나누어) 처리할 수 있도록 요청을 나누어주는 서비스
- 종류
  - OSI 7 Layer 기준으로 어떤 것을 나누는지에 따라 다름
  - L2: Mac 주소를 바탕으로 Load Balancing
  - L3: IP 주소를 바탕으로 Load Balancing
  - L4: Transport Layer(IP & Port) Level에서 Load Balancing (TCP/UDP)
    - ex) https://aaa.com/ 로 접근 시 서버 A, B로 Load Balancing
  - L7: Application Layer(User Request) Level에서 Load Balancing (HTTPS/HTTP/FTP)
    - ex) https://aaa.com/ 로 접근 시 /category와 /search를 담당 서버들로 Load Balancing