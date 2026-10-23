
```
| | |_ mail
| |_ julienschmidt
| | |_ httprouter
| |_ lib
| | |_ pq
|_ golang.org
| |_ x
| | |_ crypto
| | |_ time
|_ gopkg.in
| |_ alexcesaro
| | |_ quotedprintable.v3
|_ modules.txt
```

现在，当你运行诸如 `go run`、`go test` 或 `go build` 这样的命令时，`go` 工具会识别到 `vendor` 文件夹的存在，并且 *vendor 文件夹中的依赖代码* 将被使用——而不是你本地机器上模块缓存中的代码。

如果愿意，请继续尝试运行 API 应用。你会发现一切都能编译，并且像之前一样继续正常工作。

```
$ make run/api
go run ./cmd/api -db-dsn=postgres://greenlight:pa55word@localhost/greenlight
{"level":"INFO","time":"2021-04-18T13:18:29Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T13:18:29Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

> > **注意：** 如果你想确认确实是使用了 vendored 依赖，可以运行 `go clean -modcache` 来从本地模块缓存中删除 *所有内容*。再次运行 API 时，你会发现它仍然能正确启动，*无需* 从 Go 模块镜像重新获取依赖。

因为所有依赖的源代码现在都存储在你的项目仓库本身中，所以很容易将其与代码的其余部分一起提交到 Git（或替代的版本控制系统）。这令人安心，因为它让你对构建和运行应用程序所使用的 *所有代码* 拥有 *完全所有权*，并置于版本控制之下。

当然，这样的缺点是它会增加项目仓库的大小和臃肿。对于依赖很多且仓库会被克隆 *很多次* 的项目来说尤其令人担忧，例如 CI/CD 系统在每次新提交时都会克隆仓库的项目。

我们也来快速查看一下创建的 `vendor/modules.txt` 文件。如果你一直跟着做，它应该看起来类似这样：

```
File: vendor/modules.txt

# github.com/felixge/httpsnoop v1.0.1
## explicit
github.com/felixge/httpsnoop
# github.com/go-mail/mail/v2 v2.3.0
## explicit
github.com/go-mail/mail/v2
# github.com/julienschmidt/httprouter v1.3.0
## explicit
github.com/julienschmidt/httprouter
# github.com/lib/pq v1.10.0
## explicit
github.com/lib/pq
github.com/lib/pq/oid
github.com/lib/pq/scram
# golang.org/x/crypto v0.0.0-20210322153248-0c34fe9e7dc2
## explicit
golang.org/x/crypto/bcrypt
golang.org/x/crypto/blowfish
# golang.org/x/time v0.0.0-20210220033141-f8bda1e9f3ba
## explicit
golang.org/x/time/rate
# gopkg.in/alexcesaro/quotedprintable.v3 v3.0.0-20150716171945-2caba252f4dc
## explicit
gopkg.in/alexcesaro/quotedprintable.v3
# gopkg.in/mail.v2 v2.3.1
## explicit
```

这个 `vendor/modules.txt` 文件本质上是 vendored 包及其版本号的 *清单*。当使用 vendoring 时，`go` 工具会检查 `modules.txt` 中的模块版本号是否与 `go.mod` 文件中的版本号一致。如果有任何不一致，`go` 工具将报告错误。

> **注意：** 必须指出，没有简单的方法来验证 *vendored 依赖的校验和* 是否与 `go.sum` 文件中的校验和匹配。换句话说，没有
> 等同于 `go mod verify` 且可 *直接* 对 `vendor` 文件夹内容进行操作的命令。
> 
> 为缓解此问题，定期同时运行 *两者* `go mod verify` 和 `go mod vendor` 是个好主意。使用 `go mod verify` 会验证模块缓存中的依赖是否与 `go.sum` 文件匹配，而 `go mod vendor` 会将这些相同的依赖从模块缓存复制到你的 `vendor` 文件夹中。这就是为什么我们的 `make vendor` 规则被设置为运行这两个命令，以及为什么我们还将其作为 `make audit` 规则的先决条件的原因。

最后，你应避免对 `vendor` 目录中的代码做任何修改。这样做可能会导致混淆（因为代码将不再与源代码的原始版本一致），而且——除此之外——每次运行 `go mod vendor` 时都会覆盖你所做的任何更改。如果你需要更改依赖的代码，最好是 fork 它并导入 forked 版本。

## Vendoring 新依赖

在本书的下一节中，我们将使用 Caddy 作为反向代理部署我们的 API 应用到互联网上。这意味着就我们的 API 而言，它收到的所有请求都将来自单个 IP 地址（运行 Caddy 实例的那台）。这反过来会导致我们的基于 IP 地址限制访问的速率限制中间件出现问题。

幸运的是，像大多数其他反向代理一样，Caddy 会为每个请求添加一个 `X-Forwarded-For` 头。该头将包含客户端的 *真实 IP 地址*。

虽然我们可以自己编写逻辑来检查 `X-Forwarded-For` 头是否存在并处理它，但我建议使用 `realip` 包来帮助完成此操作。该包会从任何 `X-Forwarded-For` 或 `X-Real-IP` 头中检索客户端 IP 地址，如果两者都不存在，则回退使用 `r.RemoteAddr`。

如果你在跟着做，请继续使用 `go get` 命令安装最新版本的 `realip`：

```
$ go get github.com/tomasen/realip@latest
go: downloading github.com/tomasen/realip v0.0.0-20180522021738-f0c99a92ddce
go get: added github.com/tomasen/realip v0.0.0-20180522021738-f0c99a92ddce
```

然后打开 `cmd/api/middleware.go` 文件并像这样更新 `rateLimit()` 中间件以使用此包：

```
File: cmd/api/middleware.go

