## Tinder as a microservice architecture

### File vs Blob
#### Only few extra guarantees that a database gives you
- Mutability
- Transaction (ACID)
- Index
- Access control

This is an unnecessary feature that the database is giving us.

#### Just creat a separate file
- Cheaper
- Faster
- Content Delivery Network


### The Tinder system has four requirements
- storing profiles
- recommendations 
- noting matches
- chatting with matches

### Storing profiles
Storing profiles is trivial except for the image storage, where we argue on BLOB vs File storage. The distributed file architecture seems best when storing images.

### Chatting with matches
Direct Messaging or chatting with matches can be done using the XMPP protocol, which uses web sockets to have peer to peer communications between client and server. 

Each connection is built over TCP, ensuring that the connection is maintained. 

The session micro service can send messages to the receiver based on connection to user mappings.


Our system is decoupled as much as possible. 

### The server having a validation engine
We try to maintain accept and reject information on the client. 

On swiping left or right, the client can note the action and avoid showing the same user again, perhaps using bloom filters.

The server has a validation engine called the matcher micro service, which notes matches and allows or disallows chat between two users.

### City wise partitioning on the user data.
- This is acheived using NoSQL databases like Cassandra or Amazon Dynamo. 
- Using sharding.

## References
- [https://www.youtube.com/watch?v=tndzLznxq40&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=9](https://www.youtube.com/watch?v=tndzLznxq40&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=9)