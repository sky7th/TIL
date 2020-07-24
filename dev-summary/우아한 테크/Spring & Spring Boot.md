## Spring & Spring Boot
### Spring과 Spring Boot의 개념
#### Spring
- Spring Framework(DI, IoC)를 이용해서 엔터프라이즈 애플리케이션을 보다 쉽게 만들 수 있다.
- 엔터프라이즈 애플리케이션: 트랜잭션 처리, 대규모 데이터 관리
#### Spring Boot
- 스프링부트는 단독 실행되는, 상용화 가능한 수준의 스프링 기반 애플리케이션을 쉽게 만들어낼 수 있다. 
- 최소한의 설정으로 스프링 플랫폼과 서드파티 라이브러리들을 사용할 수 있도록 하고 있다.

### Spring과 Spring Boot의 차이
#### Spring이 해결하고자 하는 것
- 의존성 주입
  - 객체 간 결합을 느슨하게 만듬
  - 코드 재사용성 증가 및 단위테스트가 용이
- 중복된 코드 제거
  - ex) JDBCTemplate
  - 비즈니스 로직에만 집중 가능
- 다른 프레임워크와의 통합
  - ex) JUnit & Mockito for Unit Testing
  - 이미 훌륭하게 제공되는 프레임워크를 통해 해결하고자 하는 문제를 높은 품질로 해결
#### Spring Boot가 해결하고자 하는 것
- Auto Configuration 자동 설정
  - 스프링 기능을 위한 자동 설정을 지원
  - starter 의존성을 통해 간단히 설정할 수 있다.
- 쉬운 의존성 관리
- 내장 서버
  - 내장 서버는 애플리케이션 배포 시 복잡함을 피하게 해준다.