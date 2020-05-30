# db-subscriber
## 介绍
数据库订阅中间件，当订阅的数据库/表发生数据改变时，主动推送消息给业务端或者直接实现业务需求。 主要使用场景：
  1. 对Redis等缓存的更新。
  2. 多数据库数据同步。
  3. es数据同步。
  4. 其他需要监听数据库变化的业务。
## 优势: 业务端一个注解搞定，无业务侵入。
### 示例场景：运营人员在控制台手动开启一个活动，服务端需要及时将开启的活动设置到缓存中。
  传统做法：控制台更改时，发送MQ消息通知给服务端，这样控制台的业务就有了侵入性，而且有可能不会做到及时更新。
  db-subscriber能够将这类的数据同步，缓存更新的业务进行解耦，添加一个@Subscriber注解，即能感知到某条数据的变化。