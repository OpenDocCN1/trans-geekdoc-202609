

```go
"strings" // New import
"sync"
"time"

"greenlight.alexedwards.net/internal/data"
"greenlight.alexedwards.net/internal/jsonlog"
"greenlight.alexedwards.net/internal/mailer"

_ "github.com/lib/pq"
)

const version = "1.0.0"

type config struct {
    port int
    env  string
    db   struct {
        dsn          string
        maxOpenConns int
        maxIdleConns int
        maxIdleTime  string
    }
    limiter struct {
        enabled bool
        rps     float64
        burst   int
    }
    smtp struct {
        host     string
        port     int
        username string
        password string
        sender   string
    }
    // Add a cors struct and trustedOrigins field with the type []string.
    cors struct {
        trustedOrigins []string
    }
}
```

```go
// We use the strings.Fields() function to split the flag
// value into a slice based on whitespace characters and assign it to our config
// struct.
// Importantly, if the -cors-trusted-origins flag is not present,
// contains the empty string, or contains only whitespace, then strings.Fields() will return
// an empty []string slice.
flag.Func("cors-trusted-origins", "Trusted CORS origins (space separated)", func(val string) error {
    cfg.cors.trustedOrigins = strings.Fields(val)
    return nil
})

flag.Parse()

...
}
```

**注意：** 如果你想了解更多关于新的 `flag.Func()` 功能以及使用它的一些方法，我在此写了一篇更详细的博客文章。

完成之后，下一步是更新我们的 `enableCORS()` 中间件。具体来说，我们希望中间件检查请求的 `Origin` 请求头的值是否与我们的受信任源之一完全匹配（区分大小写）。如果匹配，那么我们应该设置一个 `Access-Control-Allow-Origin` 响应头，该响应头会反映（或回显）请求的 `Origin` 头的值。

```go
func (app *application) enableCORS(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Add the "Vary: Origin" header.
        w.Header().Add("Vary", "Origin")

        // Get the value of the request's Origin header.
        origin := r.Header.Get("Origin")

        // Only run this if there's an Origin request header present AND at least one
        // trusted origin is configured.
        if origin != "" && len(app.config.cors.trustedOrigins) != 0 {
            // Loop through the list of trusted origins, checking to see if the request
            // origin exactly matches one of them.
            for i := range app.config.cors.trustedOrigins {
                if origin == app.config.cors.trustedOrigins[i] {
                    // If there is a match, then set an "Access-Control-Allow-Origin"
                    // response header with the request origin as the value.
                    w.Header().Set("Access-Control-Allow-Origin", origin)
                }
            }
        }

        // Call the next handler in the chain.
        next.ServeHTTP(w, r)
    })
}
```

完成这些更改后，我们现在可以再次尝试。

重启你的 API，像这样传入 http://localhost:9000 和 http://localhost:9001 作为受信任源：

相比之下，尝试使用地址 `:9002` 运行 `cmd/examples/cors/simple` 应用程序：

```bash
$ go run ./cmd/examples/cors/simple --addr=":9002"
2021/04/17 18:24:22 starting server on :9002
```

这将使网页的来源为 `http://localhost:9002` —— 它不在我们的受信任源列表中 —— 因此当你在浏览器中访问 http://localhost:9002 时，你应该会发现跨源请求被阻止。如下所示：

![](img/30f9221bfc265d52b544dd595ca099de_657_0.png)

## 附加信息

### 部分来源匹配

如果你有大量希望支持的受信任源，那么你可能会倾向于对来源进行部分匹配检查，看它是否“以”特定值“开头”或“结尾”，或是否匹配正则表达式。如果你这样做，必须格外小心，以避免任何非预期的匹配。

举个简单的例子，如果 `http://example.com` 和 `http://www.example.com` 是你的受信任源，你的第一反应可能是检查请求的 `Origin` 请求头是否以 `example.com` 结尾。这是一个糟糕的主意，因为攻击者可以注册域名 `attackerexample.com`，而来自该来源的任何请求都会通过你的检查。

这只是一个简单的例子 —— 下面的博客文章讨论了在使用部分匹配或正则表达式检查时可能出现的一些其他漏洞：

-   CORS 的安全风险
-   利用 CORS 错误配置获取比特币和赏金

通常，最好像我们在本章中所做的那样，根据完整的受信任源的显式安全名单来检查 `Origin` 请求头。

### 空源

或者，如果使用 XMLHttpRequest，则应将 `withCredentials` 属性设置为 true。例如：

```js
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com');
xhr.withCredentials = true;
xhr.send(null);
```

*请求*。此预检请求的目的是确定*真正的*跨源请求是否会被允许。

### 演示预检请求

为了帮助演示预检请求的工作原理以及我们需要如何处理它们，让我们在 `cmd/examples/cors/` 目录下创建另一个示例网页。

我们将设置这个网页，使其向我们的 `POST /v1/tokens/authentication` 端点发出请求。在调用此端点时，我们会在 JSON 请求体中包含一个电子邮件地址和密码，以及一个 `Content-Type: application/json` 请求头。由于 `Content-Type: application/json` 请求头不被允许出现在“简单”跨源请求中，因此这应该会触发对 API 的预检请求。

继续在 `cmd/examples/cors/preflight/main.go` 创建一个新文件：

```bash
$ mkdir -p cmd/examples/cors/preflight
$ touch cmd/examples/cors/preflight/main.go
```

并添加下面的代码，它遵循了我们在几章前使用的非常相似的模式。

文件：`cmd/examples/cors/preflight/main.go`

```go
package main

import (
    "flag"
    "log"
    "net/http"
)

// Define a string constant containing the HTML for the webpage. This
// consists of a <h1> header tag, and some JavaScript which calls our POST
// /v1/tokens/authentication endpoint and writes the response body to inside the <div id="output"></div> tag.
const html = `
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
</head>
<body>
    <h1>Preflight CORS</h1>
    <div id="output"></div>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            fetch("http://localhost:4000/v1/tokens/authentication", {
                method: "POST",
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    email: 'alice@example.com',
                    password: 'pa55word'
                })
            }).then(
                function (response) {
                    response.text().then(function (text) {
                        document.getElementById("output").innerHTML = text;
                    });
                },
                function(err) {
                    document.getElementById("output").innerHTML = err;
                }
            );
        });
    </script>
</body>
</html>`

func main() {
    addr := flag.String("addr", ":9000", "Server address")
    flag.Parse()

    log.Printf("starting server on %s", *addr)

    err := http.ListenAndServe(*addr, http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte(html))
    }))
    log.Fatal(err)
}
```

如果你正在跟着操作，请继续运行此应用：

```bash
$ go run ./cmd/examples/cors/preflight
2021/04/17 18:47:55 starting server on :9000
```

然后打开第二个终端窗口，同时启动我们常规的 API 应用，使用 http://localhost:9000 作为一个

