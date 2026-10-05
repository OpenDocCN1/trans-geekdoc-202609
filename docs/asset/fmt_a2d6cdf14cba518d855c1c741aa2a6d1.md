
```go
func main() {
    http.Handle("/", home)
    http.HandleFunc("/snippet", showSnippet)
    http.HandleFunc("/snippet/create", createSnippet)

    log.Println("Starting server on :4000")
    err := http.ListenAndServe(":4000", nil)
    log.Fatal(err)
}
```

在后台，这些函数会将路由注册到一个名为 `DefaultServeM` 的地方。这没什么特别的 —— 是我们一直在使用的普通 servemux，它默认初始化并存储在 `net/http` 的一个全局变量中。这里是 Go 源码中的相关行：

```go
var DefaultServeM = NewServeMux()
```

虽然这种方法可以让你的代码稍微短一点，我不建议在生产应用中使用。

由于 `DefaultServeM` 是一个全局变量，任何包都可以访问它并注册路由 —— 包括你的应用程序导入的任何第三方包。如果这些第三方包中的一个被攻破，它们可以使用 `DefaultServeM` 向 Web 暴露恶意的处理器。

因此，出于安全考虑，通常避免 `DefaultServeM` 及其相应的辅助函数是一个好主意。使用局部作用域的 servemux，就像我们在目前为止的项目中所做的那样。

# Servemux 特性与细节

- 在 Go 的 servemux 中，较长的 URL 模式总是优先于较短的模式。因此，如果一个 servemux 包含多个匹配模式，匹配请求时，它始终会将请求分发到与最长模式对应的处理器。这有一个很棒的副作用：你可以以任何顺序注册模式，而这不会改变 servemux 的行为。

- 请求 URL 会自动进行清理。如果请求路径包含任何 `.` 或 `..` 元素或重复的斜杠，它将自动重定向用户到等效的清理 URL。例如，如果用户向 `/foo/bar/../baz` 发起请求，将自动收到 301 永久重定向到 `/foo/baz`。

- 如果已经注册了子树路径，并且接收到了该子树路径的未带尾斜杠的请求，则用户将自动被重定向到 301 带有斜杠的子树路径。例如，如果你注册了路径 `/foo/`，那么你对 `/foo` 的请求将被重定向到 `/foo/`。

## 主机名匹配

在 URL 模式中包含主机名是可能的。当你想要将所有 HTTP 请求重定向到规范 URL，或者你的应用程序作为多个站点或服务的后端时，这非常有用。例如：

```go
mux := http.NewServeMux()
mux.HandleFunc("foo.example.org/", fooHandler)
mux.HandleFunc("bar.example.org/", barHandler)
mux.HandleFunc("/baz", bazHandler)
```

在涉及模式匹配时，将首先检查任何特定主机的模式，如果匹配，则将请求分发到相应的处理器。只有在没有找到特定主机的匹配时，才会检查非特定主机的模式。

## RESTful 路由又是怎样的？

必须承认的是，Go 的 servemux 提供的路由功能相当轻量级。它不支持基于请求方法的路由，不支持包含变量的语义化 URL，也不支持基于正则表达式的模式。如果你有使用 Rails、Django 或 Laravel 等框架的背景，你可能会发现这有些局限性……而且令你惊讶！

不要让这让你望而却步。事实是，Go 的 servemux 仍然可以让你走得很远，并且对于许多应用程序来说是完全足够的。当你需要更多功能时，有大量的第三方路由器可以用来代替 Go 的 servemux。我们将在书的稍后部分介绍一些流行的选项。

## 自定义 HTTP 请求头

让我们更新应用程序，使 `/snippet/create` 路由仅响应使用 POST 方法的 HTTP 请求，如下所示：

| 方法 | 模式 | 处理器 | 动作 |
|---|---|---|---|
| ANY | `/` | `home` | 显示首页 |
| ANY | `/snippet` | `showSnippet` | 显示特定的片段 |
| POST | `/snippet/create` | `createSnippet` | 创建新片段 |

进行此更改是重要的，因为——在我们构建应用程序的后续阶段，对 `/snippet/create` 路由的请求将导致数据库中创建一个新片段。在数据库中创建新片段是一个非幂等的操作，会改变我们服务器的状态，因此我们应该遵循 HTTP 良好实践，并将此路由限制为仅处理 POST 请求。

现在我想涵盖这一点的主要是，这是一个讨论 HTTP 响应头并解释如何自定义它们的好借口。

## HTTP 状态码

让我们从更新 `createSnippet()` 处理器函数开始，除非请求方法为 POST，否则它将发送 405（方法不允许）HTTP 状态码。为了做到这一点，我们需要像这样使用 `w.WriteHeader()` 方法：

