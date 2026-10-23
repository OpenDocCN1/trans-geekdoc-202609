
```go
func main() {
    // Make the server address configurable at runtime via a command-line flag.
    addr := flag.String("addr", ":9000", "Server address")
    flag.Parse()

    log.Printf("starting server on %s", *addr)

    // Start a HTTP server listening on the given address, which responds to all
    // requests with the webpage HTML above.
    err := http.ListenAndServe(*addr, http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte(html))
    }))
    log.Fatal(err)
}
```

这里的 Go 代码应该已经很熟悉了，但让我们更仔细地看看 <script> 标签中的 JavaScript 代码，并解释它的作用。

```html
<script>
    document.addEventListener('DOMContentLoaded', function() {
        fetch("http://localhost:4000/v1/healthcheck").then(
            function (response) {
                response.text().then(function (text) {
                    document.getElementById("output").innerHTML = text;
                });
            },
            function(err) {
                document.getElementById("output").innerHTML = err;
            }
        )
    }
```

> **Note:** 我解释了以上内容因为它很有趣，但本书并不是关于 JavaScript 的，你也不必担心这里的细节。你需要知道的是 *JavaScript 会向我们的 API 的 healthcheck 端点发起一个 HTTP 请求，然后将响应输出到* `<div id="output"></div>` *元素中。*

## 演示

好的，让我们试试。继续启动新的应用程序：

```
$ go run ./cmd/examples/cors/simple
2021/04/17 17:23:14 starting server on :9000
```

然后打开第二个终端窗口，同时启动我们的常规 API 应用程序：

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-17T15:23:34Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-17T15:23:34Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

你可能还想在开发者工具中打开网络活动标签，检查与被阻止请求相关的 HTTP 头。

![](img/30f9221bfc265d52b544dd595ca099de_642_0.png)

这里有几件重要的事情需要指出。

第一点是，这些头部信息表明请求已发送到我们的 API，API 处理了请求并向 Web 浏览器返回了成功的 200 OK 响应，其中包含我们所有的标准响应头。重申一下：请求本身并未被同源策略阻止——只是浏览器不允许 JavaScript 查看响应。

第二点是，Web 浏览器会在请求上自动设置一个 `Origin` 头，以显示请求来自何处（上图中红色箭头标出）。你会看到该头部如下所示：

```
Origin: http://localhost:9000
```

我们将在下一章中使用此头部，帮助我们根据是否信任请求的来源，有选择地放宽同源策略。

最后，重要的是要强调，同源策略是 *仅适用于 Web 浏览器* 的东西。

在 Web 浏览器之外，任何人都可以从任何地方使用 `curl`、`wget` 或其他任何方式向我们的 API 发起请求并读取响应。这完全不受同源策略的影响，也不会因此改变。

```go
func (app *application) enableCORS(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Header().Set("Access-Control-Allow-Origin", "*")

        next.ServeHTTP(w, r)
    })
}
```

然后更新你的 `cmd/api/routes.go` 文件，使此中间件应用于所有应用程序路由。如下所示：

```
File: cmd/api/routes.go

```go
package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)

    router.HandlerFunc(http.MethodGet, "/v1/movies",
app.requirePermission("movies:read", app.listMoviesHandler))
    router.HandlerFunc(http.MethodPost, "/v1/movies",
app.requirePermission("movies:write", app.createMovieHandler))
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
app.requirePermission("movies:read", app.showMovieHandler))
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.requirePermission("movies:write", app.updateMovieHandler))
}
```
```

```go
router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.requirePermission("movies:write", app.deleteMovieHandler))

router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication",
app.createAuthenticationTokenHandler)

// Add the enableCORS() middleware.
return
app.recoverPanic(app.enableCORS(app.rateLimit(app.authenticate(router))))
}
```
```

这里重要的是要指出，`enableCORS()` 中间件是有意放置在中间件链的早期。

例如，如果我们将其放置在速率限制器之后，任何超过速率限制的跨源请求都 *不会设置* `Access-Control-Allow-Origin` *头部*。这意味着它们会因同源策略而被客户端的 Web 浏览器阻止，而不是客户端像应有的那样收到 `429 Too Many Requests` 响应。

好的，让我们试试。

重新启动 API 应用程序，然后再次在浏览器中访问 `http://localhost:9000`。这次跨源请求应该能成功完成，你应该能在网页上看到来自我们 healthcheck 处理程序的 JSON。如下所示：

![](img/30f9221bfc265d52b544dd595ca099de_647_0.png)

我还建议你再次快速查看与 JavaScript `fetch()` 请求相关的请求和响应头。你应该会看到响应上已设置了 `Access-Control-Allow-Origin: *` 头部，类似于这样：

![](img/30f9221bfc265d52b544dd595ca099de_648_0.png)

## 限制来源

使用通配符允许跨源请求，就像我们在上面的代码中所做的那样，在某些情况下可能很有用（例如当你有一个完全公开的 API 且没有访问控制检查时）。但更常见的是，你可能希望将 CORS 限制为更小的 *受信任来源* 集合。

为此，你需要在 `Access-Control-Allow-Origin` 头部中明确包含受信任的来源，而不是使用通配符。例如，如果你只想允许来自来源 `https://www.example.com` 的 CORS，你可以在响应中发送以下头部：

```
Access-Control-Allow-Origin: https://www.example.com
```

如果只有一个固定的来源需要允许请求，那么这样做相当简单——你只需更新 `enableCORS()` 中间件，将必要的来源值硬编码进去即可。

但如果需要支持多个受信任来源，或希望该值在运行时可配置，那么事情就会变得复杂一些。

其中一个问题是——实际上——你只能在 `Access-Control-Allow-Origin` 头部中指定 *恰好一个来源*。你不能像预期那样包含用空格或逗号分隔的多个来源值的列表。

为了规避这一限制，你需要更新 `enableCORS()` 中间件，检查 `Origin` 头部的值是否匹配你的受信任来源之一。如果匹配，你可以将该值反射（或 *回显*）回 `Access-Control-Allow-Origin` 响应头部中。

> **Note:** Web Origin 规范确实允许在 `Access-Control-Allow-Origin` 头部中使用多个 *空格分隔* 的值，但不幸的是，没有任何 Web 浏览器实际支持这一点。

