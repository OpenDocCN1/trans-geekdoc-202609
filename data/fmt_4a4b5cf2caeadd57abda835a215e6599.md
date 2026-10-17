
在建模过程中，可能会在 API 概要的操作名称和/或描述中识别出常用动词。这些动词通常为最匹配操作的 HTTP 方法提供子句。通过结合表 7.1 所示的 HTTP 方法安全分类与表 7.2 列出的操作映射，可以选择合适的 HTTP 方法。

以表 7.2 为参考，并结合第 1 步中之前创建的资源路径列表，根据预期的用途为每个操作分配相应的路径和 HTTP 方法。如果操作是与特定的资源实例交互，请在路径中包含资源标识符。结果如图所示。

# 第 3 步：分配响应代码

API 设计正在开始。下一步是为每个操作分配响应代码。这些代码属于三个主要类：

- 2xx：成功
- 4xx：客户端错误
- 5xx：服务器错误

API 客户端应该准备好处理任何响应，但没有 `{捕捉所有可能的代码。首先为每个操作识别至少一个成功响应，以及 API 可能显式返回的错误代码。虽然错误列表可能不完整，但首先识别可能返回的典型错误代码。图 7.7 显示了购物 API 可能的成功和错误代码。

| 资源路径 | 操作名称 | HTTP 方法 | 描述 | 请求 | 响应 |
|---|---|---|---|---|---|
| `/books` | `listBooks()` | `GET` | 按类别或发布日期列出书籍 | `categoryId/releaseDate` | `Book[]` |
| `/books/search` | `searchBooks()` | `GET` | 按作者或标题搜索书籍 | `searchQuery` | `Book[]` |
| `/books/{bookId}` | `viewBook()` | `GET` | 查看书籍详情 | `bookId` | `Book` |
| `/carts/{cartId}` | `viewCart()` | `GET` | 查看当前购物车和总计 | `cartId` | `Cart` |
| `/carts/{cartId}` | `clearCart()` | `DELETE` | 从客户购物车中移除所有书籍 | `cartId` | `Cart` |
| `/carts/{cartId}/items` | `addItemToCart(itemId)` | `POST` | 向客户购物车中添加书籍 | `cartId, itemId` | `Cart` |
| `/carts/{cartId}/items` | `removeItemFromCart(itemId)` | `DELETE` | 从客户购物车中移除书籍 | `cartId, itemId` | `Cart` |
| `/authors/{authorId}` | `getAuthorDetails()` | `GET` | 获取作者详情 | `authorId` | `Author` 表格格式 |

图 7.6 使用识别出的路径列表，根据预期的用途为每个操作分配相应的路径和 HTTP 方法。

## 不要发明你自己的代码

多年来，API 设计者做过一些奇怪的决定。一种是决定使用 UNIX 风格的代码，其中`0` 表示成功，`1` 到 `127` 表示错误。请不要发明你自己的代码。HTTP 设计是分层的，这意味着在客户端和服务器之间可能涉及中间服务器。创建你自己的代码会导致这些中间层出现问题。

虽然响应代码列表很大，但有几个是 API 设计中常用的。这些代码详见表 7.3。

# 第 4 步：记录 REST 设计

完成第 3 步后，高层 API 设计工作结束。利用目前完成的工作，现在是使用 API 描述格式捕捉 API 设计了。这将允许团队内部和团队之间共享 API 设计以获取反馈。

表 7.3 API 设计中常用的 HTTP 响应代码

| HTTP 响应代码 | 描述 |
|---|---|
| `200 OK` | 请求成功。 |
| `201 Created` | 请求已执行并创建了新资源。 |
| `202 Accepted` | 请求已接受处理，但处理尚未完成。 |
| `204 No Content` | 服务器已执行请求但不需要返回正体。这在删除操作中常见。 |
| `400 Bad Request` | 由于语法错误或输入无效，服务器无法理解请求。 |
| `401 Unauthorized` | 服务器需要用户身份验证。 |
| `403 Forbidden` | 服务器理解请求但拒绝执行。 |
| `404 Not Found` | 服务器未找到请求 URL/URI 的任何内容。 |
| `500 Internal Server Error` | 服务器遇到意外情况，导致无法执行请求。 |
| Resource Path | Operation Name | HTTP Method | Description | Request | Response |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `/books` | `listBooks()` | `GET` | 按类别或发布日期列出书籍 | `category/releaseDate` | `Book[] 200` |
| `/books/search` | `searchBooks()` | `POST` | 按作者、标题搜索书籍 | `searchQuery` | `Book[] 200` |
| `/books(bookid)` | `viewBook()` | `GET` | 查看书籍详情 | `bookid` | `Book 200` |
| `/carts(cartid)` | `viewCart()` | `GET` | 查看当前购物车和总计 | `cartid` | `Cart 200, 404` |
| `/carts(cartid)` | `clearCart()` | `DELETE` | 移除购物车中的所有书籍 | `cartid` | `Cart 204, 404` |
| `/carts(cartid)/items` | `addItemToCart()` | `POST` | 向客户购物车中添加书籍 | `cartid` | `Cart 201, 400` |
| `/carts(cartid)/items(cartitemid)` | `removeItemFromCart()` | `DELETE` | 从客户购物车中移除书籍 | `cartcartitemid` | `Cart 204, 401` |
| `/authors` | `getAuthorDetails()` | `GET` | 获取作者详情 | `author` | `BookAuthor 200, 404` |

图 7.7 扩展购物 API 设计，并在表格的 Response 列中捕获了成功和错误响应代码。

# 第 7 章 基于 REST 的 API 设计

组织通常有一个首有的 API 描述格式，例如 OpenAPI 规范 `OAS` 或 API Blueprint。如果尚未选择或标准化格式，请参阅第 13 章“API 文档编写”，了解更多关于可用格式的信息。无论选择何种格式，结果都是为 API 设计提供一个机器可读的版本，以便场场所处理、渲染 API 参考文档以及提供工具支持。

为了演示 API 设计阶段文档编写的关键领域，本章的示例使用了 OpenAPI 规范 v3 `OAS v3`。截图显示了使用 Swagger Editor 渲染 OAS v3 描述文件的结果，以作说明。

通过利用在整个 API 建模和设计过程中捕获的细节启动文档编写过程。包含 API 名称、描述以及关于 API 的其他细节。描述应引用可能与此 API 协作的其他 API。总结 API 的目的和提供的操作类型。避免包含 API 实现的内部细节，这些细节可以存储在 API 外部的 wiki 或共享协作工具中，以供以后参考。图 7.8 显示了在 OAS v3 中捕获这些细节的结果。

```
openapi: 3.0.0
info:
  title: 书店购物 API - REST 
  description:
    支持在线书店的购物体验，包括浏览和搜索
    可用书籍以及购物车管理。
