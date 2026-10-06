

| Resource Path | Operation Name | HTTP Method | Description | Request | Response |
| :--- | :--- | :--- | :--- | :--- | :--- |
| /books | listBooks() | GET | 按类别或发布日期列出书籍 | category/releaseDate | Book[] 200 |
| /books/search | searchBooks() | POST | 按作者、标题搜索书籍 | searchQuery | Book[] 200 |
| /books(bookid) | viewBook() | GET | 查看书籍详情 | bookid | Book 200 |
| /carts(cartid) | viewCart() | GET | 查看当前购物车和总计 | cartid | Cart 200, 404 |
| /carts(cartid) | clearCart() | DELETE | 移除购物车中的所有书籍 | cartid | Cart 204, 404 |
| /carts(cartid)/items | addItemToCart() | POST | 向客户购物车中添加书籍 | cartid | Cart 201, 400 |
| /carts(cartid)/items(cartitemid) | removeItemFromCart() | DELETE | 从客户购物车中移除书籍 | cartcartitemid | Cart 204, 401 |
| /authors | getAuthorDetails() | GET | 获取作者详情 | author | BookAuthor 200, 404 |

图 7.7 扩展购物 API 设计，并在表格的 Response 列中捕获了成功和错误响应代码。

# 第 7 章基于 REST 的 API 设计

组织通常有一个首有的 API 描述格式，例如 OpenAPI 规范 (OAS) 或 API Blueprint。如果尚未选择或标准化格式，请参阅第 13 章“API 文档编写”，了解更多关于可用格式的信息。无论选择何种格式，结果都是为 API 设计提供一个机器可读的版本，以便场场所处理、渲染 API 参考文档以及提供工具支持。

为了演示 API 设计阶段文档编写的关键领域，本章的示例使用了 OpenAPI 规范 v3 (OAS v3)。截图显示了使用 Swagger Editor 渲染 OAS v3 描述文件的结果，以作说明。

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

# REST API 设计流程

接下来，捕获每个操作的细节。对于 OAS v3，这从路径开始，随后是该路径支持的每个 HTTP 方法。建议为每个操作添加 `operationId` 属性。使用第 6 章定义的 API 配置文件中的操作名称。这使得文档编写过程变得简单，并有助于将 OAS 描述映射回 API 配置。

使用在第 3 章“识别数字能力”创建的相关作业故事（job stories）中捕获的细节，为 API 编写一个简要总结，帮助读者理解其目的。使用第 6 章 API 配置中捕获的信息扩展设计字段中的细节。此外，确保所有路径参数和查询参数都已捕获。如图 7.9 所示。

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

# 第 7 章 基于 REST 的 API 设计

最后，在 OAS v3 描述的 schema 部分捕获所有资源表示。使用第 6 章所述的 API 建模期间创建的资源模型。如图 7.10 所示，其中捕获了 ListBooks 操作。

注意图 7.10，ListBooks 操作返回一个包含搜索结果中每本书基本信息的 BookSummary 实例数组。为数组响应或每个操作的请求/负载定义适当的 schema 通常是必要的。

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