package main

import (
    "errors"
    "expvar"
    "fmt"
"net/http"
"strconv"
"strings"
"sync"
"time"

"greenlight.alexedwards.net/internal/data"
"greenlight.alexedwards.net/internal/validator"

"github.com/felixge/httpsnoop"
"github.com/tomasen/realip" // New import
"golang.org/x/time/rate"
)

...

func (app *application) rateLimit(next http.Handler) http.Handler {

    ...

    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        if app.config.limiter.enabled {
            // Use the realip.FromRequest() function to get the client's real IP address.
            ip := realip.FromRequest(r)

            mu.Lock()

            if _, found := clients[ip]; !found {
                clients[ip] = &client{
                    limiter:
                    rate.NewLimiter(rate.Limit(app.config.limiter.rps),
                    app.config.limiter.burst),
                }
            }

            clients[ip].lastSeen = time.Now()

            if !clients[ip].limiter.Allow() {
    mu.Unlock()
    app.rateLimitExceededResponse(w, r)
    return
  }

    mu.Unlock()
  }

    next.ServeHTTP(w, r)
  })
}
...
```

如果你现在再次尝试运行 API 应用，你应该会收到类似这样的错误信息：

```
$ make run/api

go: inconsistent vendoring in /home/alex/Projects/greenlight:
    github.com/tomasen/realip@v0.0.0-20180522021738-f0c99a92ddce: is
explicitly
    required in go.mod, but not marked as explicit in
vendor/modules.txt

    To ignore the vendor directory, use -mod=readonly or -mod=mod.
    To sync the vendor directory, run:
        go mod vendor
make: *** [Makefile:24: run/api] Error 1
```

本质上发生的情况是 Go 在我们的 vendor 目录中查找 github.com/tomasen/realip 包，但目前该包并不存在于其中。

为了解决这个问题，你需要手动运行 `make vendor` 或 `make audit` 命令，如下所示：

```
$ make vendor
Tidying and verifying module dependencies...
go mod tidy
go: finding module for package github.com/tomasen/realip
go: downloading github.com/tomasen/realip v0.0.0-20180522021738-f0c99a92ddce
go: found github.com/tomasen/realip in github.com/tomasen/realip v0.0.0-20180522021738-f0c99a92ddce
go mod verify
all modules verified
Vendoring dependencies...
go mod vendor
```

完成之后，一切应该又能正常工作了：

```
$ make run/api
go run ./cmd/api -db-dsn=postgres://greenlight:pa55word@localhost/greenlight
{"level":"INFO","time":"2021-04-18T13:33:33Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T13:33:33Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

## 附加信息

