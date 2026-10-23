
![](img/30f9221bfc265d52b544dd595ca099de_28_0.png)

状态: 可用
环境: 开发
版本: 1.0.0

或者，你可以使用 curl 从终端发出请求：

```
$ curl -i localhost:4000/v1/healthcheck
HTTP/1.1 200 OK
Date: Mon, 05 Apr 2021 17:46:14 GMT
Content-Length: 58
Content-Type: text/plain; charset=utf-8

status: available
environment: development
version: 1.0.0
```

- 1. 通过为所有 URL 前缀添加你的 API 版本，例如 `/v1/healthcheck` 或 `/v2/healthcheck`。
- 2. 通过在请求和响应中使用自定义 Accept 和 Content-Type 头来传达 API 版本，例如 `Accept: application/vnd.greenlight-v1`。

从 HTTP 语义的角度来看，使用头来传达 API 版本是更“纯粹” 的方法。但从用户体验的角度来看，使用 URL 前缀可以说更好。它使开发人员能够一目了然地看到使用的是哪个版本的 API，并且还意味着 API 仍可使用普通 Web 浏览器进行探索（如果需要自定义头则更困难）。

在整本书中，我们将通过为所有 URL 路径添加 `/v1/` 前缀来对 API 进行版本控制——就像本章中对 `/v1/healthcheck` 端点所做的那样。

## API 端点和 RESTful 路由

在本书接下来的几个部分中，我们将逐步构建我们的 API，使其端点看起来像这样：

| 方法 | URL 模式 | 处理器 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用程序信息 |
| GET | /v1/movies | listMoviesHandler | 显示所有电影的详细信息 |
| POST | /v1/movies | createMovieHandler | 创建新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |
| PUT | /v1/movies/:id | editMovieHandler | 更新特定电影的详细信息 |
| DELETE | /v1/movies/:id | deleteMovieHandler | 删除特定电影 |

如果你之前构建过使用 REST 风格端点的 API，那么上面的表格可能对你来说非常熟悉，不需要太多解释。但如果你是新手，那么有几件重要的事情需要指出。

首先，具有相同 URL 模式的请求将根据 *HTTP 请求方法* 路由到 *不同的处理器*。出于安全性和语义正确性的考虑，使用适当的 HTTP 方法对于处理器执行的操作非常重要。

总结：

| 方法 | 用法 |
|---|---|
| GET | 用于仅检索信息且不更改应用程序或任何数据的状态的操作。 |
| POST | 用于修改状态的 *非幂等* 操作。在 REST API 的上下文中，`POST` 通常用于 *创建* 新资源的操作。 |
| PUT | 用于修改特定 URL 处资源状态的 *幂等* 操作。在 REST API 的上下文中，`PUT` 通常用于 *替换* 或 *更新* 现有资源的操作。 |
| PATCH | 用于 *部分更新* 特定 URL 处资源的操作。该操作可以是幂等也可以是非幂等的。 |
| DELETE | 用于 *删除* 特定 URL 处资源的操作。 |

另一件重要的事情是，我们的 API 端点将使用干净的 URL，并在 URL 路径中插值参数。例如——要检索特定电影的详细信息，客户端将发出类似 `GET /v1/movies/1` 的请求，而不是像 `GET /v1/movies?id=1` 这样在查询字符串参数中附加电影 ID。

## 选择路由器

当你在 Go 中构建具有此类端点的 API 时，你会遇到的第一个障碍之一是 `http.ServeMux`——Go 标准库中的路由器——在功能方面相当有限。特别是它不允许你根据请求方法（`GET`、`POST` 等）将请求路由到不同的处理器，也不提供对带有插值参数的干净 URL 的支持。

虽然你可以绕过这些限制，或实现自己的路由器，但通常使用众多可用的第三方路由器之一会更容易。