订单创建 API 用于将购物车转换为订单，准备接受收货详情、支付和履约跟踪。
该 API 按照功能包含以下购物操作：
| Capability | Operation |
| List Books | 列出店内最近的书籍 |
| List Books | 按主题或关键词搜索书籍 |
| View Book | 查看详情 |
| Place Order | 创建购物车 |
| Place Order | 添加到购物车 |
| Place Order | 从购物车中移除书籍 |
| Place Order | 修改购物车中的书籍 |
| Place Order | 查看购物车总计 |
contact:
  version: '1.0'
servers:
- url: https://{defaultHost}
variables:
  defaultHost:
    default: www.example.com/shop
```

图 7.8 将购物 API 设计捕获到 OpenAPI 规范 v3 中，从名称、描述和其他细节开始。

- 1. https://swagger.io

## REST API 设计流程

接下来，捕获每个操作的细节。对于 OAS v3，这从路径开始，随后是该路径支持的每个 HTTP 方法。建议为每个操作添加 `operationId` 属性。使用第 6 章定义的 API 配置文件中的操作名称。这使得文档编写过程变得简单，并有助于将 OAS 描述映射回 API 配置。

使用在第 3 章“识别数字能力”创建的相关作业故事 `job stories` 中捕获的细节，为 API 编写一个简要总结，帮助读者理解其目的。使用第 6 章 API 配置中捕获的信息扩展设计字段中的细节。此外，确保所有路径参数和查询参数都已捕获。如图 7.9 所示。

```
paths:
  books:
    get:
      tags:
        - Books
      summary: 根据搜索标准返回可用书籍的分页列表
      description: 根据搜索标准返回可用书籍的分页列表。如果没有提供搜索标准，将按字母顺序返回书籍。 
      operationId: ListBooks
      parameters:
        - name: q
          in: query
          description: 用于通过标题和描述过滤书籍的查询字符串。如果未提供，将列出所有可用书籍。注意查询参数 'q' 是通用查询的常用标准
          style: form
          explode: true
          schema:
            type: string
        - name: daysSinceBookReleased
          in: query
          description: 用于过滤过去若干天内书籍的查询字符串，例如 7 表示过去 7 天内。默认值 0 表示不应用过滤。过滤的最大天数是 30 天。
          style: form
          explode: true
          schema:
            type: integer
            format: int32
        - name: offset
          in: query
          description: 获取列表的偏移量，偏移为 0 表示第一页。默认偏移为 0
          style: form
