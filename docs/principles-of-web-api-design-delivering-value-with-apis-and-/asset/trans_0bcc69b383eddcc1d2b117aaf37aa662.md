
依赖资源嵌套在父资源下，要求路径中包含父级标识符才能与依赖资源交互。

# 关于依赖资源的警告

当从关系数据库开始自底向上设计 API，或使用关系型风格进行资源设计时，通常会看到大量的依赖资源。嵌套依赖资源是为了将子资源的导航范围限制在父资源的范围内。虽然创建依赖资源可能很有吸引力，但请记住，每个嵌套层都需要 API 消费者在路径中包含父级标识符。例如：

```
GET /users/{userId}/projects/{projectId}/tasks/{taskId}
```

API 消费者为了通过给定的标识符检索任务，还需要父级项目和用户标识符。这增加了客户端跟踪这些父级标识符的额外工作。嵌套依赖资源是一个实用的设计选项，但应仅在提高 API 可用性时使用。

结果如图 7.4 所示。注意资源集合使用的是复数名称。虽然这是要求的，但这种约定在 REST API 中很常见。
将操作列表（包括其描述和请求/响应详情）迁移到新的表格格式，用于捕捉高层设计。如图 7.5 所示。

| 资源路径 |
| :--- |
| /books |
| /carts |
| /carts/(cartId)/items |
| /authors |

**图 7.4** 将每个资源名称转换为 URL 友好型名称，并将依赖资源嵌套在父资源下。

# 第 7 章 基于 REST 的 API 设计

| 资源路径 | 操作名称 | HTTP 方法 | 描述 | 请求 | 响应 |
|---|---||---|---|---|
| /books | listBooks() | GET | 按类别或发布日期列出书籍 | categoryId/releaseDate | Book[] |
| /books/search | searchBooks() | GET | 按作者或标题搜索书籍 | searchQuery | Book[] |
| /books/{bookId} | viewBook() | GET | 查看书籍详情 | bookId | Book |
| /carts/{cartId} | viewCart() | GET | 查看当前购物车和总计 | cartId | Cart |
| /carts/{cartId} | clearCart() | DELETE | 从客户购物车中移除所有书籍 | cartId | Cart |
| /carts/{cartId}/items | addItemToCart(itemId) | POST | 向客户购物车中添加书籍 | cartId, itemId | Cart |
| /carts/{cartId}/items | removeItemFromCart(itemId) | DELETE | 从客户购物车中移除书籍 | cartId, itemId | Cart |
| /authors/{authorId} | getAuthorDetails() | GET | 获取作者详情 | authorId | Author 表格格式 |

图 7.5 将 API 概要的操作列表、描述和请求迁移到新的以设计为中心的格式。

# 第 2 步：将 API 操作映射到 HTTP 方法

下一步是确定哪个 HTTP 方法适用于每个操作。表 6.1 概述了每个 HTTP 方法可能分配的三种安全分类：安全的（safe）、幂等的（idempotent）。表 7.1 根据预期的用途概述了常用 HTTP 方法的安全分类。

在建模过程中，可能会在 API 概要的操作名称和/或描述中识别出常用动词。这些动词通常为最匹配操作的 HTTP 方法提供子句。通过结合表 7.1 所示的 HTTP 方法安全分类与表 7.2 列出的操作映射，可以选择合适的 HTTP 方法。

以表 7.2 为参考，并结合第 1 步中之前创建的资源路径列表，根据预期的用途为每个操作分配相应的路径和 HTTP 方法。如果操作是与特定的资源实例交互，请在路径中包含资源标识符。结果如图 7.6 所示。

| HTTP 方法 | 方法描述 | 安全分类 | 安全描述 |
|---|---||---|---|
| GET | 返回请求的数据 | 安全的 | 不发生状态更改 |
| POST | 用于各种场景，从计算到创建新资源 | 不安全的 | 无法保证相同输入多次调用的结果相同 |
| PUT | 客户端提供的整个资源表示表示 | 幂等的 | 保证相同输入多次调用的结果相同 |
| PATCH | 执行资源的部分更新 | 不安全的 | 无法保证相同输入多次调用的结果相同，因为客户端仅提供了资源表示 |
| DELETE | 从服务器删除资源 | 幂等的 | 多次调用同一资源仍会导致资源被删除（即使不存在） |

# 第 7 章 基于 REST 的 API 设计

