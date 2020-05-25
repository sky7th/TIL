## What is a Message Queue and Where is it used?

Messaging Queues are widely use in asynchronous systems. Message processing in an asynchronous fashion allows the client to relieve itself from waiting for a task to complete and, hence, can do other jobs during that time. It also allows a server to process it's jobs in the order it wants to.

A system having a message queue can move to higher level requirements while abstracting implementation details of message delivery and event handling to the messaging queue.

The 'queue' is just a name for this data structure. In practice, it could be storing messages using any policy. 

Some examples of message queues are Kafka and RabbitMQ. They are widely used for various purposes such as command query request segregation (CQRS) and event sourcing.
- [나만 모르고 있던 CQRS & EventSourcing](https://www.popit.kr/cqrs-eventsourcing/)
- [이벤트 소싱(Event Sourcing) 소개](https://justhackem.wordpress.com/2017/02/05/introducing-event-sourcing/)

### What MQ does 
- It is notifier, load balancing, and heart beat.
- It takes task
- It persists them
- It assigns them to the correct server and waits for them to complete.

If it's taking too long for the server to give an acknowledgment, it feels that server is dead and then assigns it to the next server.

So there are multiple strategies of course for assigning it.

That is just like load balancing has multiple strategies, but that's all encapsulated by a task queue.

#### And this is an important concept in system design
- using messaging queues or task queues to get work done easily so that you can encapsulate all that complexity into just one thing.

---

MQ를 언제 사용하면 좋은지 알아보자.

### 애플리케이션/시스템 간의 통신
서버가 갑자기 죽거나 서버 점검(다운타임) 등이 발생하는 동안에는 요청을 보낼 수가 없다.

MQ를 이용하면 더욱 간편하게 처리할 수 있다.

(요청하는 서버에서 failover 처리를 해놓고 연계 시스템이 다시 살아났을 때 요청을 보내는 방법도 있다.)

#### MQ를 사용할 경우 
- 클라이언트는 서버에 직접 요청하는 것이 아닌 MQ에 전달한다. 
- 그럼 서버는 MQ로 부터 요청 데이터를 수신해서 처리한다. 

만약 서버가 요청을 받을 수 없을 수 없는 상황이라면 해당 요청은 서버가 받을 때까지 MQ에 머무르게 된다.

이런 상황에서 MQ에 다운타임이 발생하면 무용지물이 되어버리기 때문에 많은 MQ가 고가용성을 위해 클러스터링 등을 지원한다.

### 서버 부하가 많은 작업
이미지 처리, 비디오 인코딩, 대용량 데이터 처리와 같은 작업은 메모리와 CPU를 많이 사용한다.

이러한 작업은 동시에 처리할 수 있는 양이 상당히 한정적이어서 필요하다고 무작정 요청을 처리할 수는 없다.

#### MQ를 사용할 경우 
- 처리해야할 작업을 MQ에 넣어둔다.
- 서버는 자신이 동시에 처리할 수 있는 양에 따라 하나의 작업이 끝나면 다음에 처리할 작업을 MQ에서 가져와 처리하면 된다.

### 부하분산
#### 처리할 데이터가 많아질 때 MQ를 사용
- 여러 대의 서버가 하나의 큐를 바라보도록 구성한다.
- 각 서버는 자신의 처리량에 맞게 태스크를 가져와 처리할 수 있다.
- 이러한 구조는  horizontal scaling에 유리하다.

### 데이터 손실 방지
MQ로부터 가져온 태스크를 일정 시간이 지나도록 처리했다고 다시 MQ에 알려주지 않으면 MQ는 이 태스크를 다시 큐에 넣어 다시 처리할 수 있도록 한다.

### MQ가 어울리지 않는 경우
- 요청 결과를 즉시 응답해야할 때
  - 요청과는 별개로 처리할 수 있는 비동기 처리에 어울린다.
- 서버에서 간단하게 처리할 수 있는 일을 MQ를 통해 전달
  - 필요없는 오버헤드될 수도 있다.




## References
- [https://www.youtube.com/watch?v=oUJbuFMyBDk&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=5](https://www.youtube.com/watch?v=oUJbuFMyBDk&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=5)

- [https://www.icelancer.com/2016/12/message-queue.html](https://www.icelancer.com/2016/12/message-queue.html)