

# RESTful API 中的优雅关闭

构建 RESTful API 时，在服务器层面实现优雅关闭至关重要。无论发生故障还是发布新版本，我们都希望让所有正在进行中的请求完成工作。以下是来自 `main.go` 的优雅关闭示例：

```go
func main() {
	port := 8080
	engine := internal.BuildEngine()
	srv := &http.Server{
		Addr:    fmt.Sprintf(":%d", port),
		Handler: engine,
	}
	log.Printf("Starting server on port %d", port)
	startHTTPServer(srv)
}

func startHTTPServer(srv *http.Server) {
	// 创建一个监听来自操作系统中断信号的上下文。
	sigCtx, stopSig := signal.NotifyContext(context.Background(), syscall.SIGINT, syscall.SIGTERM)
	defer stopSig()

	go func() {
		if err := srv.ListenAndServe(); err != nil && err != http.ErrServerClosed {
			log.Print("error while running API gin server", "error", err.Error())
			os.Exit(1)
		}
	}()

	// 监听中断信号。
	<-sigCtx.Done()

	// 恢复中断信号的默认行为并通知用户正在关闭。
	stopSig()

	// 请求当前正在进行中；等待 10 秒以便它们完成。
	ctx, cancel := context.WithTimeout(context.Background(), 10*time.Second)
	defer cancel()

	if err := srv.Shutdown(ctx); err != nil {
		log.Print("server forced to shutdown: ", "error", err.Error())
	}
}
```

实现优雅关闭的函数是 `startHTTPServer`。首先，我们获取后台上下文并监听来自系统的中断信号。然后，在一个 goroutine 中运行 `ListenAndServe()` 函数。当接收到某个信号时，我们使用 `context.WithTimeout` 给系统 10 秒的时间来完成工作。请注意，此时间因服务器而异，取决于服务器的内部功能和 API 的用途。

# 过滤与排序

过滤和排序是我们可以在端点中实现的两大最常用功能。这是在我们之前看到的分页功能之外的补充。

## 过滤

实现过滤有三种主要方式：

### 路径参数

我们在本章中已经提到了路径参数。按路径参数过滤通常用于特定用例。

`GET /api/accounts/{category} -> GET /api/accounts/Enterprise`

在此示例中，我们按 Enterprise 类别过滤了所有账户。当然，我们需要在 OpenAPI 中声明它并在服务器中实现它。

### 查询参数

这是执行过滤最常用的方式。URL 应该非常直观，主要使用 `?` 和 `&` 关键字来分隔过滤参数。查询参数过滤有 URL 限制，我们希望尽可能保持简单。如果变得更复杂，我们应该考虑第三种过滤选项。

`GET /api/accounts?category=Enterprise&size_gt=500`

在此示例中，我们想要获取大小大于 500 的所有企业账户。同样，我们可以使用不同的过滤器，如 `size_lt`（小于）、`size=`（等于）、`size_not`（不等于）和 `size_gte`（大于或等于）。

### 请求体

偶尔，我们需要更复杂的过滤。此时，使用请求体非常方便。

```http
POST /api/accounts
Content-Type: application/json

{
  "or": {
    "category": "Enterprise",
    "size_gt": 500
  }
}
```

在前面的示例中，我们使用带有 JSON 的 HTTP POST 请求，询问所有属于企业类别或大小大于 500 的账户。

## 排序

排序是 API 按特定顺序（如用户需求）排列响应数据的能力。对数据进行排序有三种主要方式：

### 升序

此技术用于按特定字段从最低值排序到最高值。

`GET /api/accounts?sort=size&order=asc`

在示例中，我们将所有账户从最小排序到最大。惯例是使用 sort 和 order 作为查询参数。

### 降序

与升序相同，但顺序相反。它按从最高值到最低值返回数据。

`GET /api/accounts?sort=size&order=desc`

惯例是使用 `asc` 表示升序，`desc` 表示降序。

### 多字段排序

当单个字段不足时，我们可以使用多个字段进行更复杂的排序。

`GET /api/account?sort=effective_score,-size`

在前面的示例中，字段 `effective_score` 是 1 到 5 之间的排名数字，用于确定账户的有效权重。我们想要检索最高效的账户（升序），且在相同效率下尺寸最小的账户（因 `-` 号而降序）。

# 缓存

缓存是存储频繁使用数据的能力。缓存的位置可根据情况而变化。位置可以在负载均衡器或服务器级别，分布式缓存通常使用 Redis。让我们快速回顾一下 HTTP 方法缓存：

*   `GET`：默认缓存，除非发生特定情况。
*   `POST`：默认不缓存，除非请求显式声明需要缓存数据。
*   `PUT` 和 `DELETE` 完全不可缓存。

要实现缓存，我们需要利用中间件的力量并实现一个中间件。缓存功能依赖于 TTL（生存时间）和请求头定义：

### Expires

此头指定缓存过期的绝对时间。

`Expires: Sun, 21 June 2023 16:27:59 GMT`

### Cache-Control

此头声明指令，指明响应是否可缓存。指令示例包括 `max-age=3600`、`must-revalidate`、`no-cache` 等。可在 [https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control) 找到它们。

### Last-Modified

它确定上次生成响应的时间。

最后，必须记住缓存的目的是在响应所需数据时改善延迟并减少服务器工作量。如果缓存未能实现其初衷，我们需要移除或修复缓存层。

# 约定

在此，我们将详述与 RESTful API 相关的所有约定和最佳实践。

*   资源可以是集合或单例。例如：
    *   `GET /api/accounts`：集合资源
    *   `GET /api/accounts/{id}`：单例资源；当我们想要检索单例资源时，将使用**复数**形式的 `accounts`。

*   集合/单例资源可以包含子集合，例如：
    *   `GET /api/accounts/{id}/users` - users 是子集合资源。

*   **使用名词，而非动词**：URI 旨在将资源描述为实体（名词）而非动作（动词）。此外，不要在 URI 中包含操作名称。
    *   `GET /api/deleteAccounts/{id}` - 不好
    *   `DELETE /api/accounts/{id}` - 好

*   **字符约定**：
    *   使用 `-` 提高 URI 可读性：
        `GET /api/user-management`
    *   不要使用尾部斜杠：
        `GET /api/account/` - 不好
        `GET /api/account` - 好
    *   始终使用正斜杠 `/` 而非反斜杠 `\`
    *   避免使用文件扩展名：
        `GET /api/accounts/billing.json` - 不好
        `GET /api/accounts/billing` - 好

在少数场景中，端点会变得高度复杂，我们需要尽可能简化它。如果变得过于复杂，我们应该考虑将其拆分为两个或多个端点。

# 版本控制与弃用

