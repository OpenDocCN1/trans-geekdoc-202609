

# 314 附录

实体标签（也称为 ETag）是一个表示当前资源状态的不透明值。客户端可以在 GET、POST 或 PUT 请求后存储 ETag，并使用该值通过 HEAD 或 GET 请求来检查发生的变化。

ETag 是整个响应的哈希值。或者，服务器也可以提供弱 ETag（weak ETag），它在语义上是等价的，但在字节上可能并非完全相同。

以下是一个使用 ETag 而不是修改时间的客户端/服务器交互：

```
GET /projects/12345 HTTP/1.1
Accept: application/json;q=0.5, application/xml;q=1.0

HTTP/1.1 200 OK
Date: Tue, 22 December 2020 06:57:43 GMT
Content-Type: application/xml
Cache-Control: max-age=240
Location: /projects/12345
ETag: "17f0fff99ed5ae4edffd6496d7311f"

<project>...</project>
```

```
GET /projects/12345 HTTP/1.1
Accept: application/json;q=0.5, application/xml;q=1.0
If-None-Match: "17f0fff99ed5ae4edffd6496d7311f"

HTTP/1.1 304 Not Modified
Date: Tue, 22 December 2020 07:03:43 GMT

GET /projects/12345 HTTP/1.1
Accept: application/json;q=0.5, application/xml;q=1.0
If-None-Match: "17f0fff99ed5ae4edffd6496d7311f"

HTTP/1.1 200 OK
Date: Tue, 22 December 2020 07:33:04 GMT
Content-Type: application/xml
Cache-Control: max-age=240
Location: /projects/12345
ETag: "b252d66ab3ec050b5fd2c3a6263ffaf51db10ffcb"

<project>...</project>
```

条件请求减少了验证和重新获取缓存资源所需的努力。ETag 是表示当前内部状态的不透明值，而最后修改时间戳而非 ETag 则可能被用于基于时间的比较。在对资源进行修改时，它们也常用于并发控制。

## HTTP 中的并发控制

使用 HTTP 进行并发控制是需要支持不同用户同时修改数据 API 的团队所面临的一项挑战。一些 API 设计师找到了巧妙的方法，在 HTTP 上实现资源级锁定。然而，HTTP 内置了并发控制机制，使得团队无需自行构建它。

条件请求也用于支持 HTTP 中的并发控制。通过将 ETag 或最后修改日期与 PUT、PATCH 或 DELETE 等状态更改方法相结合，我们可以确保数据不会被另一个 API 客户端通过单独 HTTP 请求意外覆盖。

要应用条件请求，API 客户端会在请求中添加预条件（precondition），如果资源的最后修改时间或 ETag 已发生变化，则阻止修改。服务器将返回 412 Precondition Failed（前提条件失败）响应。API 服务器还可能强制要求预条件头，如果请求中未发现任何一个条件头，则通过响应 428 Precondition Required（需要前提条件）来执行并发控制。

以下是一个两个 API 客户端尝试修改项目的示例。首先，每个客户端都使用 GET 请求获取项目资源，然后每个客户端尝试进行更改，但只有第一个 API 客户端能够应用该更改：

```
GET /projects/12345 HTTP/1.1
Accept: application/json;q=0.5, application/xml;q=1.0
HTTP/1.1 200 OK
Date: Tue, 22 December 2020 07:33:04 GMT
Content-Type: application/xml
Cache-Control: max-age=240
Location: /projects/12345
ETag: "b252d6ab33ec055fd2c3a62af5110b"

<project>...</project>
```

# 316 附录

```
PUT /projects/1234
If-Match: "b252d6ab33ec055fd2c3a62af5110b"
```

```
{ "name":"Project 1234", "Description":"My project" }
```

```
HTTP/1.1 200 OK
Date: Tue, 22 December 2020 08:21:20 GMT
Content-Type: application/xml
Cache-Control: max-age=240
Location: /projects/12345
ETag: "1d720c9d54e1a9cf73be41eff24fffb"
```

```
<project>...</project>
```

```
PUT /projects/1234
If-Match: "1d720c9d54e1a9cf73be41eff24fffb"
```

```
{ "name":"Project 5678", "Description":"No, is my project" }
```

```
HTTP/1.1 412 Precondition Failed
Date: Tue, 22 December 2020 08:21:24 GMT
```

