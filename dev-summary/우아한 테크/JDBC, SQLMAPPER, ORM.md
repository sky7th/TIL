## JDBC, SQLMAPPER, ORM
### Persistence
데이터를 생성한 프로그램의 실행이 종료되더라도 사라지지 않는 데이터의 특성

### JDBC
- JDBC API(Java)
  - Java 진영의 Database 연결 표준 인터페이스
- 불편한 점
  - 중복 코드가 많다.
  - 쿼리를 일일히 써야한다.
  - 커넥션 관리를 해야한다.

### SQLMAPPER
- JDBC(Spring)
  - JDBC API의 불편함을 해결하기 위해 생김
- MyBatis
  - SQL을 분리하자.
  - 쿼리를 Java에서 XML로
    - 복잡한 JDBC코드 X
    - ResultSet과 같이 결과값을 매핑하는 객체 X
    - 메소드에 쿼리를 매핑
    - 간단한 설정, 관심사 분리!

### ORM
SQL에 의존적인 개발.. 굉장히 불편함

물리적으로 SQL과 JDBC API를 데이터 접근 계층에 숨기는 데 성공했을지는 몰라도, 논리적으로는 엔티티와 아주 강한 의존 관계를 가지고 있다.

패러다임의 불일치! -> 객체 지향 안해! -> ORM 등장!

- JPA(Java)
- Hibernate(JPA 구현체)
- JPA(Spring)
  - EntityManager 복잡해 -> 한단계 더 추상화 -> Repository 
  - Application - Spring Data JPA(Repository) - JPA - Hibernate - JDBC - RDB
- JDBC(Spring)
  - ORM이라고 하기엔 좀 애매함
  - Spring Data JDBC a simple, limited, opinionated ORM.
  - Application - Spring Date JDBC - JDBC API - JDBC Driver Manager - JDBC Driver - DBMS