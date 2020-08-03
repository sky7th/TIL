## Process & Thread

### Process

#### Program
- 실행되기 전 상태의 명령어, 코드 및 정적인 데이터의 묶음

#### Process
- 실행 중인 Program
- 운영체제로부터 시스템 자원을 할당 받는 작업의 단위

#### Process 구조
- Stack -> 매개변수, 지역 변수 등 임시적인 자료
- Heap -> 동적으로 할당되는 메모리
- Data -> 전역 변수
- Text(Code) -> Program의 코드

#### PCB (Process Control Block)
- 각 프로세스는 운영체제에서 PCB로 표현
- PID: 프로세스 식별자
- 프로세스 상태: new, ready, running, waiting, halted 등
- 프로그램 카운터: 다음 실행할 명령어의 주소
- 스케줄링 정보: 우선순위 등


### Thread

#### Thread
- 프로세스 내에서 실행되는 흐름의 단위
- CPU 이용의 기본 단위
- Text, data, heap 영역을 공유
- 각 thread는 별도의 stack 영역을 가짐

### Multi Thread
- 프로세스의 자원을 공유
- 향상된 응답성
- Context switching 비용이 적음
- 자원을 공유하는 만큼 충돌을 주의해야 함 (Thread-safe 하게!)
- ex) Web Server

### Multi Process
- 하나의 작업을 여러 개의 프로세스가 처리
- 프로세스간 통신 (IPC, Interprocess communication)
- Context switching 비용이 큼
- 자식 프로세스 중 하나가 문제가 생겨도 다른 프로세스에 영향이 없음
- ex) Google Chrome