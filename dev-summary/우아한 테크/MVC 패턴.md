## MVC 패턴

### MVC 흐름
- 클라이언트는 필요한 기능을 컨트롤러에 요청
- 컨트롤러는 알맞은 모델에게 비즈니스 로직 수행을 맡김
- 알맞은 뷰 선택
- 결과 화면 출력

#### Model
- 데이터와 행동을 갖는 객체
- 비즈니스 로직 수행
  - 상태 변화 처리
  - 상태 정보 반환

#### View
- 데이터의 시각화
- 모델이 처리한 데이터를 받아서 사용
- 데이터, 로직 X

#### Controller
- 사용자의 요청을 해석하여 처리하고 결과를 반환
- 모델과 뷰를 느슨하게 연결
- 데이터의 흐름 제어


### MVC를 사용하는 이유
- 동시다발적개발: 백엔드 개발자와 프론트엔드 개발자가 독립적으로 개발 진행
- 구성요소들의 재사용
- 확장성 증가
- 중복 코딩 제거

### MVC 패턴에서 자주 실수하는 부분들
- Model에서 View의 접근 또는 역할 수행
- View에서 일어나는 '과한' 값 검증과 예외 처리
  - 입력받은 값은 Presentation Layer에서 체크
  - 사용자의 권한, 혹은 논리적인 값(존재유무, 일치 여부) 등은 Service Layer에서 체크
  - 값 형식은 유효하지만, 도메인 모델에서 확인해야 할 부분들은 생성자에서 체크하는 것이 좋다.
- View에서 일어나는 비즈니스 로직

### Layer: 5-layer
#### 기존 MVC의 문제점
- 비대한 컨트롤러
- 컨트롤러의 중복 로직
- MVC 중에 어디가 DB에 접근해야 하는지에 대한 애매함이 존재

#### Business Logic Layer: Service Logic
- 클래스 간의 관계 관리
- 상태 저장
- 트랜잭션
- Control - Persistance 계층의 연결

#### Business Logic Layer: Domain Object
- 데이터와 행위를 갖는 객체
- 핵심 비즈니스 로직
- 주요 검증
- Persistance Layer에 맵핑

#### Persistance Layer
- 데이터 처리(CRUD)
- DAO 패턴, ORM

#### Domain Model Layer
- 각 계층 사이에서 전달되는 객체
- DTO 패턴
- 대부분 도메인 모델을 DTO로 사용

### 유효성 검증
#### View
- 간단한 검증
  - 비어있는 값
  - 적절하지 않은 타입(정수 등등)

#### Controller
- 파라미터 존재 유무 검증
  - @PathVariable, @RequestBody

#### Model
- 데이터 검증
  - @Valid
- 로직에 대한 검증

### MVC의 대안
- MVC: 컨트롤러와 뷰의 강한 결합
- MVP: Presenter를 사용하여 뷰의 인터페이스와 결합
- MVVM: View가 ViewModel을 구독