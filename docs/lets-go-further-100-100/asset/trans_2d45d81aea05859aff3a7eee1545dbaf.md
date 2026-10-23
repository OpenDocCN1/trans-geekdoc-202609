
```json
],
"version": 1,
"runtime": "102 mins"
}
```

从技术角度来看，这并不重要，因为 JSON RFC 指出，JSON 对象是零个或多个名称/值对的*无序*集合。但从美学或用户界面的角度来看，它可能仍会令人不满意；或者，如果你为了向后兼容而需要保持精确的字段顺序，它可能会带来问题。

## 发送错误消息

目前，我们的 API 对于成功的请求会发送格式良好的 JSON 响应，但如果客户端发出了错误的请求——或者我们的应用程序中出现了问题——我们仍然会通过 `http.Error()` 和 `http.NotFound()` 函数向客户端发送纯文本错误消息。

在本章中，我们将通过创建一些额外的辅助函数来管理错误并向客户端发送相应的 JSON 响应，从而解决这个问题。

如果你在跟着操作，请创建一个新的 `cmd/api/errors.go` 文件：

```bash
$ touch cmd/api/errors.go
```

然后像这样添加一些辅助方法：

```go
File: cmd/api/errors.go

package main

import (
    "fmt"
    "net/http"
)

// The logError() method is a generic helper for logging an error message.
// Later in the book we'll upgrade this to use structured logging, and record additional
// information about the request including the HTTP method and URL.
func (app *application) logError(r *http.Request, err error) {
    app.logger.Println(err)
}

// The errorResponse() method is a generic helper for sending JSON-formatted error
// messages to the client with a given status code. Note that we're using an interface{}
// type for the message parameter, rather than just a string type, as this gives us
// more flexibility over the values that we can include in the response.
func (app *application) errorResponse(w http.ResponseWriter, r *http.Request,
status int, message interface{}) {
    env := envelope{"error": message}

    // Write the response using the writeJSON() helper. If this happens to return an
    // error then log it, and fall back to sending the client an empty response with a
    // 500 Internal Server Error status code.
    err := app.writeJSON(w, status, env, nil)
    if err != nil {
        app.logError(r, err)
        w.WriteHeader(500)
    }
}

// The serverErrorResponse() method will be used when our application encounters an
// unexpected problem at runtime. It logs the detailed error message, then uses the
// errorResponse() helper to send a 500 Internal Server Error status code and JSON
// response (containing a generic error message) to the client.
func (app *application) serverErrorResponse(w http.ResponseWriter, r *http.Request, err error) {
    app.logError(r, err)

    message := "the server encountered a problem and could not process your request"
    app.errorResponse(w, r, http.StatusInternalServerError, message)
}

// The notFoundResponse() method will be used to send a 404 Not Found status code and
// JSON response to the client.
func (app *application) notFoundResponse(w http.ResponseWriter, r *http.Request) {
    message := "the requested resource could not be found"
    app.errorResponse(w, r, http.StatusNotFound, message)
}

// The methodNotAllowedResponse() method will be used to send a 405 Method Not Allowed
// status code and JSON response to the client.
func (app *application) methodNotAllowedResponse(w http.ResponseWriter, r *http.Request) {
    message := fmt.Sprintf("the %s method is not supported for this resource", r.Method)
    app.errorResponse(w, r, http.StatusMethodNotAllowed, message)
}
```

现在这些辅助函数已经就绪，让我们更新 API 处理器，用这些新的辅助函数替代 `http.Error()` 和 `http.NotFound()` 函数。如下所示：

```go
File: cmd/api/healthcheck.go

package main

...

func (app *application) healthcheckHandler(w http.ResponseWriter, r *http.Request) {
    env := envelope{
        "status": "available",
        "system_info": map[string]string{
            "environment": app.config.env,
            "version":     version,
        },
    }

    err := app.writeJSON(w, http.StatusOK, env, nil)
    if err != nil {
        // Use the new serverErrorResponse() helper.
        app.serverErrorResponse(w, r, err)
    }
}
```

