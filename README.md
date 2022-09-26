# Internal Flow of Loopback Repository

## Query Call Structure with juggler
- An example of user repository:

![image](https://user-images.githubusercontent.com/110156023/192253293-37080676-f75c-4675-aac4-059a53190e4a.png)

A summary of the code flow is:
 
1. LB4 Repository calls Juggler Model Class `.create`
2. Juggler Model Class gets the above method (and others) from being [mixin-ed](https://github.com/loopbackio/loopback-datasource-juggler/blob/f8d7ca94740887e9beefc586442f025c12c29e7f/lib/datasource.js#L742) Juggler [DataAccessObject](https://github.com/loopbackio/loopback-next/blob/e6eacffa3b36c1769861ad5a4db71c615c17b1f3/packages/repository/src/repositories/legacy-juggler-bridge.ts#L497) by default
3. Juggler DataAccessObject `.create` [calls](https://github.com/loopbackio/loopback-datasource-juggler/blob/1d2d6cb4e155df70dc3285bfb8e53e5bcdc23e1c/lib/dao.js#L450) the Juggler SQL Connectors' `.create`
4. The Juggler SQL Connectors inherit from `loopback-connector`'s [`SQLConnector`](https://github.com/loopbackio/loopback-connector/blob/6785802301fa39ab0d1dab93ad608d3cad413083/lib/sql.js#L620)
 
--- 
Ref: https://github.com/loopbackio/loopback-next/issues/3357#issuecomment-1166597214
