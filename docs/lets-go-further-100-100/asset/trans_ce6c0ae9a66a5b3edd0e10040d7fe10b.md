
> 并且以每秒 r 个令牌的速率重新填充。

把这个场景放到我们 API 应用的场景中……

- 我们将有一个初始包含 b 个令牌的桶。
- 每当我们收到一个 HTTP 请求，就会从桶中移除一个令牌。
- 每 1/r 秒，一个令牌会被添加回桶中——最多总共 b 个令牌。
- 如果我们收到 HTTP 请求时桶已为空，就应返回 429 Too Many Requests 响应。

实际上，这意味着我们的应用程序允许在短时间内连续最多发出 b 个 HTTP 请求（即一次“突发”），但从长期来看，它平均每秒允许 r 个请求。

为了使用 golang.org/x/time/rate 创建令牌桶速率限制器，我们需要使用 NewLimiter() 函数。它的签名如下：

```
// Note that the Limit type is an 'alias' for float64.
func NewLimiter(r Limit, b int) *Limiter
```

因此，如果我们想创建一个速率限制器，允许平均每秒 2 个请求，且单次“突发”最多 4 个请求，可以这样实现：

```
// Allow 2 requests per second, with a maximum of 4 requests in a burst.
limiter := rate.NewLimiter(2, 4)
```

## 实施全局速率限制

好了，完成了这些高层解释后，让我们直接看一些代码，看看它在实践中如何工作。

我们正在使用的中间件模式的一个好处是，可以很方便地包含“初始化”代码，这些代码只在我们用中间件包装某个东西时运行一次，而不是在中间件处理的每个请求上都运行。

```
func (app *application) exampleMiddleware(next http.Handler) http.Handler {
    // Any code here will run only once, when we wrap something with the middleware.
    
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Any code here will run for every request that the middleware handles.
        
        next.ServeHTTP(w, r)
    })
}
```

在我们的例子中，我们将创建一个新的 rateLimit() 中间件方法，在“初始化”代码中创建一个新的速率限制器，然后为它后续处理的每个请求使用这个速率限制器。

如果你正在跟着做，请打开 cmd/api/middleware.go 文件，并像这样创建中间件：

```
File: cmd/api/middleware.go

package main

import (
    "fmt"
    "net/http"

    "golang.org/x/time/rate" // New import
)

...

func (app *application) rateLimit(next http.Handler) http.Handler {
    // Initialize a new rate limiter which allows an average of 2 requests
per second,
    // with a maximum of 4 requests in a single ‘burst’.
    limiter := rate.NewLimiter(2, 4)

    // The function we are returning is a closure, which 'closes over' the
limiter
    // variable.
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Call limiter.Allow() to see if the request is permitted, and if
it's not,
        // then we call the rateLimitExceededResponse() helper to return a
429 Too Many Requests response (we will create this helper in a minute).
if !limiter.Allow() {
    app.rateLimitExceededResponse(w, r)
    return
}

next.ServeHTTP(w, r)
})
}
```

在这段代码中，每当我们调用速率限制器上的 Allow() 方法时，都会从桶中消耗恰好一个令牌。如果桶中没有剩余令牌，Allow() 将返回 false，这成为我们向客户端发送 429 Too Many Requests 响应的触发条件。

同样重要的是，Allow() 方法背后的代码受互斥锁（mutex）保护，可以安全地并发使用。

现在让我们进入 cmd/api/errors.go 文件，创建 rateLimitExceededResponse() 辅助函数。如下所示：

```
File: cmd/api/errors.go

package main

...

func (app *application) rateLimitExceededResponse(w http.ResponseWriter, r *http.Request) {
    message := "rate limit exceeded"
    app.errorResponse(w, r, http.StatusTooManyRequests, message)
}
```

最后，在 `cmd/api/routes.go` 文件中，我们要将 `rateLimit()` 中间件添加到中间件链中。它应该位于 panic 恢复中间件之后（这样 `rateLimit()` 中的任何 panic 都能被恢复），但除此之外，我们希望它尽可能早地被使用，以防止服务器做不必要的工作。

请按此更新文件：

```
File: cmd/api/routes.go

package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)

    router.HandlerFunc(http.MethodGet, "/v1/movies", app.listMoviesHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.updateMovieHandler)
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
```

## 基于 IP 的速率限制

当你希望对 API 的请求总速率实施严格限制，并且不关心请求来自哪里时，使用全局速率限制器会很有用。但通常更常见的需求是为每个客户端设置独立的速率限制器，这样一来，某个不良客户端发送过多请求不会影响其他所有客户端。

实现这一点的一个概念上很直接的方法是创建一个内存中的 *速率限制器映射表*，以每个客户端的 IP 地址作为映射的键。

每当新客户端向我们的 API 发出请求时，我们都会初始化一个新的速率限制器并将其添加到映射中。对于后续请求，我们将从映射中取出该客户端的速率限制器，并通过调用其 `Allow()` 方法来检查请求是否被允许，就像我们之前做的那样。

由于可能会有多个 goroutine 并发访问该映射，我们需要使用互斥锁来保护对映射的访问，以防止竞态条件。

如果你正在跟着做，让我们直接看代码，更新我们的 `rateLimit()` 中间件来实现这一点。

```
File: cmd/api/middleware.go
```

```
package main

import (
    "fmt"
    "net" // New import
    "net/http"
    "sync" // New import

    "golang.org/x/time/rate"
)

...

func (app *application) rateLimit(next http.Handler) http.Handler {
    // Declare a mutex and a map to hold the clients' IP addresses and rate limiters.
    var (
        mu      sync.Mutex
        clients = make(map[string]*rate.Limiter)
    )

    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Extract the client's IP address from the request.
        ip, _, err := net.SplitHostPort(r.RemoteAddr)
        if err != nil {
            app.serverErrorResponse(w, r, err)
            return
        }

        // Lock the mutex to prevent this code from being executed concurrently.
        mu.Lock()

        // Check to see if the IP address already exists in the map. If it doesn't, then
            // initialize a new rate limiter and add the IP address and limiter to the map.
        if _, found := clients[ip]; !found {
            clients[ip] = rate.NewLimiter(2, 4)
        }

        // Call the Allow() method on the rate limiter for the current IP address. If
        // the request isn't allowed, unlock the mutex and send a 429 Too Many Requests
        // response, just like before.
        if !clients[ip].Allow() {
            mu.Unlock()
            app.rateLimitExceededResponse(w, r)
            return
        }

        // Very importantly, unlock the mutex before calling the next handler in the
        // chain. Notice that we DON'T use defer to unlock the mutex, as that would mean
        // that the mutex isn't unlocked until all the handlers downstream of this
        // middleware have also returned.
        mu.Unlock()

        next.ServeHTTP(w, r)
    })
}
```

## 删除旧的限制器

上面的代码可以工作，但有一个小问题——`clients` 映射会无限增长，随着我们每添加一个新的 IP 地址和速率限制器，它会占用越来越多的资源。