接收到失败条件响应的第二个 API 客户端现在必须重新获取资源的表示，告知用户更改，并询问用户是重新提交更改还是保持原样。

并发控制可以通过请求头中的条件请求添加到 API 中。如果 ETag/修改日期未更改，则正常处理请求。如果已更改，则返回 412 响应，防止两个独立的客户端并发修改数据。这是 HTTP 内置的一种强大功能，避免了团队自行发明并发控制。

## 总结

HTTP 是一种强大的协议，拥有一系列功能，其中某些较为人知。内容协商允许 API 客户端和服务器就支持的媒体类型达成一致。缓存控制指令提供了客户端和中间件支持。HTTP 条件请求可用于保护资源不被覆盖。通过应用这些技术，团队能够以一种弹性且可扩展的方式构建复杂的应用程序。

## 索引

### A
- 验收（Acceptance）,22
- ActiveMQ, 226
- ADDR 过程中的步骤, 24, 25
- ADDR, 参见 Align-Define-Refine (ADDR)
- 高级消息队列协议（Advanced Message Queuing Protocol (AMQP)), 7, 164, 165, 166
- 分析（Analytics）, 在 MVP, 259
- 228
- 可可用性（Affordances）, 107
- 聚合笔记（Aggregate note）, 55
- 敏捷宣言（Agile Manifesto）, 22
- API 优先设计的敏捷性（Agility of API design-first）, 22–23
- Amazon Alexa, 6
- Align, 在 ADDR 过程中, 23
- Align-Define-Refine (ADDR), 23–26
- 反馈（feedback）, 23, 24
- 达成的目标, 24–25
- 过程概述, 25
- 阶段, 24
- 现实设计中使用的步骤, 25–26
- 捕获与步骤, 45–65
- 数字能力（digital capabilities）, 31–43
- ALPS（应用级配置 Application-Level Profile）, 83, 245–46
- Amazon Kinesis, 169
- Amazon Web Services (AWS), 221, 281
- AMQP（高级消息队列协议）, 7, 164, 166
- Amundsen, Pike, 128
- 接入层（Antruption layer）, 11
- 避免反模式（Antipatterns avoiding）, 70–71
- 全能 API 反模式（all-in-one API antipattern）, 70
- 过载 API 反模式（overloaded API antipattern）, 70–71

### B
- 业务能力（business capabilities of）, 4
- 边界上下文、子域和 API（bounded contexts, subdomains, and APIs）, 71–72
- 发现（finding）, 72
- 加剧为了（Exacerbating for）, 72–74

### C
- Apache Avro, 126, 178
- Apache Kafka, 169, 173
- Apache Lucene, 16, 19
- Apache Pulsar, 169
- Apache Spark, 170
- 基于 API 的编排（API-based orchestration）, 201, 202
- API Blueprint, 238–40
- API 边界（API boundaries）, 69–78
- 相应的活动, 74–75
- 在 ADDR 过程中识别的, 24, 25
- 识别（identifying）, 69–78
- API 命名和范围划分（naming and scoping APIs）, 75, 77, 78
- APIset生命周期（API consumption lifecycle）, 300
- API 合约测试（API contract testing）, 227–28
- API 描述格式（API description formats）, 234–48
- ALPS, 245–46
- 使用 API 改进 API 设计（improving API design using APIs）, 247–48
- JSON Schema, 244–45
- OAS, 235–37
- RAML, 240–46
- API 设计反模式（API design antipats）, 16–20
- 编码（coding）, 16
- 方法（approach）, 13, 14
- 通信（communication）, 6–7
- 数据模型（data model exposed in）, 11
- 元素（elements of）, 4, 6, 102
- 以结果为导向（outcome-based focus of）, 4
- 原则（principles of）, 13–14
- 过程（process）, 15–28

### D
- 弃用（deprecating）, 268–70
- 确定最佳 API（determining what is best for API）
- ADDR 中的 API 适配（API adaptation in）, 16–20
- API 优先设计方法（API design-first approach in）, 20–23
- 有效应用（applying effectively）, 28
- 应用 API 产品思维（API product thinking to）, 5
- API 通信（API communication in）, 6–15
- DDD 中的（DDD in）, 26
- 原因（reasons for）, 15–16
- API 设计会议涉及的角色（roles involved in API design sessions）, 27
- 软件设计及原则（software design and, reviewing principles of）, 7–10

