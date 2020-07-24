## Servlet & Spring
### Servlet, Spring 이란?
- Servlet
  - 웹 애플리케이션을 만들 때 필요한 인터페이스
- Spring Web MVC (Servlet을 사용)
  - Spring Framework에 있는 모듈
  - MVC 패턴을 사용해서 Web Service를 만든다.

### 발전 흐름
- 정적 데이터만 전달하는 Web Server
- 동적 데이터를 처리하는 CGI
  - CGI: Web Server와 프로그램 사이의 규약
- CGI의 문제점
  - 요청이 들어올 때 마다 프로세스를 만듬
    - Process에서 Thread로
  - 같은 구현체를 사용해도 요청(스레드)가 다르면 하나씩 구현체가 생김
    - 싱글톤 패턴으로 해결(Servlet)
    - 이때 WAS가 생김(Web Container가 중간에 생김)
      - Web Container: 요청이 들어오면 Thread를 생성하고, Servlet을 실행시킨다. Servlet Interface에 따라 Servlet을 관리한다.

### Servlet
#### Servlet Interface
  - Init: Servlet Instance 생성
  - Service: 실제 기능이 수행되는 곳
    - abstract class HttpServlet extends Servelt
    - HTTP Method에 따라 doGet(), doPost(), doPut(), doDelete(), doXXX() 메서드를 호출한다.
  - Destroy: Servlet Instance가 사라진다.
    - 보통 container가 종료되는 시점에 destroy() 호출
    - 특정 servlet 로드/언로드 시에만 사용   
  - 각 메서드는 Servlet Container(Tomcat)이 호출해준다.

#### Servlet 사용
- Web.xml(설정 파일) Servlet Mapping
- WAS에게 Servlet 객체 - URL mapping 정보를 알려준다.
- 흐름
  - Url마다 Servlet이 생기고 그 Servlet을 Web Container에게 알려주기 위해서 Web.xml에서 Url과 Servlet을 매핑시켜준다.

### Spring Web MVC에서는 Servlet을 어떻게 사용할까?
- 모든 요청이 들어왔을 때, Dispatcher Servlet으로 간다. 
- 요청에 따라 적절한 Controller를 찾는다.
  - 찾는 방법은 Spring Framework에서 제공한다.
  - 어떤 방식의 HandlerMapping을 사용할지 설정파일에 지정한다. 
    - BeanNameHandlerMapping
    - ControllerClassNameHandlerMapping
    - SimpleUrlHandlerMapping
    - DefaultAnnotationHandlerMapping
- HandlerMapping에서 찾은 Handler(Controller)의 메서드를 호출한다.
  - ModelAndView 형태로 바꿔준다.
- View Resolver가 View 이름을 가지고 실제 View 객체를 찾아서 생성한다.
- View에 Model(data)를 포함시킨다.

### Spring Web MVC 존재 유무의 차이
- 없을 때
  - Url마다 Servlet을 생성
  - Web.xml로 Servlet 관리
  - View로 보여주는 것까지 다 만듬
- 있을 때
  - Servlet은 DispatcherServlet 1개로 관리
  - View를 강제로 분리