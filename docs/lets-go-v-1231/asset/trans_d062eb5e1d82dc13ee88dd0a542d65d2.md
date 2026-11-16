

仅限路径。但有一种特殊情况。

如果路由模式以通配符结尾，并且此最终通配符标识符以 ... 结尾，则该通配符将匹配请求路径中的任何和所有剩余段。

例如，如果你声明类似 "/post/{path...}" 的路由模式，它将匹配 /post/a、/post/a/b、/post/a/b/c 等请求 —— 这非常类似于子树路径模式的行为。但区别在于，你可以在处理程序中通过 r.PathValue() 方法访问整个通配符部分。在此示例中，你可以通过调用 r.PathValue("path") 来获取 {path...} 的通配符值。

## 基于方法的路由

接下来，让我们遵循 HTTP 最佳实践，限制我们的应用程序，使其仅响应带有适当 HTTP 方法的请求。

随着我们应用程序构建的推进，我们的 `home`、`snippetView` 和 `snippetCreate` 处理程序将仅检索信息并向用户显示页面，因此将这些处理程序限制为仅处理 `GET` 请求是合理的。

要将路由限制为特定 HTTP 方法，可以在声明路由模式时在其前加上所需的 HTTP 方法，如下所示：

```
File: main.go

package main

...

func main() {
	mux := http.NewServeMux()
	// Prefix the route patterns with the required HTTP method (for now, we will
	// restrict all three routes to acting on GET requests).
	mux.HandleFunc("GET /{$}", home)
	mux.HandleFunc("GET /snippet/view/{id}", snippetView)
	mux.HandleFunc("GET /snippet/create", snippetCreate)

	log.Print("starting server on :4000")

	err := http.ListenAndServe(":4000", mux)
	log.Fatal(err)
}
```

> 注意：路由模式中的 HTTP 方法区分大小写，且应始终大写，后面至少跟一个空格字符（空格和制表符均可）。每个路由模式中只能包含一个 HTTP 方法。

还值得一提的是，当你注册使用 `GET` 方法的路由模式时，它将同时匹配 `GET` 和 `HEAD` 请求。所有其他方法（如 `POST`、`PUT` 和 `DELETE`）都需要精确匹配。

让我们使用 curl 向我们的应用程序发送一些请求来测试此更改。如果你在跟随操作，首先对 `http://localhost:4000/` 发送一个常规 `GET` 请求，如下所示：

```
$ curl -i localhost:4000/
HTTP/1.1 200 OK
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 21
Content-Type: text/plain; charset=utf-8

Hello from Snippetbox
```

此处的响应看起来不错。我们可以看到路由仍然有效，并且我们得到了一个 `200 OK` 状态和一个 `Hello from Snippetbox` 响应体，与之前一样。

你也可以继续尝试对同一 URL 发出 `HEAD` 请求。你会发现这也能正常工作，仅返回 *HTTP 响应头*，没有响应体。

```
$ curl --head localhost:4000/
HTTP/1.1 200 OK
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 21
Content-Type: text/plain; charset=utf-8
```

相比之下，让我们尝试向 `http://localhost:4000/` 发出 `POST` 请求。`POST` 方法不支持此路由，因此你应该会收到类似这样的错误响应：

```
$ curl -i -d "" localhost:4000/
HTTP/1.1 405 Method Not Allowed
Allow: GET, HEAD
Content-Type: text/plain; charset=utf-8
X-Content-Type-Options: nosniff
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 19

Method Not Allowed
```

> 注意：curl 的 `-d` 标志用于声明你想要包含在请求体中的任何 HTTP `POST` 数据。在上述命令中，我们使用 `-d ""`，这意味着请求体将为空，但请求仍将使用 HTTP 方法 `POST` 发送（而不是默认方法 `GET`）。

这一切看起来非常好。我们可以看到 Go 的 servemux 已经自动为我们发送了一个 `405 Method Not Allowed` 响应，其中包含一个 `Allow` 头，列出了请求 URL *支持* 的 HTTP 方法。

## 添加仅限 POST 的路由和处理程序

我们还要向代码库中添加一个新的 `snippetCreatePost` 处理程序，稍后将用它在数据库中创建和保存新代码片段。因为创建和保存代码片段是一个非幂等操作，会更改服务器的状态，所以我们要确保此处理程序仅处理 `POST` 请求。

总而言之，我们希望第四个处理程序和路由如下所示：