```go
File: main.go
package main
...
func createSnippet(w http.ResponseWriter, r *http.Request) {
    // 使用 r.Method 检查请求是否在使用 POST。
    // 如果不是，使用 w.WriteHeader() 方法发送 405 状态码，
    // 并使用 w.Write() 方法写入 "Method Not Allowed" 响应体。
    // 然后从函数返回，以便后续代码不执行。
    if r.Method != "POST" {
        w.WriteHeader(405)
        w.Write([]byte("Method Not Allowed"))
        return
    }

    w.Write([]byte("Create a new snippet..."))
}
```

尽管此更改看起来简单，但有几个细微差别我应该解释：

- 每个响应只能调用一次 `w.WriteHeader()`，在状态码写入后就无法再更改。如果你尝试第二次调用 `w.WriteHeader()`，Go 将记录一条警告消息。

- 如果你没有显式地调用 `w.WriteHeader()`，那么第一次调用 `w.Write()` 将自动向用户发送 200 OK 状态码。

因此，如果你想发送非 200 状态码，必须在调用任何 `w.Write()` 之前调用 `w.WriteHeader()`。

让我们来看这个操作。

重启服务器，然后打开第二个终端窗口并使用 `curl` 向 `http://localhost:4000/snippet/create` 发送 POST 请求。你应该得到一个类似下方的带有 200 OK 状态码的 HTTP 响应：

```bash
$ curl -i -X POST http://localhost:4000/snippet/create
HTTP/1.1 200 OK
Date: Thu, 02 Aug 2018 12:58:54 GMT
Content-Length: 23
Content-Type: text/plain
```

但如果你使用不同的方法——比如 PUT——你现在应该得到 405 Method Allowed 响应。例如：

```bash
$ curl -i -X PUT http://localhost:4000/snippet/create
HTTP/1.1 405 Method Allowed
Allow: POST
Date: Thu, 02 Aug 2018 12:59:14 GMT
Content-Length: 18
Content-Type: text/plain
```

## 自定义标头

我们可以做的另一个改进是在每个响应中包含 `Allow: POST` 头，让用户知道支持哪些方法。我们可以通过使用 `Header().Set()` 方法来实现这一点，如下所示：

```go
File: main.go
package main
...
func createSnippet(w http.ResponseWriter, r *http.Request) {
	if r.Method != "POST" {
		// 使用 Header().Set() 方法向响应添加 'Allow: POST' 头
		w.Header().Set("Allow", "POST")
		w.WriteHeader(405)
		w.Write([]byte("Method Not Allowed"))
		return
	}

	w.Write([]byte("Create a new snippet..."))
}
```

这里必须指出的是，在调用 `w.WriteHeader()` 或 `w.Write()` 之后更改头部 map 对用户接收到的响应没有影响。你需要在调用这些方法之前确保你的头部 map 包含了你想要的所有头部。

让我们通过向我们的 `/snippet/create` 发送非 POST 请求来观察此效果：

```bash
curl -i -X PUT http://localhost:4000/snippet/create
HTTP/1.1 405 Method Allowed
Allow: POST
Date: Thu, 02 Aug 2018 13:01:16 GMT
Content-Length: 18
Content-Type: text/plain
```

## http.Error 快捷方法

如果你想发送非 200 状态码和纯文本响应体（如我们在上面的代码中所示），这是使用 `http.Error()` 快捷方法的绝佳机会。这是一个轻量级辅助函数，它接收给定的消息和状态码，然后在后台为我们调用 `w.WriteHeader()` 和 `w.Write()` 方法。

让我们更新代码使用它。

```go
File: main.go
package main
...
func createSnippet(w http.ResponseWriter, r *http.Request) {
	if r.Method != "POST" {
		w.Header().Set("Allow", "POST")
		// 使用 http.Error() 函数发送 405 状态码和 "Method
		// Not Allowed" 字符串作为响应体。
		http.Error(w, "Method Not Allowed", 405)
		return
	}

	w.Write([]byte("Create a new snippet..."))
}
...
```

在功能方面几乎完全一样。最大的区别是，我们现在将 `http.ResponseWriter` 传递给另一个函数，该函数向用户发送响应。将 `http.ResponseWriter` 传递给其他函数的模式在 Go 中非常常见，我们在整个书中会经常这样做。在实践中，很少像我们目前为止所做的那样直接使用 `w.Write()` 和 `w.WriteHeader()` 方法。但我想预先介绍它们，因为它们是更高级（更有趣！）的响应方式的基础。

## 操作 Header 映射

在上面的代码中，我们使用 `w.Header().Set()` 向响应头映射中添加新的 header。但你也可以使用 `Add()`、`Del()` 和 `Get()` 方法来读取和操作 header 映射。

