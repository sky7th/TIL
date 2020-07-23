### 스프링 부트 기능정의
- 단독실행 가능한 스프링 애플리케이션 생성
- 내장 컨테이너로 톰캣, 제티 혹은 언더토우 중에서 선택가능
- 스타터를 통해 간결한 의존성 구성 지원
- 스프링에 대한 자동구성 제공
- 더이상 XML구성 필요없음
- 제품출시 후 운영에 필요한 다양한 기능(상태점검, 모니터링) 제공

한마디로 스프링 프레임워크를 기반으로 한 개발 플랫폼

### 스프링 부트 구성요소
- 빌드도구(그레이들 vs 메이블)
- 스프링 프레임워크(4.X vs 5.x)
- 스프링 부트(1.5 vs 2.0)
- 스프링 부트 스타터

### Starter
- sprint-boot-autoconfigure + sprint-boot-dependencies
- 스타터를 통해 간결한 의존성 구성 지원
- 개발자가 신경써야 하는 것
  - 스프링 부트 버전
  - 사용하려는 라이브러리의 스프링 부트 스타터 지원 여부
  - 지원하지 않는 경우 사용하려는 라이브러리 등록 방법

### 자동구성(Auto-Configuration)
- 스프링 부트가 기술흐름에 따라 제공하는 관례(Convention)적인 구성
- 봐야할 모듈: spring-boot-autoconfigure
- 동작선언
  - @EnableAutoConfiguration(in @SpringBootApplication)
  - @Configuration
- 사용 애너테이션
  - @Configuration
  - @ConditionOn
    - 있거나 없거나
- ~AutoConfiguration 접미사

### 외부구성(External Configuration)
- 실행인자
  - SPRING_APPLICATION_JSON
- 환경변수
- application.yml or application.properties
- application-(default|profiles).yml or application-(default|profiles).properties

### Programming in Spring Environment
- @ComponentScan을 통해 ApplicationContext 적재
  - @Repository
  - @Component
  - @Service
  - @Controller & @RestController
  - @Configuration
    - @Bean
    - @ConfigurationProperties
- DI, IoC, @Autowired
- @Value vs @ConfigurationProperties
- AOP


### setting.gradle
`rootProject.name = 'spring-boot'`
- 멀티 프로젝트 구성시 사용
- 프로젝트 이름
- 하위 프로젝트 정의
- 하위 프로젝트 설명


