
GET `/tasks/event-stream`

Accept: text/event-stream

task_created:

data: `{"id": "12345"}`

id: 12345

task_created:

data: `{"id": "6789"}`

id: 6789

<<Disconnected>>

GET `/tasks/event-stream`

Accept: text/event-stream

Last-Event-Id: 6789

![](img/6a422bfe4f2691ab7de274bb6978b0eb_207_0.png)

**图 9.8** 使用服务器发送事件 (SSE) 允许 API 服务器通过长连接向客户端推送到事件。连接可以使用 Last-Event-Id 请求头恢复。

## 第 9 章 用于事件驱动和流处理的异步 API

SSE 确实在某些情况下可能并不适用：

- API 网关（API gateway）无法处理长连接，或者超时时间非常短（例如小于 30 秒）。虽然这并不意味着无法使用，但它将要求客户端频繁地重新连接。
- 某些浏览器不支持 SSE。更多信息请参考 Mozilla 的兼容浏览器列表$^{12}$。
- 客户端和服务器之间需要进行双向通信。在这种情况下，WebSocket 协议可能是更好的选择，因为 SSE 仅支持服务器推送。

W3C 的 SSE 规范易于读懂，并提供了额外的规范说明和示例。

## 通过 WebSocket 实现双向通知

WebSocket 支持在由 HTTP 发起的 TCP 连接中隧道化全双工协议，该协议被称为子协议（subprotocol）。由于它们是全双工的，API 客户端与服务器之间变得可能的双向通信。客户端能够通过 WebSocket 连接向服务器推送请求，而服务器也可以向客户端推送事件和响应。

WebSocket 是一个由互联网工程任务组（IETF）维护的 RFC 6455 标准协议$^{13}$。大多数浏览器都支持 WebSocket，使其易用于浏览器到服务器、服务器到浏览器以及服务器到服务器的场景。由于 WebSocket 连接是通过 HTTP 连接进行隧道化的，它们还可以克服某些组织内部的代理限制。

一个一个需要记住的重要因素是，WebSocket 的行为并不像 HTTP，尽管它使用 HTTP 来建立连接。它必须选择一个子协议。IANA 官方注册了许多子协议$^{14}$。WebSocket 同时支持文本（text）和二进制（binary）格式子协议。图 9.9 显示了一个使用纯文本子协议的 WebSocket 交互示例。

WebSocket 的实现更为复杂，但它支持双向通信。这意味着它允许客户端在同一个连接上向服务器发送数据，并从服务器接收数据。虽然 SSE 更容易实现，但客户端无法在同一条连接上发送请求，因此在需要全双工通信时，WebSocket 是更好的选择。在选择异步 API 时请记住这一点。

