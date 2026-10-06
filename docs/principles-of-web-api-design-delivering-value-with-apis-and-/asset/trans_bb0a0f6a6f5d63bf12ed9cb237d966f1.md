
API 描述格式 241

```yaml
types:
ListBooksResponse:
```yaml
ListBooksResponse:
display: ListBooksResponse
description: 列表或过滤结果的书籍摘要列表
request:
  type: object
  properties:
    books:
      required: false
      displayName: books
      type: array
      items:
        type: BookSummary
BookSummary:
  display: BookSummary
  description: 总结书店库存的书籍...
  type: object
  properties:
    bookId:
      required: false
      displayName: bookId
      description: 内部标识符，与 ISBN 独立，用于在库存中标识书籍
      type: string
    isbn:
      required: false
      displayName: isbn
      description: 书籍的 ISBN
      type: string
    title:
      required: false
      displayName: title
      description: 书名，例如《API 设计的实用方法》
    Design:
      type: string
    authors:
      required: false
      displayName: authors
      type: array
```

## 第 13 章 文档化 API 设计

```yaml
items:
  type: BookAuthor
BookAuthor:
  display: BookAuthor
  description: 代表一本书的单个作者。由于一本书可能有多个作者，...
  type: object
  properties:
    authorId:
      required: false
      displayName: authorId
      description: 引用作者的内部标识符
      type: string
    fullName:
      required: false
      displayName: fullName
      description: 作者的全名，例如 D. Keith Casey
      type: string
/books:
  get:
    display: ListBooks
    description: 根据提供的搜索条件提供分页的书籍列表...
    queryParameters:
      q:
        required: false
        display: q
        description: 用于通过标题过滤书籍的查询字符串
        description: 如果未提供，将列出所有可用书籍...
        type: string
      offset:
        required: false
        default: 0
        example:
          value: 0
        display: offset
        description: 从该偏移量获取书籍列表，偏移量为 0 表示结果的第一页...
        type: integer
        minimum: 0
        format: int32
      limit:
        required: false
        default: 25
        example:
          value: 25
        displayName: limit
        description: API 调用中包含的记录数，如果未提供，则默认包含 25 条记录...
        type: integer
        minimum: 1
        maximum: 100
        format: int32
    headers:
      Authorization:
        required: true
        displayName: Authorization
        description: 用于授权您的请求调用此操作的 OAuth 2.0 令牌...
        type: string
    responses:
      200:
        description: 成功
        headers:
          Content-Type:
            default: application/json
            displayName: Content-Type
            type: string
      body:
        application/json:
          displayName: response
          description: 成功
          type: ListBooksResponse
      401:
        description: 请求失败。当使用无效的 API 凭据进行请求时接收...
        body: {}
      403:
        description: 请求失败。当使用有效的 API 凭据请求您无访问权限的 API 操作或资源时接收。
        body: {}
```

# JSON Schema

JSON Schema 规范提供了一种机器可读的格式，用于捕捉基于 JSON 的结构和验证规则。该规范分为核心基础规则和验证规则，使其成为需要验证的 JSON Schema 的全面解决方案。JSON Schema 可以被视为 XML Schema 的 JSON 等版本。

虽然 JSON Schema 独立于任何特定的 API 风格，但它可以用于描述基于 REST 的 API 以及其他 API 风格的资源表示。它在组织中也被用作定义跨企业领域对象模式的单一格式。

虽然 OAS 的架构定义部分非常灵活，但它缺乏 JSON Schema 提供的某些健壮定义支持。最近的努力帮助了 JSON Schema 和 OAS 保持一致，允许同时使用这两种格式。鉴于 JSON Schema 在 OAS 描述格式中的接受度，预计其在未来将继续获得工具链的支持。列表 13.4 展示了 JSON Schema 的示例。

**列表 13.4** 示例 JSON Schema

```json
{
  "$id": "https://example.com/BookSummary.schema.json",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "description": "总结书店库存的书籍...",
  "type": "object",
  "properties": {
    "bookId": {
      "type": "string"
    },
    "isbn": {
      "type": "string"
    },
    "title": {
      "type": "string"
    },
    "authors": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/BookAuthor"
      }
    }
  },
  "definitions": {
    "BookAuthor": {
      "type": "object",
      "properties": {
        "authorId": {
          "type": "string"
        },
        "fullName": {
        "type": "string"
      }
    }
  }
}
```

# 使用 XML 描述 ALPS 语义

```xml
<alps version="1.0">
  <descriptor id="help"><text>帮助</text>
  <link rel="help" href="http://example.com/help.html" />
  <descriptor id="collection" type="safe" rel="BookSummary">
    <text>根据提供的搜索条件提供分页的书籍列表...</text>
    <descriptor id="q">
      <text>用于通过标题过滤书籍的查询字符串</text>
      <text>如果未提供，将列出所有可用书籍...</text>
    </descriptor>
  </descriptor>
  <descriptor id="offset">
    <text>从该偏移量获取书籍列表，偏移量为 0 表示结果的第一页...</text>
  </descriptor>
  <descriptor id="limit">
    <text>API 调用中包含的记录数，如果未提供，则默认包含 25 条记录...</text>
  </descriptor>
  </descriptor>
  <descriptor id="BookSummary" type="semantic">
    <descriptor id="bookId"><text>内部标识符，与 ISBN 独立，用于在库存中标识书籍</text></descriptor>
    <descriptor id="isbn"><text>书籍的 ISBN</text></descriptor>
    <descriptor id="title"><text>书名，例如《API 设计的实用方法》</text></descriptor>
    <descriptor id="authors">
      <descriptor id="authorId"><text>引用作者的内部标识符</text></descriptor>
      <descriptor id="fullName"><text>作者的全名，例如 D. Keith Casey</text></descriptor>
    </descriptor>
  </descriptor>
</alps>
```

# 使用 APIs.json 改进 API 发现

多个 API 描述格式可能是必要的，以帮助开发者使用各种工具消费 API。APIs.json 是一种通过索引文件描述格式，类似于网站地图，引导搜索引擎索引器访问网站的重要区域。

单个 APIs.json 文件可以引用多个 API，使得该格式适用于将多个独立的 API 描述文件封装到单一产品或平台视图中。与其他机器可读格式结合时，API 可以被发现、索引并在公共或私有 API 目录中可用。
正如名称所示，默认格式是 JSON，尽管列表 13.6 中的 YAML 格式同样可用。

```json
{
  "name": "书店示例",
  "type": "索引",
  "description": "书店示例中基于 REST 的 API 支持在线书店的购物体验，带有...",
  "tags": [
    "应用程序编程接口",
    "API"
  ],
  "created": "2020-12-10",
  "url": "http://example.com/apis.json",
  "specificationVersion": "0.14",
  "is": [
    {
      "name": "书店购物 API",
      "description": "书店示例中基于 REST 的 API 支持在线书店的购物体验",
      "humanURL": "http://example.com",
      "baseURL": "http://api.example.com",
      "tags": [
        "API",
        "应用程序编程接口"
      ],
      "properties": [
        {
          "type": "文档",
          "url": "https://example.com/documentation"
        }
      ]
    }
  ]
}
```