

## REST 约束

* `Statelessness` : 客户端向服务器发出的每个 HTTP 请求都必须包含理解和处理该请求所需的所有信息。换句话说，服务器不应在请求之间存储任何客户端状态。这使得 RESTful 系统具有高度可扩展性和易于维护。
* `Resource-Based` : REST 将数据和功能视为可由 URL 标识的资源。资源是可以利用标准 HTTP 方法进行操作的实体。例如，在 RESTful API 中，博客文章可以表示为可通过诸如 `/posts/123` 的 URL 访问的资源。
* `Representation` : 资源可以有多种表示形式，例如 JSON、XML、HTML 或其他。客户端可以通过内容协商请求特定表示，通常通过 HTTP 请求中的 `Accept` 头。
* `Stateless Communication` : 客户端向服务器发出的每个请求都必须包含理解和处理该请求所需的所有信息。这意味着服务器不依赖于之前的请求或共享的会话状态。
* `Standard Methods` : RESTful API 使用标准 HTTP 方法（`GET`、`POST`、`PUT`、`DELETE` 等）对资源执行操作。例如，`GET` 用于检索资源，`POST` 用于创建新资源，`PUT` 用于更新资源，`DELETE` 用于删除资源。
* `Uniform Interface` : RESTful 系统具有一致且统一的接口，这简化了客户端和服务器之间的交互。这种一致性基于标准 HTTP 方法和资源 URI。
* `Client-Server Separation` : 客户端和服务器是通信于无状态协议（`HTTP`）上的独立实体。这种分离使它们能够独立演进。客户端负责用户界面和用户体验，而服务器负责处理请求和管理资源。
* `Layered System` : REST 允许在客户端和服务器之间使用中间件，例如代理、负载均衡器和缓存服务器。这些中间件可以在不影响整体系统的情况下增强性能、安全性和可扩展性。
* `Cacheability` : 服务器的响应可以明确标记为可缓存或不可缓存。这允许高效使用缓存机制，减少对服务器的重复请求需求。
* `Code on Demand` : REST 允许服务器通过在响应中传输可执行代码（例如 JavaScript）来扩展客户端的功能。此功能是可选的，在实践中并不常用。

这些 REST 特性和约束有助于创建简单、可扩展且易于理解的 Web 服务和 API。它们已成为构建互联网上许多基于 Web 的系统和服务的基石。

# REST 的关键原则和架构

Representational State Transfer (`REST`) 架构由多个关键架构元素组成，这些元素定义了 RESTful 系统的结构和行为。这些元素协同工作，创建了一个可扩展、无状态且高效的框架，用于设计网络应用程序。主要 REST 架构元素包括：

* `Resources` : 资源是 REST 中的基本抽象。它们代表客户端可以交互的对象、数据或服务。资源由统一资源标识符（`URIs`）标识，`URIs` 用作访问它们的唯一地址。
* `HTTP Methods` : REST 依赖标准 HTTP 方法（也称为 HTTP 动词）对资源执行操作。RESTful 系统中主要使用的 HTTP 方法有：
  * `GET` : 检索资源的表示
  * `POST` : 创建新资源
  * `PUT` : 更新现有资源或在不存在时创建它
  * `DELETE` : 删除资源
  * `PATCH` : 部分更新资源
  * `HEAD` : 仅检索资源的头部
  * `OPTIONS` : 获取资源的通信选项信息
* `Representations` : 资源可以有多种表示形式，例如 JSON、XML、HTML 或其他。客户端可以通过内容协商请求特定表示，通常由 HTTP 请求中的 `Accept` 头控制。
* `Stateless Communication` : RESTful 系统是无状态的，这意味着客户端向服务器发出的每个请求都必须包含理解和处理该请求所需的所有信息。服务器在请求之间不维护任何客户端状态，从而增强可扩展性和简洁性。
* `Uniform Interface` : 统一且一致的接口是 REST 的基本原则。它通过使用标准方法集（`GET`、`POST`、`PUT`、`DELETE` 等）和资源 URI 简化客户端和服务器之间的交互。这种一致性使客户端能够以可预测的方式处理不同资源。
* `URI Structure` : URI 用于唯一标识资源。RESTful URI 应具有意义、分层且便于阅读。它们还应避免包含实现细节并专注于资源标识。例如，RESTful API 中的博客文章或用户资料是一个资源，它具有相应的 URI，例如 `/posts/123` 或 `/users/johndoe`。
* `Status Codes` : HTTP 状态码用于指示请求的执行结果。RESTful 系统大量使用状态码，例如 `200`（`OK`）、`201`（`Created`）、`204`（`No Content`）、`404`（`Not Found`）等，以提供有关操作结果的信息。
* `Hypertext as the Engine of Application State (HATEOAS)` : `HATEOAS` 是 REST 中的一个约束，鼓励在响应中包含超链接，使客户端能够动态发现和导航可用操作和资源。此功能使 RESTful API 更具自描述性。

例如：检索用户信息：

`GET /users/1`

Response:
```
{
  "id": 1,
  "name": "John Doe",
  "email": "john.doe@example.com",
  "_links": {
    "self": { "href": "/users/1" },
    "orders": { "href": "/users/1/orders" },
    "cart": { "href": "/users/1/cart" }
  }
}
```
Orders: Link to fetch the user’s orders.

* `Layered System` : RESTful 系统可以设计为分层架构，其中代理、负载均衡器和缓存服务器等中间件可以在客户端和服务器之间引入。这些中间件增强了性能、可扩展性和安全性，而不会影响整体系统。

# HTTP 方法简介及其在 RESTful 通信中的作用

HTTP 方法，也称为 HTTP 动词，在 RESTful 通信中发挥着基础作用，通过定义客户端可以对资源执行的操作。这些方法决定了客户端与之交互时资源应如何处理。在 REST 中，HTTP 方法提供了一种一致且标准化的方式对资源执行操作，使其成为构建 Web 服务和 API 的强大架构风格。

以下是 RESTful 通信中一些常用 HTTP 方法的概述：

* `GET` : `GET` 方法用于从指定资源检索数据或信息。它是一个安全且幂等的操作，这意味着它不应对资源产生任何副作用，并且多个相同的请求应产生相同的结果。
* `POST` : `POST` 用于向指定资源提交数据以供处理。它通常会导致服务器上创建新资源。与 `GET` 不同，`POST` 请求不是幂等的，重复请求可能导致不同的结果。