> 12. MDN Docs, "Server-Sent Events," 修改于 2021 年 8 月 10 日，https://developer.mozilla.org/en-US/docs/Web/API/Server-sent-events.
> 13. Internet Engineering Task Force (IETF), The WebSocket Protocol (Request for Comments 6455, 2011 年 12 月），https://tools.ietf.org/html/rfc6455.
> 14. Internet Assigned Numbers Authority (IANA), WebSocket Protocol Registries, 修改于 2021 年 7 月 19 日，https://www.iana.org/assignments/websocket/websocket.html.

### 支持 WebSocket 的 REST API 服务器

```
HTTP/1.1 101 Switching Protocol Handshake

Date: Thu, 18 Sep 2029 14:53:18 GMT

Connection: Upgrade

Upgrade: websocket

---
```

WebSocket 升级请求

```
WebSocket upgrade response
<<WebSocket Enabled>>
Hello, server
Hello, client
```

### API 消费者（Web/移动/服务器）

```
GET ws://echo.websocket.org?encoding=text HTTP/1.1

Host: websocket.org

Connection: Upgrade

Upgrade: websocket

Sec-Websocket-Version: 13

---
```

图 9.9 API 客户端和服务器之间使用 WebSocket 和纯文本子协议创建聊天应用程序的交互示例。

![](img/6a422bfe4f2691ab7de274bb6978b0eb_209_0.png)

## gRPC 流式传输

TCP 协议针对长连接的双向通信进行了优化。HTTP/1.1 构建在 TCP 之上，但需要多个连接来允许客户端实现并发。虽然这种多连接需求是为了负载均衡和扩展，但它对性能有相当大的影响，因为每个连接都需要建立新的 TCP socket 连接并进行协议协商。

HTTP/2 是一个基于 Google 的 SPDY 协议工作成果构建的新标准，它优化了请求并包含了响应复用（response multiplexing）。在响应复用中，单个 HTTP/2 连接被用于一个或多个并发的请求。这避免了为每个请求创建新连接的开销，类似于 HTTP/1.1 支持持久连接（keep-alive connections）的方式。然而，HTTP/2 复用允许一次性发送多个请求，而不是使用持久连接按顺序发送。

此外，HTTP/2 服务器可能会向客户端推送资源，而不是要求客户端发起请求。这与 HTTP/1.1 传统的请求/响应模式相比是一个转变。

gRPC 利用了 HTTP/2 的双向通信，消除了在 SSE 之外单独在 HTTP/1.1 之上支持请求/响应或其他基于推送的方法的需求。由于 gRPC 支持双向通信，可以使用相同的协议来设计和集成异步 API。gRPC 流式传输有三种模式：客户端到服务器、服务器到客户端和双向，如图 9.10 所示。

像 WebSocket 一样，gRPC 可以作为一个全双工连接发送和接收消息及事件。与 WebSocket 不同，gRPC 不需要做出子协议决策，因为 gRPC 默认使用 Protocol Buffers。然而，浏览器没有内置的 gRPC 支持；grpc-web 项目正致力于将 gRPC 桥接到浏览器，但存在局限性。因此，gRPC 流式传输通常局限于服务与之间的交互。

#### gRPC 异步选项 1：客户端到服务器
![](img/6a422bfe4f2691ab7de274bb6978b0eb_209_0.png)

```
service Main {

  rpc GetOrders(OrderQuery) returns (stream Order);

}
```

#### gRPC 异步选项 2：服务器到客户端
![](img/6a422bfe4f2691ab7de274bb6978b0eb_209_0.png)

```
service Main {

  rpc GetOrders(OrderQuery) returns (stream Order);

}
```

#### gRPC 异步选项 3：双向流式
![](img/6a422bfe4f2691ab7de274bb6978b0eb_209_0.png)

```
service Main {

  rpc GetOrders(stream OrderQuery) returns (stream Order);

}
```

**图 9.10 gRPC 的三种选项：客户端到服务器、服务器到客户端和双向**

## 选择 API 样式

虽然异步 API 有多种样式，但根据情况和限制，某些样式可能是更好的选择。以下是每种样式的考虑因素，有助于判断：

- **Webhooks**：Webhooks 是唯一不需要客户端发起连接的样式，当需要服务器到服务器的通知时使用。
- **Server-Sent Events (SSE)**：SSE 在客户端和服务器端通常最容易实现，但不支持双向通信。当需要服务器推送事件时使用。
- **WebSocket 协议**：WebSocket 实现较为复杂，因为需要支持一个或多个子协议，它支持双向通信。WebSocket 被浏览器广泛支持。
- **gRPC 流式传输**：gRPC 充分利用了 HTTP/2，支持双向通信。gRPC 不被浏览器完全支持；适用于管理基础设施。

## 设计异步 API

设计异步 API 的过程与使用 REST、RPC 或查询样式设计传统的请求/响应 API 类似。从第 6 章“API 建模”中定义的资源开始。回顾并捕捉每个 API 配置文件的事件。然后确定哪些命令和事件对 API 消费者有益。

### 命令消息

命令消息包含了请求另一个组件执行工作所需的所有细节。在设计异步 API 的命令时，重要的是设计中要包含足够处理请求的细节。它可能包含一个发布结果消息的位置。该目标位置可以是 POST 到消息代理主题的 URL，或者是共享对象存储（如 Amazon S3）的 URL。

在设计时，使用内置语言机制（如对象序列化）来简化命令生产者和消费者的开发可能是很容易的。这将限制消费和处理这些命令的系统。相反，寻求使用语言无关的格式，例如 UBER 超媒体格式、Apache Avro、Protocol Buffers、JSON 或 XML。

以下是一个异步更新客户账单地址的 JSON 命令消息示例：

```json
{
  "messageType": "customerAddress.update",
  "requestId": "123f4567",
  "updatedAt": "2020-01-01T02:56:45Z"
}
```

```json
{
  "customerId": "330001003",
  "newBillingAddress": {
    "addressLine1": "...",
    "addressLine2": "...",
    "addressCity": "...",
    "addressState": "...",
    "addressRegionProvince": "...",
    "addressPostalCode": "..."
  }
}
```

可以提供一个额外的 `replyTo` 字段并包含回调的 URL，或者由其他订阅者监听 `customerAddress.updated` 事件来对更改做出响应，例如在第三方系统中更新账单地址。

### 事件通知

事件通知（有时被称为“精简事件”，thin events）用于通知订阅者状态更改或业务事件的发生。它们的目标仅为订阅者提供必要的信息，以便其判断该事件是否感兴趣。

事件订阅者负责通过 API 获取详情的最新表示，以避免使用过时数据。在精简事件中提供超链接，有助于将获取最新资源表示的 API 操作与事件等异步 API 整合。下例事件载负载展示了这一点：

```json
{
  "eventType": "customerAddress.updated",
  "eventId": "123e4567",
  "updatedDate": "2020-01-14T03:56:45Z",
  "customerId": "330001003",
  "_links": [
    { "rel": "self", "href": "/events/123e4567" },
    { "rel": "customer", "href": "/customers/330001003" }
  ]
}
```

精简事件用于与频繁变化的资源相关的事件，迫使事件订阅者检索最新的资源表示，以避免处理过时数据。虽然并非必须，但精简事件也可以包含更新发生时更改的特定属性的详情，以帮助消费者判断该事件是否感兴趣。

## 事件携带状态传输事件 (Event-Carried State Transfer Events)

事件携带状态传输事件包含了事件发生时的所有可用信息。这避免了联系 API 获取完整资源表示的需求，尽管可能还会使用额外的 API 来补充订阅者执行任何处理所需的数据。

事件携带状态传输优于精简事件的原因有以下几点：

- 订阅者关注的是与事件相关的资源快照，而不是精简事件提供的少数细节和相关多媒体链接。
- 数据状态通过消息流进行更改，以支持重放消息历史，这需要资源的完整时间点快照。
- 通过异步 API 进行消息传递用于服务间通信，需要发布完整的资源表示，以避免 API 流量增加以及服务之间过紧耦合。

这种消息设计风格通常会尽可能模拟 API 的表示结构。当更新事件必须提供事件中任何被修改属性的旧值和新值时，出现偏差也是很常见的。

最后，对于中大型载荷，使用嵌套结构而非扁平结构来对相关属性分组。这有助于推动演进性，因为属性名称被限制在父属性范围内，从而避免了属性名称冲突或为了澄清关系而使用长属性名。以下是扁平化结构到事件携带状态传输消息风格的演示。

```json
{
  "eventType": "customerAddress.updated",
  "eventId": "123e4567",
  "updatedAt": "2020-01-14T03:56:45Z",
  "customerId": "330001003",
  "previousBillingAddressLine1": "...",
  "previousBillingAddressLine2": "...",
  "previousBillingAddressCity": "...",
  "previousBillingAddressState": "...",
  "previousBillingAddressRegionProvince": "...",
  "previousBillingAddressPostalCode": "...",
  "newBillingAddressLine1": "...",
  "newBillingAddressLine2": "...",
  "newBillingAddressCity": "...",
  "newBillingAddressState": "...",
  "newBillingAddressRegionProvince": "...",
  "newBillingAddressPostalCode": "..."
}
```

结构化方法在如下示例所示：

```json
{
  "eventType": "customerAddress.updated",
  "eventId": "123e4567",
  "updatedAt": "2020-01-14T03:56:45Z",
  "customerId": "330001003",
  "previousBillingAddress": {
    "addressLine1": "...",
    "addressLine2": "...",
    "addressCity": "...",
    "addressState": "...",
    "addressRegionProvince": "...",
    "addressPostalCode": "..."
  },
  "newBillingAddress": {
    "addressLine1": "...",
    "addressLine2": "...",
    "addressCity": "...",
    "addressState": "...",
    "addressRegionProvince": "...",
    "addressPostalCode": "..."
  }
}
```

当将结构化组合应用于携带状态样式时，消费者能够重用值对象来包含每个嵌套对象的详情，并在之后在用户界面中轻松检测字段差异。如果没有这种模式，则需要值对象以及额外的编码工作来执行诸如检测前后地址差异的操作。

### 事件批

虽然大多数异步 API 设计为在消息可用时通知订阅者，但某些设计可能从将事件分组为批中益。事件批要求订阅者处理多条消息。一个简单的示例是用数组封装通知：

```json
{
  "events": [
    {
      "eventType": "customerAddress.updated",
      "eventId": "123e4567",
      "updatedAt": "2020-01-14T03:56:45Z",
      "customerId": "330001003",
      ...
    }
  ]
}
```

另一种设计方案是提供一个包含批额外元数据的信封：

```json
{
  "meta": {
    "eventType": "customerAddress.updated",
    "eventId": "123e4567",
    "updatedAt": "2020-01-14T03:56:45Z",
    "customerId": "330001003",
    "_links": [
      { "rel": "self", "href": "/events/123e4567" },
      { "rel": "customer", "href": "/customers/330001003" }
    ]
  },
  "events": [
    {
```
