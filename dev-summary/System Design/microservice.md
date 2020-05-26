## What is microservice architecture and it's advantages?

Why we use them instead of monolithic systems is Scalability. 

### Advantages
1) The microservice architecture is easier to reason about/design for a complicated system.
2) They allow new members to train for shorter periods and have less context before touching a system.
3) Deployments are fluid and continuous for each service.
4) They allow decoupling service logic on the basis of business responsibility
5) They are more available as a single service having a bug does not bring down the entire system. This is called a single point of failure.
6) Individual services can be written in different languages.
7) The developer teams can talk to each other through API sheets instead of working on the same repository, which requires conflict resolution.
8) New services can be tested easily and individually. The testing structure is close to unit testing compared to a monolith.

Microservices are at a disadvantage to Monoliths in some cases. 

### Monoliths are favorable when
1) The technical/developer team is very small
2) The service is simple to think of as a whole.
3) The service requires very high efficiency, where network calls are avoided as much as possible.
4) All developers must have context of all services.

## References
- [https://www.youtube.com/watch?v=qYhRvH9tJKw&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=6](https://www.youtube.com/watch?v=qYhRvH9tJKw&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=6)