```go
// 设置一个新的 cache-control header。如果已存在 "Cache-Control" header，
// 它将会被覆盖。
w.Header().Set("Cache-Control", "public, max-age=31536000")

// 与此相反，Add() 方法会追加一个新的 "Cache-Control" header，并且可以
// 多次调用
w.Header().Add("Cache-Control", "public")
w.Header().Add("Cache-Control", "max-age=31536000")

// 删除 "Cache-Control" header 的所有值。
w.Header().Del("Cache-Control")

// 获取 "Cache-Control" header 的第一个值。
w.Header().Get("Cache-Control")
```

## 系统生成的 Header 和内容嗅探

在发送响应时，Go 会自动为你设置三个*系统生成的* header：*Date*、*Content-Length* 和 *Content-Type*。

*Content-Type* header 特别有趣。Go 会尝试通过 `http.DetectContentType()` 函数对响应体进行*内容嗅探*（content sniffing），为你设置正确的 header。如果该函数无法判断内容类型，Go 将退而设置 header `Content-Type: application/octet-stream`。

`http.DetectContentType()` 函数通常工作得很好，但 Go Web 开发者常见的一个常见陷阱是，它无法区分 JSON 和纯文本。而且，默认情况下，JSON 响应将带有 `Content-Type: text/plain; charset=utf-8` header 发送。你可以通过这样手动设置正确的 header 来防止这种情况发生：

```go
w.Header().Set("Content-Type", "application/json")
w.Write([]byte(`{"name":"Alex"}`))
```

## Header 规范化（Canonicalization）

当你在 header 映射上使用 `Add()`、`Get()`、`Set()` 和 `Del()` 方法时，header 名称将始终使用 `textproto.CanonicalMIMEHeaderKey()` 函数进行规范化。这会将第一个字母以及任何连字符后的字母转换为大写，并将其余字母转换为小写。这在实践中的意义是，调用这些方法时 header 名称是不区分大小写的。

如果你需要避免这种规范化行为，可以直接编辑底层的 header 映射（它的类型为 `map[string][]string`）。例如：

```go
w.Header()["X-XSS-Protection"] = []string{"1; mode=block"}
```

**注意：** 当 header 被写入 HTTP/2 连接时，根据规范，header 名称和值将始终被转换为小写。

## 抑制系统生成的 Header

`Del()` 方法不会移除系统生成的 header。要抑制这些 header，你需要直接访问底层的 header 映射并将值设置为 `nil`。例如，如果你想抑制 `Date` header，你需要写入：

```go
w.Header()["Date"] = nil
```

## URL 查询字符串

既然谈到了路由，让我们更新 `showSnippet` 处理器，使其能够像 Stack Overflow 一样接受用户提供的 `id` 查询字符串参数：

| 方法 | 模式 | 处理器 | 动作 |
| --- | --- | --- | --- |
| ANY | `/` | `home` | 显示首页 |
| ANY | `/snippet?id=1` | `showSnippet` | 显示特定的 snippet |
| POST | `/snippet/create` | `createSnippet` | 创建新的 snippet |

稍后我们将使用这个 `id` 参数从数据库中选择特定的 snippet 并将其显示给用户。现在，我们只需读取 `id` 参数的值并将其插值占位符响应中。

为了实现此功能，我们需要更新 `showSnippet` 处理器函数来完成两件事：

1. 它需要从 URL 查询字符串中获取 `id` 参数的值，我们可以使用 `r.URL.Query().Get()` 方法来实现。这将始终为参数返回一个字符串值，如果不存在匹配的参数则返回空字符串。

2. 因为 `id` 参数是不可信的用户输入，我们应该对其进行验证，以确保它是合法的。为了我们的 Snippet 目的，我们只需要检查它是否是一个正整数。

- `pkg` 目录将包含项目中使用的辅助性非应用特定代码。我们将使用它来存放可能的可重用代码，例如验证辅助函数和项目的 SQL 数据库模型。

- `ui` 目录将包含应用程序使用的用户界面资源。具体来说，`ui/html` 目录将包含 HTML 模板，而 `ui/static` 目录将包含静态文件（如 CSS 和图像）。

我们为什么要使用这种结构呢？

有两个巨大的好处：

1. 它实现了 Go 代码与非 Go 资源之间清晰的隔离。我们编写的所有代码都将专门放在 `cmd` 和 `pkg` 目录下，留出项目根目录来存放非 Go 资源，如 UI 文件、makefile 和模块定义（包括我们的 `go.mod` 文件）。这可以使得在未来构建和部署应用程序时，管理工作变得简单。

2. 如果你想在项目中添加另一个可执行的应用程序，这种结构具有良好的扩展性。例如，你将来可能想添加一个 CLI（命令行界面）来自动执行某些管理任务。通过这种结构，你可以在 `cmd/cli` 下创建这个 CLI 应用程序，并能够导入复用你在 `pkg` 目录下编写的所有代码。

### 重构你的现有代码

让我们快速将已经编写的代码迁移到这种新结构。