| 路由模式 | 处理程序 | 动作 |
| --- | --- | --- |
| `GET /{$}` | home | 显示主页 |
| `GET /snippet/view/{id}` | snippetView | 显示特定代码片段 |
| `GET /snippet/create` | snippetCreate | 显示创建新代码片段的表单 |
| `POST /snippet/create` | snippetCreatePost | 保存新代码片段 |

让我们继续将必要代码添加到我们的 `main.go` 文件中，如下所示：

```
File: main.go

package main

...

// Add a snippetCreatePost handler function.
func snippetCreatePost(w http.ResponseWriter, r *http.Request) {
  w.Write([]byte("Save a new snippet..."))
}

func main() {
  mux := http.NewServeMux()
  mux.HandleFunc("GET /{$}", home)
  mux.HandleFunc("GET /snippet/view/{id}", snippetView)
  mux.HandleFunc("GET /snippet/create", snippetCreate)

  // Create the new route, which is restricted to POST requests only.
  mux.HandleFunc("POST /snippet/create", snippetCreatePost)

  log.Print("starting server on :4000")

  err := http.ListenAndServe(":4000", mux)
  log.Fatal(err)
}
```

请注意，声明两个（或更多）具有不同 HTTP 方法但否则具有相同模式的独立路由完全没问题，就像我们在这里对 "`GET /snippet/create`" 和 "`POST /snippet/create`" 所做的那样。

如果你重启应用程序并尝试使用 URL 路径 `/snippet/create` 发出一些请求，你现在应该会根据所使用的请求方法看到不同的响应。

```
$ curl -i localhost:4000/snippet/create
HTTP/1.1 200 OK
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 50
Content-Type: text/plain; charset=utf-8

Display a form for creating a new snippet...

$ curl -i -d "" localhost:4000/snippet/create
HTTP/1.1 200 OK
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 21
Content-Type: text/plain; charset=utf-8

Save a new snippet...

$ curl -i -X DELETE localhost:4000/snippet/create
HTTP/1.1 405 Method Not Allowed
Allow: GET, HEAD, POST
Content-Type: text/plain; charset=utf-8
X-Content-Type-Options: nosniff
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 19

Method Not Allowed
```

## 其他信息

### 方法优先级

如果由于 HTTP 方法而导致路由模式重叠，*最具体的模式优先*规则也同样适用。

重要的是要意识到，不包含方法的路由模式（例如 "/article/{id}"）将匹配 *任何方法* 的传入 HTTP 请求。相比之下，像 "POST /article/{id}" 这样的路由只会匹配具有 POST 方法的请求。因此，如果你在应用程序中声明重叠的路由 "/article/{id}" 和 "POST /article/{id}"，那么 "POST /article/{id}" 路由将优先。

### 处理程序命名

我还想强调，在 Go 中为处理程序命名没有对错之分。

在这个项目中，我们将遵循一种约定：为任何处理 POST 请求的处理程序名称加上后缀 'Post'。如下所示：

| 路由模式 | 处理程序 | 动作 |
|---|---|---|
| GET /snippet/create | snippetCreate | 显示创建新代码片段的表单 |
| POST /snippet/create | snippetCreatePost | 创建新代码片段 |

但在你自己的工作中，没有必要遵循此模式。例如，你可以改为用 'get' 和 'post' 等词作为处理程序名称的前缀，如下所示：

| 路由模式 | 处理程序 | 动作 |
|---|---|---|
| GET /snippet/create | getSnippetCreate | 显示创建新代码片段的表单 |
| POST /snippet/create | postSnippetCreate | 创建新代码片段 |

甚至可以给处理程序完全不同的名称。例如：

| 路由模式 | 处理程序 | 动作 |
|---|---|---|
| GET /snippet/create | newSnippetForm | 显示创建新代码片段的表单 |
| POST /snippet/create | createSnippet | 创建新代码片段 |

基本上，在 Go 中，你有自由为你的处理程序选择适合你且符合你思维习惯的命名约定。

## 第三方路由器

我们在过去两章中一直在使用的通配符和基于方法的路由功能在 Go 中相对较新——它直到 Go 1.22 才成为标准库的一部分。虽然这是对语言非常受欢迎的补充，也是一项重大改进，但你可能会发现，标准库的路由功能有时仍然无法提供你所需的一切。

例如，目前不支持以下内容：

- 向用户发送自定义 404 Not Found 和 405 Method Not Allowed 响应（尽管对此有一个开放的提案）。
- 在路由模式或通配符中使用正则表达式。
- 在单个路由声明中匹配多个 HTTP 方法。
- 自动支持 OPTIONS 请求。

