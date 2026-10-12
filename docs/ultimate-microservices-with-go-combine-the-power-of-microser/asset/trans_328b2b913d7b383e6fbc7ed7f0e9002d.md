
# 创建引擎

要创建一个新引擎，我们使用了 `gin.New()`。在构建引擎时，我们将声明所有适用于服务器中所有端点的中间件。在示例中，这些包括 logger、recovery 和 CORS（我们将在下一节讨论它们）。声明完所有需要的中间件后，我们将声明分组。Gin 允许我们将服务器划分为多个分组。我们不会重点关注这一点，而是为所有服务器分配单个分组。有时，开发人员会为一个类别分配一个分组，为一个子类别分配一个子分组。在示例中，分组仅为 `"/api"`。我们将通过 `routes_registrator.go` 文件中的 `RegisterRoutes` 函数将所有端点分配给该分组。

```go
func RegisterRoutes(routerGroup *gin.RouterGroup) {
    apple.RegisterRoutes(routerGroup)
}
```

使用此函数中的多个分组，我们可以将更相关的中间件分配给特定分组。现在，让我们观察单个端点即单个资源的内部结构。这是我们将在 `routes.go` 文件中找到的代码：

```go
package apple

import "github.com/gin-gonic/gin"

var Path = "/fruits/apple"

func RegisterRoutes(group *gin.RouterGroup) {
    group.GET(Path, gin.HandlersChain{ProcessRequest}...)
}
```

而在 `controller.go` 文件中：

```go
package apple

import "github.com/gin-gonic/gin"

func ProcessRequest(c *gin.Context) {
    c.JSON(200, gin.H{
        "color": "red",
        "date": "2023-12-11",
        "taste": "sweet",
    })
}
```

当然，响应只是模拟数据；相反，我们需要在 `server.go` 文件中执行业务逻辑函数，该函数几乎总是会从 `db.go` 文件查询数据。

# 责任链

如果简化来看，责任链是一种将多个命令链接在一起的设计模式，使得一个命令会引导至另一个命令。这种模式有助于我们满足分层系统的约束。该模式的实现通过中间件进行。

利用我们之前展示的模块化，我们可以将相关中间件应用于整个 API（在 `BuildEngine` 函数中）。我们可以更具体地将中间件应用于 `RegisterRoutes` 函数中的特定分组（类别）。甚至更详细地，我们可以在 `routes.go` 的资源级别应用特定中间件。

# CORS

CORS 是一种浏览器安全功能，全称为跨源资源共享。此功能旨在限制不需要的 HTTP 请求。我们必须指定哪些源可以从 Web 浏览器向我们的 RESTful API 服务器发送请求。以下是创建可处理此问题的 Gin 中间件的方法：

```go
func CORS() gin.HandlerFunc {
    return func(c *gin.Context) {
        c.Writer.Header().Set("Access-Control-Allow-Origin", "*")
        c.Writer.Header().Set("Access-Control-Allow-Credentials", "true")
        c.Writer.Header().Set("Access-Control-Allow-Methods", "POST, GET")
        c.Next()
    }
}
```

# API 能力

如前所述，每个 API 都需要支持作为产品需求衍生出的能力。许多流行的能力几乎存在于每个 API 中，也有一些则不然。我们将在此详述流行的能力。每个 API 能力很可能会被多个 API 使用，至少流行的那些是如此。最佳实践是创建一个可配置的共享基础设施，作为一个包提供服务，或者如果是单体仓库，则置于 `pkg` 目录下。例如，如果一个 API 使用特定类型的分页，同一公司的其他服务很可能也需要以相同方式使用分页。

# 分页

分页是将内容分离到单独页面/部分的过程。它通常用于导航或获取海量数据。例如，如果用户阅读在线书籍，我们不需要一次性获取所有书籍内容。相反，每当他翻页时，我们可以请求下一页。另一个例子是当我们需要特定账户的所有用户，但用户数量巨大，无法作为单个响应获取所有用户；此时我们可以使用分页。

存在各种分页算法，部分算法可应用于数据库层面。例如，在 PostgreSQL 的 SQL 中使用 limit 和 offset。流行的分页算法有：

*   **页码：** 最直接但最不常用的算法。选择固定 limit，然后将 limit 与页码相乘。
    `GET /api/users?page=2`
*   **偏移量和限制：** 类似于上述分页算法。区别在于我们必须选择 limit 大小，而不是使用默认 limit。客户端需要在每次请求之间使用 offset，这符合客户端交互。这是最常用的分页算法。
    `GET /api/users?limit=10`
    `GET /api/users?limit=10&offset=10`
    `GET /api/users?limit=10&offset=20`
*   **ID 的自增主键：** 也是一种普遍的算法。该算法依赖某个 ID 来排列数据，并将该 ID 用作游标。
    `GET /api/users?limit=10`
    `GET /api/users?limit=10&cursor=<last_id_from_previous_request>`
    `GET /api/users?limit=10&cursor=<last_id_from_previous_request>`

# 速率限制

速率限制是阻止用户、机器人和请求过度使用的一种方式。为保持服务器正常运行，我们必须限制发往服务器的请求数量。速率限制通常是每个时间间隔的恒定请求数，例如每分钟 10,000 个请求。

我们将在共享包中将速率限制作为中间件实现，并在每个服务中使用该中间件。没必要自己实现速率限制。有许多适合 Gin 的优秀包可以做到这一点。最后，当请求数量超过限制时，返回的 HTTP 状态码为 429（请求过多）。

# Panic 恢复

我们已经简要讨论了 Go 中的错误处理和 `panic()`。我们可以将 panic 比作其他编程语言中的 raise/throw 异常。当发生意外情况时我们使用 `panic()`，因此必须使整个应用程序崩溃。编写 RESTful API 时，端点内部的 `panic()` 很奇怪，因为单个端点不应影响其他端点。

如果该端点发生严重问题，我们必须返回错误状态码。编写 RESTful API 时，我们可能会在服务器启动时或与整个服务器崩溃相关的功能中使用 `panic()`。请也注意明智地使用 panic，因为发生 `panic()` 时会执行所有 defer 语句。

开发人员经常错误地使用 `panic()`，意外地将其放在端点内，或使用将 `panic()` 传播到我们程序的包。为应对这种情况，我们可以创建一个能从 panic 中恢复的中间件。我们可以使用 Gin 默认的 panic 恢复中间件：

```go
engine.Use(gin.Recovery())
```

或者我们可以使用 `recover()` 函数制作自定义 panic 恢复：

```go
func WithCustomRecovery() gin.HandlerFunc {
    return func(c *gin.Context) {
        defer func() {
            if err := recover(); err != nil {
                _ = c.Error(fmt.Errorf("[recovered] panic: %v", err))
                c.AbortWithStatusJSON(http.StatusInternalServerError, gin.H{"Error": "Internal Server Error"})
            }
        }()
        c.Next()
    }
}
```

在前面的示例中，我们制作了一个自定义恢复，并可以放入任何我们想要的自定义功能。注意，此中间件将针对每个在途请求发生。

# 优雅关闭

优雅关闭是指系统或应用程序关闭或收到需要关闭的信号（发布或任何其他原因）时的行为。在接收到关闭信号时，应用程序有在途任务。优雅关闭给应用程序一个宽限期来完成其任务。