在本章中，我们将把流行的 `httprouter` 包集成到我们的应用程序中。最重要的是，`httprouter` 稳定、经过充分测试并提供了我们需要的功能——作为奖励，它还非常快，这得益于其使用基数树进行 URL 匹配。如果你正在构建供公众使用的 REST API，那么 `httprouter` 是一个可靠的选择。

如果你跟随本书一起编码，请使用 `go get` 下载 `httprouter` 的 `v1.3.0` 版本，如下所示：

```
$ go get github.com/julienschmidt/httprouter@v1.3.0
go: downloading github.com/julienschmidt/httprouter v1.3.0
go get: added github.com/julienschmidt/httprouter v1.3.0
```

> **注意：** 如果你机器上已有来自另一个项目的 `httprouter v1.3.0` 副本，那么将使用现有副本，你将看不到 `go: downloading...` 消息。

为了演示 `httprouter` 的工作原理，我们将首先向代码库中添加用于 *创建新电影* 和 *显示特定电影的详细信息* 的两个端点。到本章结束时，我们的 API 端点将如下所示：

| 方法 | URL 模式 | 处理器 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用程序信息 |
| POST | /v1/movies | createMovieHandler | 创建新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |

## 封装 API 路由

为了防止 API 增长时我们的 `main()` 函数变得杂乱，让我们将所有路由规则封装到新的 `cmd/api/routes.go` 文件中。

如果你跟随操作，请创建此新文件并添加以下代码：

```
$ touch cmd/api/routes.go
```

文件：cmd/api/routes.go

```
package main

import (
    "net/http"

    "github.com/julienschmidt/httprouter"
)

func (app *application) routes() *httprouter.Router {
    // Initialize a new httprouter router instance.
    router := httprouter.New()

    // Register the relevant methods, URL patterns and handler functions for our
    // endpoints using the HandlerFunc() method. Note that http.MethodGet and
    // http.MethodPost are constants which equate to the strings "GET" and
    // "POST" respectively.
    router.HandlerFunc(http.MethodGet, "/v1/healthcheck", app.healthcheckHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id", app.showMovieHandler)

    // Return the httprouter instance.
    return router
}
```

```
$ touch cmd/api/movies.go
```

然后添加以下代码：

文件：cmd/api/movies.go

```
package main

import (
    "fmt"
    "net/http"
    "strconv"

    "github.com/julienschmidt/httprouter"
)

// Add a createMovieHandler for the "POST /v1/movies" endpoint. For now we simply
// return a plain-text placeholder response.
func (app *application) createMovieHandler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintln(w, "create a new movie")
}

// Add a showMovieHandler for the "GET /v1/movies/:id" endpoint. For now, we retrieve
// the interpolated "id" parameter from the current URL and include it in a placeholder
// response.
func (app *application) showMovieHandler(w http.ResponseWriter, r *http.Request) {
    // When httprouter is parsing a request, any interpolated URL parameters
    // will be stored in the request context. We can use the ParamsFromContext() function to
    // retrieve a slice containing these parameter names and values.
    params := httprouter.ParamsFromContext(r.Context())

    // We can then use the ByName() method to get the value of the "id" parameter from
    // the slice. In our project all movies will have a unique positive integer ID, but
    // the value returned by ByName() is always a string. So we try to convert it to a
    // base 10 integer (with a bit size of 64). If the parameter couldn't be converted,
    // or is less than 1, we know the ID is invalid so we use the http.NotFound()
    // function to return a 404 Not Found response.
    id, err := strconv.ParseInt(params.ByName("id"), 10, 64)
    if err != nil || id < 1 {
        http.NotFound(w, r)
        return
    }

    // Otherwise, interpolate the movie ID in a placeholder response.
    fmt.Fprintf(w, "show the details of movie %d\n", id)
}
```

到此，我们现在准备好尝试了！

继续重启 API 应用程序…

```
$ go run ./cmd/api
2021/04/06 08:57:25 starting development server on :4000
```