```

图 7.9 扩展 API 设计以包含每个操作。

最后，在 OAS v3 描述的 schema 部分捕获所有资源表示。使用第 6 章所述的 API 建模期间创建的资源模型。如图 7.10 所示，其中捕获了 `ListBooks` 操作。

注意图 7.10，`ListBooks` 操作返回一个包含搜索结果中每本书基本信息的 `BookSummary` 实例数组。为数组响应或每个操作的请求/负载定义适当的 schema 通常是必要的。

**图 7.10** 完成 API 设计以包含 schema 定义。

| Line | Value |
| :--- | :--- |
| 427 | NewCart: |
| 428 | title: NewCart |
| 429 | required: |
| 430 | - bookId |
| 431 | - quantity |
| 432 | type: object |
| 433 | properties: |
| 434 | bookId: |
| 435 | type: string |
| 436 | description: 添加到购物车的书籍 |
| 437 | quantity: |
| 438 | minimum: 1 |
| 439 | type: integer |
| 440 | description: 添加到购物车的书籍数量 |
| 441 | format: int32 |
| 442 | description: 创建一个带有初始购物车项的购物车 |
| 443 | NewCartItem: |
| 444 | title: NewCartItem |
| 445 | required: |
| 446 | - bookId |
| 447 | - quantity |
| 448 | type: object |
| 449 | properties: |
| 450 | bookId: |
| 451 | type: string |
| 452 | description: 添加到购物车的书籍 |
| 453 | quantity: |
| 454 | minimum: 1 |
| 455 | type: integer |
| 456 | description: 添加到购物车的书籍数量 |
| 457 | format: int32 |
| 458 | description: 指定要添加到购物车的书籍和数量 |

# 第 124 页 第7 章 基于 REST 的 API 设计

![](img/6a422bfe4f2691ab7de274bb6978b0eb_158_0.png)

**图 7.12** 使用序列图来验证 API 设计是否满足之前建模的需求。

## 第 5 步：共享并收集反馈

最后一步是共享 API 设计，以获取直接团队、组织内的 API 架构师以及计划在 API 准备绪后立即集成的内部/外部团队的反馈。

一旦 API 正式发布并集成，API 设计就会被锁定，之后只能进行非破坏性的更改。可以添加新的端点，可能会向现有的资源表示中添加新字段，但重命名或修改现有端点会破坏现有的 API 消费者，导致客户不满，并可能引发客户流失。第一次做对至关重要。尽早共享 API 设计以获取反馈有助于避免发布后发生重大的设计变更。

API 的 Mock 模拟实现也有助于探索 API 设计。因为阅读 API 文档只能对 API 有基本的了解，Mock 实现为开发者提供了一个使用模拟数据体验 API 如何运行的机会。目前开始出现一些工具，它们可以接受 OAS 等 API 描述格式，并在无需编写一行代码的情况下生成 Mock API 实现。

请参阅第 16 章“继续 API 设计之旅”，了解其他 API 全生命周期技术，这些技术有助于在 API 开发和部署后仍获得反馈。

## 选择表示格式

到目前为止，关于资源设计的讨论集中在资源名称和属性上。然而，API 资源的表示格式也需要确定。选择表示格式是重要的一步。

对于某些组织来说，首选表示格式已经作为 API 风格指南的一部分确定。在这种情况下，决策已经做出，无需采取进一步行动。但是，如果这是一个新的 API 产品、程序或平台，则需要投入更多工作来完成设计。

尽可能选择一种单一格式作为所有 API 提供的默认表示。使用单一格式可以确保开发者在与该组织及其未来的 API 集成时保持一致性。

随着时间的推移可能会添加额外的格式，允许在不破坏现有集成的情况下缓慢迁移到新格式。多格式方法需要使用 HTTP 让客户端指定所需的表示格式。内容协商 `Content negotiation` 在附录 I 中进行了讨论。

表 7.4 总结了可用的四类表示格式。每个类别都建立在前一个的基础上，为资源和消息格式提供了更多选项。然而，随着选项的增加，复杂度也随之增加。每个类别都进行了解释，并提供了一个示例。本章提供的示例可在 GitHub 工作库中找到。

4. https://bit.ly/design-examples

表 7.4 API 表示格式分类

| 类别 | 概述 |
| --- | --- |
| 资源序列化 `Resource Serialization` | 将资源表示为各种格式，例如 JSON、XML、Protocol Buffers 和 Apache Avro |
| 超媒体序列化 `Hypermedia Serialization` | 支持嵌入超媒体控件的序列化表示 |
| 超媒体消息 `Hypermedia Messaging` | 支持超媒体控件属性的通用格式 |
| 语义超媒体消息 `Semantic Hypermedia Messaging` | 支持超媒体字段映射的通用格式 |

## 资源序列化

资源序列化表示格式最为常见。它们直接将资源的属性及其值映射到所需的格式，通常是 JSON、XML 或 YAML。Protocol Buffers 和 Apache Avro 等二进制格式也越来越受到接受。

这些表示格式需要显式代码来处理资源与目标格式之间的序列化。这种映射逻辑可以通过代码生成器或硬编码来实现。格式化程序和表示库通常有助于管理目标格式与表示资源的对象或结构之间的映射。

无论如何处理序列化，解析和映射代码都是唯一的，因为它必须感知预期的字段和嵌套结构。列表 7.1 提供了一个使用 JSON 序列化表示 `Book` 资源的示例。

### 列表 7.1 使用 JSON 的序列化表示