### @WebMvcAutoConfiguration
Spring Boot를 사용했을때 WebMvcAutoConfiguration 클래스를 통해서 Spring MVC를 자동으로 설정한다. 여기서 자동설정이 되는 조건이 중요하다.
```java
@Configuration
@ConditionalOnWebApplication
@ConditionalOnClass({ Servlet.class, DispatcherServlet.class,
		WebMvcConfigurerAdapter.class })
@ConditionalOnMissingBean(WebMvcConfigurationSupport.class)
@AutoConfigureOrder(Ordered.HIGHEST_PRECEDENCE + 10)
@AutoConfigureAfter({ DispatcherServletAutoConfiguration.class,
		ValidationAutoConfiguration.class })
public class WebMvcAutoConfiguration {
  ...
}
```
Spring Boot에서 WebMvcAutoConfiguration이 자동으로 설정될 조건은 아래와 같다.
- 클래스패스에 Servlet.class, DispatcherServlet.class, WebMvcConfigurerAdapter.class가 존재해야한다.
- WebMvcConfigurationSupport 타입의 빈이 존재해서는 안된다.
- 웹 어플리케이션으로 실행된다. (ApplicationContext가 WebApplicationContext인 경우)
- [출처: https://gunju-ko.github.io/spring/2018/06/28/@EnableWebMvc.html](https://gunju-ko.github.io/spring/2018/06/28/@EnableWebMvc.html)

### @Bean
- 주로 개발자가 제어할 수 없는 외부 라이브러리 클래스 등록할 때 사용

### @Component
- 주로 내가 작성한 클래스 등록할 때 사용

### @Service
- 트랜잭션 필요할 때
- 필요없으면 @Component

### 스프링 Bean 객체
- 스프링 IoC 컨테이너에서 생성하고 호출하고 소멸되기까지 생명주기를 관리하는 객체

### @ControllerAdvice
- [@ControllerAdvice, @ExceptionHandler를 이용한 예외처리 분리, 통합하기(Spring에서 예외 관리하는 방법, 실무에서는 어떻게?)](https://jeong-pro.tistory.com/195)

### spring-restdocs
- [Spring Rest Docs를 이용한 API 문서 만들기](https://jaehun2841.github.io/2019/08/04/2019-08-04-spring-rest-docs/#spring-rest-docs-architecture)
- [Spring Rest Docs 적용](https://woowabros.github.io/experience/2018/12/28/spring-rest-docs.html)

### @Profile -Type
-

### 계층화된 테스트
- @SpringBootTest
- @WebMvcTest
- @WebFluxTest
- @DataJpaTest
- @JdbcTest
- ...

### 프로젝트 진행 순서
- 서비스 기획
- 기능분석 및 설계
- 구현
- 빌드
- 배포
- 운영

### 기능분석 및 설계 (예시)
- 지원플랫폼: 웹, 아이폰, 안드로이드
- 개발언어: Java
- 개발도구: IntelliJ
- 빌드도구: Gradle
- 개발플랫폼: Spring Boot
- 운영플랫폼: AWS(에만 하고 싶지만 개인정보 보호법, IDC 사용해야 함)
- 필요한 기능
  - 플랫폼에서 호출할 REST API
  - 관리시스템(백오피스)
    - 고객관리
    - 도서유형관리
    - 도서관리
  - 메일발송 시스템
    - Mail Chimp, SendGrid, ...
  - 알림푸시 시스템
    - AWS SNS, Firebase, ...
  - 포인트 시스템
  - 정산 시스템
  - 통계 및 매출차트 지원
  - ...
- 소스버전관리 시스템: Git with Github
- 빌드배포 시스템: 젠킨스
- 로그수집...
- 개발환경
  - local, test, dev, beta(경우에 따라 생략했다가 나중에..), prod
- DB
  - MariaDB

### 프로젝트 모듈 구성 (예시)
- common
  - 프로젝트에서 공통으로 사용하는 유틸리티, 예외
- core
  - 프로젝트 도메인(@Entity, @Repository)
- api
  - 외부에 정보를 제공하는 REST API 모듈
- admin
  - 서비스를 관리하기 위한 백오피스
- batch
  - 정기적으로 실행될 배치 프로그램 모음
- message
  - 알림톡, SMS, 메일 발송 등 담당

### 프로젝트 구성 시 필수조건
- README를 작성하라.
- 실행절차를 설명하라.
- 실행절차에 따라 빌드하고 실행되도록 하라.
- 커밋 및 푸시는 테스트 및 빌드가 성공되었을때 하라.
- 코딩 컨벤션은 팀원과 함꼐 만들자.

### 프로파일 구성
- local: 개발자 로컬 실행환경
  - 개발자가 자유롭게 초기화 및 구성을 수행할 수 있다.
- test: 통합테스트 환경 (주로 빌드 전 실행된다)
  - 테스트 실행때마다 초기화된다.
- dev: 개발서버 실행환경
  - 운영서버와 동일한 환경을 가지며 개발기능을 확인하는 용도로 사용된다.
- beta: (준)운영서버 실행환경
  - 운영서버와 동일한 환경으로 큰 배포에 앞서서 운영서버의 데이터를 복제하여 정상 동작을 확인
- prod: 운영서버 실행환경
  - (가급적) 손대지 않아야 할 환경

#### One Source Multi Use !

### CI/CD: 코드를 푸시하면 배포가 일어난다
- 기능을 정의하고 이를 관리받기 위한 이슈 발급
- 기능(feature)개발 하고 리뷰 받고 OK하면 develop 브랜치에 푸시
- 개발서버에 배포
- 개발서버에서 기능확인
- 베타서버 배포
- 베타서버에서 기능관련자(기획자)의 기능확인
- develop 브랜치 코드를 master에 머지하고 푸시
- 운영서버 배포
- 운영서버 적용

### 이제 코딩 시작!
- 기본적인 개발방식은 도메인 계층을 먼저 개발한다.
  - @Repository
  - @Entity
- 그리고 도메인간 서로 연계되는 부분이 있는 경우 서비스 계층에서 개발한다.
  - @Service
  - @Transaction 트랜잭션 관리도 이 영역에서!
- 외부에 노출되는 부분에서는 표현 계층에서 개발한다.
  - @Controller, @RestController + @ViewController
  - @RequestMapping
  - ModelAndView

### 출처
- [[토크ON세미나] 스프링 부트를 이용한 웹 서비스 개발 5강 - 스프링부트를 이용한 웹서비스 만들기 | T아카데미](https://www.youtube.com/watch?v=hQaQp1gEcjc)