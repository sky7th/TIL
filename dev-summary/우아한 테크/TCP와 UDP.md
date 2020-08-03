## TCP와 UDP

### Transport Layer
End Point간 신뢰성있는 데이터 전송을 담당하는 계층
- 신뢰성: 데이터를 순차적, 안정적인 전달
- 전송: 포트 번호에 해당하는 프로세스에 데이터를 전달

#### 전송 계층이 없다면
- 데이터의 순차 전송 원활히 X
- Flow (흐름 문제)
  - 원인: 송수신자 간의 데이터 처리 속도 차이. 수신자가 처리할 수 있는 데이터량을 초과했을 경우
- Congestion (혼잡 문제)
  - 원인: 네트워크의 데이터 처리 속도 (ex. 라우터). 네트워크가 혼잡할 때
- 결과적으로는 데이터의 손실이 발생한다.

### TCP (Transmission Control Protocol)
- 신뢰성있는 데이터 통신을 가능하게 해주는 프로토콜
- 특징: Connection 연결 (3 way-handshake) - 양방향 통신
- 데이터의 순차 전송을 보장
- Flow Control (흐름 제어)
- Congestion Control (혼잡 제어)
- Error Detection (오류 감지)

#### 세그먼트 (Segment)
- TCP 프로토콜의 PDU 

#### TCP Header
- ACK: 받는 사람이 다시 전송해줄 때 제어하기 위해 사용하는 flag 비트
- SYN: TCP가 커넥션을 연결할 때 사용하는 flag 비트
- FIN: 커넥션을 끊을 때 사용하는 비트 

#### TCP의 3 way-handshake (Connection 연결)
1. SYN 비트를 1로 설정해 패킷 송신 (Client -> Server)
2. SYN, ACK 비트를 1로 설정해 패킷 송신 (Server -> Client)
3. ACK 비트를 1로 설정해 패킷 송신 (Client -> Server)

#### TCP의 데이터 전송 방식
1. Client가 패킷 송신
2. Server에서 ACK 송신
3. ACK를 수신하지 못하면 재전송

#### TCP의 4 way-handshake (Connection close)
1. 데이터를 전부 송신한 Client가 FIN 송신
2. Server가 ACK 송신
3. Server에서 남은 패킷 송신 (일정 시간 대기)
4. Server가 FIN 송신
5. Client가 ACK 송신

#### TCP의 문제점
- 전송의 신뢰성을 보장하지만 매번 Connection을 연겨해서 시간 손실 발생 (3 way-handshake)
- 패킷을 조금만 손실해도 재전송

### UDP (User Datagram Protocol)
- TCP보다 신뢰성이 떨어지지만 전송 속도가 일반적으로 빠른 프로토콜
- 순차 전송 X, 흐름 제어 X, 혼잡 제어 X
- Connection (3 way-handshake X)
- Error Detection
- 비교적 데이터의 신뢰성이 중요하지 않을 때 사용 (ex. 영상 스트리밍)

#### User Datagram 
- UDP 프로토콜의 PDU
- 쪼개지 않음
- 직접 어플리케이션 단에서 쪼개줘야함

#### UDP의 데이터 전송 방식
1. Client가 패킷 송신

### 중요한 점
- TCP, UDP의 특성을 파악하고 상황에 따라 적절한 프로토콜을 사용할 수 있다.
- TCP, UDP의 헤더에 대해 파악하고 성능 개선에 이용할 수 있다.