| 表 7.2 操作名称/描述中发现常用动词映射到 HTTP |
| 操作动词 | 典型 HTTP 方法 + 资源示例 |
|---|---|
| List, Search, Match, View All | 资源集合 <br> GET /books |
| Show, Retrieve, View | 资源实例 <br> GET /books/123 |
| Create, Add | 资源集合 <br> POST /books |
| Replace | 资源实例或集合 <br> PUT /carts/123 |
| Update | 资源实例 <br> PATCH /carts/123 |
| Delete, Remove All, Clear, Reset | 资源实例 <br> DELETE /carts/123 |
| Delete | 资源实例 <br> DELETE /carts/123/items |
| Search, Secure Search | 资源集合的自定义操作 <br> POST /carts/search |
| <其他动词> | 资源集合或实例的自定义操作 <br> POST |

# 第 3 步：将 API 操作映射到 HTTP 方法

下一步是确定适用于每个操作的 HTTP 方法。表 6.1 概述了每个 HTTP 方法可能分配的三种安全分类：安全的、幂等的。表 7.1 根据预期的用途概述了常用 HTTP 方法的安全分类。

在建模过程中，可能会在 API 概要的操作名称和/或描述中识别出常用动词。这些动词通常为最匹配操作的 HTTP 方法提供子句。通过结合表 7.1 所示的 HTTP 方法安全分类与表 7.2 列出的操作映射，可以选择合适的 HTTP 方法。

以表 7.2 为参考，并结合第 1 步中之前创建的资源路径列表，根据预期的用途为每个操作分配相应的路径和 HTTP 方法。如果操作是与特定的资源实例交互，请在路径中包含资源标识符。结果如图所示。

# 第 3 步：分配响应代码

API 设计正在开始。下一步是为每个操作分配响应代码。这些代码属于三个主要类：
- 2xx：成功
- 4xx：客户端错误
- 5xx：服务器错误

API 客户端应该准备好处理任何响应，但没有 {捕捉所有可能的代码。首先为每个操作识别至少一个成功响应，以及 API 可能显式返回的错误代码。虽然错误列表可能不完整，但首先识别可能返回的典型错误代码。图 7.7 显示了购物 API 可能的成功和错误代码。

| 资源路径 | 操作名称 | HTTP 方法 | 描述 | 请求 | 响应 |
|---|---|---|---|---|---|
| /books | listBooks() | GET | 按类别或发布日期列出书籍 | categoryId/releaseDate | Book[] |
| /books/search | searchBooks() | GET | 按作者或标题搜索书籍 | searchQuery | Book[] |
| /books/{bookId} | viewBook() | GET | 查看书籍详情 | bookId | Book |
| /carts/{cartId} | viewCart() | GET | 查看当前购物车和总计 | cartId | Cart |
| /carts/{cartId} | clearCart() | DELETE | 从客户购物车中移除所有书籍 | cartId | Cart |
| /carts/{cartId}/items | addItemToCart(itemId) | POST | 向客户购物车中添加书籍 | cartId, itemId | Cart |
| /carts/{cartId}/items | removeItemFromCart(itemId) | DELETE | 从客户购物车中移除书籍 | cartId, itemId | Cart |
| /authors/{authorId} | getAuthorDetails() | GET | 获取作者详情 | authorId | Author 表格格式 |

图 7.6 使用识别出的路径列表，根据预期的用途为每个操作分配相应的路径和 HTTP 方法。

# 不要发明你自己的代码

多年来，API 设计者做过一些奇怪的决定。一种是决定使用 UNIX 风格的代码，其中0 表示成功，1 到 127 表示错误。请不要发明你自己的代码。HTTP 设计是分层的，这意味着在客户端和服务器之间可能涉及中间服务器。创建你自己的代码会导致这些中间层出现问题。

虽然响应代码列表很大，但有几个是 API 设计中常用的。这些代码详见表 7.3。

# 第 4 步：记录 REST 设计

完成第 3 步后，高层 API 设计工作结束。利用目前完成的工作，现在是使用 API 描述格式捕捉 API 设计了。这将允许团队内部和团队之间共享 API 设计以获取反馈。

表 7.3 API 设计中常用的 HTTP 响应代码

| HTTP 响应代码 | 描述 |
|---|---|
| 200 OK | 请求成功。 |
| 201 Created | 请求已执行并创建了新资源。 |
| 202 Accepted | 请求已接受处理，但处理尚未完成。 |
| 204 No Content | 服务器已执行请求但不需要返回正体。这在删除操作中常见。 |
| 400 Bad Request | 由于语法错误或输入无效，服务器无法理解请求。 |
| 401 Unauthorized | 服务器需要用户身份验证。 |
| 403 Forbidden | 服务器理解请求但拒绝执行。 |
| 404 Not Found | 服务器未找到请求 URL/URI 的任何内容。 |
| 500 Internal Server Error | 服务器遇到意外情况，导致无法执行请求。 |

