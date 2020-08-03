## Sticky Session & Session Clustering

### Sticky Session
- 첫 request에 대한 응답을 준 서버에 껌딱지철머 붙어있는 것
- 특정 세션의 요청을 처음 처리한 서버로만 보내는 것
- 일반적으로 Cookie를 사용하거나 클라이언트의 IP tracking
- AWS ELB는 Cookie를 사용
- Sticky Session을 On 해높으면 Http Response에 Cookie를 이용
- 해당 클라이언트가 가는 EC2 instance의 정보를 저장해놓는다.

#### Sticky Session 단점
- 로드밸런싱이 잘 동작하지 않을 수 있다.
- 특정 서버만 과부화가 올 수 있다.
- 특정 서버 Fail시 해당 서버에 붙어 있는 세션들이 소실될 수 있다.


### Session Clustering
여러 WAS의 세션을 동일한 세션으로 관리하는 것

#### 단점
- 새로운 서버가 하나 뜰 때마다 기존 WAS에 새로운 서버의 IP/Port를 입력해서 클러스터링 해줘야 함


### Session Server 분리
Session Clustering의 단점을 없애고 새로운 서버에만 세션 서버에 대한 정보를 입력해주면 그 세션 서버에 접근해서 그 세션에 대한 클러스터링을 할 수 있다.

ex) Spring Session, Redis Session Server