```go
File: cmd/api/movies.go

package main

...

func (app *application) showMovieHandler(w http.ResponseWriter, r *http.Request) {
    id, err := app.readIDParam(r)
    if err != nil {
        // Use the new notFoundResponse() helper.
        app.notFoundResponse(w, r)
        return
    }

    movie := data.Movie{
        ID:          id,
        CreatedAt: time.Now(),
        Title:       "Casablanca",
        Runtime:     102,
        Genres:      []string{"drama", "romance", "war"},
        Version:     1,
    }

    err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
    if err != nil {
        // Use the new serverErrorResponse() helper.
        app.serverErrorResponse(w, r, err)
    }
}
```

## 路由错误

我们自己的 API 处理器发送的任何错误消息现在都将成为格式良好的 JSON 响应。这很棒！

但是，当 httprouter 找不到匹配的路由时，它会自动发送的错误消息呢？默认情况下，这些仍然会是我们在本书前面看到的那种纯文本（非 JSON）响应。

幸运的是，httprouter 允许我们在初始化路由器时设置自己的自定义错误处理器。这些自定义处理器必须满足 http.Handler 接口，这对我们来说是个好消息，因为这意味着我们可以轻松地重用刚刚创建的 `notFoundResponse()` 和 `methodNotAllowedResponse()` 辅助函数。

打开 `cmd/api/routes.go` 文件，并按如下方式配置 `httprouter` 实例：

```go
File: cmd/api/routes.go

package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

    // Convert the notFoundResponse() helper to a http.Handler using the
    // http.HandlerFunc() adapter, and then set it as the custom error handler for 404
    // Not Found responses.
    router.NotFound = http.HandlerFunc(app.notFoundResponse)

    // Likewise, convert the methodNotAllowedResponse() helper to a http.Handler and set
    // it as the custom error handler for 405 Method Not Allowed responses.
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
    app.healthcheckHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
    app.showMovieHandler)

    return router
}
```

让我们测试这些更改。重新启动应用程序，然后尝试对一些不存在的端点或使用不支持的 HTTP 方法的端点发出请求。你现在应该会收到一些漂亮的 JSON 错误响应，类似于下面这些：

```
$ curl -i localhost:4000/foo
HTTP/1.1 404 Not Found
Content-Type: application/json
Date: Tue, 06 Apr 2021 15:13:42 GMT
Content-Length: 58

{
  "error": "the requested resource could not be found"
}

$ curl -i localhost:4000/v1/movies/abc
HTTP/1.1 404 Not Found
Content-Type: application/json
Date: Tue, 06 Apr 2021 15:14:01 GMT
Content-Length: 58

{
  "error": "the requested resource could not be found"
}

$ curl -i -X PUT localhost:4000/v1/healthcheck
HTTP/1.1 405 Method Not Allowed
Allow: GET, OPTIONS
Content-Type: application/json
Date: Tue, 06 Apr 2021 15:14:21 GMT
Content-Length: 66

{
  "error": "the PUT method is not supported for this resource"
}
```

在这个最后的示例中，请注意，`httprouter` 仍然会自动为我们设置正确的 `Allow` 响应头，即使它现在使用我们的自定义错误处理器来生成响应？

## 补充信息

### 系统生成的错误响应

既然我们在讨论错误，我想提一下，在某些情况下，Go 的 `http.Server` 仍然可能会自动生成并发送纯文本 HTTP 响应。这些场景包括：

- HTTP 请求指定了不受支持的 HTTP 协议版本。
- HTTP 请求包含缺失或无效的 `Host` 头，或者包含多个 `Host` 头。
- HTTP 请求包含无效的头部名称或值。
- HTTP 请求包含不受支持的 `Transfer-Encoding` 头。
- HTTP 请求头的大小超过了服务器的 `MaxHeaderBytes` 设置。
- 客户端向 HTTPS 服务器发出了 HTTP 请求。
