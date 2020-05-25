## Horizontal vs. Vertical Scaling

Systems design a procedure by which we define the architecture of a system to satisfy given requirements. 
It is a technique by which the required amounts of scalability, reliability, performance and consistency are satisfied in real world systems.

### Why system design is required
The first concept in designing a system is scalability. We discuss the two main approaches to solve this problem: Horizontal scaling and vertical scaling.

### Horizontal scaling
Horizontal scaling is adding more machines to deal with increasing requirements. These machines handle requests in parallel to improve user experience. 

### Vertical scaling
Vertical scaling is replacing the current machines with more advanced machines to improve throughput and hence response time. The techniques are used in conjunction in real world systems.

### Comparison

| Buy bigger machines | Buy more machines |
|:------:|:------:|
| Load balancing required | N/A |
| Resilient | Single point of failure |
| Network calls(RPC) | Inter process communication |
| Data inconsistency | Consistent |
| Scales well | Hardware limit |

## References
- [https://www.youtube.com/watch?v=xpDnVSmNFX0&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=1](https://www.youtube.com/watch?v=xpDnVSmNFX0&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=1)