# 继续前行 1.0.0 1.0.0






![](img/30f9221bfc265d52b544dd595ca099de_1_0.png)











| 方法 | URL 模式 | 操作 |
|---|---|---|
| POST | /v1/tokens/authentication | 生成新的身份验证令牌 |
| POST | /v1/tokens/password-reset | 生成新的密码重置令牌 |
| GET | /debug/vars | 显示应用指标 |

为了让你了解 API 从客户端视角会是什么样，到本书结束时，GET /v1/movies/:id 端点将返回类似如下的响应：

```
$ curl -H "Authorization: Bearer RIDBIAE3AMMK57T61AEBUGA7ZQ"
localhost:4000/v1/movies/1
{
    "movie": {
        "id": 1,
        "title": "Moana",
        "year": 2016,
        "runtime": "107 mins",
        "genres": [
            "animation",
            "adventure"
        ],
        "version": 1
    }
}
```

在幕后，我们将使用 PostgreSQL 作为数据库来持久存储所有数据。本书结束时，我们将把完成的 API 部署到运行在 Digital Ocean 上的 Linux 服务器。

## 约定

在本书中，代码块以银色背景显示，如下面的片段所示。如果代码块特别长，不相关的部分可能会被省略号替换。为了便于跟进，大多数代码块顶部还有一个标题栏，指示我们正在处理的文件名称。

```
File: hello.go

package main

... // Indicates that some existing code has been omitted.

func sayHello() {
    fmt.Println("Hello world!")
}
```

终端（命令行）说明以黑色背景显示，通常以美元符号开头。这些命令应可在任何基于 Unix 的操作系统上运行，包括 macOS 和 Linux。示例输出以银色显示在命令下方，如下所示：

```
$ echo "Hello world!"
Hello world!
```

如果你使用 Windows，应将这些命令替换为 DOS 等效命令，或通过正常的 Windows GUI 执行操作。

本书中的一些章节以 *附加信息* 部分结尾。这些部分包含与我们的应用构建无关的信息，但仍然很重要（有时只是有趣）需要了解。

## 关于作者

嗨，我是 Alex Edwards，一名全栈 Web 开发者和作者。我从 2013 年开始使用 Go，并几乎在同一时间开始教授他人并撰写有关该语言的内容。

我使用 Go 构建了各种生产应用，从简单的网站到高频交易系统。我还维护多个开源 Go 包，包括流行的会话管理系统 SCS。

我住在奥地利因斯布鲁克附近。你可以在 GitHub、Instagram、Twitter 和我的博客上关注我。






## 先决条件

### 背景知识

本书是 *让我们开始* 的后续作品，我们将在此再次利用该书中的大量信息和代码模式。

如果你已经阅读并喜欢 *让我们开始*，那么本书应该很适合你，也是你学习中的理想下一步。如果你还没有，我强烈建议先从 *让我们开始* 开始——尤其是如果你是 Go 的新手。

你可以将其作为独立书籍阅读，但请注意它有些高级——它不会详细解释基础知识，一些主题（如测试）完全没有涉及，因为它们在前一本书中已大量涵盖。但如果你对使用 Go 很熟悉，并且已有相当的经验，那么本书也可能很适合你。请随意直接开始。

### Go 1.16

本书中的信息适用于 Go 的最新主要版本（版本 1.16），如果你想跟随应用构建一起编码，建议安装此版本。

如果你已安装 Go，可以通过在终端中使用 `go version` 命令来检查版本号。输出应类似于以下内容：

```
$ go version
go version go1.16 linux/amd64
```

如果你需要升级 Go 版本，请现在进行升级。适用于你操作系统的说明可以在这里找到。

### 其他软件

如果你想完全跟进，有几项软件你应确保在计算机上可用。它们是：

- 用于从终端处理 HTTP 请求和响应的 `curl` 工具。在 MacOS 和 Linux 机器上它应已预装或可在软件仓库中获取。否则，你可以从这里下载最新版本。
- 用于执行基本负载测试的 `hey` 工具。如果你的计算机上安装了 Go 1.16，你可以使用 `go install` 命令安装 hey：

```
$ go install github.com/rakyll/hey@latest
```




- git版本控制系统。所有操作系统的安装说明均可在此处找到。
- 一个带有良好开发者工具的网页浏览器。本书将使用Firefox，但Chromium、Chrome或Microsoft Edge也可以。
- 你喜欢的文本编辑器 😊

此时，你会看到项目目录的根目录下创建了一个`go.mod`文件。如果你打开它，内容应类似于这样：

```
File: go.mod

module greenlight.alexedwards.net

go 1.16
```

我们在第一本*Let’s Go*书中详细讨论了模块，但作为快速回顾，我们在这里重温一下要点。

- 当你的项目目录根目录存在有效的`go.mod`文件时，你的项目*就是一个模块*。
- 当你在项目目录内工作并通过`go get`下载依赖时，依赖的确切版本将被记录在`go.mod`文件中。由于确切版本已知，这使得在不同机器和环境中确保可复现构建变得更加容易。
- 当你运行或构建项目中的代码时，Go将使用`go.mod`文件中列出的确切依赖。如果本地机器上还没有必要的依赖，Go将自动为你下载它们——同时也会下载任何递归依赖。
- `go.mod`文件还定义了*模块路径*（在我的例子中是`greenlight.alexedwards.net`）。这本质上是用作项目中包的*根导入路径*的标识符。
- 一个好的实践是使模块路径对你和你的项目是唯一的。Go社区的一个常见约定是将其基于你拥有的URL。

**提示：**如果你对模块的任何方面或其工作原理感到不确定，官方Go Modules Wiki是一个很好的资源，包含了大量常见问题的答案——但请注意，在编写本文时，它尚未完全更新到Go 1.16。

## 生成骨架目录结构

好了，既然我们已经创建了项目目录并有了`go.mod`文件，你可以继续运行以下命令来为项目生成高级骨架结构：

```
$ mkdir -p bin cmd/api internal migrations remote
$ touch Makefile
$ touch cmd/api/main.go
```

此时，你的项目目录应该如下所示：

```
.
├── bin
├── cmd
│   └── api
│       └── main.go
├── internal
├── migrations
├── remote
├── go.mod
└── Makefile
```

让我们花点时间讨论这些文件和文件夹，并解释它们在我们完成项目中将发挥的作用。

- `bin`目录将包含我们编译后的应用程序二进制文件，准备部署到生产服务器。
- `cmd/api`目录将包含我们的*Greenlight* API应用程序的特定于应用程序的代码。这将包括运行服务器、读写HTTP请求以及管理身份验证的代码。
- `internal`目录将包含我们的API使用的各种辅助包。它将包含与数据库交互、进行数据验证、发送电子邮件等代码。基本上，任何*不是*应用程序特定且可能被重用的代码都将放在这里。我们在`cmd/api`下的Go代码将*导入*`internal`目录中的包（但绝不会反过来）。
- `migrations`目录将包含我们数据库的SQL迁移文件。
- `remote`目录将包含生产服务器的配置文件和设置脚本。
- `go.mod`文件将声明我们的项目依赖、版本和模块路径。
- `Makefile`将包含用于自动化常见管理任务的*配方*——比如审计Go代码、构建二进制文件和执行数据库迁移。

需要指出的是，目录名`internal`在Go中带有特殊的含义和行为：此目录下的任何包只能被`internal`目录的*父目录内部的*代码导入。在我们的例子中，这意味着任何位于`internal`中的包只能被我们的`greenlight`项目目录内的代码导入。

或者，换个角度看，这意味着`internal`下的任何包*不能被我们项目之外的代码导入*。

这很有用，因为它阻止其他代码库导入并依赖我们`internal`目录中的（可能未版本化且不受支持的）包——即使项目代码在GitHub等地方公开可用。

## 你好，世界！

```
// Read the value of the port and env command-line flags into the config struct. We
// default to using the port number 4000 and the environment "development" if no
// corresponding flags are provided.
    flag.IntVar(&cfg.port, "port", 4000, "API server port")
    flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")
    flag.Parse()

    // Initialize a new logger which writes messages to the standard out stream,
// prefixed with the current date and time.
    logger := log.New(os.Stdout, "", log.Ldate | log.Ltime)

    // Declare an instance of the application struct, containing the config struct and
// the logger.
    app := &application{
        config: cfg,
        logger: logger,
    }

    // Declare a new servemux and add a /v1/healthcheck route which dispatches requests
// to the healthcheckHandler method (which we will create in a moment).
    mux := http.NewServeMux()
    mux.HandleFunc("/v1/healthcheck", app.healthcheckHandler)

    // Declare a HTTP server with some sensible timeout settings, which listens on the
// port provided in the config struct and uses the servemux we created above as the
// handler.
    srv := &http.Server{
        Addr:         fmt.Sprintf(":%d", cfg.port),
        Handler:      mux,
        IdleTimeout:  time.Minute,
        ReadTimeout:  10 * time.Second,
    WriteTimeout: 30 * time.Second,
}

    // Start the HTTP server.
    logger.Printf("starting %s server on %s", cfg.env, srv.Addr)
    err := srv.ListenAndServe()
    logger.Fatal(err)
}
```

> **重要：**如果你对上述代码中的任何术语或模式感到不熟悉，我强烈推荐阅读第一本*Let's Go*书籍，其中详细解释了它们。

## 创建healthcheck处理器

接下来我们需要做的是创建`healthcheckHandler`方法来响应HTTP请求。目前，我们将这个处理器的逻辑保持得非常简单，让它返回一个纯文本响应，其中包含三条信息：

- 一个固定的`"status: available"`字符串。
- 来自硬编码`version`常量的API版本。
- 来自`env`命令行标志的操作系统环境名称。

继续创建一个新的`cmd/api/healthcheck.go`文件：

```
$ touch cmd/api/healthcheck.go
```

然后添加以下代码：

~~~
File: cmd/api/healthcheck.go

```go
package main

import (
    "fmt"
    "net/http"
)

// Declare a handler which writes a plain-text response with information about the
// application status, operating environment and version.
func (app *application) healthcheckHandler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintln(w, "status: available")
    fmt.Fprintf(w, "environment: %s\n", app.config.env)
    fmt.Fprintf(w, "version: %s\n", version)
}
```
~~~

这里需要指出的重要一点是，`healthcheckHandler`是作为我们`application`结构体上的一个*方法*实现的。

这是一种有效且惯用的方式，使依赖项可用于我们的处理器，而无需借助全局变量或闭包——`healthcheckHandler`需要的任何依赖项都可以在`main()`中初始化`application`结构体时作为字段包含进去。




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


Content-Length: 19

方法不允许

看起来效果很好。`httprouter` 包已经自动为我们发送了 `405 Method Not Allowed` 响应，并包含一个 `Allow` 头部，列出了该端点*支持*的 HTTP 方法。

同样，你可以向一个特定 URL 发起 `OPTIONS` 请求，`httprouter` 会返回一个带有 `Allow` 头部的响应，其中详细列出了支持的 HTTP 方法。如下所示：

```
$ curl -i -X OPTIONS localhost:4000/v1/healthcheck
HTTP/1.1 200 OK
Allow: GET, OPTIONS
Date: Tue, 06 Apr 2021 07:01:29 GMT
Content-Length: 0
```

最后，你可能想尝试向 `GET /v1/movies/:id` 端点发出请求，并在 URL 中使用负数或非数值的 `id` 值。这应该会导致 `404 Not Found` 响应，类似于这样：

```
$ curl -i localhost:4000/v1/movies/abc
HTTP/1.1 404 Not Found
Content-Type: text/plain; charset=utf-8
X-Content-Type-Options: nosniff
```

Date: Tue, 06 Apr 2021 07:02:01 GMT
Content-Length: 19

404 page not found

## 创建辅助函数读取 ID 参数

从像 `/v1/movies/:id` 这样的 URL 中提取 `id` 参数的代码，在我们的应用程序中会反复用到，所以让我们将这个逻辑抽象成一个可复用的小型辅助方法。

继续创建一个新的 `cmd/api/helpers.go` 文件：

```
$ touch cmd/api/helpers.go
```

并在 `application` 结构体上添加一个新的 `readIDParam()` 方法，如下所示：

```
File: cmd/api/helpers.go

package main

import (
    "errors"
    "net/http"
    "strconv"

    "github.com/julienschmidt/httprouter"
)

// Retrieve the "id" URL parameter from the current request context, then
// convert it to
// an integer and return it. If the operation isn't successful, return 0 and
// an error.
func (app *application) readIDParam(r *http.Request) (int64, error) {
    params := httprouter.ParamsFromContext(r.Context())

    id, err := strconv.ParseInt(params.ByName("id"), 10, 64)
    if err != nil || id < 1 {
        return 0, errors.New("invalid id parameter")
    }

    return id, nil
}
```

> **注意**：`readIDParam()` 方法没有使用我们 `application` 结构体中的任何依赖，所以它*可以*只是一个普通函数，而不是 `application` 上的方法。但总的来说，我建议把你所有的应用特定处理器和辅助函数都设置为 `application` 上的方法。这有助于保持代码结构的一致性，也为将来这些处理器和辅助函数发生变化并*确实*需要访问某个依赖时做好了准备。

有了这个辅助方法后，我们 `showMovieHandler` 中的代码就可以变得简单很多：

你不能注册一个像 `GET /foo/new` 的路由，同时又注册另一个与之冲突的带参数段的路由——比如 `GET /foo/:id`。

如果你的 API 端点使用了标准的 REST 结构——就像本书中我们将要使用的——那么这个限制不太可能给你带来太多问题。

事实上，这可以说是一件好事。因为不允许路由冲突，你就不需要担心路由优先级规则，这降低了应用程序中出现 bug 和意外行为的风险。

但如果你的确需要支持冲突路由（例如，你可能需要为了向后兼容而完全复制现有 API 的端点），那么我建议改用 `pat`、`chi` 或 Gorilla `mux`。这些都是不错的路由器，*确实*允许冲突路由。

## 自定义 httprouter 行为

`httprouter` 包提供了一些配置选项，你可以用它们进一步自定义应用程序的行为，包括启用*尾部斜杠重定向*和启用*自动 URL 路径清理*。

关于可用设置的更多信息可以在[这里](here)找到。

## 发送 JSON 响应

在本书的这一部分，我们将更新 API 处理器，让它们返回 JSON 响应，而不仅仅是纯文本。

JSON（是 *JavaScript Object Notation* 的缩写）是一种人类可读的文本格式，可用于表示结构化数据。例如，在我们的项目中，一部电影可以用以下 JSON 表示：

```
{
  "id": 123,
  "title": "Casablanca",
  "runtime": 102,
  "genres": [
    "drama",
    "romance",
    "war"
  ],
  "version": 1
}
```

为了给你一个*非常*快速的 JSON 语法概述…

- 花括号 {} 定义一个 *JSON 对象*，它由逗号分隔的键值对组成。
- 键必须是字符串，值可以是字符串、数字、布尔值、其他 JSON 对象，或者这些内容的*数组*（用 [] 括起来）。
- 字符串必须用双引号 "（而不是单引号 '）括起来，布尔值只能是 `true` 或 `false`。
- 在字符串之外，JSON 中的空白字符*不*具有任何意义——我们用下面的 JSON 来表示同一部电影同样是完全有效的：

```
{"id":123,"title":"Casablanca","runtime":102,"genres":
["drama","romance","war"],"version":1}
```

如果你以前从未使用过 JSON，那么这个初学者指南提供了全面的介绍，我建议你在继续之前先读一读。

在本节中，你将学到：

- 如何从你的 REST API 发送 JSON 响应（包括错误响应）。
- 如何使用 `encoding/json` 包将原生的 Go 对象编码为 JSON。
- 自定义 Go 对象编码为 JSON 的不同技巧——首先使用结构体标签，然后利用 `json.Marshaler` 接口。
- 如何创建一个可复用的辅助函数来发送 JSON 响应，这将确保你所有的 API 响应都具有合理且一致的 structure。

File: cmd/api/healthcheck.go

```
```go
package main

import (
    "fmt"
    "net/http"
)

func (app *application) healthcheckHandler(w http.ResponseWriter, r *http.Request) {
    // Create a fixed-format JSON response from a string. Notice how we're using a raw
    // string literal (enclosed with backticks) so that we can include double-quote
    // characters in the JSON without needing to escape them? We also use the %q verb to
    // wrap the interpolated values in double-quotes.
    js := `{"status": "available", "environment": %q, "version": %q}`
    js = fmt.Sprintf(js, app.config.env, version)

    // Set the "Content-Type: application/json" header on the response. If you forget to
    // this, Go will default to sending a "Content-Type: text/plain; charset=utf-8"
    // header instead.
    w.Header().Set("Content-Type", "application/json")

    // Write the JSON as the HTTP response body.
    w.Write([]byte(js))
}
```
```

完成这些更改后，重启 API，打开第二个终端，并使用 curl 向 `GET /v1/healthcheck` 端点发送请求。你现在应该会收到一个类似于这样的响应：

```
$ curl -i localhost:4000/v1/healthcheck
HTTP/1.1 200 OK
Content-Type: application/json
Date: Tue, 06 Apr 2021 08:38:12 GMT
Content-Length: 73

{"status": "available", "environment": "development", "version": "1.0.0"}
```

你可能还想在你的浏览器中尝试访问 `localhost:4000/v1/healthcheck`。

如果你运行的是较新版本的 Firefox，你会发现它知道响应包含 JSON（由于 `Content-Type` 头），并且会使用内置的 JSON 查看器来呈现响应。像这样：

![](img/30f9221bfc265d52b544dd595ca099de_52_0.png)

如果你点击 **Raw Data**（原始数据）选项卡，你应该会看到原始的未格式化 JSON 响应：

![](img/30f9221bfc265d52b544dd595ca099de_53_0.png)

或者你甚至可以选中 **Pretty Print**（美化打印）选项来添加空白，像这样：

![](img/30f9221bfc265d52b544dd595ca099de_54_0.png)

```
{
  "status": "available",
  "environment": "development",
  "version": "1.0.0"
}
```

当然，像我们在本章中使用固定格式字符串这种方法是生成 JSON 响应的一种非常简单且低技术含量的做法。但值得记住，这是一个有效的选项。它对于总是返回相同静态 JSON 的 API 端点很有用，或者作为一种快速简便的方法来生成像我们这里这样的小型动态响应。

## 附加信息

## JSON 字符集




在你的编程生涯中，你可能会遇到其他 JSON API，它们发送的响应头是 `Content-Type: application/json; charset=utf-8`。

像这样包含 `charset` 参数通常是不必要的。JSON RFC 指出：

> 不在封闭生态系统内的系统之间交换的 JSON 文本必须使用 UTF-8 编码。

这里的关键词是“必须”。由于我们的 API 将是一个面向公众的应用，这意味着我们的 JSON 响应必须始终使用 UTF-8 编码。这也意味着客户端可以安全地假设它收到的响应始终是 UTF-8 编码的。因此，包含 `charset=utf-8` 参数是多余的。

RFC 还明确指出，`application/json` 媒体类型没有定义 `charset` 参数，这意味着在技术上包含该参数也是不正确的。

基本上，在我们的应用中，`charset` 参数没有任何作用，不在我们的 `Content-Type: application/json` 响应头中包含它是安全（且正确）的。

## JSON 编码

让我们继续探讨一些更有趣的内容，看看如何将原生的 Go 对象（如 map、struct 和 slice）编码为 JSON。

从高层次来看，Go 的 `encoding/json` 包提供了两种将内容编码为 JSON 的选项。你可以调用 `json.Marshal()` 函数，或者声明并使用 `json.Encoder` 类型。

我们将在本章解释这两种方法的工作原理，但是——就发送 HTTP 响应中的 JSON 而言——使用 `json.Marshal()` 通常是更好的选择。所以让我们先从这里开始。

`json.Marshal()` 的工作方式在概念上非常简单——你将一个原生的 Go 对象作为参数传递给它，它会以 `[]byte` 切片的形式返回该对象的 JSON 表示。函数签名如下：

```go
func Marshal(v interface{}) ([]byte, error)
```

> **注意：** 上面的方法中的 `v` 参数类型为 `interface{}`（称为 `空接口`）。这实际上意味着我们可以将任何 Go 类型作为 `v` 参数传递给 `Marshal()`。

```go
return
}
    // Append a newline to the JSON. This is just a small nicety to make it easier to
    // view in terminal applications.
    js = append(js, '\n')

    // At this point we know that encoding the data worked without any
    // problems, so we
    // can safely set any necessary HTTP headers for a successful response.
    w.Header().Set("Content-Type", "application/json")

    // Use w.Write() to send the []byte slice containing the JSON as the
    // response body.
    w.Write(js)
}
```

如果你重新启动 API 并在浏览器中访问 localhost:4000/v1/healthcheck，你现在应该会得到类似这样的响应：

![](img/30f9221bfc265d52b544dd595ca099de_59_0.png)

看起来不错——我们可以看到 map 已经自动为我们编码成了一个 JSON 对象，map 中的键/值对在 JSON 对象中表现为*按字母排序*的键/值对。

## 创建 writeJSON 辅助方法

随着 API 的增长，我们将发送大量 JSON 响应，因此将部分逻辑移入可复用的 `writeJSON()` 辅助方法是合理的。

除了创建和发送 JSON 之外，我们还希望设计这个辅助方法，以便能够在成功的响应中包含*任意响应头*。

```go
// Append a newline to make it easier to view in terminal applications.
js = append(js, '\n')

// At this point, we know that we won't encounter any more errors before writing the
// response, so it's safe to add any headers that we want to include. We loop
// through the header map and add each header to the http.ResponseWriter header map.
// Note that it's OK if the provided header map is nil. Go doesn't throw an error
// if you try to range over (or generally, read from) a nil map.
for key, value := range headers {
    w.Header()[key] = value
}

// Add the "Content-Type: application/json" header, then write the status code and
// JSON response.
w.Header().Set("Content-Type", "application/json")
w.WriteHeader(status)
w.Write(js)

return nil
}
```

既然 `writeJSON()` 辅助方法已经就位，我们可以大大简化 `healthcheckHandler` 中的代码，如下所示：

```go
File: cmd/api/healthcheck.go

package main

import (
    "net/http"
)

func (app *application) healthcheckHandler(w http.ResponseWriter, r *http.Request) {
    data := map[string]string{
        "status":      "available",
        "environment": app.config.env,
        "version":     version,
    }

    err := app.writeJSON(w, http.StatusOK, data, nil)
    if err != nil {
        app.logger.Println(err)
        http.Error(w, "The server encountered a problem and could not process your request", http.StatusInternalServerError)
    }
}
```

如果你现在再次运行应用程序，一切都会正确编译，对 GET `/v1/healthcheck` 端点的请求应该会产生与之前相同的 HTTP 响应。

## 附加信息

## 不同 Go 类型的编码方式

在本章中，我们一直在将 `map[string]string` 类型编码为 JSON，这产生了一个 JSON 对象，其中的键/值对值是 JSON 字符串。但 Go 还支持编码许多其他原生类型。

下表总结了编码过程中不同 Go 类型如何映射到 JSON 数据类型：

| Go 类型 | ⇒ | JSON 类型 |
|---|---|---|
| bool | ⇒ | JSON 布尔值 |
| string | ⇒ | JSON 字符串 |
| int*, uint*, float*, rune | ⇒ | JSON 数字 |
| array, slice | ⇒ | JSON 数组 |
| struct, map | ⇒ | JSON 对象 |
| nil 指针、接口值、切片、映射等 | ⇒ | JSON null |
| chan, func, complex* | ⇒ | 不支持 |
| time.Time | ⇒ | RFC3339 格式的 JSON 字符串 |
| []byte | ⇒ | Base64 编码的 JSON 字符串 |

最后两个是特殊的例子，需要进一步解释：

-   Go 的 `time.Time` 值（实际上在幕后是一个 `struct`）将被编码为 RFC 3339 格式的 JSON 字符串，如 `"2020-11-08T06:27:59+01:00"`，而不是 JSON 对象。
-   一个 `[]byte` 切片将被编码为 base64 编码的 JSON 字符串，而不是 JSON 数组。例如，一个字节切片 `[]byte{'h','e','l','l','o'}` 在 JSON 输出中将显示为 `"aGVsbG8="`。base64 编码使用填充和标准字符集。

还有其他一些重要的事情需要提及：

-   支持嵌套对象的编码。例如，如果你在 Go 中有一个*结构体切片*，它将在 JSON 中编码为*对象数组*。
-   通道、函数和 `complex` 数字类型无法编码。如果你尝试这样做，运行时将出现 `json.UnsupportedTypeError` 错误。
-   任何指针值将编码为*所指向的值*。同样，`interface{}` 值将编码为接口中包含的值。

## 使用 json.Encoder

在本章开头，我提到也可以使用 Go 的 `json.Encoder` 类型来执行编码。这允许你一步将对象编码为 JSON，并*将该 JSON 写入输出流*。

这意味着你无法根据 `Encode()` 方法是否返回错误来有条件地设置 HTTP 响应头。

例如，假设你想在成功响应时设置 `Cache-Control` 响应头，但如果 JSON 编码失败而不得不返回错误响应时，则不设置 `Cache-Control` 响应头。

在使用 `json.Encoder` 模式时，干净利落地实现这一点是相当困难的。

你可以在出错时设置 `Cache-Control` 响应头，然后再次从响应头映射中删除它——但这非常 hacky。

另一种选择是将 JSON 写入一个临时的 `bytes.Buffer`，而不是直接写入 `http.ResponseWriter`。然后你可以在设置 `Cache-Control` 响应头并将 JSON 从 `bytes.Buffer` 复制到 `http.ResponseWriter` 之前检查是否有错误。但一旦你开始这样做，使用替代的 `json.Marshal()` 方法会更加简单、干净（也稍快一些）。

## json.Encoder 和 json.Marshal 的性能

说到速度，你可能会想知道使用 `json.Encoder` 和 `json.Marshal()` 之间是否存在性能差异。简短的回答是有的……但差异很小，在大多数情况下你不必担心。

以下基准测试展示了使用此 gist 中的代码对这两种方法的性能（请注意，每个基准测试


测试重复三次)：

```
$ go test -run=^$ -bench=. -benchmem -count=3 -benchtime=5s
goos: linux
goarch: amd64
BenchmarkEncoder-8    3477318    1692 ns/op    1046 B/op    15 allocs/op
BenchmarkEncoder-8    3435145    1704 ns/op    1048 B/op    15 allocs/op
BenchmarkEncoder-8    3631305    1595 ns/op    1039 B/op    15 allocs/op
BenchmarkMarshal-8    3624570    1616 ns/op    1119 B/op    16 allocs/op
BenchmarkMarshal-8    3549090    1626 ns/op    1123 B/op    16 allocs/op
BenchmarkMarshal-8    3548070    1638 ns/op    1123 B/op    16 allocs/op
```

在这些结果中，我们可以看到 json.Marshal() 所需的内存（B/op）比 json.Encoder 略多一些，并且还多进行了一次堆内存分配（allocs/op）。

这两种方法在平均运行时间（ns/op）上没有明显可观察到的差异。也许使用更大的基准测试样本或更大的数据集时差异可能会变得清晰，但它很可能在微秒级别，而不会更大。

## 额外的 JSON 编码细微差别

在 Go 中将事物编码为 JSON 大多相当直观。但有一些行为可能会让你措手不及或在初次遇到时感到惊讶。

我们在本章中已经提到了其中一些（特别是 — *map 条目按字母顺序排序* 和 *字节切片被 base-64 编码*），但我已在本附录中列出了完整清单。

第 3.3 章。

## 编码结构体

在本章中，我们将回到之前创建的 `showMovieHandler` 方法，并更新它以返回一个 JSON 响应，表示我们系统中单个电影。类似这样：

```
{
  "id": 123,
  "title": "Casablanca",
  "runtime": 102,
  "genres": [
    "drama",
    "romance",
    "war"
  ],
  "version": 1
}
```

而不是像上一章那样通过编码 map 来创建此 JSON 对象，这次我们将编码一个自定义的 `Movie` 结构体。

所以，首先，我们需要通过定义一个自定义的 `Movie` 结构体来开始。我们将在新的 `internal/data` 包内执行此操作，该包以后将扩展以封装项目的 *所有* 自定义数据类型以及与数据库交互的逻辑。

如果你跟着操作，请继续创建一个包含 movies.go 文件的新 internal/data 目录：

```
$ mkdir internal/data
$ touch internal/data/movies.go
```

在这个新文件中，让我们像这样定义自定义的 Movie 结构体：

```
File: internal/data/movies.go

package data

import (
    "time"
)

type Movie struct {
    ID        int64     // Unique integer ID for the movie
    CreatedAt time.Time // Timestamp for when the movie is added to our database
    Title     string    // Movie title
    Year      int32     // Movie release year
    Runtime   int32     // Movie runtime (in minutes)
    Genres    []string  // Slice of genres for the movie (romance, comedy, etc.)
    Version   int32     // The version number starts at 1 and will be incremented each
                          // time the movie information is updated
}
```

> **重要：** 这里必须指出，我们的 `Movie` 结构体中的所有字段都是导出的（即以大写字母开头），这是它们对 Go 的 `encoding/json` 包可见所必需的。任何字段 *未* 导出在将结构体编码为 JSON 时都不会被包含。

完成之后，让我们更新 `showMovieHandler` 以初始化包含一些虚拟数据的 `Movie` 结构体实例，然后使用我们的 `writeJSON()` 辅助函数将其作为 JSON 响应发送。

实际上非常简单：

```
File: `cmd/api/movies.go`

```go
package main

import (
    "fmt"
    "net/http"
    "time" // New import

    "greenlight.alexedwards.net/internal/data" // New import
)

...

func (app *application) showMovieHandler(w http.ResponseWriter, r *http.Request) {
    id, err := app.readIDParam(r)
    if err != nil {
        http.NotFound(w, r)
        return
```

```
}
```

    // Create a new instance of the Movie struct, containing the ID we
    extracted from
    // the URL and some dummy data. Also notice that we deliberately haven't
    set a
    // value for the Year field.
    movie := data.Movie{
        ID:         id,
        CreatedAt:  time.Now(),
        Title:      "Casablanca",
        Runtime:    102,
        Genres:     []string{"drama", "romance", "war"},
        Version:    1,
    }

    // Encode the struct to JSON and send it as the HTTP response.
    err = app.writeJSON(w, http.StatusOK, movie, nil)
    if err != nil {
        app.logger.Println(err)
        http.Error(w, "The server encountered a problem and could not process your request", http.StatusInternalServerError)
    }
}
```

好的，让我们试试这个！

重启 API，然后在浏览器中访问 `localhost:4000/v1/movies/123`。你应该会看到一个类似这样的 JSON 响应：

![](img/30f9221bfc265d52b544dd595ca099de_73_0.png)

```
{
  "ID": 123,
  "CreatedAt": "2020-11-09T10:50:32.304100456+01:00",
  "Title": "Casablanca",
  "Year": 0,
  "Runtime": 102,
  "Genres": [
    "drama",
    "romance",
    "war"
  ],
  "Version": 1
}
```

这个响应中有一些有趣的地方值得指出：

- 我们的 Movie 结构体已被编码为单个 JSON 对象，字段名和值作为键/值对。
- 默认情况下，JSON 对象中的键等于结构体中的字段名（ID、CreatedAt、Title 等）。我们稍后会讨论如何自定义它们。
- 如果结构体字段没有显式设置值，则该字段的零值的 JSON 编码会出现在输出中。我们可以在上面的响应中看到一个例子——我们在 Go 代码中没有为 Year 字段设置值，但它仍然以值 0 出现在 JSON 输出中。

如果你重启服务器并再次访问 `localhost:4000/v1/movies/123`，你现在应该会看到一个带有 `snake_case` 键的响应，类似这样：

![](img/30f9221bfc265d52b544dd595ca099de_75_0.png)

## 在 JSON 对象中隐藏结构体字段

也可以通过使用 `omitempty` 和 `-` 结构体标签指令来控制单个结构体字段在 JSON 中的可见性。

`-`（连字符）指令可用于你 *从不* 希望某个结构体字段出现在 JSON 输出中的情况。这对于包含内部系统信息且与

```
directive
    Genres    []string `json:"genres,omitempty"`  // Add the omitempty
directive
    Version   int32    `json:"version"`
}
```

**提示：** 如果你想使用 `omitempty` 而 *不* 更改键名，则可以在结构体标签中将其留空——像这样：`json:",omitempty"`。请注意，前导逗号仍然是必需的。

现在当你重启应用程序并刷新网页浏览器时，你应该会看到一个完全像这样的响应：

![](img/30f9221bfc265d52b544dd595ca099de_77_0.png)

我们可以看到 `CreatedAt` 结构体字段现在完全不再出现在 JSON 中，并且 `Year` 字段（其值为 `0`）也不再出现，这要归功于 `omitempty` 指令。我们对 `Runtime` 和 `Genres` 使用了 `omitempty` 的其他字段不受影响。

> **注意：** 你也可以通过简单地使其未导出来防止结构体字段出现在 JSON 输出中。但使用 `json:"-"` 结构体标签通常是更好的选择：它明确地向 Go 以及你代码的任何未来读者表明你不希望该字段包含在 JSON 中，并且有助于防止如果有人在未来将该字段导出而未意识到后果时出现问题。
> 
> `go vet` 的旧版本在尝试在未导出的字段上使用结构体标签时会引发错误，但这在 Go 1.16 中已得到修复。

## 附加信息

## 字符串结构体标签指令

最后，一个较少使用的结构体标签指令是 `string`。你可以在单个结构体字段上使用它，以强制数据在 JSON 输出中表示为字符串。




例如，如果我们希望将 Runtime 字段的值表示为 JSON 字符串（而不是数字），可以使用 string 指令，如下所示：

```
type Movie struct {
    ID          int64       `json:"id"`
    CreatedAt   time.Time   `json:"-"`
    Title       string      `json:"title"`
    Year        int32       `json:"year,omitempty"`
    Runtime     int32       `json:"runtime,omitempty,string"` // Add the string directive
    Genres      []string    `json:"genres,omitempty"`
    Version     int32       `json:"version"`
}
```

而生成的 JSON 输出将如下所示：

```
{
    "id": 123,
    "title": "Casablanca",
    "runtime": "102",     ← This is now a string
    "genres": [
        "drama",
        "romance",
        "war"
    ],
    "version": 1
}
```

请注意，`string` 指令仅适用于类型为 `int*`、`uint*`、`float*` 或 `bool` 的结构体字段。对于其他任何类型的结构体字段，该指令将不起作用。

### 第 3.4 章

## 格式化与封装响应

到目前为止，在本书中，我们通常使用 Firefox 向 API 发起请求，得益于内置 JSON 查看器提供的“美化打印”，JSON 响应很容易阅读。

但是，如果你尝试使用 curl 发起一些请求，你会看到实际的 JSON 响应数据都挤在一行，没有空白字符。

```
$ curl localhost:4000/v1/healthcheck
{"environment":"development","status":"available","version":"1.0.0"}

$ curl localhost:4000/v1/movies/123
{"id":123,"title":"Casablanca","runtime":102,"genres":["drama","romance","war"],"version":1}
```

我们可以使用 `json.MarshalIndent()` 函数（而不是常规的 `json.Marshal()` 函数）来编码响应数据，从而让它们在终端中更易读。该函数会自动为 JSON 输出添加空白字符，将每个元素放在单独的行上，并为每一行添加可选的*前缀*和*缩进*字符。

让我们更新 `writeJSON()` 辅助函数来使用这个功能：

注意：在幕后，`json.MarshalIndent()` 的工作方式是正常调用 `json.Marshal()`，然后通过独立的 `json.Indent()` 函数处理 JSON 以添加空白字符。还有一个反向函数 `json.Compact()` 可用，你可以使用它从 JSON 中移除空白字符。

## 封装响应

接下来，让我们更新响应，使 JSON 数据始终*封装*在父级 JSON 对象中。类似于这样：

```
{
  "movie": {
    "id": 123,
    "title": "Casablanca",
    "runtime": 102,
    "genres": [
      "drama",
      "romance",
      "war"
    ],
    "version":1
  }
}
```

注意这里电影数据是如何嵌套在键 "movie" 下的，而不是作为顶层的 JSON 对象本身？

```
package main

...

// Define an envelope type.
type envelope map[string]interface{}

// Change the data parameter to have the type envelope instead of interface{}.
func (app *application) writeJSON(w http.ResponseWriter, status int, data envelope, headers http.Header) error {
    js, err := json.MarshalIndent(data, "", "\t")
    if err != nil {
        return err
    }

    js = append(js, '\n')

    for key, value := range headers {
        w.Header()[key] = value
    }

    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(status)
    w.Write(js)

    return nil
}
```

然后我们需要更新 showMovieHandler，创建一个包含电影数据的 envelope 映射实例，并将它传递给 writeJSON() 辅助函数，而不是直接传递电影数据。

就像这样：

```go
package main

...

func (app *application) showMovieHandler(w http.ResponseWriter, r *http.Request) {
    id, err := app.readIDParam(r)
    if err != nil {
        http.NotFound(w, r)
        return
    }

    movie := data.Movie{
        ID:         id,
        CreatedAt:  time.Now(),
        Title:      "Casablanca",
        Runtime:    102,
        Genres:     []string{"drama", "romance", "war"},
        Version:    1,
    }

    // Create an envelope{"movie": movie} instance and pass it to writeJSON(), instead
    // of passing the plain movie struct.
    err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
    if err != nil {
        app.logger.Println(err)
        http.Error(w, "The server encountered a problem and could not process your request", http.StatusInternalServerError)
    }
}
```

我们还需要更新 healthcheckHandler 中的代码，使它也将 envelope 类型传递给 writeJSON() 辅助函数：

```
File: cmd/api/healthcheck.go

package main

...

func (app *application) healthcheckHandler(w http.ResponseWriter, r *http.Request) {
    // Declare an envelope map containing the data for the response. Notice that the way
    // we've constructed this means the environment and version data will now be nested
    // under a system_info key in the JSON response.
    env := envelope{
        "status": "available",
        "system_info": map[string]string{
            "environment": app.config.env,
            "version":     version,
        },
    }

    err := app.writeJSON(w, http.StatusOK, env, nil)
    if err != nil {
        app.logger.Println(err)
        http.Error(w, "The server encountered a problem and could not process your request", http.StatusInternalServerError)
    }
}
```

好了，让我们试试这些改动。重启服务器，然后使用 curl 再次向 API 端点发起一些请求。

现在你应该会得到如下格式的响应。

```
$ curl localhost:4000/v1/movies/123
{
    "movie": {
        "id": 123,
        "title": "Casablanca",
        "runtime": 102,
        "genres": [
            "drama",
            "romance",
            "war"
        ],
        "version":1
    }
}

$ curl localhost:4000/v1/healthcheck
{
    "status": "available",
    "system_info": {
        "environment": "development",
        "version": "1.0.0"
    }
}
```

## 附加信息

## 响应结构

## 高级 JSON 自定义

通过使用结构体标签、添加空白字符和封装数据，我们已经能够为 JSON 响应添加相当多的自定义。但当这些还不够，你需要更大的自由来进一步自定义 JSON 时，会发生什么？

要回答这个问题，我们首先需要讨论一些关于 Go 在幕后如何处理 JSON 编码的理论。需要理解的关键点是：

> *当 Go 将特定类型编码为 JSON 时，它会检查该类型是否实现了 `MarshalJSON()` 方法。如果有，Go 将调用此方法来确定如何对其进行编码。*

这种表述有点模糊，所以让我们说得更精确些。

严格来说，当 Go 将特定类型编码为 JSON 时，它会检查该类型是否满足 `json.Marshaler` 接口，该接口如下所示：

```
type Marshaler interface {
    MarshalJSON() ([]byte, error)
}
```

如果该类型确实满足该接口，Go 将调用其 `MarshalJSON()` 方法，并使用它返回的 `[]byte` 切片作为编码后的 JSON 值。

如果该类型没有 `MarshalJSON()` 方法，则 Go 将回退到基于自身内部规则尝试将其编码为 JSON。

因此，如果我们想要自定义某些内容的编码方式，我们所需要做的就是在其上实现一个 `MarshalJSON()` 方法，该方法返回一个 `[]byte` 切片，其中包含*其自身的自定义 JSON 表示*。

> **提示：** 如果你查看 Go 的 `time.Time` 类型的源代码，就能看到这一点。在幕后，`time.Time` 实际上是一个 `struct`，但它有一个 `MarshalJSON()` 方法，该方法输出其自身的 RFC 3339 格式表示。每当 `time.Time` 值被编码为 JSON 时，调用的就是这个方法。

## 自定义 Runtime 字段

为了帮助说明这一点，让我们看看应用程序中的一个具体例子。

当我们的 `Movie` 结构体被编码为 JSON 时，`Runtime` 字段（属于 `int32` 类型）当前被格式化为 JSON 数字。让我们将其改为以字符串格式 `"<runtime> mins"` 进行编码。就像这样：


```
{
  "id": 123,
  "title": "Casablanca",
  "runtime": "102 mins",    ← This is now a string
  "genres": [
    "drama",
    "romance",
    "war"
  ],
  "version":1
}
```

有几种方法可以实现这一点，但一种简洁明了的方法是为 Runtime 字段专门创建一个自定义类型，并在该自定义类型上实现 MarshalJSON() 方法。

防止 internal/data/movie.go 文件变得杂乱，让我们创建一个新文件来存放 Runtime 类型的逻辑：

```
$ touch internal/data/runtime.go
```

然后继续添加以下代码：

```
File: internal/data/runtime.go

package data

import (
  "fmt"
  "strconv"
)
// Declare a custom Runtime type, which has the underlying type int32 (the
same as our
// Movie struct field).
type Runtime int32

// Implement a MarshalJSON() method on the Runtime type so that it satisfies
the
// json.Marshaler interface. This should return the JSON-encoded value for
the movie
// runtime (in our case, it will return a string in the format "<runtime>
mins").
func (r Runtime) MarshalJSON() ([]byte, error) {
    // Generate a string containing the movie runtime in the required format.
    jsonValue := fmt.Sprintf("%d mins", r)

    // Use the strconv.Quote() function on the string to wrap it in double
quotes. It
    // needs to be surrounded by double quotes in order to be a valid *JSON
string*.
    quotedJSONValue := strconv.Quote(jsonValue)

    // Convert the quoted string value to a byte slice and return it.
    return []byte(quotedJSONValue), nil
}
```

这里有两点我想强调：

- 如果你的 MarshalJSON() 方法返回一个 JSON 字符串值，像我们这样，那么你必须在返回前用双引号将字符串包裹起来。否则它不会被解释为 JSON 字符串，你会收到类似以下的运行时错误：

```
json: error calling MarshalJSON for type data.Runtime: invalid character 'm' after top-level value
```

- 我们故意为 `MarshalJSON()` 方法使用 *值接收者* 而不是像 `func (r *Runtime) MarshalJSON()` 这样的 *指针接收者*。这样做可以提供更大的灵活性，因为这意味着我们的自定义 JSON 编码既适用于 `Runtime` 值，也适用于指向 `Runtime` 值的指针。Effective Go 中提到：

> 关于接收者指针与值的规则是：值方法可以对指针和值调用，但指针方法只能对指针调用。

**提示：** 如果你对指针接收者和值接收者之间的区别没有把握，那么这篇博客文章提供了很好的总结。

好的，现在自定义 `Runtime` 类型已定义，打开你的 `internal/data/movies.go` 文件并按如下方式更新 `Movie` 结构体以使用它：

```
File: internal/data/movies.go

package data

import (
"time"
)

type Movie struct {
    ID          int64       `json:"id"`
    CreatedAt   time.Time   `json:"-"`
    Title       string      `json:"title"`
    Year        int32       `json:"year,omitempty"`
    // Use the Runtime type instead of int32. Note that the omitempty
    directive will
    // still work on this: if the Runtime field has the underlying value 0,
    then it will
    // be considered empty and omitted -- and the MarshalJSON() method we
    just made
    // won't be called at all.
    Runtime Runtime    `json:"runtime,omitempty"`
    Genres  []string   `json:"genres,omitempty"`
    Version int32      `json:"version"`
}
```

让我们通过重启 API 并向 GET /v1/movies/:id 端点发出请求来试试。你现在应该会看到一个包含自定义 runtime 值的响应，格式为 "<runtime> mins"，类似于这样：

```
$ curl localhost:4000/v1/movies/123
{
    "movie": {
        "id": 123,
        "title": "Casablanca",
        "runtime": "102 mins",
        "genres": [
            "drama",
            "romance",
            "war"
        ],
        "version": 1
    }
}
```

总的来说，这是一种生成自定义 JSON 的相当不错的方法。我们的代码简洁清晰，而且我们拥有一个自定义的 Runtime 类型，可以在任何需要时使用。

但也有一个缺点。需要注意的是，使用自定义类型在将代码与其他包集成时有时会显得 awkward，你可能需要执行类型转换，将自定义类型转换为其他包理解和接受的值，反之亦然。

## 附加信息

这里有几种可行的替代方法可以达到同样的最终结果，我想快速描述一下并讨论它们的优缺点。如果你正在跟随构建进行编码，请不要做这些更改（除非你好奇，当然！）。

### 替代方案 #1 - 自定义 Movie 结构体

如果不创建自定义 Runtime 类型，我们本可以在 Movie 结构体上实现 MarshalJSON() 方法并自定义整个结构体。像这样：

```
// Note that there are no struct tags on the Movie struct itself.
type Movie struct {
    ID          int64
    CreatedAt   time.Time
    Title       string
    Year        int32
    Runtime     int32
    Genres      []string
    Version     int32
}

// Implement a MarshalJSON() method on the Movie struct, so that it satisfies the
// json.Marshaler interface.
func (m Movie) MarshalJSON() ([]byte, error) {
    // Declare a variable to hold the custom runtime string (this will be the empty
    // string "" by default).
    var runtime string

    // If the value of the Runtime field is not zero, set the runtime variable to be a
    // string in the format "<runtime> mins".
    if m.Runtime != 0 {
        runtime = fmt.Sprintf("%d mins", m.Runtime)
    }

    // Create an anonymous struct to hold the data for JSON encoding. This has exactly
    // the same fields, types and tags as our Movie struct, except that the Runtime
    // field here is a string, instead of an int32. Also notice that we don't
```

"<runtime> mins" 首先。然后最后，我们将匿名结构体编码为 JSON —— 而不是原始的 Movie 结构体 —— 并返回它。

也值得指出的是，这样的设计使得 omitempty 指令仍然适用于我们的自定义编码。如果 Runtime 字段的值为零，则本地 runtime 变量将保持等于 ""，这（正如我们之前提到的）在编码目的上被视为“空”。

### 替代方案 #2 - 嵌入别名

上述方法的缺点是代码感觉相当冗长且重复。你可能会想：有没有更好的方法？

为了减少重复，而不是逐行写出所有结构体字段，可以在匿名结构体中嵌入 Movie 结构体的别名。像这样：

```
// Notice that we use the - directive on the Runtime field, so that it never appears
// in the JSON output.
type Movie struct {
    ID        int64     `json:"id"`
    CreatedAt time.Time `json:"-"`
    Title     string    `json:"title"`
    Year      int32     `json:"year,omitempty"`
    Runtime   int32     `json:"-"`
    Genres    []string  `json:"genres,omitempty"`
    Version   int32     `json:"version"`
}
```

```
func (m Movie) MarshalJSON() ([]byte, error) {
    // Create a variable holding the custom runtime string, just like before.
    var runtime string

    if m.Runtime != 0 {
        runtime = fmt.Sprintf("%d mins", m.Runtime)
    }

    // Define a MovieAlias type which has the underlying type Movie. Due to
    the way that
        // Go handles type definitions
    (https://golang.org/ref/spec#Type_definitions) the
        // MovieAlias type will contain all the fields that our Movie struct has
    but,
        // importantly, none of the methods.
    type MovieAlias Movie

    // Embed the MovieAlias type inside the anonymous struct, along with a
    Runtime field
        // that has the type string and the necessary struct tags. It's important
    that we
        // embed the MovieAlias type here, rather than the Movie type directly,
    to avoid
        // inheriting the MarshalJSON() method of the Movie type (which would
    result in an
        // infinite loop during encoding).
    aux := struct {
        MovieAlias
        Runtime string `json:"runtime,omitempty"`
    }{
        MovieAlias: MovieAlias(m),
        Runtime:    runtime,
    }

    return json.Marshal(aux)
}
```

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




例如，如果我们尝试发送一个带有无效 Host 头的请求，我们会得到如下响应：

```
$ curl -i -H "Host: こんにちは" http://localhost:4000/v1/healthcheck
HTTP/1.1 400 Bad Request: malformed Host header
Content-Type: text/plain; charset=utf-8
Connection: close

400 Bad Request: malformed Host header
```

遗憾的是，这些响应是 Go 标准库中硬编码的，我们无法自定义它们以改用 JSON。

但尽管这是需要注意的一点，却不一定需要担心。在生产环境中，行为良好、非恶意的客户端相对不太可能触发这些响应，而且如果坏客户端有时收到纯文本响应而不是 JSON，我们也不应过分担心。

## 第4章

## 解析 JSON 请求

到目前为止，我们一直在研究如何从 API 创建和发送 JSON 响应，但在本书的这一部分，我们将从另一面探讨问题，并讨论如何*读取和解析来自客户端的 JSON 请求*。

为了帮助演示这一点，我们将开始处理之前设置的 `POST /v1/movies` 端点和 `createMovieHandler`。

| 方法 | URL 模式 | 处理器 | 动作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用程序信息 |
| POST | /v1/movies | createMovieHandler | 创建新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |

当客户端调用此端点时，我们期望他们提供一个 JSON 请求体，其中包含他们想要在我们的系统中创建的电影数据。例如，如果客户端想要向我们的 API 添加一条电影*海洋奇缘*的记录，他们会发送类似这样的请求体：

```json
{
  "title": "Moana",
  "year": 2016,
  "runtime": 107,
  "genres": ["animation", "adventure"]
}
```

现在，我们只专注于处理这个 JSON 请求体的读取、解析和验证方面。具体来说，你将学到：

- 如何使用 `encoding/json` 包读取请求体并将其解码为原生 Go 对象。
- 如何处理来自客户端的错误请求和无效 JSON，并返回清晰、可操作的错误消息。
- 如何创建一个可重用的辅助包来验证数据，确保其符合你的业务规则。
- 控制和自定义 JSON 解码方式的不同技术。

```
...
func (app *application) createMovieHandler(w http.ResponseWriter, r
*http.Request) {
    // Declare an anonymous struct to hold the information that we expect to
be in the
    // HTTP request body (note that the field names and types in the struct
are a subset
    // of the Movie struct that we created earlier). This struct will be our
*target
    // decode destination*.
    var input struct {
        Title   string  `json:"title"`
        Year    int32   `json:"year"`
        Runtime int32   `json:"runtime"`
        Genres  []string `json:"genres"`
    }

    // Initialize a new json.Decoder instance which reads from the request
body, and
    // then use the Decode() method to decode the body contents into the
input struct.
    // Importantly, notice that when we call Decode() we pass a *pointer* to
the input
    // struct as the target decode destination. If there was an error during
decoding,
    // we also use our generic errorResponse() helper to send the client a
400 Bad
    // Request response containing the error message.
    err := json.NewDecoder(r.Body).Decode(&input)
    if err != nil {
        app.errorResponse(w, r, http.StatusBadRequest, err.Error())
        return
    }

    // Dump the contents of the input struct in a HTTP response.
    fmt.Fprintf(w, "%+v\n", input)
}
```

```
...
```

关于这段代码，有几点重要且有趣的地方需要指出：

- 调用 `Decode()` 时，你必须传递一个*非空指针*作为目标解码目的地。如果你不使用指针，它会在运行时返回一个 `json.InvalidUnmarshalError` 错误。
- 如果目标解码目的地是一个结构体——就像我们的情况一样——结构体的字段必须被导出（以大写字母开头）。就像编码一样，它们需要被导出，以便对 `encoding/json` 包可见。
- 当将 JSON 对象解码到结构体时，JSON 中的键/值对根据结构体标签名称映射到结构体字段。如果没有匹配的结构体标签，Go 将尝试将值解码到与键名匹配的字段中（优先精确匹配，但会回退到不区分大小写的匹配）。*任何无法成功映射到结构体字段的 JSON 键/值对将被静默忽略。*
- 读取 `r.Body` 后无需关闭它。这将由 Go 的 `http.Server` 自动完成，因此你不必这样做。

好的，让我们来试试看。

发送一个 JSON 中没有 `year` 的请求，如下所示：

```
$ BODY='{"title":"Moana","runtime":107, "genres":["animation","adventure"]}'
$ curl -d "$BODY" localhost:4000/v1/movies
{Title:Moana Year:0 Runtime:107 Genres:[animation adventure]}
```

你可能已经猜到，当我们这样做时，`input` 结构体中的 `Year` 字段会保留其零值（恰好是 `0`，因为 `Year` 字段是 `int32` 类型）。

这引出一个有趣的问题：如何区分客户端没有提供键/值对，和提供了键/值对但故意将其设置为零值这两种情况？就像这样：

```
$ BODY='{"title":"Moana","year":0,"runtime":107, "genres":
["animation","adventure"]}'
$ curl -d "$BODY" localhost:4000/v1/movies
{Title:Moana Year:0 Runtime:107 Genres:[animation adventure]}
```

尽管 HTTP 请求不同，最终结果是一样的，而且并不容易一眼看出如何区分这两种情况。我们会在本书后面回到这个话题，但现在，只需意识到这种行为即可。

## 附加信息

## 支持的目标类型

需要特别说明的是，某些 JSON 类型只能成功解码为特定的 Go 类型。例如，如果你有 JSON 字符串 `"foo"`，它可以解码为 Go 的 `string`，但尝试将其解码为 Go 的 `int` 或 `bool` 将在运行时导致错误（我们将在下一章演示）。

下表显示了不同 JSON 类型支持的目标解码目的地：

| JSON 类型 | ⇒ | 支持的 Go 类型 |
|---|---|---|
| JSON 布尔值 | ⇒ | bool |
| JSON 字符串 | ⇒ | string |
| JSON 数字 | ⇒ | int*、uint*、float*、rune |
| JSON 数组 | ⇒ | array、slice |
| JSON 对象 | ⇒ | struct、map |

## 使用 json.Unmarshal 函数

正如我们在本章开头提到的，也可以使用 `json.Unmarshal()` 函数来解码 HTTP 请求体。

例如，你可以在处理器中这样使用：

## 处理错误请求

现在，我们的 `createMovieHandler` 在收到带有适当数据的有效 JSON 请求体时可以正常工作。但此时你可能会想：

- 如果客户端发送的不是 JSON，而是 XML 或一些随机字节，会发生什么？
- 如果 JSON 格式错误或包含错误，会发生什么？
- 如果 JSON 类型与我们尝试解码到的类型不匹配，会发生什么？
- 如果请求根本不包含请求体，会怎样？

好吧……让我们来看看！

```
### 发送一些 XML 作为请求体
$ curl -d '<?xml version="1.0" encoding="UTF-8"?><note><to>Alice</to></note>' localhost:4000/v1/movies
{
  "error": "invalid character '\u003c' looking for beginning of value"
}

### 发送一些格式错误的 JSON（注意尾部的逗号）
$ curl -d '{"title": "Moana", }' localhost:4000/v1/movies
{
  "error": "invalid character '}' looking for beginning of object key string"
}
```


但对于面向公众的 API 而言，这些错误信息本身并不理想。有些过于详细，暴露了底层 API 实现的信息；有些则描述不足（比如 "EOF"），还有一些令人困惑、难以理解。此外，格式和语言也不统一。

为了改进这一点，我们将解释如何对 `Decode()` 返回的错误进行*分类处理*，并用更清晰、易于采取行动的错误信息替换它们，以帮助客户端准确调试其 JSON 中的问题。

## 对 Decode 错误进行分类

在我们应用程序构建的这个阶段，`Decode()` 方法可能返回以下五种类型的错误：

| 错误类型 | 原因 |
|---|---|
| `json.SyntaxError`<br>`io.ErrUnexpectedEOF` | 被解码的 JSON 存在语法问题。 |
| `json.UnmarshalTypeError` | JSON 值不适合目标 Go 类型。 |
| `json.InvalidUnmarshalError` | 解码目标无效（通常因为它不是指针）。这实际上是应用程序代码的问题，而不是 JSON 本身的问题。 |
| `io.EOF` | 被解码的 JSON 为空。 |

```go
}
    return fmt.Errorf("body contains incorrect JSON type (at character %d)", unmarshalTypeError.Offset)

    // An io.EOF error will be returned by Decode() if the request body
is empty. We
    // check for this with errors.Is() and return a plain-english error
message
    // instead.
    case errors.Is(err, io.EOF):
        return errors.New("body must not be empty")

    // A json.InvalidUnmarshalError error will be returned if we pass a
non-nil
    // pointer to Decode(). We catch this and panic, rather than
returning an error
    // to our handler. At the end of this chapter we'll talk about
panicking
    // versus returning errors, and discuss why it's an appropriate thing
to do in
    // this specific situation.
    case errors.As(err, &invalidUnmarshalError):
        panic(err)

    // For anything else, return the error message as-is.
    default:
        return err
    }
}
    return nil
}
```

有了这个新的辅助函数，让我们回到 `cmd/api/movies.go` 文件，更新我们的 `createMovieHandler` 来使用它。如下所示：

继续重启 API，然后让我们重复本章开头发出的相同错误请求来测试一下。你现在应该会看到我们新的、定制化的错误消息，类似于这样：

```
### Send some XML as the request body
$ curl -d '<?xml version="1.0" encoding="UTF-8"?><note><to>Alex</to></note>' localhost:4000/v1/movies
{
    "error": "body contains badly-formed JSON (at character 1)"
}

### Send some malformed JSON (notice the trailing comma)
$ curl -d '{"title": "Moana", }' localhost:4000/v1/movies
{
    "error": "body contains badly-formed JSON (at character 20)"
}

### Send a JSON array instead of an object
$ curl -d '["foo", "bar"]' localhost:4000/v1/movies
{
    "error": "body contains incorrect JSON type (at character 1)"
}

### Send a numeric 'title' value (instead of string)
$ curl -d '{"title": 123}' localhost:4000/v1/movies
{
    "error": "body contains incorrect JSON type for \"title\""
}

### Send an empty request body
$ curl -X POST localhost:4000/v1/movies
{
    "error": "body must not be empty"
}
```

```
package main

...

func (app *application) createMovieHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title   string  `json:"title"`
        Year    int32   `json:"year"`
        Runtime int32   `json:"runtime"`
        Genres  []string `json:"genres"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        // Use the new badRequestResponse() helper.
        app.badRequestResponse(w, r, err)
        return
    }

    fmt.Fprintf(w, "%+v\n", input)
}

...
```

这是一个小改动，但很有用。随着我们的应用程序逐渐变得更加复杂，使用这样的专用辅助函数来管理不同类型的错误，将有助于确保我们所有端点的错误响应保持一致。

## 附加信息

### Panic 与返回错误

在 `readJSON()` 辅助函数中，如果遇到 `json.InvalidUnmarshalError` 错误就触发 panic，这个决定并非轻率之举。你可能也知道，在 Go 中，通常认为最佳实践是返回错误并优雅地处理它们。

但是——*在某些特定情况下*——触发 panic 是可以的。当合理时，你不应该对*不触发 panic* 过于教条。

在这里，区分应用程序可能遇到的两类错误是有帮助的。

第一类错误是*预期错误*，可能在正常操作期间发生。预期错误的一些例子包括由数据库查询超时、网络资源不可用或用户输入错误引起的错误。这些错误并不一定意味着你的程序本身有问题——事实上，它们通常是由程序无法控制的因素引起的。在几乎所有情况下，返回这类错误并优雅地处理它们都是良好的实践。

另一类错误是*意外错误*。这些错误在正常操作期间不应发生，如果发生了，很可能是开发人员错误或代码库中的逻辑错误导致的。这些错误确实是例外情况，在这种情况下使用 panic 被更广泛地接受。事实上，Go

幸运的是，Go 的 `json.Decoder` 提供了一个 `DisallowUnknownFields()` 设置，我们可以用它来在发生这种情况时生成错误。

我们遇到的另一个问题是，`json.Decoder` 被设计为支持 JSON 数据*流*。当我们对请求体调用 `Decode()` 时，它实际上只从请求体中读取*第一个 JSON 值*并对其进行解码。如果我们第二次调用 `Decode()`，它会读取并解码第二个值，依此类推。

但由于我们在 `readJSON()` 辅助函数中只调用一次 `Decode()`——而且仅此一次——请求体中第一个 JSON 值之后的任何内容都会被忽略。这意味着你可以发送包含多个 JSON 值的请求体，或者在第一个 JSON 值之后包含垃圾内容，而我们的 API 处理器不会引发错误。例如：

```
### Body contains multiple JSON values
$ curl -i -d '{"title": "Moana"}{"title": "Top Gun"}'
localhost:4000/v1/movies
HTTP/1.1 200 OK
Date: Tue, 06 Apr 2021 18:53:57 GMT
Content-Length: 41
Content-Type: text/plain; charset=utf-8

{Title:Moana Year:0 Runtime:0 Genres:[]}

### Body contains garbage content after the first JSON value
$ curl -i -d '{"title": "Moana"} :~()' localhost:4000/v1/movies
HTTP/1.1 200 OK
Date: Tue, 06 Apr 2021 18:54:15 GMT
Content-Length: 41
```

```
Content-Type: text/plain; charset=utf-8

{Title:Moana Year:0 Runtime:0 Genres:[]}
```

同样，这种行为可能非常有用，但不适合我们的用例。我们希望发送到 `createMovieHandler` 处理器的请求在请求体中只包含一个 JSON 对象，其中包含要在系统中创建的电影信息。

为了确保请求体中没有额外的 JSON 值（或任何其他内容），我们需要在 `readJSON()` 辅助函数中第二次调用 `Decode()`，并检查它是否返回 `io.EOF`（文件结束）错误。

最后，目前我们接受的请求体最大大小没有上限。这意味着我们的 `createMovieHandler` 会成为那些希望对我们的 API 执行拒绝服务攻击的恶意客户端的良好目标。我们可以通过使用 `http.MaxBytesReader()` 函数来限制请求体的最大大小，从而解决这个问题。

让我们更新 `readJSON()` 辅助函数来修复这三个问题：

```
File: cmd/api/helpers.go

package main

import (
    "encoding/json"
    "errors"
```





```go
"fmt"
"io"
"net/http"
"strconv"
"strings" // New import

"github.com/julienschmidt/httprouter"
)

...

func (app *application) readJSON(w http.ResponseWriter, r *http.Request, dst interface{}) error {
    // Use http.MaxBytesReader() to limit the size of the request body to 1MB.
    maxBytes := 1_048_576
    r.Body = http.MaxBytesReader(w, r.Body, int64(maxBytes))

    // Initialize the json.Decoder, and call the DisallowUnknownFields() method on it
    // before decoding. This means that if the JSON from the client now includes any
    // field which cannot be mapped to the target destination, the decoder will return
    // an error instead of just ignoring the field.
    dec := json.NewDecoder(r.Body)
    dec.DisallowUnknownFields()

    // Decode the request body to the destination.
    err := dec.Decode(dst)
    if err != nil {
        var syntaxError *json.SyntaxError
        var unmarshalTypeError *json.UnmarshalTypeError
        var invalidUnmarshalError *json.InvalidUnmarshalError

        switch {
        case errors.As(err, &syntaxError):
            return fmt.Errorf("body contains badly-formed JSON (at character %d)", syntaxError.Offset)
```
```
case errors.Is(err, io.ErrUnexpectedEOF):
    return errors.New("body contains badly-formed JSON")

case errors.As(err, &unmarshalTypeError):
    if unmarshalTypeError.Field != "" {
        return fmt.Errorf("body contains incorrect JSON type for field %q", unmarshalTypeError.Field)
    }
    return fmt.Errorf("body contains incorrect JSON type (at character %d)", unmarshalTypeError.Offset)

case errors.Is(err, io.EOF):
    return errors.New("body must not be empty")

    // If the JSON contains a field which cannot be mapped to the target destination
    // then Decode() will now return an error message in the format
    "json: unknown
    // field \"<name>\". We check for this, extract the field name from
    the error,
    // and interpolate it into our custom error message. Note that
    there's an open
    // issue at https://github.com/golang/go/issues/29035 regarding
    turning this
    // into a distinct error type in the future.
    case strings.HasPrefix(err.Error(), "json: unknown field "):
        fieldName := strings.TrimPrefix(err.Error(), "json: unknown field ")
        return fmt.Errorf("body contains unknown key %s", fieldName)

    // If the request body exceeds 1MB in size the decode will now fail
    with the
    // error "http: request body too large". There is an open issue about
    turning
    // this into a distinct error type at
    https://github.com/golang/go/issues/30715.
    case err.Error() == "http: request body too large":
        return fmt.Errorf("body must not be larger than %d bytes",
maxBytes)

    case errors.As(err, &invalidUnmarshalError):
        panic(err)

    default:
        return err
    }
}

    // Call Decode() again, using a pointer to an empty anonymous struct as the
    // destination. If the request body only contained a single JSON value this will
    // return an io.EOF error. So if we get anything else, we know that there is
    // additional data in the request body and we return our own custom error message.
    err = dec.Decode(&struct{}{})
    if err != io.EOF {
        return errors.New("body must only contain a single JSON value")
    }

    return nil
}
```

做完这些修改后，让我们再试一下本章前面提到的请求：

```
$ curl -d '{"title": "Moana", "rating":"PG"}' localhost:4000/v1/movies
{
    "error": "body contains unknown key \"rating\""
}

$ curl -d '{"title": "Moana"}{"title": "Top Gun"}' localhost:4000/v1/movies
```
```
{
  "error": "body must only contain a single JSON value"
}

$ curl -d '{"title": "Moana"} :~()' localhost:4000/v1/movies
{
  "error": "body must only contain a single JSON value"
}
```

现在这些处理得好多了——请求处理会被终止，客户端会收到一条清晰的错误消息，准确解释了问题所在。

最后，我们来尝试发送一个非常大的 JSON 请求体。

为了演示这一点，我创建了一个 1.5MB 的 JSON 文件，你可以运行以下命令将其下载到 `/tmp` 目录：

```
$ wget -O /tmp/largefile.json
https://www.alexedwards.net/static/largefile.json
```

如果你尝试将这个文件作为请求体发送到 `POST /v1/movies` 端点，`http.MaxBytesReader()` 检查就会生效，你应该会得到类似如下的响应：

```
$ curl -d @/tmp/largefile.json localhost:4000/v1/movies
{
```

## 自定义 JSON 解码

在本书前面，我们为 API 添加了一些自定义 JSON 编码行为，以便在 JSON 响应中以 "<runtime> mins" 的格式显示电影时长信息。

在本章中，我们将从另一个角度来看待这个问题，并更新我们的应用程序，使 `createMovieHandler` 接受这种格式的时长信息。

如果你现在就尝试发送一个带有这种电影时长格式的请求，你会得到 `400 Bad Request` 响应（因为无法将 JSON 字符串解码为 `int32` 类型）。如下所示：

```
$ curl -d '{"title": "Moana", "runtime": "107 mins"}'
localhost:4000/v1/movies
{
  "error": "body contains incorrect JSON type for \"runtime\""
}
```

要使其工作，我们需要做的是*拦截解码过程*，并手动将 "<runtime> mins" 这个 JSON 字符串转换为 `int32`。

那么我们该怎么做呢？

```go
package main

...

func (app *application) createMovieHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title   string       `json:"title"`
        Year    int32        `json:"year"`
        Runtime data.Runtime `json:"runtime"` // Make this field a data.Runtime type.
        Genres  []string     `json:"genres"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    fmt.Fprintf(w, "%+v\n", input)
}

...
```

然后，让我们打开 `internal/data/runtime.go` 文件，为我们 `Runtime` 类型添加一个 `UnmarshalJSON()` 方法。在这个方法中，我们需要解析格式为 "`<runtime> mins`" 的 JSON 字符串，将时长数字转换为 `int32`，然后将其赋值给 `Runtime` 值本身。

这实际上有点复杂，而且有一些重要细节，所以最好直接进入代码，并随着代码逐步用注释来解释。

## 验证 JSON 输入

在许多情况下，你会希望对来自客户端的数据执行额外的验证检查，以确保在处理之前符合你的特定业务规则。在本章中，我们将通过更新 `createMovieHandler` 来演示如何在 JSON API 中做到这一点，检查以下内容：

- 客户端提供的电影标题不能为空，并且不能超过 500 个字节。
- 电影年份不能为空，并且必须在 1888 年到当前年份之间。
- 电影时长不能为空，并且必须是一个正整数。
- 电影必须包含一至五个（不重复的）类型。

如果这些检查中有任何一项失败，我们就会向客户端发送一个 `422 Unprocessable Entity` 响应，并附带清晰描述验证失败的错误消息。

## 创建 validator 包

为帮助我们在整个项目中进行验证，我们将创建一个小的 `internal/validator` 包，其中包含一些简单的可复用辅助类型和函数。如果你正在跟着编码，请在机器上创建以下目录和文件：

```go
// New is a helper which creates a new Validator instance with an empty
errors map.
func New() *Validator {
    return &Validator{Errors: make(map[string]string)}
}

// Valid returns true if the errors map doesn't contain any entries.
func (v *Validator) Valid() bool {
    return len(v.Errors) == 0
}

// AddError adds an error message to the map (so long as no entry already
exists for
// the given key).
func (v *Validator) AddError(key, message string) {
    if _, exists := v.Errors[key]; !exists {
        v.Errors[key] = message
    }
}

// Check adds an error message to the map only if a validation check is not
'ok'.
func (v *Validator) Check(ok bool, key, message string) {
    if !ok {
        v.AddError(key, message)
    }
}

// In returns true if a specific value is in a list of strings.
func In(value string, list ...string) bool {
    for i := range list {
        if value == list[i] {
            return true
        }
    }
    return false
}

// Matches returns true if a string value matches a specific regexp pattern.
```





```
"^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?(?:\\.
[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?)*$"
```

在你的代码中，这个正则表达式模式应该全部在同一行，且没有空白字符。

## 执行验证检查

好了，让我们开始使用 Validator 类型吧！

我们需要做的第一件事是更新我们的 `cmd/api/errors.go` 文件，添加一个新的 `failedValidationResponse()` 辅助函数，该函数会写出 `422 Unprocessable Entity` 状态码，并将我们新的 `Validator` 类型中 errors map 的内容作为 JSON 响应体。

```
File: cmd/api/errors.go

package main

...

// Note that the errors parameter here has the type map[string]string, which is exactly
// the same as the errors map contained in our Validator type.
func (app *application) failedValidationResponse(w http.ResponseWriter, r *http.Request, errors map[string]string) {
    app.errorResponse(w, r, http.StatusUnprocessableEntity, errors)
}
```

完成之后，回到你的 createMovieHandler，更新它以对输入结构体执行必要的验证检查。如下所示：

```
File: cmd/api/movies.go

package main

import (
    "fmt"
    "net/http"
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator" // New import
)

func (app *application) createMovieHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title    string       `json:"title"`
        Year     int32        `json:"year"`
        Runtime  data.Runtime `json:"runtime"`
        Genres   []string     `json:"genres"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    // Initialize a new Validator instance.
    v := validator.New()
```

```
// Use the Check() method to execute our validation checks. This will add the
// provided key and error message to the errors map if the check does not evaluate
// to true. For example, in the first line here we "check that the title is not
// equal to the empty string". In the second, we "check that the length of the title
// is less than or equal to 500 bytes" and so on.
v.Check(input.Title != "", "title", "must be provided")
v.Check(len(input.Title) <= 500, "title", "must not be more than 500 bytes long")

v.Check(input.Year != 0, "year", "must be provided")
v.Check(input.Year >= 1888, "year", "must be greater than 1888")
v.Check(input.Year <= int32(time.Now().Year()), "year", "must not be in the future")

v.Check(input.Runtime != 0, "runtime", "must be provided")
v.Check(input.Runtime > 0, "runtime", "must be a positive integer")

v.Check(input.Genres != nil, "genres", "must be provided")
v.Check(len(input.Genres) >= 1, "genres", "must contain at least 1 genre")
v.Check(len(input.Genres) <= 5, "genres", "must not contain more than 5 genres")
// Note that we're using the Unique helper in the line below to check that all
// values in the input.Genres slice are unique.
v.Check(validator.Unique(input.Genres), "genres", "must not contain duplicate values")

// Use the Valid() method to see if any of the checks failed. If they did, then use
// the failedValidationResponse() helper to send a response to the client, passing
// in the v.Errors map.
if !v.Valid() {
```

```
app.failedValidationResponse(w, r, v.Errors)
    return
}

    fmt.Fprintf(w, "%+v\n", input)
}
...
```

完成这些后，我们应该可以尝试一下了。重启 API，然后向 POST /v1/movies 端点发出一个包含无效数据的请求。类似如下：

```
$ BODY='{"title":"","year":1000,"runtime":"-123 mins","genres":["sci-fi","sci-fi"]}'
$ curl -i -d "$BODY" localhost:4000/v1/movies
HTTP/1.1 422 Unprocessable Entity
Content-Type: application/json
Date: Wed, 07 Apr 2021 10:33:57 GMT
Content-Length: 180

{
  "error": {
    "genres": "must not contain duplicate values",
    "runtime": "must be a positive integer",
    "title": "must be provided",
    "year": "must be greater than 1888"
  }
}
```

看起来很棒。我们的验证检查正在工作，并阻止了请求被成功执行——甚至更好——客户端会得到一个格式良好的 JSON 响应，其中包含清晰、信息丰富的错误消息，指出了每个问题。

如果你愿意，也可以尝试发送一个有效的请求。你会发现所有检查都成功通过，`input` 结构体会像之前一样被输出到 HTTP 响应中：

```
$ BODY='{"title":"Moana","year":2016,"runtime":"107 mins","genres":["animation","adventure"]}'
$ curl -i -d "$BODY" localhost:4000/v1/movies
HTTP/1.1 200 OK
Date: Wed, 07 Apr 2021 10:35:40 GMT
Content-Length: 65
Content-Type: text/plain; charset=utf-8

{Title:Moana Year:2016 Runtime:107 Genres:[animation adventure]}
```

## 使验证规则可重用

在大型项目中，你很可能希望在多个地方重用一些相同的验证检查。在我们的例子中——例如——当客户端*编辑*电影数据时，我们以后会用到许多相同的检查。

为了避免重复，我们可以将电影的验证检查收集到一个独立的 `ValidateMovie()` 函数中。理论上，这个函数几乎可以存在于我们代码库的任何地方——位于 `cmd/api/movies.go` 文件中的处理器旁边，或者可能在 `internal/validators` 包中。但就个人而言，我喜欢将验证检查放在 `internal/data` 包中，靠近相关的领域类型。

如果你在跟着做，请重新打开 `internal/data/movies.go` 文件，并添加一个 `ValidateMovie()` 函数，其中包含如下检查：

```
File: internal/data/movies.go

package data

import (
    "time"

    "greenlight.alexedwards.net/internal/validator" // New import
)

type Movie struct {
    ID        int64     `json:"id"`
    CreatedAt time.Time `json:"-"`
    Title     string    `json:"title"`
    Year      int32     `json:"year,omitempty"`
    Runtime   Runtime   `json:"runtime,omitempty"`
    Genres    []string  `json:"genres,omitempty"`
    Version   int32     `json:"version"`
}

func ValidateMovie(v *validator.Validator, movie *Movie) {
    v.Check(movie.Title != "", "title", "must be provided")
    v.Check(len(movie.Title) <= 500, "title", "must not be more than 500 bytes long")

    v.Check(movie.Year != 0, "year", "must be provided")
    v.Check(movie.Year >= 1888, "year", "must be greater than 1888")
    v.Check(movie.Year <= int32(time.Now().Year()), "year", "must not be in the future")
}
```

Title    string      `json:"title"`
Year     int32       `json:"year"`
Runtime  data.Runtime `json:"runtime"`
Genres   []string    `json:"genres"`
}

err := app.readJSON(w, r, &input)
if err != nil {
    app.badRequestResponse(w, r, err)
    return
}

// Copy the values from the input struct to a new Movie struct.
movie := &data.Movie{
    Title:    input.Title,
    Year:     input.Year,
    Runtime:  input.Runtime,
    Genres:   input.Genres,
}

// Initialize a new Validator.
v := validator.New()

// Call the ValidateMovie() function and return a response containing the errors if
// any of the checks fail.
if data.ValidateMovie(v, movie); !v.Valid() {
    app.failedValidationResponse(w, r, v.Errors)
    return
}

fmt.Fprintf(w, "%+v\n", input)
}
...

当你看到这段代码时，脑海中可能会出现几个问题。

首先，你可能想知道为什么我们在处理器中初始化 `Validator` 实例并将其传递给 `ValidateMovie()` 函数——而不是在 `ValidateMovie()` 中初始化它并将其作为返回值传递回来。

这是因为随着应用程序变得越来越复杂，我们需要从处理器调用*多个*验证辅助函数，而不是像上面那样只调用一个。因此，在处理器中初始化 `Validator` 并进行传递，为我们提供了更大的灵活性。

你可能还会想，为什么我们要将 JSON 请求解码到 `input` 结构体中，然后复制数据，而不是直接解码到 `Movie` 结构体中。

直接解码到 `Movie` 结构体的问题是，客户端可能会在其 JSON 请求中提供 `id` 和 `version` 键，并且相应的值会*毫无差错地*被解码到 `Movie` 结构体的 `ID` 和 `Version` 字段中——即使我们不希望如此。我们*可以*在事后检查 `Movie` 结构体中必要的字段，以确保它们是空的，但这感觉有点 hacky，而解码到一个中间结构体（就像我们在处理器中所做的那样）是一种更干净、更简单、更健壮的方法——尽管稍显冗长。

好了，这些解释说完后，你应该能够再次启动应用程序，并且从客户端角度来看，一切应该和以前一样工作。如果你发出无效请求，




第5章

## 数据库设置与配置

在本书的下一部分，我们将继续推进项目构建，并设置一个 SQL 数据库来持久化存储我们的电影数据。

与第一本 *Let's Go* 书（我们在其中使用 MySQL 作为数据库）不同，这次我们将使用 PostgreSQL。它是开源的、非常可靠，并拥有一些有用的现代特性——包括对数组和 JSON 数据类型、全文搜索以及地理空间查询的支持。在构建过程中，我们将使用其中一些现代 PostgreSQL 特性。

在本节中，你将学习：

- 如何在本地机器上安装和设置 PostgreSQL。
- 如何使用 `psql` 交互工具创建数据库、PostgreSQL 扩展和用户账户。
- 如何在 Go 中初始化数据库连接池并配置其设置以提高性能和稳定性。

安装期间，你的计算机上应该也已经创建了一个名为 `postgres` 的*操作系统*用户。在基于 Unix 的系统上，你可以通过检查 `/etc/passwd` 文件来确认这一点，如下所示：

```
$ cat /etc/passwd | grep 'postgres'
postgres:x:127:134:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
```

这很重要，因为默认情况下，PostgreSQL 对来自本地机器的任何连接使用一种称为*对等认证*的认证方案。对等认证意味着，如果当前操作系统用户的用户名与有效的 PostgreSQL 用户用户名匹配，他们就可以作为该用户登录 PostgreSQL，而无需进一步认证。整个过程不涉及密码。

因此，如果我们切换到名为 `postgres` 的*操作系统*用户，我们就应该能够使用 `psql` 连接 PostgreSQL，而无需任何进一步认证。事实上，你可以通过以下命令一步完成这两件事：

```
$ sudo -u postgres psql
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
Type "help" for help.

postgres=#
```

**提示：** 在 PostgreSQL 中，`\` 字符表示一个*元命令*。其他一些有用的元命令包括 `\l` 用于列出所有数据库，`\dt` 用于列出表，`\du` 用于列出用户。你还可以运行 `\?` 查看所有可用元命令的完整列表。

现在我们已经创建了 `greenlight` 数据库并连接到了它，还有几项任务需要完成。

第一个任务是创建一个新的 `greenlight` 用户，该用户没有超级用户权限，我们可以使用它来执行 SQL 迁移并从 Go 应用程序连接到数据库。我们希望将这个新用户设置为使用*基于密码*的认证，而不是对等认证。

PostgreSQL 还有*扩展*的概念，这些扩展在标准功能之上增加了额外的特性。随 PostgreSQL 一起提供的扩展列表可以在此处找到，还有一些其他扩展你可以单独下载。

在这个项目中，我们将使用 `citext` 扩展。它为 PostgreSQL 添加了一种不区分大小写的字符串类型，我们将在本书后面使用它来存储用户电子邮件地址。需要注意，扩展只能由*超级用户*添加到*特定数据库*中。

请继续运行以下命令，创建一个带特定密码的新 `greenlight` 用户，并将 `citext` 扩展添加到我们的数据库中：

```
greenlight=# CREATE ROLE greenlight WITH LOGIN PASSWORD 'pa55word';
CREATE ROLE
greenlight=# CREATE EXTENSION IF NOT EXISTS citext;
CREATE EXTENSION
```

> **重要：** 如果你在跟着操作，请务必记住你为 `greenlight` 用户设置的密码。你在接下来的步骤中会用到它。

成功完成后，你可以输入 `exit` 或 `\q` 关闭基于终端的界面，并恢复为正常的操作系统用户。

```
greenlight=# exit
```

### 以新用户身份连接

在继续之前，让我们先证明一切设置正确，尝试以 `greenlight` 用户身份连接到 `greenlight` 数据库。当系统提示时，输入你在上述步骤中设置的密码。

```
$ psql --host=localhost --dbname=greenlight --username=greenlight
Password for user greenlight:
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256,
compression: off)
Type "help" for help.

greenlight=> SELECT current_user;
 current_user
-------------
 greenlight
(1 row)

greenlight=> exit
```

太好了！这确认了我们的数据库和带有密码凭据的新 greenlight 用户工作正常，我们能够以该用户身份毫无问题地执行 SQL 语句。

## 补充信息

### 优化 PostgreSQL 设置

PostgreSQL 自带的默认设置相当保守，你通常可以通过调整 `postgresql.conf` 文件中的值来提高数据库的性能。

你可以通过以下 SQL 查询检查你的 `postgresql.conf` 文件所在位置：

```
$ sudo -u postgres psql -c 'SHOW config_file;'
        config_file
------------------------------------
/etc/postgresql/13/main/postgresql.conf
(1 row)
```

这篇文章很好地介绍了 PostgreSQL 的一些最重要设置，并指导了哪些值可以作为合理的起始点。如果你对优化 PostgreSQL 感兴趣，我建议你读一读这篇文章。

或者，你可以使用这个基于 Web 的工具，根据你可用的系统硬件生成建议值。这个工具的一个好功能是，它还会输出 `ALTER SYSTEM` SQL 语句，你可以对数据库运行这些语句来更改设置，而无需手动修改 `postgresql.conf` 文件。

## 连接到 PostgreSQL

好的，现在我们的新 `greenlight` 数据库已经设置好了，让我们看看如何从 Go 应用程序连接到它。

你可能还记得 *Let's Go* 中的内容，要使用 SQL 数据库，我们需要使用一个*数据库驱动*作为 Go 与数据库本身之间的“中间人”。你可以在 Go wiki 中找到 PostgreSQL 可用驱动列表，但在我们的项目中，我们将选择流行、可靠且成熟的 `pq` 包。

如果你在跟着本书编码，那么请使用 `go get` 下载 `pq` 的 `v1.10.0` 版本，如下所示：

```
$ go get github.com/lib/pq@v1.10.0
go: downloading github.com/lib/pq v1.10.0
go get: added github.com/lib/pq v1.10.0
```

要连接数据库，我们还需要一个*数据源名称*（DSN），它基本上是一个包含必要连接参数字符串。DSN 的确切格式取决于你使用的数据库驱动（应该在驱动文档中描述），但使用 `pq` 时，你应该能够使用以下 DSN 以 `greenlight` 用户身份连接到本地 `greenlight` 数据库：

```
postgres://greenlight:pa55word@localhost/greenlight
```

### 建立连接池

我们将用于从 Go 应用程序连接到 `greenlight` 数据库的代码与第一本 *Let's Go* 书中的几乎完全相同。因此我们不会赘述细节，希望这一切都会让人感到非常熟悉。

在高层次上：

- 我们希望 DSN 在运行时是可配置的，因此我们会通过命令行标志将其传递给应用程序，而不是硬编码。为了在开发期间简化，我们将使用上面的 DSN 作为该标志的默认值。
- 在我们的 `cmd/api/main.go` 文件中，我们将创建一个新的 `openDB()` 辅助函数。在这个辅助函数中，我们将使用 `sql.Open()` 函数建立一个新的 `sql.DB` 连接池，然后——因为到数据库的连接是按需惰性建立的，仅在首次需要时建立——我们还需要使用 `db.PingContext()` 方法来真正创建一个连接并验证一切设置正确。

让我们回到 `cmd/api/main.go` 文件并按如下方式更新它：

```
File: cmd/api/main.go
```




```
package main

import (
    "context"    // New import
    "database/sql" // New import
    "flag"
    "fmt"
    "log"
    "net/http"
    "os"
    "time"

    // Import the pq driver so that it can register itself with the
    // database/sql package. Note that we alias this import to the blank identifier, to
    // stop the Go
    // compiler complaining that the package isn't being used.
    _ "github.com/lib/pq"
)

const version = "1.0.0"

// Add a db struct field to hold the configuration settings for our database
// connection
// pool. For now this only holds the DSN, which we will read in from a
// command-line flag.
type config struct {
    port int
    env  string
    db   struct {
        dsn string
    }
}

type application struct {
    config config
    logger *log.Logger
}
```

```
config: cfg,
    logger: logger,
}

srv := &http.Server{
    Addr:         fmt.Sprintf(":%d", cfg.port),
    Handler:      app.routes(),
    IdleTimeout:  time.Minute,
    ReadTimeout:  10 * time.Second,
    WriteTimeout: 30 * time.Second,
}

logger.Printf("starting %s server on %s", cfg.env, srv.Addr)
// Because the err variable is now already declared in the code above, we need
// to use the = operator here, instead of the := operator.
err = srv.ListenAndServe()
logger.Fatal(err)
}

// The openDB() function returns a sql.DB connection pool.
func openDB(cfg config) (*sql.DB, error) {
    // Use sql.Open() to create an empty connection pool, using the DSN from the config
    // struct.
    db, err := sql.Open("postgres", cfg.db.dsn)
    if err != nil {
        return nil, err
    }

    // Create a context with a 5-second timeout deadline.
    ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
    defer cancel()

    // Use PingContext() to establish a new connection to the database,
    passing in the
    // context we created above as a parameter. If the connection couldn't be
    // established successfully within the 5 second deadline, then this will
return an
```

目前，我们的 DSN 的命令行标志默认值被显式地写成 `cmd/api/main.go` 文件中的一个字符串。

尽管 DSN 中的用户名和密码只是用于你本地机器上的开发数据库，但最好还是不要将这些信息硬编码到我们的项目文件中（这些文件将来可能会被共享或分发）。

因此，让我们采取一些步骤，将 DSN 从项目代码中解耦出来，改为将其存储为你本地机器上的一个环境变量。

如果你正在跟着操作，请新建一个 `GREENLIGHT_DB_DSN` 环境变量，将下面这一行添加到你的 `$HOME/.profile` 或 `$HOME/.bashrc` 文件中：

```
File: $HOME/.profile

...

export GREENLIGHT_DB_DSN='postgres://greenlight:pa55word@localhost/greenlight'
```

完成后，你需要重启电脑；或者——如果现在不方便——在你刚刚编辑过的文件上运行 `source` 命令以使更改生效。例如：

```
$ source $HOME/.profile
```

> **注意：** 运行 `source` 只会影响*当前终端窗口*。因此，如果你切换到另一个终端窗口，你需要再次运行它才能生效。

无论采用哪种方式，一旦你重启或运行了 `source`，你应该就能在终端中通过运行 `echo` 命令看到 `GREENLIGHT_DB_DSN` 环境变量的值。如下所示：

```
$ echo $GREENLIGHT_DB_DSN
postgres://greenlight:pa55word@localhost/greenlight
```

现在，让我们更新 `cmd/api/main.go` 文件，使用 `os.Getenv()` 函数访问该环境变量，并将其设置为 DSN 命令行标志的默认值。

实际操作起来相当简单：

```
File: cmd/api/main.go

package main

...

func main() {
    var cfg config
```

```
flag.IntVar(&cfg.port, "port", 4000, "API server port")
flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

// Use the value of the GREENLIGHT_DB_DSN environment variable as the default value
// for our db-dsn command-line flag.
flag.StringVar(&cfg.db.dsn, "db-dsn", os.Getenv("GREENLIGHT_DB_DSN"), "PostgreSQL DSN")

flag.Parse()

...
}
```

如果你现在再次重启应用，你会发现它编译正常，并且和之前一样正常工作。

你还可以在运行应用时尝试指定 `-help` 标志。这应该会输出我们三个命令行标志的描述文本和默认值，包括从环境变量中读取的 DSN 值。类似这样：

```
$ go run ./cmd/api -help
Usage of /tmp/go-build417842398/b001/exe/api:
  -db-dsn string
      PostgreSQL DSN (default
"postgres://greenlight:pa55word@localhost/greenlight")
  -env string
      Environment (development|staging|production) (default "development")
  -port int
      API server port (default 4000)
```

## 补充信息
### 在 psql 中使用 DSN

将 DSN 存储为环境变量有一个额外的好处：你可以直接以 `greenlight` 用户的身份轻松连接到 `greenlight` 数据库，而不必在运行 `psql` 时手动指定所有连接选项。如下所示：

```
$ psql $GREENLIGHT_DB_DSN
psql (13.2 (Ubuntu 13.2-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

greenlight=>
```

## 配置数据库连接池

在第一本 *Let's Go* 书中，我们从较高的层面讨论了 `sql.DB` 连接池，并演示了如何使用它的核心原则。但在本章中，我们将深入探讨——解释连接池在后台是如何运作的，并探索可以用来改变和优化其行为的设置。

> **注意：** 本章包含相当多的理论内容，虽然有趣，但对应用构建并不*关键*。如果你觉得内容过于艰深，现在可以略读，之后再回来深入阅读。

那么，`sql.DB` 连接池究竟*是怎样*工作的？

最重要的是要理解，`sql.DB` 池包含两种类型的连接——‘使用中’（in-use）连接和‘空闲’（idle）连接。当你使用某个连接执行数据库任务（例如执行 SQL 语句或查询行）时，该连接会被标记为使用中；当任务完成后，该连接会被标记为空闲。

当你让 Go 执行数据库任务时，它首先会检查池中是否有可用的空闲连接。如果有一个可用，

风险在于，*连接池本身*会成为应用中的一个瓶颈。

但是，让连接数保持无限并不一定是最好的做法。默认情况下，PostgreSQL 对打开连接数有 100 个的硬性限制，如果在高负载下达到这个硬性限制，就会导致我们的 `pq` 驱动返回一个 "`sorry, too many clients already`" 错误。

> **注意：** 可以通过 `postgresql.conf` 文件中的 `max_connections` 设置来更改打开连接数的硬性限制。

为了避免这个错误，我们应该将连接池中的打开连接数限制在远低于 100 的水平，为其他也需要使用 PostgreSQL 的应用或会话留出足够的余量。

设置 `MaxOpenConns` 限制的另一个好处是，它可以起到一个非常基本的节流作用，防止数据库同时被大量任务淹没。

但设置限制有一个重要的告诫：如果达到了 `MaxOpenConns` 限制，且所有连接都处于使用中，那么任何后续的数据库任务都将被迫等待，直到某个连接变为空闲并标记为空闲。在我们的 API 场景下，用户的 HTTP 请求可能会在等待空闲连接时无限期“挂起”。因此，为了缓解这个问题，务必始终使用 `context.Context` 对象为数据库任务设置超时。我们将在本书后面解释如何做到这一点。



## SetConnMaxLifetime 方法

`SetConnMaxLifetime()` 方法设置 `ConnMaxLifetime` 限制——连接可被重用的最大时长。默认情况下，没有最大生命周期，连接将被永久重用。

例如，如果我们将 `ConnMaxLifetime` 设置为一小时，则意味着所有连接在首次创建后一小时将被标记为“已过期”，并且过期后无法再次重用。但请注意：

- 这并不能保证连接会在池中存在整整一小时；连接可能由于某种原因变得不可用并在之前被自动关闭。
- 连接在创建一小时后仍可能处于使用中——它只是不能在该时间之后*开始*被重用。
- 这不是空闲超时。连接将在首次创建后一小时过期——而不是最后一次变为空闲后一小时。
- Go 每秒运行一次后台清理操作，以从池中移除已过期的连接。

理论上，将 `ConnMaxLifetime` 保持为无限制（或设置较长的生命周期）有助于性能，因为它降低了需要从头创建新连接的可能性。但在某些情况下，强制执行更短的生命周期是有用的。例如：

- 如果你的 SQL 数据库对连接强制执行最大生命周期，则将 `ConnMaxLifetime` 设置为稍短的值是合理的。
- 为了帮助在负载均衡器后面平滑地切换数据库。

如果你决定为池设置 `ConnMaxLifetime`，重要的是要考虑到连接过期的频率（随后会被重新创建）。例如，如果池中有 100 个打开的连接且 `ConnMaxLifetime` 为 1 分钟，那么你的应用程序平均每秒可能最多杀死并重新创建 1.67 个连接。你不希望频率大到最终影响性能。

## SetConnMaxIdleTime 方法

`SetConnMaxIdleTime()` 方法（在 Go 1.15 中引入）设置 `ConnMaxIdleTime` 限制。其工作原理与 `ConnMaxLifetime` 非常相似，只是它设置的是连接在被标记为过期之前可以处于*空闲*状态的最长时间。默认情况下没有限制。

例如，如果我们将 `ConnMaxIdleTime` 设置为 1 小时，则自上次使用以来在池中空闲 1 小时的任何连接都将被标记为过期并由后台清理操作移除。

此设置非常有用，因为它意味着我们可以为池中的空闲连接数量设置相对较高的限制，但通过定期移除我们知道不再真正使用的空闲连接来释放资源。

## 付诸实践

这么多信息需要消化……在实践中这意味着什么？让我们将以上内容总结为一些可操作的要点。

- 1. 作为经验法则，你应该显式设置一个 `MaxOpenConns` 值。这应该舒适地低于数据库和基础设施对连接数量的任何硬性限制，你可能还希望将其保持在相对较低的水平以充当基础的节流。

对于本项目，我们将 `MaxOpenConns` 限制设置为 25 个连接。我发现这对于小型到中型的 Web 应用程序和 API 来说是一个合理的起点，但理想情况下你应该根据基准测试和负载测试的结果为你的硬件调整此值。

- 2. 通常，较高的 `MaxOpenConns` 和 `MaxIdleConns` 值会导致更好的性能。但收益递减，你应该意识到拥有过大的空闲连接池（其中连接不经常被重用）实际上可能导致性能下降和不必要的资源消耗。

因为 `MaxIdleConns` 应该始终小于或等于 `MaxOpenConns`，所以对于本项目我们也将 `MaxIdleConns` 限制为 25 个连接。

- 3. 为了缓解上述第 2 点的风险，你通常应该设置一个 `ConnMaxIdleTime` 值以移除长时间未使用的空闲连接。在本项目中我们将 `ConnMaxIdleTime` 时长设置为 15 分钟。

- 4. 除非你的数据库对连接生命周期强制执行硬性限制，或你需要它专门用于促进诸如平滑切换数据库之类的操作，否则将 `ConnMaxLifetime` 保持为无限制可能是可以的。两者在本项目中都不适用，因此我们将保持默认的无限制设置。

## 配置连接池

而不是硬编码这些设置，让我们更新 `cmd/api/main.go` 文件以将其作为命令行标志接受。

`ConnMaxIdleTime` 值的命令行标志特别有趣，因为我们希望它传达一个*时间段*，最终需要将其转换为 Go `time.Duration` 类型。这里有几个选项：

- 1. 我们可以使用整数来表示秒数（或分钟数）并将其转换为 `time.Duration`。
- 2. 我们可以使用表示时长的字符串——比如 "5s"（5 秒）或 "10m"（10 分钟）——然后使用 `time.ParseDuration()` 函数解析它。

这两种方法都可行，但在本项目中我们将采用选项 2。继续按如下方式更新 `cmd/api/main.go` 文件：

文件: cmd/api/main.go

```go
package main

...

// Add maxOpenConns, maxIdleConns and maxIdleTime fields to hold the
// configuration
// settings for the connection pool.
type config struct {
    port int
    env  string
    db   struct {
        dsn          string
        maxOpenConns int
        maxIdleConns int
        maxIdleTime  string
    }
}

...

func main() {
    var cfg config

    flag.IntVar(&cfg.port, "port", 4000, "API server port")
    flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

    flag.StringVar(&cfg.db.dsn, "db-dsn", os.Getenv("GREENLIGHT_DB_DSN"), "PostgreSQL DSN")

    // Read the connection pool settings from command-line flags into the config struct.
    // Notice the default values that we're using?
    flag.IntVar(&cfg.db.maxOpenConns, "db-max-open-conns", 25, "PostgreSQL max open connections")
flag.IntVar(&cfg.db.maxIdleConns, "db-max-idle-conns", 25, "PostgreSQL max idle connections")
    flag.StringVar(&cfg.db.maxIdleTime, "db-max-idle-time", "15m", "PostgreSQL max connection idle time")

    flag.Parse()

    ...
}

func openDB(cfg config) (*sql.DB, error) {
    db, err := sql.Open("postgres", cfg.db.dsn)
    if err != nil {
        return nil, err
    }

    // Set the maximum number of open (in-use + idle) connections in the
pool. Note that
    // passing a value less than or equal to 0 will mean there is no limit.
    db.SetMaxOpenConns(cfg.db.maxOpenConns)

    // Set the maximum number of idle connections in the pool. Again, passing
a value
    // less than or equal to 0 will mean there is no limit.
    db.SetMaxIdleConns(cfg.db.maxIdleConns)

    // Use the time.ParseDuration() function to convert the idle timeout
duration string
    // to a time.Duration type.
    duration, err := time.ParseDuration(cfg.db.maxIdleTime)
    if err != nil {
        return nil, err
    }

    // Set the maximum idle timeout.
    db.SetConnMaxIdleTime(duration)

    ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
    defer cancel()

err = db.PingContext(ctx)
if err != nil {
    return nil, err
}

return db, nil
}
```

如果你现在重新运行应用程序，一切仍然应该正常工作。你不会真正注意到任何变化，目前我们也无法做太多来展示这些设置的影响。

但在本书后面我们会做一些负载测试，并解释如何使用 db.Stats() 方法实时监控连接池的状态。届时，你将能够看到本章中讨论的一些行为的实际表现。




## SQL 迁移

让我们回到本书下一节中更具体、更实际的内容，并着手在我们的`greenlight`数据库中创建一个`movies`表。

为此，我们可以再次简单地使用`psql`工具，对我们的数据库执行必要的`CREATE TABLE`语句。但相反，我们将探索如何使用*SQL 迁移*来创建表（以及更一般地，管理整个项目的数据库 Schema 变更）。

你将了解到：

-   SQL 迁移背后的高层原则，以及它们为什么有用。
-   如何使用命令行`migrate`工具以编程方式管理数据库 Schema 的变更。

```bash
$ curl -L https://github.com/golang-migrate/migrate/releases/download/v4.14.1/migrate.linux-amd64.tar.gz | tar xzv
$ mv migrate.linux-amd64 $GOPATH/bin/migrate
```

在继续之前，请在你的机器上尝试执行带`-version`标志的`migrate`二进制文件，检查它是否可用并正常工作。它应该输出类似于这样的当前版本号：

```bash
$ migrate -version
4.14.1
```

## 使用 SQL 迁移

现在`migrate`工具已安装，让我们通过在数据库中创建一个新的`movies`表来演示如何使用它。

我们需要做的第一件事是使用`migrate create`命令生成一对*迁移文件*。如果你正在跟着操作，请在终端中运行以下命令：

```
$ migrate create -seq -ext=.sql -dir=./migrations create_movies_table
/home/alex/Projects/greenlight/migrations/000001_create_movies_table.up.sql
/home/alex/Projects/greenlight/migrations/000001_create_movies_table.down.sql
```

在此命令中：

-   `-seq`标志表示我们希望为迁移文件使用顺序编号，如`0001`、`0002`、`...`（而不是默认的 Unix 时间戳）。
-   `-ext`标志表示我们希望给予迁移文件`.sql`扩展名。
-   `-dir`标志表示我们希望将迁移文件存储在`./migrations`目录中（如果该目录尚不存在，会自动创建）。

> 如上所述。实际上，我们本可以在第一对迁移文件中将`CHECK`约束与`CREATE TABLE`语句一起包含进来，但为了本书的目的，将它们放在第二个独立的迁移中有助于说明`migrate`工具的工作方式。

## 执行迁移

好了，现在我们准备对`greenlight`数据库运行两个“向上”迁移。

如果你正在跟着操作，请使用以下命令执行迁移，并从环境变量中传入数据库 DSN。如果一切设置正确，你应该会看到一些输出，确认迁移已成功执行。类似于这样：

```
$ migrate -path=./migrations -database=$GREENLIGHT_DB_DSN up
1/u create_movies_table (38.19761ms)
2/u add_movies_check_constraints (63.284269ms)
```

此时，不妨打开一个到数据库的连接，并使用`\dt`元命令列出表：

```
$ psql $GREENLIGHT_DB_DSN
Password for user greenlight:
```

```
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

greenlight=> \dt
```

| 模式 | 名称 | 类型 | 所有者 |
|---|---|---|---|
| public | movies | 表 | greenlight |
| public | schema_migrations | 表 | greenlight |

你应该看到`movies`表已经创建，同时还有一个`schema_migrations`表，两者都属于`greenlight`用户。

`schema_migrations`表由`migrate`工具自动生成，用于跟踪哪些迁移已被应用。让我们快速查看一下它的内容：

```
greenlight=> SELECT * FROM schema_migrations;
```

| version | dirty |
|---|---|
| 2 | f |

这里的`version`列表示我们按顺序编号一直到 2（含）的迁移文件都已在数据库中执行。`dirty`列的值为`false`，这表明迁移文件已被*无任何错误地*干净执行，且其中包含的 SQL 语句已被*完整地*成功应用。

如果你愿意，还可以对`movies`表运行`\d`元命令，查看表的结构并确认`CHECK`约束是否创建正确。操作如下：

```
greenlight-> \d movies
```

Table "public.movies"

| 列 | 类型 | 排序规则 | 可空 | 默认值 |
|---|---|---|---|---|
| id | bigint |  | not null | nextval('movies_id_seq'::regclass) |
| created_at | timestamp(0) with time zone |  | not null | now() |
| title | text |  | not null |  |
| year | integer |  | not null |  |
| runtime | integer |  | not null |  |
| genres | text[] |  | not null |  |
| version | integer |  | not null | 1 |

索引：
  "movies_pkey" PRIMARY KEY, btree (id)
检查约束：
  "genres_length_check" CHECK (array_length(genres, 1) >= 1 AND array_length(genres, 1) <= 5)
  "movies_runtime_check" CHECK (runtime >= 0)
  "movies_year_check" CHECK (year >= 1888 AND year::double precision <= date_part('year'::text, now()))

## 附加信息

### 迁移到特定版本

除了查看`schema_migrations`表之外，如果你想知道数据库当前处于哪个迁移版本，可以运行`migrate`工具的`version`命令，操作如下：

```
$ migrate -path=./migrations -database=$EXAMPLE_DSN version
2
```

你也可以使用`goto`命令向上或向下迁移到特定版本：

```
$ migrate -path=./migrations -database=$EXAMPLE_DSN goto 1
```

### 执行向下迁移

你可以使用`down`命令回滚指定数量的迁移。例如，要回滚*最近的迁移*，你可以运行：

```
$ migrate -path=./migrations -database=$EXAMPLE_DSN down 1
```

```go
package main

import (
    "context"
    "database/sql"
    "flag"
    "fmt"
    "log"
    "net/http"
    "os"
    "time"

    "github.com/golang-migrate/migrate/v4"
    "github.com/golang-migrate/migrate/v4/database/postgres"
    _ "github.com/golang-migrate/migrate/v4/source/file"
    _ "github.com/lib/pq"
)

func main() {
    ...

    db, err := openDB(cfg)
    if err != nil {
        logger.Fatal(err)
    }
    defer db.Close()

    logger.Printf("database connection pool established")

    migrationDriver, err := postgres.WithInstance(db, &postgres.Config{})
    if err != nil {
        logger.PrintFatal(err, nil)
    }

    migrator, err :=
    migrate.NewWithDatabaseInstance("file:///path/to/your/migrations",
    "postgres", migrationDriver)
```

```go
if err != nil {
    logger.PrintFatal(err, nil)
}

err = migrator.Up()
if err != nil && err != migrate.ErrNoChange {
    logger.PrintFatal(err, nil)
}

logger.Printf("database migrations applied")

...
}
```

尽管这种方法有效——而且最初可能看起来很有吸引力——但将迁移的执行与应用程序源代码紧密耦合，从长远来看可能会带来限制和问题。

《将数据库迁移与服务器启动解耦》这篇文章对此进行了很好的讨论，如果你对这个话题感兴趣，我建议你读一读。它侧重于 Python，但不要因此望而却步——同样的原则也适用于 Go 应用。





## 第 7 章

## CRUD 操作

在本书的这一部分中，我们将专注于为系统构建*创建、读取、更新和删除*电影的功能。

在接下来的几个章节中，我们会取得相当快的进展；到本部分结束时，以下 API 端点将全部完成并完全可用：

| 方法 | URL 模式 | 处理器 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用信息 |
| POST | /v1/movies | createMovieHandler | 创建一部新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |
| PUT | /v1/movies/:id | updateMovieHandler | 更新特定电影的详细信息 |
| DELETE | /v1/movies/:id | deleteMovieHandler | 删除特定电影 |

在本部分中，你将学到：

- 如何创建一个*数据库模型*，将针对你的数据库执行 SQL 查询的所有逻辑隔离开来。
- 如何在 API 的上下文中，对特定资源实现四种基本的 CRUD（创建、读取、更新和删除）操作。

// Define a MovieModel struct type which wraps a sql.DB connection pool.
type MovieModel struct {
    DB *sql.DB
}

// Add a placeholder method for inserting a new record in the movies table.
func (m MovieModel) Insert(movie *Movie) error {
    return nil
}

// Add a placeholder method for fetching a specific record from the movies table.
func (m MovieModel) Get(id int64) (*Movie, error) {
    return nil, nil
}

// Add a placeholder method for updating a specific record in the movies table.
func (m MovieModel) Update(movie *Movie) error {
    return nil
}

// Add a placeholder method for deleting a specific record from the movies table.
func (m MovieModel) Delete(id int64) error {
    return nil
}

作为额外的一步，我们将把 MovieModel 包裹在一个父级 Models 结构体中。这样做完全可选，但它有一个好处：能为你提供一个便捷的单一“容器”，随着应用的增长，它可以容纳并代表你的所有数据库模型。

如果你正在跟着操作，请创建一个新的 `internal/data/models.go` 文件并添加以下代码：

```
```bash
$ touch internal/data/models.go
```
```

文件：internal/data/models.go

```
```go
package data

import (
    "database/sql"
    "errors"
)

// Define a custom ErrRecordNotFound error. We'll return this from our Get() method when
// looking up a movie that doesn't exist in our database.
var (
    ErrRecordNotFound = errors.New("record not found")
)

// Create a Models struct which wraps the MovieModel. We'll add other models to this,
// like a UserModel and PermissionModel, as our build progresses.
type Models struct {
    Movies MovieModel
}

// For ease of use, we also add a New() method which returns a Models struct containing
// the initialized MovieModel.
func NewModels(db *sql.DB) Models {
    return Models{
```

```

}

func main() {
    var cfg config

    flag.IntVar(&cfg.port, "port", 4000, "API server port")
    flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

    flag.StringVar(&cfg.db.dsn, "db-dsn", os.Getenv("GREENLIGHT_DB_DSN"), "PostgreSQL DSN")

    flag.IntVar(&cfg.db.maxOpenConns, "db-max-open-conns", 25, "PostgreSQL max open connections")
    flag.IntVar(&cfg.db.maxIdleConns, "db-max-idle-conns", 25, "PostgreSQL max idle connections")
    flag.StringVar(&cfg.db.maxIdleTime, "db-max-idle-time", "15m", "PostgreSQL max connection idle time")

    flag.Parse()

    logger := log.New(os.Stdout, "", log.Ldate|log.Ltime)

    db, err := openDB(cfg)
    if err != nil {
        logger.Fatal(err)
    }

    defer db.Close()
    logger.Printf("database connection pool established")

    // Use the data.NewModels() function to initialize a Models struct,
    passing in the
    // connection pool as a parameter.
    app := &application{
        config: cfg,
        logger: logger,
        models: data.NewModels(db),
    }
}
```

这种总体结构也很容易扩展。将来当我们创建更多数据库模型时，只需将它们包含在 `Models` 结构体中，它们就会自动提供给我们的 API 处理器使用。

## 补充信息

### 模拟模型

只需对这个模式稍作调整，就可以支持为了单元测试而对数据库模型进行模拟（mock）。关于这一点，我们已经在 *Let’s Go* 中详细讨论过，所以我不想在这里重复同样的信息和指导。不过，作为一个快速示例，你可以创建一个类似于这样的 `MockMovieModel` 结构体：

```
File: internal/data/movies.go

package data

...

type MockMovieModel struct{}

func (m MockMovieModel) Insert(movie *Movie) error {
```

```
Insert(movie *Movie) error
Get(id int64) (*Movie, error)
Update(movie *Movie) error
Delete(id int64) error
    }
}

...

// Create a helper function which returns a Models instance containing the mock models
// only.
func NewMockModels() Models {
    return Models{
        Movies: MockMovieModel{},
    }
}
```

然后，在单元测试中需要用到它时，你可以调用 `NewMockModels()` 来替代“真正的” `NewModels()` 函数。

```
"time"

"greenlight.alexedwards.net/internal/validator"

"github.com/lib/pq" // New import
)

...

// The Insert() method accepts a pointer to a movie struct, which should
contain the
// data for the new record.
func (m MovieModel) Insert(movie *Movie) error {
    // Define the SQL query for inserting a new record in the movies table
    and returning
    // the system-generated data.
    query := `
        INSERT INTO movies (title, year, runtime, genres)
        VALUES ($1, $2, $3, $4)
        RETURNING id, created_at, version`

    // Create an args slice containing the values for the placeholder
    parameters from
    // the movie struct. Declaring this slice immediately next to our SQL
    query helps to
    // make it nice and clear *what values are being used where* in the
    query.
    args := []interface{}{movie.Title, movie.Year, movie.Runtime,
    pq.Array(movie.Genres)}

    // Use the QueryRow() method to execute the SQL query on our connection
    pool,
    // passing in the args slice as a variadic parameter and scanning the
    system-
    // generated id, created_at and version values into the movie struct.
    return m.DB.QueryRow(query, args...).Scan(&movie.ID, &movie.CreatedAt,
    &movie.Version)
}
```

```
...
```

这段代码既漂亮又简洁，但有几件重要的事情需要说明。

因为 `Insert()` 方法签名将 `*Movie` 指针作为参数，所以当我们调用 `Scan()` 读取系统生成的数据时，我们是在更新*参数所指向的位置*处的值。本质上，我们的 `Insert()` 方法会*修改*我们传入的 `Movie` 结构体，并将系统生成的值添加到其中。

接下来要讨论的是占位符参数输入，我们像这样在 `args` 切片中声明它们：

```
args := []interface{}{movie.Title, movie.Year, movie.Runtime,
pq.Array(movie.Genres)}
```

将输入存储在切片中并不是严格必需的，但正如上面代码注释中所提到的，这是一个很好的模式，有助于提高代码的清晰度。就我个人而言，对于占位符参数超过三个的 SQL 查询，我通常会这样做。

另外，你注意到切片中的最后一个值了吗？为了将我们的 `movie.Genres` 值（它是一个 `[]string` 切片）存储到数据库中，我们需要在执行 SQL 查询之前先让它通过 `pq.Array()` 适配器函数。

在底层，`pq.Array()` 适配器会获取我们的 `[]string` 切片，并将其转换为 `pq.StringArray` 类型。反过来，`pq.StringArray` 类型实现了 `driver.Valuer` 和 `sql.Scanner` 接口，这两个接口对于在我们的原生 `[]string` 切片与 PostgreSQL 数据库能够理解并存储在 `text[]` 数组列中的值之间进行相互转换是必需的。

**提示：** 在你的 Go 代码中，你也可以用同样的方式，将 `pq.Array()` 适配器函数用于 `[]bool`、`[]byte`、`[]int32`、`[]int64`、`[]float32` 和 `[]float64` 切片。

## 接入我们的 API 处理器

现在到了激动人心的部分。让我们将 `Insert()` 方法接入 `createMovieHandler`，使我们的 `POST /v1/movies` 端点完全可用。如下所示：

```
File: cmd/api/movies.go

```go
package main

...

func (app *application) createMovieHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title   string        `json:"title"`
        Year    int32         `json:"year"`
        Runtime data.Runtime  `json:"runtime"`
    }
```



## 附加信息

## $N 记法

PostgreSQL 占位符参数 $N 记法的一个不错的特性是，你可以在 SQL 语句的多个位置使用相同参数值。例如，像这样编写代码是完全可以接受的：

// This SQL statement uses the $1 parameter twice, and the value `123` will
be used in
// both locations where $1 appears.
stmt := "UPDATE foo SET bar = $1 + $2 WHERE bar = $1"
err := db.Exec(stmt, 123, 456)
if err != nil {
...
}

## 执行多条语句

偶尔你可能会发现自己处于想要在同一个数据库调用中执行多条 SQL 语句的位置，像这样：

```
stmt := `
    UPDATE foo SET bar = true;
    UPDATE foo SET baz = false;`
```

第 7.3 章。

## 获取电影

现在让我们继续进行 *获取并显示特定电影的数据* 的代码。

再次，我们将从这里的数据库模型开始，并开始更新 `Get()` 方法以执行以下 SQL 查询：

```
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE id = $1
```

因为我们的 `movies` 表使用 `id` 列作为其主键，所以此查询永远只会返回恰好一行数据库记录（或根本不返回）。因此，使用 Go 的 `QueryRow()` 方法再次执行此查询是合适的。

如果你跟随操作，请打开你的 `internal/data/movies.go` 文件并像这样更新它：

```
File: internal/data/movies.go

package data

import (
```
"database/sql"
"errors" // New import
"time"

"greenlight.alexedwards.net/internal/validator"

"github.com/lib/pq"
)

...

func (m MovieModel) Get(id int64) (*Movie, error) {
    // The PostgreSQL bigserial type that we're using for the movie ID starts
    // auto-incrementing at 1 by default, so we know that no movies will have ID values
    // less than that. To avoid making an unnecessary database call, we take
a shortcut
    // and return an ErrRecordNotFound error straight away.
    if id < 1 {
        return nil, ErrRecordNotFound
    }

    // Define the SQL query for retrieving the movie data.
    query := `
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        WHERE id = $1`

    // Declare a Movie struct to hold the data returned by the query.
    var movie Movie

    // Execute the query using the QueryRow() method, passing in the provided
id value
    // as a placeholder parameter, and scan the response data into the fields
of the
    // Movie struct. Importantly, notice that we need to convert the scan
target for the
    // genres column using the pq.Array() adapter function again.
    err := m.DB.QueryRow(query, id).Scan(
```
&movie.ID,
&movie.CreatedAt,
&movie.Title,
&movie.Year,
&movie.Runtime,
pq.Array(&movie.Genres),
&movie.Version,
)

// Handle any errors. If there was no matching movie found, Scan() will return
// a sql.ErrNoRows error. We check for this and return our custom ErrRecordNotFound
// error instead.
if err != nil {
    switch {
    case errors.Is(err, sql.ErrNoRows):
        return nil, ErrRecordNotFound
    default:
        return nil, err
    }
}

// Otherwise, return a pointer to the Movie struct.
return &movie, nil
}
...
```

希望上面的代码看起来清晰且熟悉——它直接取自我们在 *Let's Go* 中详细讨论过的模式。

唯一真正需要注意的是，我们在从

```
...
func (app *application) showMovieHandler(w http.ResponseWriter, r
*http.Request) {
    id, err := app.readIDParam(r)
    if err != nil {
        app.notFoundResponse(w, r)
        return
    }

    // Call the Get() method to fetch the data for a specific movie. We also
need to
    // use the errors.Is() function to check if it returns a
data.ErrRecordNotFound
    // error, in which case we send a 404 Not Found response to the client.
    movie, err := app.models.Movies.Get(id)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrRecordNotFound):
            app.notFoundResponse(w, r)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }

    err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

太好了！这都很简洁，得益于我们已经建立的结构和辅助函数。

```
{
  "error": "the requested resource could not be found"
}
```

## 附加信息

## 为什么不为电影 ID 使用无符号整数？

在 Get() 方法开始时，我们有以下检查电影 id 参数是否小于 1 的代码：

```
func (m MovieModel) Get(id int64) (*Movie, error) {
    if id < 1 {
        return nil, ErrRecordNotFound
    }
    ...
}
```

这可能会让你想知道：如果电影 ID 从不为负，为什么我们不在 Go 代码中使用无符号 uint64 类型来存储 ID，而不是 int64？

这有两个原因。

第一个原因是 *PostgreSQL 没有无符号整数*。通常将 Go 和数据库整数类型保持一致是明智的，以避免溢出或其他兼容性问题，因此由于 PostgreSQL 没有无符号整数，这意味着我们也应避免在 Go 代码中为读写 PostgreSQL 的任何值使用 `uint*` 类型。

相反，最好根据以下表格对齐整数类型：

| PostgreSQL 类型 | Go 类型 |
|---|---|
| `smallint`, `smallserial` | `int16` (-32768 到 32767) |
| `integer`, `serial` | `int32` (-2147483648 到 2147483647) |
| `bigint`, `bigserial` | `int64` (-9223372036854775808 到 9223372036854775807) |

还有另一个更微妙的原因。Go 的 `database/sql` 包实际上不支持大于 9223372036854775807（`int64` 的最大值）的任何整数值。`uint64` 值可能大于此值，这反过来会导致 Go 生成类似这样的运行时错误：

```
sql: converting argument $1 type: uint64 values with high bit set are not supported
```

通过在 Go 代码中坚持使用 `int64`，我们消除了 ever 遇到此错误的 risk。

## 更新电影

在本章中，我们将继续构建应用程序并添加一个全新的端点，允许客户端 *更新特定电影的数据*。

| 方法 | URL 模式 | 处理程序 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用程序信息 |
| POST | /v1/movies | createMovieHandler | 创建新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详情 |
| PUT | /v1/movies/:id | updateMovieHandler | 更新特定电影的详情 |

更精确地说，我们将设置端点，以便客户端可以编辑电影的 `title`、`year`、`runtime` 和 `genres` 值。在我们的项目中，`id` 和 `created_at` 值一旦创建就不应更改，并且 `version` 值不是客户端应控制的内容，因此我们不允许编辑这些字段。

目前，我们将配置此端点以对电影的值执行 *完全替换*。这意味着客户端需要在其 JSON 请求体中提供 *所有* 可编辑字段的值……即使他们只想更改其中一个。

例如，如果客户端想在数据库中为电影 *Black Panther* 添加类型 `sci-fi`，他们需要发送如下所示的 JSON 请求体：

```
{
  "title": "Black Panther",
  "year": 2018,
  "runtime": "134 mins",
  "genres": [
    "action",
    "adventure",
    "sci-fi"
  ]
}
```

## 执行 SQL 查询

让我们再次回到数据库模型，并编辑 `Update()` 方法以执行以下 SQL 查询：

```
UPDATE movies
SET title = $1, year = $2, runtime = $3, genres = $4, version = version + 1
WHERE id = $5
RETURNING version
```

这里注意我们正在查询的一部分中递增 `version` 值？然后在最后我们使用 `RETURNING` 子句来



返回这个新的、递增后的 `version` 值。

和之前一样，这个查询返回单行数据，因此我们也需要使用 Go 的 `QueryRow()` 方法来执行它。如果你在跟着做，请回到你的 `internal/data/movies.go` 文件，并按如下方式填写 `Update()` 方法：

```
File: internal/data/movies.go

package data

...

func (m MovieModel) Update(movie *Movie) error {
    // Declare the SQL query for updating the record and returning the new version
    // number.
    query := `
        UPDATE movies
        SET title = $1, year = $2, runtime = $3, genres = $4, version =
        version + 1
        WHERE id = $5
        RETURNING version`

    // Create an args slice containing the values for the placeholder parameters.
    args := []interface{}{
        movie.Title,
        movie.Year,
        movie.Runtime,
        pq.Array(movie.Genres),
        movie.ID,
    }

    // Use the QueryRow() method to execute the query, passing in the args
    // slice as a variadic parameter and scanning the new version value into the movie
    // struct.
    return m.DB.QueryRow(query, args...).Scan(&movie.Version)
}
...
```

需要强调的是——就像我们的 Insert() 方法一样——Update() 方法将指向 Movie 结构体的指针作为输入参数，并再次就地修改它——这次仅更新新的版本号。

## 创建 API 处理器

现在让我们回到 cmd/api/movies.go 文件，并更新它，以包含全新的 updateMovieHandler 方法。

| 方法 | URL 模式 | 处理器 | 操作 |
|--------|-------------|---------|--------|
| PUT | /v1/movies/:id | updateMovieHandler | 更新特定电影的详细信息 |

这个处理器的优点在于，我们已经为它打好了所有基础——我们在这里的工作主要就是把已经写好的代码和辅助函数连接起来，以处理请求。

具体来说，我们需要：

- 1. 使用 `app.readIDParam()` 辅助函数从 URL 中提取电影 ID。
- 2. 使用我们在上一章中编写的 `Get()` 方法从数据库中获取相应的电影记录。
- 3. 将包含更新后电影数据的 JSON 请求体读取到 `input` 结构体中。
- 4. 将数据从 `input` 结构体复制到电影记录中。
- 5. 使用 `data.ValidateMovie()` 函数检查更新后的电影记录是否有效。
- 6. 调用 `Update()` 方法将更新后的电影记录存储到数据库中。
- 7. 使用 `app.writeJSON()` 辅助函数将更新后的电影数据写入 JSON 响应。

那么，让我们直接开始吧：

```
File: cmd/api/movies.go

package main

...

func (app *application) updateMovieHandler(w http.ResponseWriter, r *http.Request) {
    // Extract the movie ID from the URL.
    id, err := app.readIDParam(r)
    if err != nil {
        app.notFoundResponse(w, r)
        return
    }
}

// Fetch the existing movie record from the database, sending a 404 Not Found
// response to the client if we couldn't find a matching record.
movie, err := app.models.Movies.Get(id)
if err != nil {
    switch {
    case errors.Is(err, data.ErrRecordNotFound):
        app.notFoundResponse(w, r)
    default:
        app.serverErrorResponse(w, r, err)
    }
    return
}

// Declare an input struct to hold the expected data from the client.
var input struct {
    Title    string       `json:"title"`
    Year     int32        `json:"year"`
    Runtime  data.Runtime `json:"runtime"`
    Genres   []string     `json:"genres"`
}

// Read the JSON request body data into the input struct.
err = app.readJSON(w, r, &input)
if err != nil {
    app.badRequestResponse(w, r, err)
    return
}

// Copy the values from the request body to the appropriate fields of the movie
// record.
movie.Title = input.Title
movie.Year = input.Year
movie.Runtime = input.Runtime
movie.Genres = input.Genres

// Validate the updated movie record, sending the client a 422 Unprocessable Entity
// response if any checks fail.
v := validator.New()

if data.ValidateMovie(v, movie); !v.Valid() {
    app.failedValidationResponse(w, r, v.Errors)
    return
}

// Pass the updated movie record to our new Update() method.
err = app.models.Movies.Update(movie)
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

// Write the updated movie record in a JSON response.
err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```

最后，为了收尾，我们还需要更新应用路由，以包含新的端点。如下所示：

```
File: cmd/api/routes.go

package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

router.NotFound = http.HandlerFunc(app.notFoundResponse)
router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)
router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
app.showMovieHandler)
// Add the route for the PUT /v1/movies/:id endpoint.
router.HandlerFunc(http.MethodPut, "/v1/movies/:id",
app.updateMovieHandler)

return router
}
```

## 使用新的端点

至此，我们现在可以尝试一下了！

为了演示，让我们继续使用本章开头给出的示例，将 *黑豹* 的记录更新为包含 `sci-fi` 类型。提醒一下，当前记录看起来像这样：

```
$ curl localhost:4000/v1/movies/2
{
    "movie": {
        "id": 2,
        "title": "Black Panther",
        "year": 2018,
        "runtime": "134 mins",
        "genres": [
            "action",
```

你还应该能够通过再次发出 GET `/v1/movies/2` 请求来验证更改是否已持久化，如下所示：

```
$ curl localhost:4000/v1/movies/2
{
  "movie": {
    "id": 2,
    "title": "Black Panther",
    "year": 2018,
    "runtime": "134 mins",
    "genres": [
      "sci-fi",
      "action",
      "adventure"
    ],
    "version": 2
  }
}
```

## 删除电影

在本章中，我们将添加最后一个 CRUD 端点，以便客户端可以从我们的系统中 *删除特定电影*。

| 方法 | URL 模式 | 处理器 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用信息 |
| POST | /v1/movies | createMovieHandler | 创建新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |
| PUT | /v1/movies/:id | updateMovieHandler | 更新特定电影的详细信息 |
| DELETE | /v1/movies/:id | deleteMovieHandler | 删除特定电影 |

与我们 API 中的其他端点相比，我们在这里要实现的行为相当直接。

- 如果 URL 中提供的 `id` 对应的电影存在于数据库中，我们希望删除相应的记录，并向客户端返回成功消息。
- 如果电影 `id` 不存在，我们希望向客户端返回 `404 Not Found` 响应。

```go
if err != nil {
    switch {
    case errors.Is(err, data.ErrRecordNotFound):
        app.notFoundResponse(w, r)
    default:
        app.serverErrorResponse(w, r, err)
    }
    return
}

// Return a 200 OK status code along with a success message.
err = app.writeJSON(w, http.StatusOK, envelope{"message": "movie successfully deleted"}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
```

注意：你可能更倾向于在这里发送一个空响应体和 `204 No Content` 状态码，而不是 `"movie successfully deleted"` 消息。这实际上取决于你的客户端是谁——如果它们是人类，那么发送一条类似上面的消息是一种很好的用户体验；如果它们是机器，那么 `204 No Content` 响应可能就足够了。

最后，我们需要在我们的 `cmd/api/routes.go` 文件中接入新路由：

```
File: cmd/api/routes.go
```




```go
package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.updateMovieHandler)
    // Add the route for the DELETE /v1/movies/:id endpoint.
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.deleteMovieHandler)

    return router
}
```

OK，让我们重新启动 API 并通过从电影数据库中删除 *Deadpool* 来试用此功能（如果你一直跟着操作的话，它应该具有 ID 为 3）。删除操作应该不会有任何问题，你应该会收到如下确认消息：

```bash
$ curl -X DELETE localhost:4000/v1/movies/3
{
    "message": "movie successfully deleted"
}
```

如果你重复相同的请求来删除已经被删除的电影，你现在应该会收到 404 Not Found 响应和错误消息。类似这样：

```
$ curl -X DELETE localhost:4000/v1/movies/3
{
  "error": "the requested resource could not be found"
}
```

## 高级 CRUD 操作

在本书的这一节中，我们将研究一些你可能希望为 API 提供的 CRUD 端点使用的更“高级”的模式。

You’ll learn:
- 如何支持对资源的 *partial* 更新（这样客户端只需发送想要更改的数据）。
- 如何使用 *optimistic concurrency control* 来避免两个客户端同时尝试更新同一资源时发生的竞态条件。
- 如何使用 *context timeouts* 来终止长时间运行的数据库查询并防止不必要的资源使用。

## 处理部分更新

在本章中，我们将更改 `updateMovieHandler` 的行为，使其支持电影记录的 *partial updates*。从概念上讲，这比进行 *complete replacement* 稍微复杂一些，这就是为什么我们首先用那种方法打下基础的原因。

例如，假设我们注意到数据库中 *The Breakfast Club* 的发行年份是错误的（实际上应该是 1985，而不是 1986）。如果我们能够发送一个只包含需要应用的更改的 JSON 请求，而不是所有电影数据，那就太好了，像这样：

```
{"year": 1985}
```

让我们快速看看如果现在尝试发送此请求会发生什么：

```
$ curl -X PUT -d '{"year": 1985}' localhost:4000/v1/movies/4
{
  "error": {
    "genres": "must be provided",
    "runtime": "must be provided",
    "title": "must be provided"
  }
}
```

正如我们在书中前面提到的，在解码请求体时，我们的 `input` 结构体中任何 *don’t* 具有对应 JSON 键/值对的字段都将保留其 `zero-value`。我们在验证期间恰好会检查这些零值并返回你上面看到的错误消息。

在部分更新的上下文中，这会导致一个问题。我们如何区分以下两种情况：
- 客户端 *providing a key/value pair which has a zero-value value* ——像 `{"title": ""}` ——在这种情况下，我们希望返回验证错误。
- 客户端在 JSON 中 *not providing a key/value pair* ——在这种情况下，我们希望‘skip’更新该字段但不发送验证错误。

为了帮助回答这个问题，让我们快速回顾一下不同 Go 类型的零值是什么。

| Go 类型 | 零值 |
|---|---|
| `int*`, `uint*`, `float*`, `complex` | `0` |
| `string` | `""` |
| `bool` | `false` |
| `func`, `array`, `slice`, `map`, `chan` 和 `pointers` | `nil` |

这里需要注意的关键点是，指针的零值为 nil。

所以——从理论上讲——我们可以将输入结构体中的字段更改为指针。然后，要查看客户端是否在 JSON 中提供了特定的键/值对，我们只需简单检查输入结构体中对应字段是否等于 nil 即可。

```
// Use pointers for the Title, Year and Runtime fields.
var input struct {
    Title   *string        `json:"title"`   // This will be nil if there is no corresponding key in the JSON.
    Year    *int32         `json:"year"`    // Likewise...
    Runtime *data.Runtime  `json:"runtime"` // Likewise...
    Genres  []string       `json:"genres"`  // We don't need to change this because slices already have the zero-value nil.
}
```

### 执行部分更新

让我们付诸实践，并按如下方式编辑我们的 updateMovieHandler 方法以支持部分更新：

```
File: cmd/api/movies.go
```

```go
package main

...

func (app *application) updateMovieHandler(w http.ResponseWriter, r *http.Request) {
    id, err := app.readIDParam(r)
    if err != nil {
        app.notFoundResponse(w, r)
        return
    }

    // Retrieve the movie record as normal.
    movie, err := app.models.Movies.Get(id)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrRecordNotFound):
            app.notFoundResponse(w, r)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }

    // Use pointers for the Title, Year and Runtime fields.
    var input struct {
        Title    *string        `json:"title"`
        Year     *int32         `json:"year"`
        Runtime  *data.Runtime  `json:"runtime"`
        Genres   []string       `json:"genres"`
    }

    // Decode the JSON as normal.
    err = app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }
}
```

```go
}

err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```

总结一下：我们已更改 `input` 结构体，使其所有字段现在都具有零值 `nil`。在解析 JSON 请求后，我们然后遍历 `input` 结构体字段，只有当新值 *not* 为 `nil` 时才更新电影记录。

除此之外，对于执行资源 *partial updates* 的 API 端点，使用 HTTP 方法 `PATCH` 而不是 `PUT`（`PUT` 用于完全替换资源）是合适的。

因此，在尝试新代码之前，让我们快速更新 `cmd/api/routes.go` 文件，使我们的 `updateMovieHandler` 仅用于 `PATCH` 请求。

```
File: cmd/api/routes.go

package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)
}
}
```

再一次，看起来不错。我们可以看到 `year` 值已正确更新，并且 `version` 数字已递增，但其他数据字段均未更改。

让我们也快速尝试相同的请求，但包含一个空的 `title` 值。在这种情况下，更新将被阻止，你应该会收到验证错误，如下所示：

```
$ curl -X PATCH -d '{"year": 1985, "title": ""}' localhost:4000/v1/movies/4
{
  "error": {
    "title": "must be provided"
  }
}
```

## 附加信息

## JSON 中的 Null 值

需要注意的一个特殊情况是，当客户端明确 *supplies a field in the JSON request with the value* `null` 时。在这种情况下，我们的处理程序将忽略该字段并将其视为未提供。

例如，以下请求将导致电影记录没有任何更改（除版本号递增之外）：

```
$ curl -X PATCH -d '{"title": null, "year": null}' localhost:4000/v1/movies/4
{
    "movie": {
        "id": 4,
        "title": "The Breakfast Club",
        "year": 1985,
        "runtime": "96 mins",
        "genres": [
            "drama"
        ],
        "version": 3
    }
}
```

在理想世界中，此类请求应返回某种验证错误。但——除非你编写自己的自定义 JSON 解析器——否则无法区分客户端在 JSON 中未提供键/值对，还是提供了值为 null 的情况。

在大多数情况下，probably 足够在端点的客户端文档中解释这种特殊情况的行为，并说明类似“JSON items with null values will be ignored and will remain unchanged”之类的话。




## 乐观并发控制

细心的你可能已经注意到我们 `updateMovieHandler` 中的一个小问题——如果两个客户端在完全相同的时间尝试更新同一条电影记录，就会存在竞态条件。

为了说明这一点，我们假设有两个客户端在使用我们的 API：Alice 和 Bob。Alice 想将 *The Breakfast Club* 的时长值更正为 97 分钟，而 Bob 想为同一部电影添加类型‘comedy’。

现在想象一下，Alice 和 Bob 在 *完全相同* 的时间发送这两个更新请求。正如我们在 *Let’s Go* 中解释的那样，Go 的 `http.Server` 会在自己的 goroutine 中处理每个 HTTP 请求，因此这种情况发生时，我们的 `updateMovieHandler` 中的代码将在两个不同的 goroutine 中并发运行。

让我们逐步分析在此场景下可能发生的情况：

- 1. Alice 的 goroutine 调用 `app.models.Movies.Get()` 来检索电影记录的副本（版本号为 `N`）。
- 2. Bob 的 goroutine 调用 `app.models.Movies.Get()` 来检索电影记录的副本（仍然是版本 `N`）。
- 3. Alice 的 goroutine 在其电影记录副本中将时长更改为 97 分钟。
- 4. Bob 的 goroutine 在其电影记录副本中更新类型以包含‘comedy’。
- 5. Alice 的 goroutine 使用其电影记录副本调用 `app.models.Movies.Update()`。电影记录被写入数据库，版本号递增到 `N+1`。
- 6. Bob 的 goroutine 使用其电影记录副本调用 `app.models.Movies.Update()`。电影记录被写入数据库，版本号递增到 `N+2`。

尽管进行了两次独立的更新，最终只有 Bob 的更新会反映在数据库中，因为两个 goroutine 在 *竞争* 修改。Alice 对电影时长的更新会在 Bob 的更新用旧的时长值覆盖它时丢失。而且这会静默发生——没有任何信息通知 Alice 或 Bob 存在问题。

> **注意：** 这种特定类型的竞态条件被称为 *数据竞争*。当两个或多个 goroutine 同时尝试使用一段共享数据（在此示例中为电影记录）时，如果它们操作的结果取决于调度器执行指令的确切顺序，就会发生数据竞争。

## 防止数据竞争

现在我们理解了数据竞争的存在以及其发生的原因，*我们如何防止它？*

有几种选择，但在此情况下最简单、最干净的方法是使用基于电影记录中版本号的乐观锁形式。

修复方法如下：

- 1. Alice 和 Bob 的 goroutine 都调用 `app.models.Movies.Get()` 来检索电影记录的副本。这两个记录的版本号均为 `N`。
- 2. Alice 和 Bob 的 goroutine 对电影记录做出各自的更改。
- 3. Alice 和 Bob 的 goroutine 使用其电影记录副本调用 `app.models.Movies.Update()`。但只有在 *数据库中的版本号仍为 N* 时才会执行更新。如果它已更改，则我们不执行更新，而是向客户端发送错误消息。

这意味着第一个到达数据库的更新请求将成功，而进行第二次更新的人将收到错误消息，而不是应用其更改。

为了使其工作，我们需要更改更新电影的 SQL 语句，使其如下所示：

```sql
UPDATE movies
SET title = $1, year = $2, runtime = $3, genres = $4, version = version + 1
WHERE id = $5 AND version = $6
RETURNING version
```

注意，在 `WHERE` 子句中，我们现在正在查找具有特定 ID *和特定版本号* 的记录？

如果找不到匹配的记录，此查询将导致 `sql.ErrNoRows` 错误，我们知道版本号已被更改（或记录已被完全删除）。无论哪种情况，这都是一种 *编辑冲突*，我们可以用它作为触发器向客户端发送适当的错误响应。

## 实现乐观锁

好了，理论就讲到这里……让我们付诸实践！

我们将首先创建一个自定义的 `ErrEditConflict` 错误，以便在发生冲突时从数据库模型中返回。我们稍后在处理用户记录时也会使用它，因此将其定义在 `internal/data/models.go` 文件中是有意义的，如下所示：

文件：internal/data/models.go

```go
package data

import (
    "database/sql"
    "errors"
)

var (
    ErrRecordNotFound = errors.New("record not found")
    ErrEditConflict   = errors.New("edit conflict")
)
```

接下来让我们更新数据库模型的 Update() 方法以执行新的 SQL 查询并处理找不到匹配记录的情况。

文件：internal/data/movies.go

```go
package data

...

func (m MovieModel) Update(movie *Movie) error {
    // Add the 'AND version = $6' clause to the SQL query.
    query := `
        UPDATE movies
        SET title = $1, year = $2, runtime = $3, genres = $4, version =
        version + 1
        WHERE id = $5 AND version = $6
        RETURNING version`

    args := []interface{}{
        movie.Title,
        movie.Year,
        movie.Runtime,
        pq.Array(movie.Genres),
        movie.ID,
        movie.Version, // Add the expected movie version.
    }

    // Execute the SQL query. If no matching row could be found, we know the movie
    // version has changed (or the record has been deleted) and we return our custom
    // ErrEditConflict error.
    err := m.DB.QueryRow(query, args...).Scan(&movie.Version)
    if err != nil {
        switch {
        case errors.Is(err, sql.ErrNoRows):
            return ErrEditConflict
        default:
            return err
        }
    }

    return nil
}
...
```

接下来让我们前往 cmd/api/errors.go 文件并创建一个新的 editConflictResponse() 辅助函数。我们希望它发送 409 Conflict 响应，并附带用通俗英语解释问题的错误消息以告知客户端。

文件：cmd/api/errors.go

```go
package main

...

func (app *application) editConflictResponse(w http.ResponseWriter, r *http.Request) {
    message := "unable to update the record due to an edit conflict, please try again"
    app.errorResponse(w, r, http.StatusConflict, message)
}
```

然后作为最后一步，我们需要更改 `updateMovieHandler`，使其检查 `ErrEditConflict` 错误，并在必要时调用 `editConflictResponse()` 辅助函数。如下所示：

文件：cmd/api/movies.go

```go
package main

...

func (app *application) updateMovieHandler(w http.ResponseWriter, r *http.Request) {

    ...

    // Intercept any ErrEditConflict error and call the new editConflictResponse() helper.
    err = app.models.Movies.Update(movie)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrEditConflict):
            app.editConflictResponse(w, r)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }

    err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }

}
```

在这一点上，我们的 `updateMovieHandler` 现在应该已免受我们一直在讨论的竞态条件的影响。如果两个 goroutine 同时执行代码，第一个更新将成功，第二个将失败，因为数据库中的 `version` 号不再与预期值匹配。

让我们通过作为并发后台任务向我们的端点发出一对请求来试用此功能。假设你的终端足够紧密地一起执行请求，你会发现一个请求成功，另一个请求以 `409 Conflict` 状态码失败。

```
$ curl -i -X PATCH -d '{"runtime": "97 mins"}' "localhost:4000/v1/movies/4" &
\
curl -i -X PATCH -d '{"genres": ["comedy","drama"]}'
"localhost:4000/v1/movies/4" &
[1] 75637
[2] 75638
$ HTTP/1.1 200 OK
Content-Type: application/json
Date: Thu, 08 Apr 2021 10:17:34 GMT
Content-Length: 150

{
    "movie": {
        "id": 4,
        "title": "The Breakfast Club",
        "year": 1985,
        "runtime": "97 mins",
        "genres": [


```
"comedy"
    ],
    "version": 10
  }
}
HTTP/1.1 409 Conflict
Content-Type: application/json
Date: Thu, 08 Apr 2021 10:17:34 GMT
Content-Length: 86

{
  "error": "unable to update the record due to an edit conflict, please try again"
}
```

这样好多了。我们可以看到第二次更新没有被应用，数据竞争被避免了，并且客户端收到了清晰的错误响应。

你可以在终端中按 Ctrl+C 返回到常规终端提示符：

```
^C
[1]-  Done      curl -X PATCH -d '{"runtime": "97 mins"}'
"localhost:4000/v1/movies/4"
[2]+  Done      curl -X PATCH -d '{"genres": ["comedy","drama"]}'
"localhost:4000/v1/movies/4"
```

综上所述，我们在本章中演示的竞争条件相当无害。但在其他应用程序中，这类竞争条件可能会产生更严重的后果——例如更新在线商店中产品的库存水平，或更新账户余额。

正如我在 *Let’s Go* 中简要提到的，养成向客户端发送清晰错误响应的习惯是好的。在本章中，我们将更新我们的应用程序来实现这一点。

## 模拟一个长时间运行的查询

为了帮助演示这一切是如何工作的，让我们首先调整数据库模型中的 `Get()` 方法，使其模拟一个长时间运行的查询。具体来说，我们将更新 SQL 查询，使其返回一个 `pg_sleep(10)` 值，这将使 PostgreSQL 在返回结果之前休眠 10 秒。

文件：internal/data/movies.go

```
package data

...

func (m MovieModel) Get(id int64) (*Movie, error) {
    if id < 1 {
        return nil, ErrRecordNotFound
    }

    // Update the query to return pg_sleep(10) as the first value.
    query := `
        SELECT pg_sleep(10), id, created_at, title, year, runtime, genres,
version
        FROM movies
        WHERE id = $1`

    var movie Movie

    // Importantly, update the Scan() parameters so that the pg_sleep(10)
return value
    // is scanned into a []byte slice.
    err := m.DB.QueryRow(query, id).Scan(
        &[]byte{}, // Add this line.
        &movie.ID,
        &movie.CreatedAt,
        &movie.Title,
        &movie.Year,
        &movie.Runtime,
        pq.Array(&movie.Genres),
        &movie.Version,
    )

    if err != nil {
        switch {
        case errors.Is(err, sql.ErrNoRows):
```
```
        return nil, ErrRecordNotFound
    default:
        return nil, err
    }
}

    return &movie, nil
}
...

```

如果你重新启动应用程序，并向 GET `/v1/movies/:id` 端点发起请求，你会发现在最终获得显示电影信息的成功响应之前，请求会挂起 10 秒。类似这样：

```
$ curl -w '\nTime: %{time_total}s \n' localhost:4000/v1/movies/1
{
  "movie": {
    "id": 1,
    "title": "Moana",
    "year": 2015,
    "runtime": "107 mins",
    "genres": [
      "animation",
      "adventure"
    ],
    "version": 1
  }
}

Time: 10.013534s
```

注意：上面这条 curl 命令中，我们使用了 -w 标志来给 HTTP 响应标注命令完成所用的总时间。关于 curl 中可用的计时信息的更多细节，请参阅这篇出色的博客文章。

## 添加查询超时

现在我们已经有了一个模拟长时间运行查询的代码，让我们强制执行一个超时时间，这样如果 SQL 查询在 3 秒内未完成，它就会被自动取消。

为此，我们需要：

- 1. 使用 `context.WithTimeout()` 函数创建一个具有 3 秒超时截止时间的 `context.Context` 实例。
- 2. 使用 `QueryRowContext()` 方法执行 SQL 查询，并将 `context.Context` 实例作为参数传递。

我将演示：

```
File: internal/data/movies.go

package data

import (
"context" // New import
"database/sql"
"errors"
"time"
)
```
```
"greenlight.alexedwards.net/internal/validator"
"github.com/lib/pq"
)
...
func (m MovieModel) Get(id int64) (*Movie, error) {
    if id < 1 {
        return nil, ErrRecordNotFound
    }

    query := `
        SELECT pg_sleep(10), id, created_at, title, year, runtime, genres,
version
        FROM movies
        WHERE id = $1`

    var movie Movie

    // Use the context.WithTimeout() function to create a context.Context
which carries a
    // 3-second timeout deadline. Note that we're using the empty
context.Background()
    // as the 'parent' context.
    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)

    // Importantly, use defer to make sure that we cancel the context before
the Get()
    // method returns.
    defer cancel()

    // Use the QueryRowContext() method to execute the query, passing in the
context
    // with the deadline as the first argument.
    err := m.DB.QueryRowContext(ctx, query, id).Scan(
        &[]byte{},
        &movie.ID,
```




```
&movie.CreatedAt,
&movie.Title,
&movie.Year,
&movie.Runtime,
pq.Array(&movie.Genres),
&movie.Version,
)

if err != nil {
    switch {
    case errors.Is(err, sql.ErrNoRows):
        return nil, ErrRecordNotFound
    default:
        return nil, err
    }
}

return &movie, nil
}

...
```

关于上面的代码，我想重点强调并解释几点：

- `defer cancel()` 这一行是必要的，因为它确保与我们的上下文相关联的资源在 `Get()` 方法返回之前始终会被释放，从而防止内存泄漏。没有这一行，资源将不会释放，直到 3 秒超时被触发，或父上下文（在这个具体例子中是 `context.Background()`）被取消。
- 超时倒计时从使用 `context.WithTimeout()` 创建上下文的那一刻就开始了，任何来自 PostgreSQL 的耗时也都计入其中。从这个角度看，这是合理的：*我们的应用程序* 就是用户，我们有意识地要在 3 秒后取消查询。

所以，这实际上非常好，一切都在按照我们期望的方式工作。

3 秒后，上下文超时到期，我们的 `pq` 数据库驱动会向 PostgreSQL† 发送一个取消信号。PostgreSQL 随即终止正在运行的查询，释放相应的资源，并返回我们在上面看到的错误消息。客户端随后会收到一个 `500 Internal Server Error` 响应，错误也会被记录下来，这样我们就能知道出了问题。

> † 更准确地说，我们的上下文（即具有 3 秒超时的那个上下文）有一个 `Done` 通道，当超时到期时，`Done` 通道会被关闭。在 SQL 查询运行期间，我们的数据库驱动 `pq` 也会运行一个后台 goroutine，它监听这个 `Done` 通道。如果通道被关闭，`pq` 就会向 PostgreSQL 发送取消信号。PostgreSQL 终止该查询，然后将我们上面看到的错误消息作为响应发送回原始的 `pq` goroutine。该错误消息随后被返回给我们数据库模型的 `Get()` 方法。

## PostgreSQL 之外的超时

这里还有一点很重要：*超时截止时间可能在 PostgreSQL 查询真正开始之前就已经到了*。

你可能还记得，在本书前面，我们将 `sql.DB` 连接池配置为最多允许 25 个打开连接。如果所有这些连接都已被占用，那么任何额外的查询都会被 `sql.DB` “排队”，直到有连接可用。在这种场景下——或任何其他导致延迟的场景下——超时截止时间可能会在空闲数据库连接甚至可用之前就已经到了。如果发生这种情况，`QueryRowContext()` 将返回一个 `context.DeadlineExceeded` 错误。

事实上，我们可以通过将最大打开连接数设置为 1，并向我们的端点发出两个并发请求来演示这一点。请使用 `-db-max-open-conns=1` 标志重新启动 API，如下所示：

```
$ go run ./cmd/api -db-max-open-conns=1
2020/12/04 11:50:39 database connection pool established
2020/12/04 11:50:39 starting development server on :4000
```

然后在另一个终端窗口中，同时向 `GET /v1/movies/:id` 端点发出两个请求。在 3 秒超时到期的那一刻，我们应该有一个正在运行的 SQL 查询，而另一个仍“排队”在 `sql.DB` 连接池中。你应该会看到类似下面的两个错误响应：

```
$ curl localhost:4000/v1/movies/1 & curl localhost:4000/v1/movies/1 &
[1] 33221
[2] 33222
$ {
  "error": "the server encountered a problem and could not process your request"
}
{
  "error": "the server encountered a problem and could not process your request"
}
```

现在回到你的原始终端，你应该会看到两条不同的错误消息：

```
$ go run ./cmd/api -db-max-open-conns=1
2021/04/08 14:21:36 database connection pool established
2021/04/08 14:21:36 starting development server on :4000
2021/04/08 14:21:50 context deadline exceeded
2021/04/08 14:21:50 pq: canceling statement due to user request
```

这里的 `pq: canceling statement due to user request` 错误消息与正在运行的 SQL 查询被终止有关，而 `context deadline exceeded` 消息则与排队中的 SQL 查询在空闲数据库连接可用之前就被取消有关。

类似地，超时截止时间也可能在稍后处理查询返回的数据时（在 `Scan()` 中）被触发。如果发生这种情况，`Scan()` 也会返回一个 `context.DeadlineExceeded` 错误。

## 更新我们的数据库模型

让我们快速更新数据库模型，为所有操作设置 3 秒的超时截止时间。趁此机会，我们也将从 `Get()` 方法中移除 `pg_sleep(10)` 子句。

```
File: internal/data/movies.go

package data

...

func (m MovieModel) Insert(movie *Movie) error {
    query := `
        INSERT INTO movies (title, year, runtime, genres)
        VALUES ($1, $2, $3, $4)
        RETURNING id, created_at, version`

    args := []interface{}{movie.Title, movie.Year, movie.Runtime, pq.Array(movie.Genres)}

    // Create a context with a 3-second timeout.
    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    // Use QueryRowContext() and pass the context as the first argument.
    return m.DB.QueryRowContext(ctx, query, args...).Scan(&movie.ID, &movie.CreatedAt, &movie.Version)
}
```

```
func (m MovieModel) Get(id int64) (*Movie, error) {
    if id < 1 {
        return nil, ErrRecordNotFound
    }

    // Remove the pg_sleep(10) clause.
    query := `
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        WHERE id = $1`

    var movie Movie

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    // Remove &[ ]byte{} from the first Scan() destination.
    err := m.DB.QueryRowContext(ctx, query, id).Scan(
        &movie.ID,
        &movie.CreatedAt,
        &movie.Title,
        &movie.Year,
        &movie.Runtime,
        pq.Array(&movie.Genres),
        &movie.Version,
    )

    if err != nil {
        switch {
        case errors.Is(err, sql.ErrNoRows):
            return nil, ErrRecordNotFound
        default:
            return nil, err
        }
    }

    return &movie, nil
}
```

```
func (m MovieModel) Update(movie *Movie) error {
    query := `
        UPDATE movies
        SET title = $1, year = $2, runtime = $3, genres = $4, version =
version + 1
        WHERE id = $5 AND version = $6
        RETURNING version`

    args := []interface{}{
        movie.Title,
        movie.Year,
        movie.Runtime,
        pq.Array(movie.Genres),
        movie.ID,
        movie.Version,
    }

    // Create a context with a 3-second timeout.
    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    // Use QueryRowContext() and pass the context as the first argument.
    err := m.DB.QueryRowContext(ctx, query, args...).Scan(&movie.Version)
    if err != nil {
        switch {
        case errors.Is(err, sql.ErrNoRows):
            return ErrEditConflict
        default:
            return err
        }
    }

    return nil
}

func (m MovieModel) Delete(id int64) error {
    if id < 1 {
        return ErrRecordNotFound
    }
}
```

作为上面代码中我们所采用模式的替代方案，我们可以*在处理器中*使用*请求上下文*作为父上下文来创建带超时的上下文——然后将其传递给数据库模型。

但是——这是一个很大的“但是”——这样做会引入大量行为上的复杂性，而且对*大多数*应用程序来说，收益并不足以让这种权衡变得值得。

这背后的细节非常有趣，但也相当复杂和晦涩。因此，我在[这个附录](#)中进行了进一步讨论。





## 第9章 过滤、排序与分页

在本书的这一部分，我们将重点构建一个新的 `GET /v1/movies` 端点的功能，该端点将返回 JSON 数组中多部电影的详细信息。

| 方法 | URL 模式 | 处理器 | 动作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用程序信息 |
| GET | /v1/movies | listMoviesHandler | 显示所有电影的详细信息 |
| POST | /v1/movies | createMovieHandler | 创建一部新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示指定电影的详细信息 |
| PATCH | /v1/movies/:id | updateMovieHandler | 更新指定电影的详细信息 |
| DELETE | /v1/movies/:id | deleteMovieHandler | 删除指定电影 |

我们将逐步开发此端点的功能，首先返回所有电影的数据，然后通过添加过滤、排序和分页功能逐步使其更有用、更易用。

### 解析查询字符串参数

在接下来的几章中，我们将配置 `GET /v1/movies` 端点，使客户端可以通过*查询字符串参数*控制返回哪些电影记录。例如：

```
/v1/movies?title=godfather&genres=crime,drama&page=1&page_size=5&sort=-year
```

如果客户端发送这样的查询字符串，本质上是在对我们的 API 说：“*请返回电影名称包含 `godfather` 且类型包含 `crime` 和 `drama` 的前 5 条记录，并按发布年份降序排序*”。

> **注意**：在 `sort` 参数中，我们将使用 `-` 字符表示降序排序。例如，参数 `sort=title` 表示按电影标题的字母升序排序，而 `sort=-title` 表示按降序排序。

因此，我们要讨论的第一件事是*如何在我们的 Go 代码中解析这些查询字符串参数*。

为了帮助实现这一点，我们将创建三个新的辅助函数：`readString()`、`readInt()` 和 `readCSV()`。我们将使用这些辅助函数从查询字符串中提取和解析值，或者在必要时返回默认的‘回退’值。

请打开你的 `cmd/api/helpers.go` 文件并添加以下代码：

```go
File: cmd/api/helpers.go

package main

import (
    "encoding/json"
    "errors"
    "fmt"
    "io"
    "net/http"
    "net/url" // New import
    "strconv"
    "strings"

    "greenlight.alexedwards.net/internal/validator" // New import

    "github.com/julienschmidt/httprouter"
)

...

// The readString() helper returns a string value from the query string, or
the provided default value if no matching key could be found.
func (app *application) readString(qs url.Values, key string, defaultValue string) string {
    // Extract the value for a given key from the query string. If no key
    // exists this will return the empty string "".
    s := qs.Get(key)

    // If no key exists (or the value is empty) then return the default value.
    if s == "" {
        return defaultValue
    }

    // Otherwise return the string.
    return s
}

// The readCSV() helper reads a string value from the query string and then splits it
// into a slice on the comma character. If no matching key could be found, it returns
// the provided default value.
func (app *application) readCSV(qs url.Values, key string, defaultValue []string) []string {
    // Extract the value from the query string.
    csv := qs.Get(key)

    // If no key exists (or the value is empty) then return the default value.
    if csv == "" {
        return defaultValue
    }

    // Otherwise parse the value into a []string slice and return it.
    return strings.Split(csv, ",")
}

// The readInt() helper reads a string value from the query string and
// converts it to an integer before returning. If no matching key could be found it returns the
// provided default value. If the value couldn't be converted to an integer, then we
// record an error message in the provided Validator instance.
func (app *application) readInt(qs url.Values, key string, defaultValue int, v *validator.Validator) int {
    // Extract the value from the query string.
    s := qs.Get(key)

    // If no key exists (or the value is empty) then return the default value.
    if s == "" {
        return defaultValue
    }

    // Try to convert the value to an int. If this fails, add an error message to the
    // validator instance and return the default value.
    i, err := strconv.Atoi(s)
    if err != nil {
        v.AddError(key, "must be an integer value")
        return defaultValue
    }

    // Otherwise, return the converted integer value.
    return i
}
```

### 添加 API 处理器和路由

接下来，让我们为 `GET /v1/movies` 端点创建一个新的 `listMoviesHandler`。目前，这个处理器将简单地使用我们刚刚创建的辅助工具解析请求查询字符串，然后将内容转储到 HTTP 响应中。

如果你跟着操作，请像这样创建 `listMoviesHandler`：

```go
File: cmd/api/movies.go

package main

...

func (app *application) listMoviesHandler(w http.ResponseWriter, r *http.Request) {
    // To keep things consistent with our other handlers, we'll define an input struct
    // to hold the expected values from the request query string.
    var input struct {
        Title    string
        Genres   []string
        Page     int
        PageSize int
        Sort     string
    }

    // Initialize a new Validator instance.
    v := validator.New()

    // Call r.URL.Query() to get the url.Values map containing the query string data.
    qs := r.URL.Query()

    // Use our helpers to extract the title and genres query string values, falling back
    // to defaults of an empty string and an empty slice respectively if they are not
    // provided by the client.
    input.Title = app.readString(qs, "title", "")
    input.Genres = app.readCSV(qs, "genres", []string{})

    // Get the page and page_size query string values as integers. Notice
    // that we set the default page value to 1 and default page_size to 20, and that we
    // pass the validator instance as the final argument here.
    input.Page = app.readInt(qs, "page", 1, v)
    input.PageSize = app.readInt(qs, "page_size", 20, v)

    // Extract the sort query string value, falling back to "id" if it is not provided
    // by the client (which will imply an ascending sort on movie ID).
    input.Sort = app.readString(qs, "sort", "id")

    // Check the Validator instance for any errors and use the
    // failedValidationResponse() helper to send the client a response if necessary.
    if !v.Valid() {
        app.failedValidationResponse(w, r, v.Errors)
        return
    }

    // Dump the contents of the input struct in a HTTP response.
    fmt.Fprintf(w, "%+v\n", input)
}
```

然后，我们需要在我们的 `cmd/api/routes.go` 文件中创建 `GET /v1/movies` 路由，如下所示：

```go
File: cmd/api/routes.go

package main

...

func (app *application) routes() *httprouter.Router {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck", app.healthcheckHandler)

    // Add the route for the GET /v1/movies endpoint.
    router.HandlerFunc(http.MethodGet, "/v1/movies", app.listMoviesHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id", app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id", app.updateMovieHandler)
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id", app.deleteMovieHandler)

    return router
}
```

至此，我们已经准备好看看它的实际效果了！

请尝试向 GET `/v1/movies` 端点发送一个包含预期查询字符串参数的请求，如下所示。

> **重要提示：** 使用 curl 发送包含多个查询字符串参数的请求时，你**必须**将 URL 用引号括起来才能正常工作。




```
$ curl "localhost:4000/v1/movies?
title=godfather&genres=crime,drama&page=1&page_size=5&sort=year"
{Title:godfather Genres:[crime drama] Page:1 PageSize:5 Sort:year}
```

看起来不错——我们可以看到查询字符串中提供的值都已正确解析并包含在 `input` 结构体中。

如果愿意，你也可以尝试发送一个*无*查询字符串参数的请求。在这种情况下，你应该会看到 `input` 结构体中的值采用了我们在 `listMoviesHandler` 代码中指定的默认值。示例如下：

```
$ curl localhost:4000/v1/movies
{Title: Genres:[] Page:1 PageSize:20 Sort:id}
```

## 创建 Filters 结构体

`page`、`page_size` 和 `sort` 查询字符串参数是你可能也想在 API 的其他端点上使用的。因此，为了让这更简单，让我们快速将它们拆分到一个可重用的 `Filters` 结构体中。

如果你在跟随操作，请继续创建一个新的 `internal/data/filters.go` 文件：

```
```bash
$ touch internal/data/filters.go
```
```

然后添加以下代码：

```
File: internal/data/filters.go

```go
package data

type Filters struct {
    Page     int
    PageSize int
    Sort     string
}
```
```

完成后，回到你的 listMoviesHandler 并像这样更新它以使用新的 Filters 结构体：

```
File: cmd/api/movies.go

```go
package main

...

func (app *application) listMoviesHandler(w http.ResponseWriter, r *http.Request) {
    // Embed the new Filters struct.
    var input struct {
        Title  string
        Genres []string
        data.Filters
    }

    v := validator.New()

    qs := r.URL.Query()

    input.Title = app.readString(qs, "title", "")
    input.Genres = app.readCSV(qs, "genres", []string{})

    // Read the page and page_size query string values into the embedded struct.
    input.Filters.Page = app.readInt(qs, "page", 1, v)
    input.Filters.PageSize = app.readInt(qs, "page_size", 20, v)

    // Read the sort query string value into the embedded struct.
    input.Filters.Sort = app.readString(qs, "sort", "id")

    if !v.Valid() {
        app.failedValidationResponse(w, r, v.Errors)
        return
    }

    fmt.Fprintf(w, "%+v\n", input)
}
```
```

此时，你应该能够再次运行 API，并且一切应该像之前一样继续工作。

## 验证查询字符串参数

得益于我们在上一章中创建的 `readInt()` 辅助函数，如果 `page` 和 `page_size` 查询字符串参数不包含整数值，我们的 API 已经应该返回验证错误了。如果你愿意，可以试试看：

```
$ curl "localhost:4000/v1/movies?page=abc&page_size=abc"
{
  "error": {
    "page": "must be an integer value",
    "page_size": "must be an integer value"
  }
}
```

但我们仍然需要在客户端提供的查询字符串值上执行一些额外的合理性检查。特别是，我们希望检查：

- `page` 值介于 1 和 10,000,000 之间。
- `page_size` 值介于 1 和 100 之间。
- `sort` 参数包含我们电影表的一个已知且受支持的值。具体来说，我们将允许 `"id"`、`"title"`、`"year"`、`"runtime"`、`"-id"`、`"-title"`、`"-year"` 或 `"-runtime"`。

为了解决这个问题，让我们打开 `internal/data/filters.go` 文件并创建一个新的 `ValidateFilters()` 函数，对这些值进行这些检查。

我们将遵循之前对 `ValidateMovie()` 函数使用的相同模式来执行此操作，如下所示：

```
File: internal/data/filters.go

```go
package data

import (
    "greenlight.alexedwards.net/internal/validator" // New import
)

// Add a SortSafelist field to hold the supported sort values.
type Filters struct {
    Page         int
    PageSize     int
    Sort         string
    SortSafelist []string
}

func ValidateFilters(v *validator.Validator, f Filters) {
    // Check that the page and page_size parameters contain sensible values.
    v.Check(f.Page > 0, "page", "must be greater than zero")
    v.Check(f.Page <= 10_000_000, "page", "must be a maximum of 10 million")
    v.Check(f.PageSize > 0, "page_size", "must be greater than zero")
    v.Check(f.PageSize <= 100, "page_size", "must be a maximum of 100")

    // Check that the sort parameter matches a value in the safelist.
    v.Check(validator.In(f.Sort, f.SortSafelist...), "sort", "invalid sort value")
}
```
```

然后我们需要更新 `listMoviesHandler` 以在 `SortSafelist` 字段中设置受支持的值，并随后调用这个新的 `ValidateFilters()` 函数。

```
File: cmd/api/movies.go

package main

...

func (app *application) listMoviesHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title string
        Genres []string
        data.Filters
    }

    v := validator.New()

    qs := r.URL.Query()

    input.Title = app.readString(qs, "title", "")
    input.Genres = app.readCSV(qs, "genres", []string{})

    input.Filters.Page = app.readInt(qs, "page", 1, v)
    input.Filters.PageSize = app.readInt(qs, "page_size", 20, v)

    input.Filters.Sort = app.readString(qs, "sort", "id")
    // Add the supported sort values for this endpoint to the sort safelist.
    input.Filters.SortSafelist = []string{"id", "title", "year", "runtime", "-id", "-title", "-year", "-runtime"}

    // Execute the validation checks on the Filters struct and send a response
    // containing the errors if necessary.
    if data.ValidateFilters(v, input.Filters); !v.Valid() {
        app.failedValidationResponse(w, r, v.Errors)
        return
    }

    fmt.Fprintf(w, "%+v\n", input)
}
```

如果重新启动 API 并尝试使用一些无效的 page、page_size 和 sort 参数发出请求，你现在应该会收到包含相关验证失败消息的错误响应。类似于这样：

```
$ curl "localhost:4000/v1/movies?page=-1&page_size=-1&sort=foo"
{
    "error": {
        "page": "must be greater than zero",
        "page_size": "must be greater than zero",
        "sort": "invalid sort value"
    }
}
```

如果愿意，请随意进一步测试，并尝试发送不同的查询字符串值，直到你确信所有验证检查都正常工作。

## 列出数据

好的，让我们继续前进，让我们的 `GET /v1/movies` 端点返回一些真实数据。

目前，我们将忽略客户端提供的任何查询字符串值并返回按电影 ID 排序的*全部*电影记录。这将为我们提供一个坚实的基础，以便在此基础上开发围绕过滤、排序和分页的更专业功能。

本章的目标是让端点返回一个包含所有电影数组的 JSON 响应，类似于这样：

```
```json
{
  "movies": [
    {
      "id": 1,
      "title": "Moana",
      "year": 2015,
      "runtime": "107 mins",
      "genres": [
        "animation",
        "adventure"
      ],
      "version": 1
    },
    {
      "id": 2,
      "title": "Black Panther",
      "year": 2018,
      "runtime": "134 mins",
      "genres": [
        "sci-fi",
        "action",
        "adventure"
      ],
      "version": 2
    },
    ... etc.
  ]
}
```
```

## 更新应用程序

为了从我们的 PostgreSQL 数据库检索这些数据，让我们在数据库模型上创建一个新的 GetAll() 方法，该方法执行以下 SQL 查询：

```
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
ORDER BY id
```

由于我们预计此 SQL 查询会返回多条记录，因此我们需要使用 Go 的 QueryContext() 方法运行它。我们已经在 *Let’s Go* 中详细解释了它的工作原理，所以让我们直接进入代码：

```
File: internal/data/movies.go
```

```
package data

...

// Create a new GetAll() method which returns a slice of movies. Although
// we're not
// using them right now, we've set this up to accept the various filter
// parameters as
// arguments.
func (m MovieModel) GetAll(title string, genres []string, filters Filters)
([]*Movie, error) {
    // Construct the SQL query to retrieve all movie records.
    query := `
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        ORDER BY id`

    // Create a context with a 3-second timeout.
    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    // Use QueryContext() to execute the query. This returns a sql.Rows
    // resultset
    // containing the result.
    rows, err := m.DB.QueryContext(ctx, query)
    if err != nil {
        return nil, err
    }

    // Importantly, defer a call to rows.Close() to ensure that the resultset
    // is closed
    // before GetAll() returns.
    defer rows.Close()

    // Initialize an empty slice to hold the movie data.
    movies := []*Movie{}
```

// Use rows.Next to iterate through the rows in the resultset.
for rows.Next() {
    // Initialize an empty Movie struct to hold the data for an
individual movie.
    var movie Movie

    // Scan the values from the row into the Movie struct. Again, note
that we're
    // using the pq.Array() adapter on the genres field here.
    err := rows.Scan(
        &movie.ID,
        &movie.CreatedAt,
        &movie.Title,
        &movie.Year,
        &movie.Runtime,
        pq.Array(&movie.Genres),
        &movie.Version,
    )
    if err != nil {
        return nil, err
    }

    // Add the Movie struct to the slice.
    movies = append(movies, &movie)
}

// When the rows.Next() loop has finished, call rows.Err() to retrieve
any error
    // that was encountered during the iteration.
if err = rows.Err(); err != nil {
    return nil, err
}

// If everything went OK, then return the slice of movies.
return movies, nil
}

接下来，我们需要调整 `listMoviesHandler`，使其调用新的 `GetAll()` 方法来检索电影数据，然后将该数据作为 JSON 响应写入。

如果您跟随操作，请继续按如下方式更新处理器：

```
File: cmd/api/movies.go

package main

...

func (app *application) listMoviesHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
        Title string
        Genres []string
        data.Filters
    }

    v := validator.New()

    qs := r.URL.Query()

    input.Title = app.readString(qs, "title", "")
    input.Genres = app.readCSV(qs, "genres", []string{})

    input.Filters.Page = app.readInt(qs, "page", 1, v)
    input.Filters.PageSize = app.readInt(qs, "page_size", 20, v)

    input.Filters.Sort = app.readString(qs, "sort", "id")
    input.Filters.SortSafelist = []string{"id", "title", "year", "runtime", "-id", "-title", "-year", "-runtime"}

    if data.ValidateFilters(v, input.Filters); !v.Valid() {
```
app.failedValidationResponse(w, r, v.Errors)
    return
}

    // Call the GetAll() method to retrieve the movies, passing in the
various filter
    // parameters.
    movies, err := app.models.Movies.GetAll(input.Title, input.Genres,
input.Filters)
    if err != nil {
        app.serverErrorResponse(w, r, err)
        return
    }

    // Send a JSON response containing the movie data.
err = app.writeJSON(w, http.StatusOK, envelope{"movies": movies}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}

现在我们应该准备好试用了。

继续重启 API，然后当您发出 GET /v1/movies 请求时，您应该会看到 GetAll() 返回的电影切片以 JSON 数组的形式呈现。类似这样：

```
$ curl localhost:4000/v1/movies
{
    "movies": [
        {
            "id": 1,
            "title": "Moana",
            "year": 2016,
```
"runtime": "107 mins",
"genres": [
    "animation",
    "adventure"
],
"version": 1
},
{
    "id": 2,
    "title": "Black Panther",
    "year": 2018,
    "runtime": "134 mins",
    "genres": [
        "sci-fi",
        "action",
        "adventure"
    ],
    "version": 2
},
{
    "id": 4,
    "title": "The Breakfast Club",
    "year": 1985,
    "runtime": "97 mins",
    "genres": [
        "comedy"
    ],
    "version": 5
}
]
}
```

## 过滤列表

本章我们将开始使用查询字符串参数，以便客户端可以根据特定的标题或类型搜索电影。

具体来说，我们将构建一个限制性过滤器，允许客户端基于电影标题不区分大小写的精确匹配和/或一个或多个电影类型进行搜索。例如：

```
```
// List all movies.
/v1/movies

// List movies where the title is a case-insensitive exact match for 'black panther'.
/v1/movies?title=black+panther

// List movies where the genres includes 'adventure'.
/v1/movies?genres=adventure

// List movies where the title is a case-insensitive exact match for 'moana' AND the
// genres include both 'animation' AND 'adventure'.
/v1/movies?title=moana&genres=animation,adventure
```
```

**注意：** 上述查询字符串中的 + 符号是 URL 编码的空格字符。或者您也可以使用 %20

> 替代... 在查询字符串的上下文中两者都有效。

## SQL 查询中的动态过滤

构建这种动态过滤功能最困难的部分是检索数据的 SQL 查询——我们需要它在没有过滤器、同时对 `title` 和 `genres` 进行过滤，或仅对其中一个进行过滤的情况下都能正常工作。

为此，一个选择是在运行时动态构建 SQL 查询……将每个过滤器所需的 SQL 拼接或插值到 `WHERE` 子句中。但这种方法会使代码变得混乱且难以理解，尤其是在需要支持大量过滤选项的大型查询中。

在本节中，我们将选择一种不同的技术并使用如下固定的 SQL 查询：

```
```sql
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (LOWER(title) = LOWER($1) OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY id
```
```

此 SQL 查询的设计使每个过滤器都表现得像“可选”的。例如，条件 `(LOWER(title) = LOWER($1) OR $1 = '')` 将在占位符参数 `$1` 与电影标题不区分大小写匹配或占位符参数等于 '' 时求值为 `true`。因此，当搜索的电影标题为空字符串 "" 时，此过滤条件本质上将被“跳过”。

(genres @> $2 OR $2 = '{}') 条件的工作方式相同。@> 符号是 PostgreSQL 数组的“包含”运算符，此条件将在占位符参数 $2 中的所有值都包含在数据库 genres 字段中或占位符参数包含空数组时返回 true。

您会记得在本书前面我们设置了 listMoviesHandler，使空字符串 "" 和空切片用作 title 和 genres 过滤参数的默认值：

```
input.Title = app.readString(qs, "title", "")
input.Genres = app.readCSV(qs, "genres", []string{})
```

因此，把这些结合起来就意味着，如果客户端在查询字符串中未提供 title 参数，则 $1 占位符的值将为空字符串 ""，SQL 查询中的过滤条件将求值为 true 并表现得像已被“跳过”。genres 参数也是如此。

注意：PostgreSQL 还提供了一系列其他有用的数组运算符和函数，包括 && ‘overlap’ 运算符、<@ ‘contained by’ 运算符和 `array_length()` 函数。完整列表[可以找到这里](.)。

好的，让我们回到 `internal/data/movies.go` 文件，并更新 `GetAll()` 方法以使用此新查询。如下所示：

```
File: internal/data/movies.go

package data

...

func (m MovieModel) GetAll(title string, genres []string, filters Filters) ([]*Movie, error) {
    // Update the SQL query to include the filter conditions.
    query := `
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        WHERE (LOWER(title) = LOWER($1) OR $1 = '')
        AND (genres @> $2 OR $2 = '{}')
        ORDER BY id`

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    // Pass the title and genres as the placeholder parameter values.
    rows, err := m.DB.QueryContext(ctx, query, title, pq.Array(genres))
    if err != nil {
        return nil, err
    }

    defer rows.Close()

    movies := []*Movie{}

```
```go
for rows.Next() {
    var movie Movie

    err := rows.Scan(
        &movie.ID,
        &movie.CreatedAt,
        &movie.Title,
        &movie.Year,
        &movie.Runtime,
        pq.Array(&movie.Genres),
        &movie.Version,
    )
    if err != nil {
        return nil, err
    }

    movies = append(movies, &movie)
}

if err = rows.Err(); err != nil {
    return nil, err
}

return movies, nil
}
```

现在让我们重启应用程序并试用，使用我们在本章开头给出的示例。如果您一直跟随操作，响应应类似于这样：

```
```
$ curl "localhost:4000/v1/movies?title=black+panther"
{
    "movies": [
        {

```
"id": 2,
"title": "Black Panther",
"year": 2018,
"runtime": "134 mins",
"genres": [
    "sci-fi",
    "action",
    "adventure"
],
"version": 2
}
]
}
```

```
$ curl "localhost:4000/v1/movies?genres=adventure"
{
    "movies": [
        {
            "id": 1,
            "title": "Moana",
            "year": 2015,
            "runtime": "107 mins",
            "genres": [
                "animation",
                "adventure"
            ],
            "version": 1
        },
        {
            "id": 2,
            "title": "Black Panther",
            "year": 2018,
            "runtime": "134 mins",
            "genres": [
                "sci-fi",
                "action",
"adventure"
],
"version": 2
}
]
}
```

```
$ curl "localhost:4000/v1/movies?title=moana&genres=animation,adventure"
{
    "movies": [
        {
            "id": 1,
            "title": "Moana",
            "year": 2016,
            "runtime": "107 mins",
            "genres": [
                "animation",
                "adventure"
            ],
            "version": 1
        }
    ]
}
```

你也可以尝试使用一个不匹配任何记录的过滤器发起请求。在这种情况下，你应该在响应中得到一个空的 JSON 数组，如下所示：

```
$ curl "localhost:4000/v1/movies?genres=western"
{
```
```
"movies": []
}
```

进展不错。我们的 API 端点现在正在返回适当过滤的电影记录，并且我们有一个模式，可以轻松地在未来扩展以包含其他过滤规则（例如对电影年份或播放时长的过滤），如果我们想要的话。

## Full-Text Search

在本章中，我们将通过使其支持 *部分匹配* 来让电影标题过滤器更易于使用，而不再要求完全匹配标题。因此，例如，如果客户端想要查找 *The Breakfast Club*，他们只需使用查询字符串 `title=breakfast` 即可找到它。

在代码库中实现此功能有几种不同的方法，但从客户端角度来看，一种有效且直观的方法是利用 PostgreSQL 的 *全文搜索* 功能，它允许你对数据库中的文本字段执行‘自然语言’搜索。

PostgreSQL 全文搜索是一个功能强大且高度可配置的工具，完整地解释其工作原理和可用选项本身就可以写成一整本书。因此，本章中的解释将保持高层次，重点关注实际实现。

为了在我们的 `title` 字段上实现基本的全文搜索，我们将更新 SQL 查询，使其如下所示：

```sql
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (to_tsvector('simple', title) @@ plainto_tsquery('simple', $1) OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY id
```

乍一看似乎相当复杂，所以让我们分解一下并解释一下发生了什么。

函数 `to_tsvector('simple', title)` 会接收电影标题并将其拆分为 *词素*。我们指定了 `simple` 配置，这意味着词素只是标题中单词的小写版本†。例如，电影标题 "The Breakfast Club" 将被拆分为词素 `'breakfast' 'club' 'the'`。

> † 其他‘非 simple’ 配置可能会对词素应用额外的规则，例如移除常用词或应用特定语言的词干提取。

函数 `plainto_tsquery('simple', $1)` 会接收搜索值并将其转换为 PostgreSQL 全文搜索可以理解的格式化的 *查询词*。它会规范化搜索值（再次使用 `simple` 配置），删除任何特殊字符，并在单词之间插入 *与运算符* &。例如，搜索值 "The Club" 将导致查询词 `'the' & 'club'`。

`@@` 运算符是匹配运算符。在我们的语句中，我们使用它来检查生成的 *查询词是否匹配词素*。继续上面的例子，查询词 `'the' & 'club'` 将匹配同时包含词素 `'the'` 和 `'club'` 的行。

上面的段落中有很多专业术语，但如果用几个例子来说明，实际上非常直观：

```
// Return all movies where the title includes the case-insensitive word 'panther'.
/v1/movies?title=panther

// Return all movies where the title includes the case-insensitive words 'the' and
// 'club'.
/v1/movies?title=the+club
```

让我们开始付诸实践。打开你的 internal/data/movies.go 文件并更新 GetAll() 方法以使用新的 SQL 查询，如下所示：

```
File: internal/data/movies.go

package data

...

func (m MovieModel) GetAll(title string, genres []string, filters Filters) ([]*Movie, error) {
    // Use full-text search for the title filter.
    query := `
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        WHERE (to_tsvector('simple', title) @@ plainto_tsquery('simple', $1) OR $1 = '')
        AND (genres @> $2 OR $2 = '{}')
ORDER BY id`

// Nothing else below needs to change.
...
}
```

如果你在跟随操作，请重启应用程序并尝试使用不同的电影标题值发起一些请求。你会发现部分搜索现在按我们上面描述的方式工作。

例如：

```
$ curl "localhost:4000/v1/movies?title=panther"
{
  "movies": [
    {
      "id": 2,
      "title": "Black Panther",
      "year": 2018,
      "runtime": "134 mins",
      "genres": [
        "sci-fi",
        "action",
        "adventure"
      ],
      "version": 2
    }
  ]
}

$ curl "localhost:4000/v1/movies?title=the+club"
{
```

## Additional Information

### Non-simple configuration and more information

如上所述，你也可以使用特定语言的配置来进行全文搜索，而不是我们当前使用的 `simple` 配置。当使用特定语言的配置创建词素或查询词时，它会剔除该语言的常用词并执行词干提取。

所以，例如，如果你使用 `english` 配置，那么为 "`One Flew Over the Cuckoo's Nest`" 生成的词素将是 '`cuckoo`' '`flew`' '`nest`' '`one`'。或者使用 `spanish` 配置时，"`Los lunes al sol`" 的词素将是 '`lun`' '`sol`'。

你可以通过在 PostgreSQL 中运行 `\dF` 元命令来检索所有可用配置的列表：

```
postgres=# \dF
        List of text search configurations
 Schema |   Name   |          Description
--------+----------+-------------------------------
 pg_catalog | arabic | configuration for arabic language
 pg_catalog | danish | configuration for danish language
 pg_catalog | dutch  | configuration for dutch language
```

```
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (STRPOS(LOWER(title), LOWER($1)) > 0 OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY id
```

从客户端角度来看，其缺点是它可能会返回一些不直观的结果。例如，搜索 title=the 在我们的数据集中会同时返回 The Breakfast Club 和 Black Panther。

从服务器角度来看，对于大型数据集来说也不理想。因为没有有效的方法对 title 字段进行索引以查看是否满足 STRPOS() 条件，这意味着每次运行查询时都可能需要进行全表扫描。

另一个选项是 ILIKE 运算符，它允许你查找匹配特定（不区分大小写）模式的行。我们可以在 SQL 查询中像这样使用它：

```
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (title ILIKE $1 OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY id
```

从服务器角度来看，这种方法会更好，因为可以使用 pg_trgm

扩展和一个 GIN 索引（详情请参阅此帖）。

从客户端来看，使用 `STRPOS()` 方法也更合理，因为他们可以通过在搜索词的前缀或后缀添加 `%` 通配符字符来控制匹配行为（该字符在 URL 查询字符串中需要转义为 `%25`）。例如，要搜索标题以“the”开头的电影，客户端可以发送查询字符串参数 `title=the%25`。

## 排序列表

现在让我们更新我们的 GET `/v1/movies` 端点的逻辑，以便客户端可以控制 JSON 响应中电影的排序方式。

正如我们之前简要解释的那样，我们希望客户端能够通过格式为 `sort={-}{field_name}` 的查询字符串参数来控制排序顺序，其中可选的 `-` 字符用于表示降序排序。例如：

// Sort the movies on the title field in ascending alphabetical order.
/v1/movies?sort=title

// Sort the movies on the year field in descending numerical order.
/v1/movies?sort=-year

在幕后，我们希望将其转换为 SQL 查询中的 `ORDER BY` 子句，这样像 `sort=-year` 这样的查询字符串参数就会产生如下 SQL 查询：

```
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (STRPOS(LOWER(title), LOWER($1)) > 0 OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY year DESC --<- Order the result by descending year
```

这里的难点在于，`ORDER BY` 子句的值需要根据客户端的查询字符串值在运行时生成。理想情况下，我们会使用占位符参数将这些动态值插入查询中，但不幸的是，*无法对列名或 SQL 关键字*（包括 `ASC` 和 `DESC`）使用占位符参数。

因此，我们需要使用 `fmt.Sprintf()` 将这些动态值插值到查询中——确保首先将值与严格的白名单进行检查，以防止 SQL 注入攻击。

在使用 PostgreSQL 时，还需要注意返回行的顺序仅由 `ORDER BY` 子句规定的规则保证。从 [官方文档]()：

> 如果未选择排序，则行将以未指定的顺序返回。在这种情况下，实际顺序取决于扫描和连接计划类型以及磁盘上的顺序，但不得依赖它。只有在显式选择排序步骤时，才能保证特定的输出顺序。

这意味着如果我们不包含一个 `ORDER BY` 子句，则 PostgreSQL 可能会以任何顺序返回电影——*并且每次运行查询时顺序可能会或可能不会改变。*

File: internal/data/filters.go

```go
package data

import (
    "strings" // New import

    "greenlight.alexedwards.net/internal/validator"
)

type Filters struct {
    Page         int
    PageSize     int
    Sort         string
    SortSafelist []string
}

// Check that the client-provided Sort field matches one of the entries in
// our safelist
// and if it does, extract the column name from the Sort field by stripping
// the leading
// hyphen character (if one exists).
func (f Filters) sortColumn() string {
    for _, safeValue := range f.SortSafelist {
        if f.Sort == safeValue {
            return strings.TrimPrefix(f.Sort, "-")
        }
    }

    panic("unsafe sort parameter: " + f.Sort)
}

// Return the sort direction ("ASC" or "DESC") depending on the prefix
// character of the
// Sort field.
func (f Filters) sortDirection() string {
    if strings.HasPrefix(f.Sort, "-") {
    return "DESC"
}

    return "ASC"
}

...
```

请注意，`sortColumn()` 函数的构造方式是，如果客户端提供的 `Sort` 值与我们的白名单中的条目不匹配，则会 panic。理论上这种情况不应该发生——`Sort` 值应该已经通过调用 `ValidateFilters()` 函数进行了检查——但这是一个合理的故障保护机制，有助于阻止 SQL 注入攻击发生。

现在让我们更新 `internal/data/movies.go` 文件以调用这些方法，并将返回值插值到 SQL 查询的 `ORDER BY` 子句中。如下所示：

```
File: internal/data/movies.go

package data

import (
    "context"
    "database/sql"
    "errors"
    "fmt" // New import
    "time"

    "greenlight.alexedwards.net/internal/validator"
)
"github.com/lib/pq"
)
...
func (m MovieModel) GetAll(title string, genres []string, filters Filters) ([]*Movie, error) {
    // Add an ORDER BY clause and interpolate the sort column and direction.
    Importantly
    // notice that we also include a secondary sort on the movie ID to ensure
    a
    // consistent ordering.
    query := fmt.Sprintf(`
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        WHERE (to_tsvector('simple', title) @@ plainto_tsquery('simple', $1) OR $1 = '')
        AND (genres @> $2 OR $2 = '{}')
        ORDER BY %s %s, id ASC`, filters.sortColumn(),
filters.sortDirection()

    // Nothing else below needs to change.
    ...
}
```

完成之后，我们就可以准备试用了。

然后重启应用程序，例如，尝试请求按标题降序排列的电影。你应该会得到如下所示的响应：

```
$ curl "localhost:4000/v1/movies?sort=-title"
{
    "movies": [
```
],
    "version": 5
    }
  ]
}
```

## 分页列表

如果你有一个端点返回包含数百或数千条记录的列表，那么出于性能或可用性的原因，你可能希望在该端点上实现某种形式的 *分页*——以便它在单个 HTTP 响应中只返回记录的子集。

为了演示如何做到这一点，在本章中我们将更新 `GET /v1/movies` 端点，使其支持“页面”的概念，并且客户端可以通过我们的 `page` 和 `page_size` 查询字符串参数请求电影列表的特定“页面”。例如：

// Return the 5 records on page 1 (records 1-5 in the dataset)
/v1/movies?page=1&page_size=5

// Return the next 5 records on page 2 (records 6-10 in the dataset)
/v1/movies?page=2&page_size=5

// Return the next 5 records on page 3 (records 11-15 in the dataset)
/v1/movies?page=3&page_size=5

基本上，修改 `page_size` 参数会改变每个“页面”上显示的电影数量，而将 `page` 参数增加一则会显示列表中下一个“页面”的电影。

```
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (to_tsvector('simple', title) @@ plainto_tsquery('simple', $1) OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY %s %s, id ASC
LIMIT 5 OFFSET 10
```

让我们首先为 Filters 结构体添加一些辅助方法来计算适当的 LIMIT 和 OFFSET 值。

如果你跟着操作，请继续更新 internal/data/filters.go 文件，如下所示：

```
File: internal/data/filters.go

package data

...

type Filters struct {
    Page        int
    PageSize    int
    Sort        string
    SortSafelist []string
}

...

func (f Filters) limit() int {
    return f.PageSize
}
```

([]*Movie, error) {
    // Update the SQL query to include the LIMIT and OFFSET clauses with placeholder
    parameter values.
    // parameter values.
    query := fmt.Sprintf(`
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        WHERE (to_tsvector('simple', title) @@ plainto_tsquery('simple', $1) OR $1 = '')
        AND (genres @> $2 OR $2 = '{}')
        ORDER BY %s %s, id ASC
        LIMIT $3 OFFSET $4`, filters.sortColumn(), filters.sortDirection())

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    // As our SQL query now has quite a few placeholder parameters, let's
    collect the
    // values for the placeholders in a slice. Notice here how we call the
    limit() and
    // offset() methods on the Filters struct to get the appropriate values
    for the
    // LIMIT and OFFSET clauses.
    args := []interface{}{title, pq.Array(genres), filters.limit(),
    filters.offset()}

    // And then pass the args slice to QueryContext() as a variadic
    parameter.
    rows, err := m.DB.QueryContext(ctx, query, args...)
    if err != nil {
        return nil, err
    }

    // Nothing else below needs to change.
    ...
}



完成之后，我们应该准备好尝试一下了。

重启服务器，然后继续使用 `page_size=2` 参数发出以下请求：

```
$ curl "localhost:4000/v1/movies?page_size=2"
{
  "movies": [
    {
      "id": 1,
      "title": "Moana",
      "year": 2016,
      "runtime": "107 mins",
      "genres": [
        "animation",
        "adventure"
      ],
      "version": 1
    },
    {
      "id": 2,
      "title": "Black Panther",
      "year": 2018,
      "runtime": "134 mins",
      "genres": [
        "sci-fi",
        "action",
        "adventure"
      ],
      "version": 2
    }
  ]
}
```

| 计数 | id | 创建时间 | 标题 | 年份 | 时长 | 类型 | 版本 |
|---|---|---|---|---|---|---|---|
| 3 | 1 | 2020-11-27 17:17:25+01 | Moana | 2015 | 107 | {animation,adventure} | 1 |
| 3 | 2 | 2020-11-27 18:01:45+01 | Black Panther | 2018 | 134 | {sci-fi,action,adventure} | 2 |
| 3 | 4 | 2020-11-27 18:02:20+01 | The Breakfast Club | 1985 | 97 | {comedy,drama} | 6 |

当 PostgreSQL 执行此 SQL 查询时，（非常简化的）事件序列大致如下：

- 1. 使用 `WHERE` 子句过滤 `movies` 表中的数据并获取 *符合条件的行*。
- 2. 应用窗口函数 `count(*) OVER()`，它统计所有符合条件的行。
- 3. 应用 `ORDER BY` 规则并对符合条件的行进行排序。
- 4. 应用 `LIMIT` 和 `OFFSET` 规则并返回已排序符合条件行的适当子集。

## 更新代码

在简要说明之后，让我们开始运行。 我们将首先更新 `internal/data/filters.go` 文件

以定义一个新的 Metadata 结构体来保存分页元数据，以及一个用于计算值的辅助函数。示例如下：

```
File: internal/data/filters.go

package data

import (
    "math" // New import
    "strings"

    "greenlight.alexedwards.net/internal/validator"
)

...

// Define a new Metadata struct for holding the pagination metadata.
type Metadata struct {
    CurrentPage int `json:"current_page,omitempty"`
    PageSize    int `json:"page_size,omitempty"`
    FirstPage   int `json:"first_page,omitempty"`
    LastPage    int `json:"last_page,omitempty"`
    TotalRecords int `json:"total_records,omitempty"`
}

// The calculateMetadata() function calculates the appropriate pagination metadata
// values given the total number of records, current page, and page size
// values. Note
// that the last page value is calculated using the math.Ceil() function,
// which rounds
// up a float to the nearest integer. So, for example, if there were 12
// records in total
// and a page size of 5, the last page value would be math.Ceil(12/5) = 3.
func calculateMetadata(totalRecords, page, pageSize int) Metadata {
    if totalRecords == 0 {
```

```
// Note that we return an empty Metadata struct if there are no records.
    return Metadata{}
}

    return Metadata{
        CurrentPage: page,
        PageSize: pageSize,
        FirstPage: 1,
        LastPage: int(math.Ceil(float64(totalRecords) /
float64(pageSize))),
        TotalRecords: totalRecords,
    }
}
```

然后我们需要回到 GetAll() 方法并更新它以使用新的 SQL 查询（带窗口函数）获取总记录数。 然后，如果一切顺利，我们将使用 calculateMetadata() 函数生成分页元数据并将其与电影数据一起返回。

继续按如下方式更新 GetAll() 函数：

```
File: internal/data/movies.go

package data

...

// Update the function signature to return a Metadata struct.
func (m MovieModel) GetAll(title string, genres []string, filters Filters) ([]*Movie, Metadata, error) {
    // Update the SQL query to include the window function which counts the
```

```
&movie.Year,
&movie.Runtime,
pq.Array(&movie.Genres),
&movie.Version,
)
if err != nil {
    return nil, Metadata{}, err // Update this to return an empty
Metadata struct.
}
    movies = append(movies, &movie)
}
    if err = rows.Err(); err != nil {
        return nil, Metadata{}, err // Update this to return an empty
Metadata struct.
    }
    // Generate a Metadata struct, passing in the total record count and
pagination
    // parameters from the client.
    metadata := calculateMetadata(totalRecords, filters.Page,
filters.PageSize)
    // Include the metadata struct when returning.
    return movies, metadata, nil
}
```

最后，我们需要更新 listMoviesHandler 处理程序以接收 GetAll() 返回的 Metadata 结构体，并在客户端的 JSON 响应中包含该信息。示例如下：

```
File: cmd/api/movies.go
```

```
package main

...

func (app *application) listMoviesHandler(w http.ResponseWriter, r *http.Request) {
	var input struct {
		Title string
		Genres []string
		data.Filters
	}

	v := validator.New()

	qs := r.URL.Query()

	input.Title = app.readString(qs, "title", "")
	input.Genres = app.readCSV(qs, "genres", []string{})

	input.Filters.Page = app.readInt(qs, "page", 1, v)
	input.Filters.PageSize = app.readInt(qs, "page_size", 20, v)

	input.Filters.Sort = app.readString(qs, "sort", "id")
	input.Filters.SortSafelist = []string{"id", "title", "year", "runtime", "-id", "-title", "-year", "-runtime"}

	if data.ValidateFilters(v, input.Filters); !v.Valid() {
		app.failedValidationResponse(w, r, v.Errors)
		return
	}

	// Accept the metadata struct as a return value.
	movies, metadata, err := app.models.Movies.GetAll(input.Title, input.Genres, input.Filters)
	if err != nil {
		app.serverErrorResponse(w, r, err)
		return
	}
}
```

```
// Include the metadata in the response envelope.
    err = app.writeJSON(w, http.StatusOK, envelope{"movies": movies,
"metadata": metadata}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

随意重启 API 并通过对 GET /v1/movies 端点发出不同的请求来尝试此新功能。 你会发现正确的分页元数据现在已包含在响应中。 例如：

```
$ curl "localhost:4000/v1/movies?page=1&page_size=2"
{
    "metadata": {
        "current_page": 1,
        "page_size": 2,
        "first_page": 1,
        "last_page": 2,
        "total_records": 3
    },
    "movies": [
        {
            "id": 1,
            "title": "Moana",
            "year": 2015,
            "runtime": "107 mins",
            "genres": [
                "animation",
                "adventure"
            ],
            "version": 1
```

```
"title": "Moana",
"year": 2015,
"runtime": "107 mins",
"genres": [
    "animation",
    "adventure"
],
"version": 1
},
{
    "id": 2,
    "title": "Black Panther",
    "year": 2018,
    "runtime": "134 mins",
    "genres": [
        "sci-fi",
        "action",
        "adventure"
    ],
    "version": 2
}
]
}
```

最后，如果你发出页码过高的请求，你应该会得到一个包含空 metadata 对象和 movies 数组的响应，如下所示：

```
$ curl localhost:4000/v1/movies?page=100
{
    "metadata": {},
    "movies": []
}
```

在过去的几章中，我们在 `GET /v1/movies` 端点上投入了大量工作。 但最终结果非常强大。 客户端现在可以更好地控制其响应的内容，支持过滤、分页和排序。

通过我们创建的 `Filters` 结构体，我们还拥有可以轻松添加到未来需要分页和排序功能的任何其他端点的东西。 而且，如果你退一步看看我们在 `listMovieHandler` 中编写的最终代码以及数据库模型 `GetAll()` 方法，与该端点早期迭代相比，并没有 *这么多* 额外的代码。



第 10.1 章

## 结构化 JSON 日志条目

目前，我们所有的日志条目都是简单的自由格式消息，前缀是当前日期和时间，写入到*标准输出*流。一个很好的例子是我们在启动 API 时看到的日志条目：

```
$ go run ./cmd/api
2021/04/09 19:43:31 database connection pool established
2021/04/09 19:43:31 starting development server on :4000
```

对于许多应用程序来说，这种简单的日志记录风格已经*足够好*，没有必要为项目引入额外的复杂性。

但对于需要进行大量日志记录的应用程序，强制为日志条目采用一致的结构和格式往往很有用。这有助于更容易地区分不同类型的日志条目（如*信息*和*错误*条目），更容易搜索和过滤日志条目，并且更容易将日志与第三方分析和监控系统集成。

因此，在本章中，我们将演示如何调整我们的应用程序，使日志条目以结构化 JSON 格式写入，类似这样：

```
{"level":"INFO","time":"2020-12-16T10:53:35Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

本质上，每个日志条目将是一个包含以下键/值对的单个 JSON 对象：

| 键 | 描述 |
|---|---|
| level | 表示日志条目严重级别的代码。在本项目中，我们将使用以下三个严重级别，按从低到高的顺序排列：
- INFO（最低严重级别）
- ERROR
- FATAL（最高严重级别） |
| time | 日志条目被记录的 UTC 时间，精确到秒。 |
| message | 包含自由文本信息或错误消息的字符串。 |
| properties | 与日志条目相关的任何附加信息，以字符串键/值对表示（可选）。 |
| trace | 用于调试目的的堆栈跟踪（可选）。 |

## 创建自定义记录器

为了在我们的 API 中实现这一点，我们将创建自己的自定义 `Logger` 类型，它以 JSON 格式写入结构化日志条目。

我们将在 `Logger` 上实现一些便捷方法，如 `PrintInfo()` 和 `PrintError()`，以便从应用程序中以单条命令轻松写入具有特定级别的日志条目。我们还将设计记录器，使得仅记录达到或超过某个*最低严重级别*的条目——因此，如果你只想记录 `ERROR` 和 `FATAL` 消息（而不是 `INFO` 消息），那很容易实现。

如果你在跟着操作，请按如下方式创建一个新的 `internal/jsonlog` 包：

```
$ mkdir internal/jsonlog
$ touch internal/jsonlog/jsonlog.go
```

然后添加以下代码：

```
File: internal/jsonlog/jsonlog.go

package jsonlog

import (
    "encoding/json"
    "io"
    "os"
    "runtime/debug"
    "sync"
    "time"
)

// Define a Level type to represent the severity level for a log entry.
type Level int8

// Initialize constants which represent a specific severity level. We use the
// iota keyword as a shortcut to assign successive integer values to the constants.
const (
    LevelInfo  Level = iota // Has the value 0.
    LevelError              // Has the value 1.
    LevelFatal              // Has the value 2.
    LevelOff                // Has the value 3.
)

// Return a human-friendly string for the severity level.
func (l Level) String() string {
    switch l {
    case LevelInfo:
        return "INFO"
    case LevelError:
        return "ERROR"
    case LevelFatal:
        return "FATAL"
    default:
        return ""
    }
}

// Define a custom Logger type. This holds the output destination that the log entries
// will be written to, the minimum severity level that log entries will be written for,
// plus a mutex for coordinating the writes.
type Logger struct {
    out      io.Writer
    minLevel Level
    mu       sync.Mutex
}

// Return a new Logger instance which writes log entries at or above a minimum severity
// level to a specific output destination.
func New(out io.Writer, minLevel Level) *Logger {
    return &Logger{
        out:      out,
        minLevel: minLevel,
    }
}

// Declare some helper methods for writing log entries at the different
// levels. Notice
// that these all accept a map as the second parameter which can contain any
// arbitrary
// 'properties' that you want to appear in the log entry.
func (l *Logger) PrintInfo(message string, properties map[string]string) {
    l.print(LevelInfo, message, properties)
}

func (l *Logger) PrintError(err error, properties map[string]string) {
    l.print(LevelError, err.Error(), properties)
}

func (l *Logger) PrintFatal(err error, properties map[string]string) {
    l.print(LevelFatal, err.Error(), properties)
    os.Exit(1) // For entries at the FATAL level, we also terminate the
application.
}

// Print is an internal method for writing the log entry.
func (l *Logger) print(level Level, message string, properties map[string]string) (int, error) {
    // If the severity level of the log entry is below the minimum severity
    // for the
    // logger, then return with no further action.
    if level < l.minLevel {
        return 0, nil
    }

    // Declare an anonymous struct holding the data for the log entry.
    aux := struct {
        Level   string        `json:"level"`
        Time    string        `json:"time"`
```

```
// We also implement a Write() method on our Logger type so that it satisfies
// the
// io.Writer interface. This writes a log entry at the ERROR level with no
// additional
// properties.
func (l *Logger) Write(message []byte) (n int, err error) {
    return l.print(LevelError, string(message), nil)
}
```

**注意：** 如果你愿意，可以扩展此代码以支持其他严重级别，如 `DEBUG` 和 `WARNING`。

本质上，我们的 `Logger` 类型是对 `io.Writer` 的一个相当薄的包装。我们有一些辅助方法，如 `PrintInfo()` 和 `PrintError()`，它们接受一些日志条目数据，将这些数据编码为 JSON，然后写入 `io.Writer`。

在这段代码中，最值得指出的两个有趣点是：我们使用 `iota` 枚举器来创建日志级别，以及使用 `sync.Mutex` 来协调写入。

你可以使用 `iota` 轻松为一组整数*常量*分配连续的整数值。它从零开始，每次常量声明递增 1，当代码中再次出现 `const` 关键字时重置为 0。我们对它的使用意味着每个严重级别都有一个整数值，且*更严重的级别具有更高的值*。

// Initialize a new jsonlog.Logger which writes any messages *at or
above* the INFO
    // severity level to the standard out stream.
    logger := jsonlog.New(os.Stdout, jsonlog.LevelInfo)

    db, err := openDB(cfg)
    if err != nil {
        // Use the PrintFatal() method to write a log entry containing the
        error at the
            // FATAL level and exit. We have no additional properties to include
        in the log
            // entry, so we pass nil as the second parameter.
        logger.PrintFatal(err, nil)
    }

    defer db.Close()
    // Likewise use the PrintInfo() method to write a message at the INFO
    level.
    logger.PrintInfo("database connection pool established", nil)

    app := &application{
        config: cfg,
        logger: logger,
        models: data.NewModels(db),
    }

    srv := &http.Server{
        Addr:         fmt.Sprintf(":%d", cfg.port),
        Handler:      app.routes(),
        IdleTimeout:  time.Minute,
        ReadTimeout:  10 * time.Second,
        WriteTimeout: 30 * time.Second,
    }

    // Again, we use the PrintInfo() method to write a "starting server"
    message at the
        // INFO level. But this time we pass a map containing additional
    properties (the


// operating environment and server address) as the final parameter.
logger.PrintInfo("starting server", map[string]string{
    "addr": srv.Addr,
    "env": cfg.env,
})

err = srv.ListenAndServe()
// Use the PrintFatal() method to log the error and exit.
logger.PrintFatal(err, nil)
}
...

我们还需要更新我们 `cmd/api/errors.go` 文件中的 `logError()` 辅助函数，使其使用我们新的 Logger 实例。这里的好处之一是，在记录错误时以属性形式包含额外信息非常简单。

如果你跟着操作，请继续更新 `logError()` 方法，使其在错误信息旁边记录请求 URL 和方法。如下所示：

```
File: cmd/api/errors.go

package main

...

func (app *application) logError(r *http.Request, err error) {
    // Use the PrintError() method to log the error message, and include the current
    // request method and URL as properties in the log entry.
    app.logger.PrintError(err, map[string]string{
```

```
{"level":"FATAL","time":"2021-04-10T08:09:53Z","message":"listen tcp :4000: bind: address already in use","trace":"..."}
exit status 1
```

## 附加信息

## 与 http.Server 错误日志的集成

重要的是要意识到 Go 的 `http.Server` 也可能会写入自己的日志消息，涉及诸如未恢复的恐慌，或接受和写入 HTTP 连接时出现的问题。

默认情况下，它会将这些消息写入标准记录器——这意味着它们将被写入标准错误流（而不是像我们其他日志消息那样写入标准输出），并且它们不会采用我们漂亮的新 JSON 格式。

如果你希望所有内容都在一个地方以相同格式记录，那么这显然是个问题。

不幸的是，你不能直接将 `http.Server` 设置为使用我们新的 `Logger` 类型。相反，你需要利用我们 `Logger` 实现了 `io.Writer` 接口这一事实（多亏了我们添加的 `Write()` 方法），并将 `http.Server` 设置为使用标准库中的常规 `log.Logger` 实例，其 *writes* 目标是我们的 `Logger`。

这比听起来简单。你只需要做类似这样的操作：

```
```go
func main() {
    ...
    // Initialize the custom logger.
    logger := jsonlog.New(os.Stdout, jsonlog.LevelInfo)
    ...
    srv := &http.Server{
        Addr:         fmt.Sprintf(":%d", cfg.port),
        Handler:      app.routes(),
        // Create a new Go log.Logger instance with the log.New() function,
        // passing in
        // our custom Logger as the first parameter. The "" and 0 indicate
        // that the
        // log.Logger instance should not use a prefix or any flags.
        ErrorLog:     log.New(logger, "", 0),
        IdleTimeout:  time.Minute,
        ReadTimeout:  10 * time.Second,
        WriteTimeout: 30 * time.Second,
    }
    ...
}
```
```

这样设置后，`http.Server` 写入的任何日志消息都将被传递到我们的 `Logger.Write()` 方法，后者反过来会在 ERROR 级别输出一条 JSON 格式的日志条目。

## 第三方日志包

### 第 10.2 章。

## 恐慌恢复

目前，我们 API 处理程序中的任何恐慌都会被 Go 的 `http.Server` 自动恢复。这将展开受影响 goroutine 的堆栈（在过程中调用任何延迟函数），关闭底层的 HTTP 连接，并记录错误消息和堆栈跟踪。

这种行为是 *OK* 的，但如果我们还能向客户端发送 `500 Internal Server Error` 响应来解释出了问题会更好——而不是在没有任何上下文的情况下直接关闭 HTTP 连接。

在 *Let’s Go* 中，我们讨论了通过创建一些中间件来 *recover* 恐慌的细节，在这里再次做同样的事情是有意义的。

如果你跟着操作，请继续创建一个 `cmd/api/middleware.go` 文件：

```
```bash
$ touch cmd/api/middleware.go
```
```

并在该文件中添加一个新的 `recoverPanic()` 中间件：

File: cmd/api/middleware.go

```
```go
package main

import (
    "fmt"
    "net/http"
)

func (app *application) recoverPanic(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Create a deferred function (which will always be run in the event
        // of a panic
        // as Go unwinds the stack).
        defer func() {
            // Use the builtin recover function to check if there has been a
            // panic or
            // not.
            if err := recover(); err != nil {
                // If there was a panic, set a "Connection: close" header on
                // the
                // response. This acts as a trigger to make Go's HTTP server
                // automatically close the current connection after a
                // response has been
                // sent.
                w.Header().Set("Connection", "close")
                // The value returned by recover() has the type interface{},
                // so we use
                // fmt.Errorf() to normalize it into an error and call our
                // serverErrorResponse() helper. In turn, this will log the
                // error using
                // our custom Logger type at the ERROR level and send the
                // client a 500
                // Internal Server Error response.
                app.serverErrorResponse(w, r, fmt.Errorf("%s", err))
            }
        }()
    }
}
```
```

```
// Wrap the router with the panic recovery middleware.
return app.recoverPanic(router)
}
```

现在设置好后，如果我们的 API 处理程序之一出现恐慌，`recoverPanic()` 中间件将捕获它并调用我们常规的 `app.serverErrorResponse()` 辅助函数。反过来，这将使用我们的自定义 `Logger` 记录错误，并向客户端发送一个漂亮的 `500 Internal Server Error` 响应，其中包含 JSON 主体。

## 附加信息

## 其他 goroutine 中的恐慌恢复

非常重要的一点是要意识到，我们的中间件只能恢复在执行 `recoverPanic()` 中间件的同一 goroutine 中发生的恐慌。

例如，如果你有一个启动另一个 goroutine 的处理程序（例如执行一些后台处理），那么在后台 goroutine 中发生的任何恐慌都不会被恢复——既不会被 `recoverPanic()` 中间件恢复……也不会被 `http.Server` 内置的恐慌恢复机制恢复。这些恐慌将导致你的应用程序退出并使服务器崩溃。

## 速率限制

如果你正在构建一个供公众使用的 API，那么你很可能希望实现某种 *rate limiting*，以防止客户端 *too many requests too quickly*，并对服务器造成过度压力。

在本书的这一节中，我们将创建一些中间件来帮助实现这一点。

本质上，我们希望此中间件检查最近 ‘N’ 秒内收到了多少请求——如果请求太多——则应向客户端发送 `429 Too Many Requests` 响应。我们将把此中间件放置在主要应用程序处理程序之前，以便在执行任何昂贵的处理（如解码 JSON 请求体或查询数据库）*before* 进行此检查。

你将学习：

- 关于 *token-bucket* 速率限制器算法背后的原理，以及如何在 API 或 Web 应用程序的上下文中应用它们。
- 如何创建中间件来限制对 API 端点的请求访问，首先通过制作单个全局速率限制器，然后扩展它以基于 IP 地址支持按客户端限制。
- 如何在运行时使速率限制器行为可配置，包括为测试目的完全禁用速率限制器。

## 全局速率限制

让我们慢慢构建，首先为我们的应用程序创建一个单一的 *global rate limiter*。这将考虑 API 接收到的 *all the requests*（而不是为每个单独客户端设置单独的速率限制器）。

而不是从头开始编写自己的速率限制逻辑，这会相当复杂且耗时，我们可以利用 `x/time/rate` 包来帮助我们。这里提供了一个经过验证的 *token bucket* 速率限制器的实现。

如果你跟着操作，请继续像这样下载此包的最新版本：

```
$ go get golang.org/x/time/rate@latest
go: downloading golang.org/x/time v0.0.0-20210220033141-f8bda1e9f3ba
go: added golang.org/x/time v0.0.0-20210220033141-f8bda1e9f3ba
```

在开始编写任何代码之前，让我们花点时间解释一下令牌桶速率限制器的工作原理。来自官方 `x/time/rate` 文档的描述说：

> 一个 Limiter 控制事件被允许发生的频率。它实现了一个大小为 b 的“令牌桶”，初始时已满

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




为了防止这种情况，让我们更新代码，以便也为每个客户端记录 *最后看到* 时间。然后我们可以运行一个后台 goroutine，定期从 `clients` map 中删除最近未被看到的任何客户端。

为了实现这一点，我们需要创建一个自定义的 `client` 结构体，为每个客户端同时保存速率限制器和最后看到的时间，并在初始化中间件时启动后台清理 goroutine。

如下所示：

```
File: cmd/api/middleware.go

package main

import (
    "fmt"
    "net"
    "net/http"
    "sync"
    "time" // New import

    "golang.org/x/time/rate"
)
...
func (app *application) rateLimit(next http.Handler) http.Handler {
    // Define a client struct to hold the rate limiter and last seen time for each
    // client.
    type client struct {
        limiter *rate.Limiter
        lastSeen time.Time
    }
    var (
        mu sync.Mutex
        // Update the map so the values are pointers to a client struct.
        clients = make(map[string]*client)
    )
    // Launch a background goroutine which removes old entries from the
    // clients map once every minute.
    go func() {
        for {
            time.Sleep(time.Minute)

            // Lock the mutex to prevent any rate limiter checks from
            // happening while the cleanup is taking place.
            mu.Lock()

            // Loop through all clients. If they haven't been seen within the
            // last three minutes, delete the corresponding entry from the map.
            for ip, client := range clients {
                if time.Since(client.lastSeen) > 3*time.Minute {
                    delete(clients, ip)
                }
            }

            // Importantly, unlock the mutex when the cleanup is complete.
            mu.Unlock()
        }
    }()

    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        ip, _, err := net.SplitHostPort(r.RemoteAddr)
        if err != nil {
            app.serverErrorResponse(w, r, err)
            return
        }

        mu.Lock()

        if _, found := clients[ip]; !found {
            // Create and add a new client struct to the map if it doesn't
            // already exist.
            clients[ip] = &client{limiter: rate.NewLimiter(2, 4)}
        }

        // Update the last seen time for the client.
        clients[ip].lastSeen = time.Now()

        if !clients[ip].limiter.Allow() {
            mu.Unlock()
            app.rateLimitExceededResponse(w, r)
            return
        }

        mu.Unlock()

        next.ServeHTTP(w, r)
    })
}
```

在此阶段，如果你重启 API 并再次快速连续发送一批请求，你会发现速率限制器从单个客户端的角度来看继续正常工作——就像之前一样。

```
$ for i in {1..6}; do curl  http://localhost:4000/v1/healthcheck; done
{
    "status": "available",
    "system_info": {
        "environment": "development",
        "version": "1.0.0"
    }
}
{
    "status": "available",
    "system_info": {
        "environment": "development",
        "version": "1.0.0"
    }
}
{
    "status": "available",
    "system_info": {
        "environment": "development",
        "version": "1.0.0"
    }
}
{
    "status": "available",
    "system_info": {
        "environment": "development",
        "version": "1.0.0"
    }
}
{
    "error": "rate limit exceeded"
}
{
    "error": "rate limit exceeded"
}
```

第 11.3 章。

## 配置速率限制器

目前，我们的每秒请求数和突发值是硬编码在 `rateLimit()` 中间件中的。这是可以的，但如果它们可以在运行时配置会更灵活。同样，有一个简单的方法来完全关闭速率限制会很有用（当你想运行基准测试或进行负载测试时很有用，此时所有请求可能都来自少数几个 IP 地址）。

为了使这些内容可配置，让我们回到 `cmd/api/main.go` 文件并像下面这样更新 `config` 结构体和命令行标志：

```
File: cmd/api/main.go

package main

...

type config struct {
    port int
    env  string
    db   struct {
        dsn          string
        maxOpenConns int
        maxIdleConns int
        maxIdleTime  string
    }
    // Add a new limiter struct containing fields for the requests-per-second
    // and burst values, and a boolean field which we can use to enable/disable rate
    // limiting altogether.
    limiter struct {
        rps      float64
        burst    int
        enabled  bool
    }
}
...

func main() {
    var cfg config

    flag.IntVar(&cfg.port, "port", 4000, "API server port")
    flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

    flag.StringVar(&cfg.db.dsn, "db-dsn", os.Getenv("GREENLIGHT_DB_DSN"), "PostgreSQL DSN")

    flag.IntVar(&cfg.db.maxOpenConns, "db-max-open-conns", 25, "PostgreSQL max open connections")
    flag.IntVar(&cfg.db.maxIdleConns, "db-max-idle-conns", 25, "PostgreSQL max idle connections")
    flag.StringVar(&cfg.db.maxIdleTime, "db-max-idle-time", "15m", "PostgreSQL max connection idle time")

    // Create command line flags to read the setting values into the config struct.
    // Notice that we use true as the default for the 'enabled' setting?
    flag.Float64Var(&cfg.limiter.rps, "limiter-rps", 2, "Rate limiter maximum requests per second")
    flag.IntVar(&cfg.limiter.burst, "limiter-burst", 4, "Rate limiter maximum burst")
    flag.BoolVar(&cfg.limiter.enabled, "limiter-enabled", true, "Enable rate
```

```
clients[ip] = &client{
    // Use the requests-per-second and burst values from the config
    // struct.
    limiter: rate.NewLimiter(rate.Limit(app.config.limiter.rps), app.config.limiter.burst),
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
```

完成之后，让我们通过使用 `-limiter-burst` 标志并将突发值降低到 2 来运行 API 来试一下：

```
$ go run ./cmd/api/ -limiter-burst=2
{"level":"INFO","time":"2021-04-10T14:46:35Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-10T14:46:35Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

如果你再次快速连续发送六个请求，你现在会发现只有前两个请求成功：

```
$ for i in {1..6}; do curl  http://localhost:4000/v1/healthcheck; done
{
  "status": "available",
  "system_info": {
    "environment": "development",
    "version": "1.0.0"
  }
}
{
  "status": "available",
  "system_info": {
    "environment": "development",
    "version": "1.0.0"
  }
}
{
  "error": "rate limit exceeded"
}
{
  "error": "rate limit exceeded"
}
{
  "error": "rate limit exceeded"
}
{
  "error": "rate limit exceeded"
}
```

同样，你也可以使用 `limiter-enabled=false` 标志像下面这样完全禁用速率限制器：

```
$ go run ./cmd/api/ -limiter-enabled=false
{"level":"INFO","time":"2021-04-10T14:53:33Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-10T14:53:33Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

你会发现所有请求现在都能成功完成，无论你发送多少个。

```
$ for i in {1..6}; do curl http://localhost:4000/v1/healthcheck; done
{
  "status": "available",
  "system_info": {
    "environment": "development",
    "version": "1.0.0"
  }
}
...
{
  "status": "available",
  "system_info": {
    "environment": "development",
    "version": "1.0.0"
  }
}
```

第 12 章。

## 优雅关闭

在本书的下一节中，我们将讨论一个重要但经常被忽视的话题：*如何安全地停止正在运行的应用*。

目前，当我们停止 API 应用时（通常通过按 `Ctrl+C`），它会被 *立即* 终止，而在途的 HTTP 请求没有机会完成。这有两个原因并不理想：

- 这意味着客户端将无法收到其在途请求的响应——他们所经历的只是 HTTP 连接的硬关闭。
- 我们处理程序正在进行的工作可能被留在不完整的状态。

我们将通过为应用添加 *优雅关闭* 功能来缓解这些问题，以便在途的 HTTP 请求有机会在应用终止 *之前* 完成处理。

你将学习关于：

- 关闭信号——它们是什么，如何发送它们，以及如何在你的 API 应用中监听它们。



第12.1章。

## 发送关闭信号

当我们的应用程序运行时，我们可以通过发送特定信号随时终止它。常见的做法（你可能已经在使用）是在键盘上按下 `Ctrl+C` 来发送 *中断* 信号——也称为 `SIGINT`。

但这并不是唯一能停止我们应用程序的信号类型。其他一些常见信号有：

| 信号 | 描述 | 键盘快捷键 | 可捕获 |
|---|---|---|---|
| `SIGINT` | 键盘中断 | `Ctrl+C` | 是 |
| `SIGQUIT` | 键盘退出 | `Ctrl+\` | 是 |
| `SIGKILL` | 终止进程（立即终止） | - | 否 |
| `SIGTERM` | 有序终止进程 | - | 是 |

重要的是要提前说明，有些信号是 *可捕获* 的，而有些则不是。可捕获信号可以被我们的应用程序拦截，然后忽略，或用于触发特定操作（如优雅关闭）。其他信号，如 `SIGKILL`，不可捕获，也无法被拦截。

让我们快速看看这些信号的实际效果。如果你跟着操作，请照常使用相同的 `go run ./cmd/api` 命令启动 API 应用程序：

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T07:33:39Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T07:33:39Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

这样做应该会在你的机器上启动一个名为 `api` 的进程。你可以使用 `pgrep` 命令来验证该进程是否存在，如下所示：

```
$ pgrep -l api
4414 api
```

在我的例子中，我可以看到 `api` 进程正在运行，并且其 *进程 ID* 为 `4414`（你的进程 ID 很可能不同）。

确认后，请继续使用 `pkill` 命令向 `api` 进程发送 `SIGKILL` 信号，如下所示：

```
$ pkill -SIGKILL api
```

如果你回到运行 API 应用程序的终端窗口，你应该会看到它已被终止，并且输出流中的最后一行是 signal: killed。类似于这样：

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T07:33:39Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T07:33:39Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
signal: killed
```

随意重复同样的过程，但改为发送 SIGTERM 信号：

```
$ pkill -SIGTERM api
```

这次你应该会在输出末尾看到 signal: terminated 行，如下所示：

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T07:35:54Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T07:35:54Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
signal: terminated
```

我们可以看到这些信号确实能有效终止我们的应用程序——但问题是它们都会导致应用程序 *立即* 退出。

幸运的是，Go 在 `os/signals` 包中提供了工具，我们可以用它来拦截可捕获信号并触发应用程序的优雅关闭。我们将在下一章中了解如何实现。

```
defer db.Close()

logger.PrintInfo("database connection pool established", nil)

app := &application{
    config: cfg,
    logger: logger,
    models: data.NewModels(db),
}

// Call app.serve() to start the server.
err = app.serve()
if err != nil {
    logger.PrintFatal(err, nil)
}
}
...
```

## 捕获 SIGINT 和 SIGTERM 信号

我们接下来要做的是更新应用程序，使其能够‘捕获’任何 SIGINT 和 SIGTERM 信号。如上所述，SIGKILL 信号不可捕获（并且总是会导致应用程序立即终止），我们将保留 SIGQUIT 的默认行为（因为如果你想通过键盘快捷键执行非优雅关闭，这很方便）。

为了捕获信号，我们需要启动一个在应用程序生命周期内运行的后台 goroutine。在这个后台 goroutine 中，我们可以使用 signal.Notify() 函数监听特定信号并将其转发到通道以供进一步处理。

我来演示。

打开 cmd/api/server.go 文件并像这样更新它：

```
File: cmd/api/server.go

package main

import (
    "fmt"
    "net/http"
    "os"      // New import
    "os/signal" // New import
    "syscall"  // New import
    "time"
)

func (app *application) serve() error {
    srv := &http.Server{
        Addr:         fmt.Sprintf(":%d", app.config.port),
        Handler:      app.routes(),
        IdleTimeout:  time.Minute,
        ReadTimeout:  10 * time.Second,
        WriteTimeout: 30 * time.Second,
    }

    // Start a background goroutine.
    go func() {
        // Create a quit channel which carries os.Signal values.
        quit := make(chan os.Signal, 1)

        // Use signal.Notify() to listen for incoming SIGINT and SIGTERM signals and
```

有一点我想快速强调一下：我们的 `quit` 通道是一个大小为 1 的 `buffered channel`。

我们需要在这里使用缓冲通道，因为 `signal.Notify()` `does not wait` 为 `quit` 通道发送信号时等待接收者可用。如果我们在这里改用普通（非缓冲）通道，则如果在信号发送的精确时刻 `quit` 通道没有准备好接收，信号可能会被‘错过’。通过使用缓冲通道，我们避免了这个问题，并确保永远不会错过信号。

好吧，让我们试试。

首先，运行应用程序，然后在键盘上按下 `Ctrl+C` 发送 `SIGINT` 信号。你应该会看到一条 `"caught signal"` 日志条目，其属性中包含 `"signal":"interrupt"`，类似于这样：

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:42:28Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:42:28Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
^C{"level":"INFO","time":"2021-04-11T10:42:29Z","message":"caught signal","properties":{"signal":"interrupt"}}
```

你也可以重新启动应用程序并尝试发送 `SIGTERM` 信号。这次日志条目属性应包含 `"signal":"terminated"`，如下所示：

```
$ pkill -SIGTERM api
```

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:42:46Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:42:46Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
{"level":"INFO","time":"2021-04-11T10:42:51Z","message":"caught signal","properties":{"signal":"terminated"}}
```

相比之下，发送 `SIGKILL` 或 `SIGQUIT` 信号仍会立即导致应用程序退出 *而不会被捕获*，因此日志中不应看到 `caught signal` 消息。例如，如果你重新启动应用程序并发出 `SIGKILL`...

```
$ pkill -SIGKILL api
```

应用程序应立即终止，日志看起来像这样：

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:43:12Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:43:12Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
{"level":"INFO","time":"2021-04-11T10:43:12Z","message":"starting
```

## 执行关闭

拦截信号很好，但如果不做任何处理就没什么用！在本章中，我们将更新应用程序，使我们拦截的 `SIGINT` 和 `SIGTERM` 信号触发 API 的优雅关闭。

具体来说，在收到这些信号之一后，我们将调用 HTTP 服务器上的 `Shutdown()` 方法。官方文档对此的描述如下：

> > *Shutdown 会在不中断任何活动连接的情况下优雅地关闭服务器。Shutdown 通过首先关闭所有打开的监听器，然后关闭所有空闲连接，然后无限期等待连接返回空闲状态后再关闭来实现。*

实际实现这一模式很难用文字描述，所以让我们直接进入代码，并在过程中讨论细节。

```
File: cmd/api/server.go

```go
package main

import (
    "context" // New import
)
```



```go
"errors" // New import
"fmt"
"net/http"
"os"
"os/signal"
"syscall"
"time"
)

func (app *application) serve() error {
    srv := &http.Server{
        Addr:         fmt.Sprintf(":%d", app.config.port),
        Handler:      app.routes(),
        IdleTimeout:  time.Minute,
        ReadTimeout:  10 * time.Second,
        WriteTimeout: 30 * time.Second,
    }

    // Create a shutdownError channel. We will use this to receive any errors returned
    // by the graceful Shutdown() function.
    shutdownError := make(chan error)

    go func() {
        // Intercept the signals, as before.
        quit := make(chan os.Signal, 1)
        signal.Notify(quit, syscall.SIGINT, syscall.SIGTERM)
        s := <-quit

        // Update the log entry to say "shutting down server" instead of "caught signal".
        app.logger.PrintInfo("shutting down server", map[string]string{
            "signal": s.String(),
        })

        // Create a context with a 5-second timeout.
        ctx, cancel := context.WithTimeout(context.Background(),
        5*time.Second)
        defer cancel()

// Call Shutdown() on our server, passing in the context we just
made.
    // Shutdown() will return nil if the graceful shutdown was
successful, or an
    // error (which may happen because of a problem closing the
listeners, or
    // because the shutdown didn't complete before the 5-second context
deadline is
    // hit). We relay this return value to the shutdownError channel.
    shutdownError <- srv.Shutdown(ctx)
}()

app.logger.PrintInfo("starting server", map[string]string{
    "addr": srv.Addr,
    "env":  app.config.env,
})

    // Calling Shutdown() on our server will cause ListenAndServe() to
immediately
    // return a http.ErrServerClosed error. So if we see this error, it is
actually a
    // good thing and an indication that the graceful shutdown has started.
So we check
    // specifically for this, only returning the error if it is NOT
http.ErrServerClosed.
    err := srv.ListenAndServe()
    if !errors.Is(err, http.ErrServerClosed) {
        return err
    }

    // Otherwise, we wait to receive the return value from Shutdown() on the
    // shutdownError channel. If return value is an error, we know that there
was a
    // problem with the graceful shutdown and we return the error.
    err = <-shutdownError
    if err != nil {
        return err
    }

// At this point we know that the graceful shutdown completed
successfully and we
    // log a "stopped server" message.
    app.logger.PrintInfo("stopped server", map[string]string{
        "addr": srv.Addr,
    })

    return nil
}
```

乍一看，这段代码可能有些复杂，但概括地说，它的行为非常简单：*当我们收到 `SIGINT` 或 `SIGTERM` 信号时，我们会让服务器停止接受任何新的 HTTP 请求，并在应用程序终止之前，给所有正在处理中的请求一个 5 秒的“宽限期”来完成。*

但有几个重要的细节需要注意：

-   `Shutdown()` 方法不会等待任何后台任务完成，也不会关闭 WebSocket 这类被劫持的长期连接。相反，你需要自行实现逻辑来协调这些部分的优雅关闭。我们会在本书后面探讨一些相关技术。
-   当前有一个未修复的 bug，它会将 HTTP/2 连接的宽限期实际上限制为 5 秒。HTTP/2 在 Go 中会自动支持 HTTPS 连接，因此如果你打算在 Go 应用中处理 HTTPS 连接，那么（目前）合理的做法是让你的上下文超时时间低于 5 秒。如果不是因为这个 bug，我会建议在本章中使用更长的宽限期（大约 20 秒）。

不过撇开这些事情不谈，现在它在我们的应用中应该运行良好了。

为了帮助演示优雅关闭的功能，你可以给 `healthcheckHandler` 方法添加一个 4 秒的休眠延迟，如下所示：

文件：cmd/api/healthcheck.go

```go
package main

import (
    "net/http"
    "time" // New import
)

func (app *application) healthcheckHandler(w http.ResponseWriter, r *http.Request) {
    env := envelope{
        "status": "available",
        "system_info": map[string]string{
            "environment": app.config.env,
            "version":     version,
        },
    }

    // Add a 4 second delay.
    time.Sleep(4 * time.Second)

    err := app.writeJSON(w, http.StatusOK, env, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

然后启动 API，并在另一个终端窗口中向 healthcheck 端点发起一个请求，然后发送一个 SIGTERM 信号。

```
$ curl localhost:4000/v1/healthcheck & pkill -SIGTERM api
```

在服务器日志中，你应该会立刻看到一条紧随 SIGTERM 信号之后的“shutting down server”消息，类似于这样：

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:54:55Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:54:55Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
{"level":"INFO","time":"2021-04-11T10:55:03Z","message":"shutting down server","properties":{"signal":"terminated"}}
```

然后，在等待 4 秒让正在进行的请求完成后，我们的 healthcheckHandler 应该会正常返回 JSON 响应，并且你会看到我们的 API 在干净退出前记录了一条最后的“stopped server”消息：

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:54:55Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:54:55Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
{"level":"INFO","time":"2021-04-11T10:55:03Z","message":"shutting down server","properties":{"signal":"terminated"}}
{"level":"INFO","time":"2021-04-11T10:55:07Z","message":"stopped server","properties":{"addr":":4000"}}
```

注意到上面时间戳中“shutting down server”和“stopped server”消息之间 4 秒的延迟了吗？

所以现在一切运行得很好。任何时候我们想要优雅地关闭应用程序，都可以通过发送 SIGINT（Ctrl+C）或 SIGTERM 信号来实现。只要没有哪个正在进行的请求耗时超过 5 秒，我们的处理器就有时间完成工作，客户端也会收到正常的 HTTP 响应。而如果我们想不经过优雅关闭直接立即退出，仍然可以通过发送 SIGQUIT（Ctrl+\）或 SIGKILL 信号来完成。

最后，如果你在跟着操作，请将 healthcheckHandler 恢复原状，移除那 4 秒的休眠。如下所示：

文件：cmd/api/healthcheck.go

```go
package main

import (
"net/http"
)

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
        app.serverErrorResponse(w, r, err)
    }
}
```

## 创建用户数据库表

让我们先在数据库中创建一个新的 users 表。如果你在跟着操作，请使用 migrate 工具生成一对新的 SQL 迁移文件：

```
$ migrate create -seq -ext=.sql -dir=./migrations create_users_table
/home/alex/Projects/greenlight/migrations/000004_create_users_table.up.sql
/home/alex/Projects/greenlight/migrations/000004_create_users_table.down.sql
```

然后分别将以下 SQL 语句添加到“up”和“down”文件中：

文件：migrations/000004_create_users_table.up.sql

```sql
CREATE TABLE IF NOT EXISTS users (
  id bigserial PRIMARY KEY,
  created_at timestamp(0) with time zone NOT NULL DEFAULT NOW(),
  name text NOT NULL,
  email citext UNIQUE NOT NULL,
  password_hash bytea NOT NULL,
  activated bool NOT NULL,
  version integer NOT NULL DEFAULT 1
);
```

文件: migrations/000004_create_users_table.down.sql

```
DROP TABLE IF EXISTS users;
```

关于这个 `CREATE TABLE` 语句，有几点有趣的事情我想快速解释一下：

- 1. `email` 列的类型为 `citext`（不区分大小写的文本）。该类型以输入时的确切形式存储文本数据——不会以任何方式更改大小写——但对数据的 *比较* 始终不区分大小写……包括对相关索引的查找。
- 2. 我们在 `email` 列上还有一个 `UNIQUE` 约束。结合 `citext` 类型，这意味着数据库中不能有两行具有相同的电子邮件值——即使它们的大小写不同。这本质上强制执行数据库级别的业务规则，即 *不应存在具有相同电子邮件地址的两个用户*。
- 3. `password_hash` 列的类型为 `bytea`（二进制字符串）。在此列中我们将存储使用 `bcrypt` 生成的用户的密码的 *单向哈希*——而不是明文密码本身。
- 4. `activated` 列存储一个布尔值，用来表示用户账户是否‘active’。我们将把此值设置为 `false`，方法是

## Magnus Carlsen. 有史以来最好的国际象棋选手吗？

虽然世界杯和大奖赛系列赛历史上一直是通往候选人锦标赛的主要途径，但国际棋联巡回赛已成为另一条途径，奖励全年持续的卓越表现。

这一调整旨在为在多项赛事中表现强劲的选手创造更多机会，确保候选人阵容反映当代国际象棋的顶尖水平。

然而，它也引入了新的战略考量。选手现在必须在参加高水平赛事和积累巡回赛积分之间取得平衡，为本已艰苦的日程增添了另一层复杂性。

关于有史以来最伟大的国际象棋选手的争论几十年来一直吸引着爱好者。

不过，还有另一种晋级候选人赛的方式，往往被忽视但同样重要：国际棋联巡回赛。

- 材质: polyresin, hand painted
- 尺寸: 30cm/11.8in tall
- 产地: Spain

> > 世界杯和大奖赛长期以来一直是国际象棋的终极试炼场，但国际棋联巡回赛正悄悄重塑通往候选人赛的道路。

随着国际象棋界展望未来，这些晋级途径之间的相互作用将成为决定性的叙事。随着新星和资深老将争夺有限的名额，通往候选人赛的旅程从未如此引人入胜。

在这种背景下，候选人锦标赛本身已不仅仅是通往世界锦标赛的门户——它是对战略深度、韧性和不懈追求卓越的庆祝。

从鲍比·菲舍尔的传奇壮举到马格努斯·卡尔森的现代统治，每个时代都涌现出重新定义游戏边界的天才。

![](img/30f9221bfc265d52b544dd595ca099de_441_0.png)

阅读更多：

| 列 | 类型 |  | 非空 | 默认值 |
|---|---|---|---|---|
|  |  |  |  | nextval('users_id_seq'::regclass) |
| created_at | timestamp(0) with time zone |  | not null | now() |
| name | text |  | not null |  |
| email | citext |  | not null |  |
| password_hash | bytea |  | not null |  |
| activated | boolean |  | not null |  |
| version | integer |  | not null | 1 |

索引:
  "users_pkey" PRIMARY KEY, btree (id)
  "users_email_key" UNIQUE CONSTRAINT, btree (email)

这里有一点很重要：我们 `email` 列上的 `UNIQUE` 约束已被自动分配名称 `users_email_key`。这将在下一章变得相关，当我们需要处理用户使用相同电子邮件地址重复注册时产生的任何错误。

### 第13.2章。

## 设置 Users 模型

现在我们的数据库表已经设置好，我们将更新 `internal/data` 包以包含一个新的 `User` 结构体（用于表示单个用户的数据），并创建一个 `UserModel` 类型（我们将用它对我们的 `users` 表执行各种 SQL 查询）。

如果你跟着做，请继续创建一个 `internal/data/users.go` 文件来存放这段新代码：

```
$ touch internal/data/users.go
```

让我们开始定义 `User` 结构体，以及一些用于设置和验证用户密码的辅助方法。

正如我们之前提到的，在本项目中我们将使用 bcrypt 在将用户密码存储到数据库之前对其进行哈希处理。因此，我们需要做的第一件事是安装 `golang.org/x/crypto/bcrypt` 包，它提供了 bcrypt 算法的易于使用的 Go 实现。

```
$ go get golang.org/x/crypto/bcrypt@latest
go: downloading golang.org/x/crypto v0.0.0-20210314154223-e6e6c4f2bb5b
go get: added golang.org/x/crypto v0.0.0-20210314154223-e6e6c4f2bb5b
```

然后在 `internal/data/users.go` 文件中，继续创建 `User` 结构体和辅助方法，如下所示：

```
File: internal/data/users.go

package data

import (
    "errors"
    "time"

    "golang.org/x/crypto/bcrypt"
)

// Define a User struct to represent an individual user. Importantly, notice how we are
// using the json:"-" struct tag to prevent the Password and Version fields appearing in
// any output when we encode it to JSON. Also notice that the Password field uses the
// custom password type defined below.
type User struct {
    ID          int64     `json:"id"`
    CreatedAt   time.Time `json:"created_at"`
    Name        string    `json:"name"`
    Email       string    `json:"email"`
    Password    password  `json:"-"`
    Activated   bool      `json:"activated"`
    Version     int       `json:"-"`
}

// Create a custom password type which is a struct containing the plaintext
and hashed
// versions of the password for a user. The plaintext field is a *pointer* to
a string,
// so that we're able to distinguish between a plaintext password not being
present in
// the struct at all, versus a plaintext password which is the empty string
"".
type password struct {
    plaintext *string
    hash      []byte
}

// The Set() method calculates the bcrypt hash of a plaintext password, and
stores both
// the hash and the plaintext versions in the struct.
func (p *password) Set(plaintextPassword string) error {
    hash, err := bcrypt.GenerateFromPassword([]byte(plaintextPassword), 12)
    if err != nil {
        return err
    }

    p.plaintext = &plaintextPassword
    p.hash = hash

    return nil
}

// The Matches() method checks whether the provided plaintext password
matches the
// hashed password stored in the struct, returning true if it matches and
false
// otherwise.
func (p *password) Matches(plaintextPassword string) (bool, error) {
    err := bcrypt.CompareHashAndPassword(p.hash, []byte(plaintextPassword))
    if err != nil {
        switch {
        case errors.Is(err, bcrypt.ErrMismatchedHashAndPassword):
            return false, nil
        default:
            return false, err
        }
    }

    return true, nil
}
```

我们之前在 *Let's Go* 中解释了 golang.org/x/crypto/bcrypt 包的工作原理，但让我们快速回顾一下要点：

- `bcrypt.GenerateFromPassword()` 函数使用特定的成本参数生成密码的 bcrypt 哈希（在上面的代码中，我们使用成本为 12）。成本越高，生成哈希的速度越慢，计算成本也越高。这里需要取得平衡——我们希望成本对攻击者来说高得难以承受，但又不能 *慢* 到损害我们 API 的用户体验。此函数返回格式为的 *哈希字符串*：

```
$2b$[cost]$[22-character salt][31-character hash]
```

- `bcrypt.CompareHashAndPassword()` 函数通过使用与我们要比较的哈希字符串中相同的 *salt 和成本参数* 对提供的密码重新哈希来工作。然后将重新哈希的值与原始哈希字符串使用 `subtle.ConstantTimeCompare()` 函数进行检查，该函数以恒定时间执行比较（以降低时序攻击的风险）。如果不匹配，则会返回 `bcrypt.ErrMismatchedHashAndPassword` 错误。





## 添加验证检查

让我们继续为 User 结构体添加一些验证检查。具体来说，我们需要：

- 检查 `Name` 字段不为空字符串，且值的长度小于 500 字节。
- 检查 `Email` 字段不为空字符串，并且匹配我们在本书前面 `validator` 包中添加的电子邮件地址正则表达式。
- 如果 `Password.plaintext` 字段不是 `nil`，则检查其值不为空字符串，且长度在 8 到 72 字节之间。
- 检查 `Password.hash` 字段永远不会是 `nil`。

**注意：** 在创建 bcrypt 哈希时，输入会被截断为最大 72 字节。因此，如果有人使用了非常长的密码，意味着在创建哈希时，该长度之后的任何字节实际上都会被忽略。为了避免用户产生困惑，我们将在验证检查中对密码实施 72 字节的硬性最大长度限制。如果你不想实施最大长度限制，可以对密码进行预哈希处理。

此外，在本书后面的内容中，我们还会单独复用电子邮件和明文密码的验证检查，因此我们将把那些检查定义在独立的函数中。

继续，更新 `internal/data/users.go` 文件，如下所示：

File: internal/data/users.go

```go
package data

import (
    "errors"
    "time"

    "greenlight.alexedwards.net/internal/validator" // New import

    "golang.org/x/crypto/bcrypt"
)
...

func ValidateEmail(v *validator.Validator, email string) {
    v.Check(email != "", "email", "must be provided")
    v.Check(validator.Matches(email, validator.EmailRX), "email", "must be a valid email address")
}

func ValidatePasswordPlaintext(v *validator.Validator, password string) {
    v.Check(password != "", "password", "must be provided")
    v.Check(len(password) >= 8, "password", "must be at least 8 bytes long")
    v.Check(len(password) <= 72, "password", "must not be more than 72 bytes long")
}

func ValidateUser(v *validator.Validator, user *User) {
    v.Check(user.Name != "", "name", "must be provided")
    v.Check(len(user.Name) <= 500, "name", "must not be more than 500 bytes long")

    // Call the standalone ValidateEmail() helper.
    ValidateEmail(v, user.Email)

    // If the plaintext password is not nil, call the standalone
    // ValidatePasswordPlaintext() helper.
    if user.Password.plaintext != nil {
        ValidatePasswordPlaintext(v, *user.Password.plaintext)
    }

    // If the password hash is ever nil, this will be due to a logic error in our
    // codebase (probably because we forgot to set a password for the user).
    // It's a useful sanity check to include here, but it's not a problem with the data
    // provided by the client. So rather than adding an error to the validation map we
    // raise a panic instead.
    if user.Password.hash == nil {
        panic("missing password hash for user")
    }
}
```

## 创建 UserModel

此过程的下一步是设置一个 `UserModel` 类型，用于隔离我们与 PostgreSQL `users` 表的数据库交互。

我们将沿用之前为 `MovieModel` 使用的模式，并实现以下三个方法：

- `Insert()` 用于在数据库中创建新的用户记录。
- `GetByEmail()` 用于获取具有特定电子邮件地址的用户数据。
- `Update()` 用于修改特定用户的数据。

再次打开 internal/data/users.go 文件，并添加以下代码：

```go
File: internal/data/users.go

package data

import (
    "context"    // New import
    "database/sql" // New import
    "errors"
    "time"

    "greenlight.alexedwards.net/internal/validator"

    "golang.org/x/crypto/bcrypt"
)

// Define a custom ErrDuplicateEmail error.
var (
    ErrDuplicateEmail = errors.New("duplicate email")
)

...

// Create a UserModel struct which wraps the connection pool.
type UserModel struct {
    DB *sql.DB
}

// Insert a new record in the database for the user. Note that the id,
// created_at and
// version fields are all automatically generated by our database, so we use
// the RETURNING clause to read them into the User struct after the insert, in
// the same way that we did when creating a movie.
func (m UserModel) Insert(user *User) error {
    query := `
        INSERT INTO users (name, email, password_hash, activated)
        VALUES ($1, $2, $3, $4)
        RETURNING id, created_at, version`

    args := []interface{}{user.Name, user.Email, user.Password.hash,
user.Activated}

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    // If the table already contains a record with this email address, then
    // when we try to perform the insert there will be a violation of the UNIQUE
    // "users_email_key" constraint that we set up in the previous chapter. We check for this
    // error specifically, and return custom ErrDuplicateEmail error instead.
    err := m.DB.QueryRowContext(ctx, query, args...).Scan(&user.ID,
&user.CreatedAt, &user.Version)
    if err != nil {
        switch {
        case err.Error() == `pq: duplicate key value violates unique constraint "users_email_key"`:
            return ErrDuplicateEmail
        default:
            return err
        }
    }

    return nil
}

// Retrieve the User details from the database based on the user's email
// address.
// Because we have a UNIQUE constraint on the email column, this SQL query
// will only return one record (or none at all, in which case we return a
// ErrRecordNotFound error).
func (m UserModel) GetByEmail(email string) (*User, error) {
    query := `
        SELECT id, created_at, name, email, password_hash, activated, version
        FROM users
        WHERE email = $1`

    var user User

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    err := m.DB.QueryRowContext(ctx, query, email).Scan(
        &user.ID,
        &user.CreatedAt,
        &user.Name,
        &user.Email,
        &user.Password.hash,
        &user.Activated,
        &user.Version,
    )

    if err != nil {
        switch {
        case errors.Is(err, sql.ErrNoRows):
            return nil, ErrRecordNotFound
        default:
            return nil, err
        }
    }

    return &user, nil
}

// Update the details for a specific user. Notice that we check against the
// version field to help prevent any race conditions during the request cycle, just
// like we did when updating a movie. And we also check for a violation of the
// "users_email_key" constraint when performing the update, just like we did when inserting the
// user record originally.
func (m UserModel) Update(user *User) error {
    query := `
        UPDATE users
        SET name = $1, email = $2, password_hash = $3, activated = $4,
        version = version + 1
        WHERE id = $5 AND version = $6
        RETURNING version`

    args := []interface{}{
        user.Name,
        user.Email,
        user.Password.hash,
        user.Activated,
        user.ID,
        user.Version,
    }

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    err := m.DB.QueryRowContext(ctx, query, args...).Scan(&user.Version)
    if err != nil {
        switch {
        case err.Error() == `pq: duplicate key value violates unique constraint "users_email_key"`:
            return ErrDuplicateEmail
        case errors.Is(err, sql.ErrNoRows):
            return ErrEditConflict
        default:
            return err
        }
    }

    return nil
}
```

希望这看起来简洁明了——我们使用的是与本书前面 `movies` 表 CRUD 操作相同的代码模式。

唯一的区别是，在某些方法中，我们专门检查是否因违反唯一性 `users_email_key` 约束而产生错误。正如我们将在下一章中看到的，通过将此视为特殊情况，我们能够向客户端返回一条“该电子邮件地址已被使用”的消息，而不是像通常那样发送 500 `Internal Server Error` 响应。

最后，为了完成所有工作，我们需要更新 `internal/data/models.go` 文件，将新的 `UserModel` 包含到父级 `Models` 结构体中。如下所示：

```go
File: internal/data/models.go

package data

...

type Models struct {
    Movies MovieModel
    Users  UserModel // Add a new Users field.
}

func NewModels(db *sql.DB) Models {
```




```
return Models{
    Movies: MovieModel{DB: db},
    Users:  UserModel{DB: db}, // Initialize a new UserModel instance.
}
}
```

### 第 13.3 章.

### 注册用户

现在基础工作已经完成，让我们开始将其付诸实践，通过创建一个新的 API 端点来管理注册（或 *注册*）新用户的流程。

| 方法 | URL 模式 | 处理程序 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用程序信息 |
| GET | /v1/movies | listMoviesHandler | 显示所有电影的详细信息 |
| POST | /v1/movies | createMovieHandler | 创建新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |
| PATCH | /v1/movies/:id | updateMovieHandler | 更新特定电影的详细信息 |
| DELETE | /v1/movies/:id | deleteMovieHandler | 删除特定电影 |
| POST | /v1/users | registerUserHandler | 注册新用户 |

当客户端调用这个新的 `POST /v1/users` 端点时，我们期望他们在 JSON 请求体中提供新用户的以下详细信息。类似于这样：

```
{
  "name": "Alice Smith",
  "email": "alice@example.com",
  "password": "pa55word"
}
```

当我们收到这些数据时，`registerUserHandler` 应该创建一个包含这些详细信息的新的 `User` 结构体，使用 `ValidateUser()` 辅助函数对其进行验证，然后将其传递给我们的 `UserModel.Insert()` 方法以创建新的数据库记录。

事实上，我们已经为 `registerUserHandler` 编写了大部分所需代码——现在只需按正确的顺序将它们拼凑起来即可。

如果你跟着操作，请继续创建一个新的 `cmd/api/users.go` 文件：

```
$ touch cmd/api/users.go
```

然后添加包含以下代码的新 `registerUserHandler` 方法：

```
File: cmd/api/users.go

package main
```

```
import (
    "errors"
    "net/http"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator"
)

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
    // Create an anonymous struct to hold the expected data from the request body.
    var input struct {
        Name     string `json:"name"`
        Email    string `json:"email"`
        Password string `json:"password"`
    }

    // Parse the request body into the anonymous struct.
    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    // Copy the data from the request body into a new User struct. Notice also that we
    // set the Activated field to false, which isn't strictly necessary because the
    // Activated field will have the zero-value of false by default. But setting this
    // explicitly helps to make our intentions clear to anyone reading the code.
    user := &data.User{
        Name:       input.Name,
        Email:      input.Email,
        Activated: false,
    }
}
```
```
// Use the Password.Set() method to generate and store the hashed and
    // plaintext
    // passwords.
    err = user.Password.Set(input.Password)
    if err != nil {
        app.serverErrorResponse(w, r, err)
        return
    }

    v := validator.New()

    // Validate the user struct and return the error messages to the client
if any of
    // the checks fail.
    if data.ValidateUser(v, user); !v.Valid() {
        app.failedValidationResponse(w, r, v.Errors)
        return
    }

    // Insert the user data into the database.
    err = app.models.Users.Insert(user)
    if err != nil {
        switch {
        // If we get a ErrDuplicateEmail error, use the v.AddError() method
to manually
        // add a message to the validator instance, and then call our
        // failedValidationResponse() helper.
        case errors.Is(err, data.ErrDuplicateEmail):
            v.AddError("email", "a user with this email address already
exists")
            app.failedValidationResponse(w, r, v.Errors)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }

    // Write a JSON response containing the user data along with a 201
Created status
```
```
// code.
err = app.writeJSON(w, http.StatusCreated, envelope{"user": user}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```

在尝试之前，我们还需要将新的 POST /v1/users 端点添加到我们的 cmd/api/routes.go 文件中。如下所示：

```
File: cmd/api/routes.go

package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck", app.healthcheckHandler)

    router.HandlerFunc(http.MethodGet, "/v1/movies", app.listMoviesHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id", app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id", app.updateMovieHandler)
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id", app.deleteMovieHandler)
```
```
// Add the route for the POST /v1/users endpoint.
router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)

return app.recoverPanic(app.rateLimit(router))
}
```

完成这些后，请确保所有文件都已保存并启动 API。

然后继续向 POST /v1/users 端点发送请求，以使用电子邮件地址 alice@example.com 注册新用户。你应该会收到 201 Created 响应，其中显示用户的详细信息，类似于这样：

```
$ BODY='{"name": "Alice Smith", "email": "alice@example.com", "password": "pa55word"}'
$ curl -i -d "$BODY" localhost:4000/v1/users
HTTP/1.1 201 Created
Content-Type: application/json
Date: Mon, 15 Mar 2021 14:42:58 GMT
Content-Length: 152

{
  "user": {
    "id": 1,
    "created_at": "2021-03-15T15:42:58+01:00",
    "name": "Alice Smith",
    "email": "alice@example.com",
    "activated": false
  }
}
```

**提示：** 如果你跟着操作，请记住你在上面请求中使用的密码——稍后你会需要它！

看起来不错。我们可以从状态码看出用户记录已成功创建，而在 JSON 响应中可以看到新用户的系统生成信息——包括用户的 ID 和激活状态。

如果查看你的 PostgreSQL 数据库，你还应该在 `users` 表中看到新记录。类似于这样：

```
$ psql $GREENLIGHT_DB_DSN
Password for user greenlight:
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

greenlight=> SELECT * FROM users;
 id | created_at | name | email |
 password_hash | activated | version
 -----+----------------------------+------------+---------------+------------------------------+------------+--------
 -----+----------------------------+------------+---------------+------------------------------+------------+--------
 1 | 2021-04-11 14:29:45+02 | Alice Smith | alice@example.com |
 \x24326124313224526157784d67356d... | f | 1
(1 row)
```

**注意：** `psql` 工具始终以十六进制编码的字符串显示 `bytea` 值。因此上面输出中的 `password_hash` 字段

显示的是 bcrypt 哈希的 *十六进制编码*。如果你愿意，可以运行以下查询将常规字符串版本也附加到表中：

```
SELECT *, encode(password_hash, 'escape') FROM users.
```

好的，让我们尝试向我们的 API 发送另一个请求，但使用一些无效的用户详细信息。这次我们的验证检查会启动，客户端应收到相关的错误消息。例如：

```
$ BODY='{"name": "", "email": "bob@invalid.", "password": "pass"}'
$ curl -d "$BODY" localhost:4000/v1/users
{
    "error": {
        "email": "must be a valid email address",
        "name": "must be provided",
        "password": "must be at least 8 bytes long"
    }
}
```

最后，尝试为 `alice@example.com` 注册第二个账户。这次你应该会收到包含“*此电子邮件地址的用户已存在*”消息的验证错误，如下所示：

```
$ BODY='{"name": "Alice Jones", "email": "alice@example.com", "password": "pa55word"}'
$ curl -i -d "$BODY" localhost:4000/v1/users
HTTP/1.1 422 Unprocessable Entity
Cache-Control: no-store
Content-Type: application/json
```




```
Date: Wed, 30 Dec 2020 14:22:06 GMT
Content-Length: 78

{
  "error": {
    "email": "a user with this email address already exists"
  }
}
```

如果你愿意，你还可以尝试使用 `alice@example.com` 的不同大小写形式来发送一些请求——例如 `ALICE@example.com` 或 `Alice@Example.com`。由于我们数据库中的 `email` 列类型为 `citext`，这些不同形式的版本也会被成功识别为重复。

## 补充信息

### 电子邮件的字母大小写敏感性

让我们稍微更详细地谈谈电子邮件地址的大小写敏感性。

- 根据 RFC 2821 中的规范，电子邮件地址的域名部分（`username@domain`）不区分大小写。这意味着我们可以确信，`alice@example.com` 背后的真实用户与 `alice@EXAMPLE.COM` 是同一个人。

- 电子邮件地址的用户名部分*可能区分大小写，也可能不区分*——这取决于电子邮件提供商。几乎所有主要的电子邮件提供商都将用户名视为不区分大小写，但这并非绝对保证。我们在这里能说的是，地址 `alice@example.com` 背后的真实用户*很有可能*（但并非绝对）与 `ALICE@example.com` 是同一个人。

那么，这对我们的应用程序意味着什么？

从安全的角度来看，我们应该始终使用用户在注册期间提供的准确大小写来存储电子邮件地址，并且**我们应该只使用该大小写给用户发送电子邮件**。如果我们不这样做，电子邮件就有可能被发送给错误的真实用户。在任何一个使用电子邮件进行身份验证的工作流程中（例如密码重置工作流程），尤其需要注意这一点。

然而，由于 `alice@example.com` 和 `ALICE@example.com` *很有可能*是同一个用户，为了比较的目的，我们通常应该将电子邮件地址视为不区分大小写。

在我们的注册工作流程中，使用不区分大小写的比较可以防止用户仅仅通过使用不同的大小写而意外（或故意）注册多个账户。而且从用户体验的角度来看，在登录、激活或密码重置等工作流程中，如果我们不要求用户提交请求时必须使用与注册时完全相同的大小写，这对用户会更加宽容。

## 用户枚举

重要的是要知道，我们的注册端点容易受到*用户枚举*攻击。例如，如果攻击者想知道 `alice@example.com` 是否在我们的服务上拥有账户，他们只需要发送一个类似这样的请求：

```bash
$ BODY='{"name": "Alice Jones", "email": "alice@example.com", "password": "pa5sword"}'
$ curl -d "$BODY" localhost:4000/v1/users
{
    "error": {
        "email": "a user with this email address already exists"
    }
}
```

而他们立刻就能得到答案。我们实际上是在明确地告诉攻击者，`alice@example.com` 已经是一个注册用户了。

那么，泄露这些信息有什么风险呢？

第一个也是最明显的风险与用户隐私有关。对于敏感或机密的服务，你可能不希望让别人轻易看出谁拥有账户。第二个风险是，它使攻击者更容易入侵用户的账户。一旦他们知道了用户的电子邮件地址，他们就可能：

- 通过社会工程学或其他类型的定向攻击来针对该用户。

- 在泄露的密码表中搜索该电子邮件地址，并在我们的服务上尝试这些相同的密码。

防止枚举攻击通常需要满足两点：

1. 确保发送给客户端的响应始终完全相同，无论用户是否存在。通常，这意味着将响应措辞改为模糊的表述，并通过侧信道（例如发送电子邮件通知用户他们已拥有账户）来告知用户任何问题。

2. 确保发送响应所花费的*时间*始终相同，无论用户是否存在。在 Go 中，这通常意味着将工作卸载到后台 goroutine。

不幸的是，这些缓解措施往往会增加应用程序的复杂性，并给工作流程增加摩擦和模糊性。对于所有并非攻击者的普通用户来说，从用户体验的角度看，它们是一种负面因素。你必须问自己：*这种权衡是否值得？*

在回答这个问题时，有几件事需要考虑。在你的应用程序中，用户隐私有多重要？一个被攻破的账户对攻击者有多大吸引力（价值有多高）？减少用户工作流程中的摩擦有多重要？这些问题的答案会因项目而异，并将帮助你做出决策。

值得注意的是，许多知名服务，包括 Twitter、GitHub 和 Amazon，都不会防止用户枚举（至少在它们的注册页面上不会）。我并不是在暗示这就可以接受——
只是说明这些公司已经认定，*在他们的具体情况中*，给用户带来的额外摩擦比隐私和安全风险更糟糕。

## 第 14 章

### 发送电子邮件

在本节中，我们将为 API 注入一些交互性，并调整我们的 `registerUserHandler`，使其在用户成功注册后向用户发送一封欢迎邮件。

在这个过程中，我们将涉及几个有趣的主题。你将学到：

- 如何在开发过程中使用 Mailtrap SMTP 服务发送和监控测试电子邮件。

- 如何使用 `html/template` 包和新的 Go 1.16 *嵌入式文件*功能为你的电子邮件内容创建动态且易于管理的模板。

- 如何创建一个可复用的 `internal/mailer` 包，用于从你的应用程序发送电子邮件。

- 如何实现一种在后台 goroutine 中发送电子邮件的模式，以及在优雅关闭期间如何等待这些 goroutine 完成。

## SMTP 服务器设置

为了开发我们的电子邮件发送功能，我们需要访问一个可以安全用于测试目的的 SMTP（简单邮件传输协议）服务器。

有大量的 SMTP 服务提供商（例如 Postmark、Sendgrid 或 Amazon SES）可供我们用来发送电子邮件——或者你甚至可以安装并运行自己的 SMTP 服务器。但在本书中，我们将使用 Mailtrap。

使用 Mailtrap 的原因是，它是一种专门用于在开发和测试期间发送电子邮件的服务。本质上，它会将所有电子邮件发送到一个你可以访问的收件箱，而不是将它们发送给实际的收件人。

我与该公司没有任何关联——我只是觉得这项服务运行良好且易于使用。他们还提供了一个“永久免费”计划，对于任何跟着本书一起编码的人来说应该足够了。

> **注意：** 如果你已经拥有自己的 SMTP 服务器，或者有想要使用的其他 SMTP 提供商，那完全没问题。请随意跳到下一章。

## 设置 Mailtrap

要设置 Mailtrap 账户，请前往注册页面，你可以使用电子邮件地址或 Google 或 GitHub 账户（如果你有的话）进行注册。

注册并登录后，你应该会看到一个页面，列出你可用的*收件箱*，类似于下面的截图。

![](img/30f9221bfc265d52b544dd595ca099de_471_0.png)

每个 Mailtrap 账户都附带一个免费收件箱，默认名为**演示收件箱**。如果你愿意，可以通过单击**操作**下方的铅笔图标来更改名称。

如果你继续点击进入该收件箱，你应该会看到它当前是空的，不包含任何电子邮件，类似于这样：

![](img/30f9221bfc265d52b544dd595ca099de_472_0.png)

每个收件箱都有自己的一组 SMTP 凭据，你可以通过单击**显示凭据**链接（在上面的截图中用红色框标出）来显示它们。这将展开显示收件箱的 SMTP 凭据，类似于下面的截图。





![](img/30f9221bfc265d52b544dd595ca099de_473_0.png)

基本上，使用这些 SMTP 凭据发送的任何电子邮件都会进入此收件箱，而不会发送到真正的收件人。

如果你正在跟着操作，请记下屏幕上显示的凭据（或者直接保持浏览器标签页打开）——下一章会用到它们。

> **注意：** 上面截图中的凭据已被重置，不再有效，所以请不要尝试使用它们！

## 创建电子邮件模板

首先，我们会让欢迎邮件的内容保持非常简单，用一段简短的消息告诉用户注册成功，并确认他们的用户 ID 号。类似于这样：

```
Hi,

Thanks for signing up for a Greenlight account. We're excited to have you on board!

For future reference, your user ID number is 123.

Thanks,

The Greenlight Team
```

**注意：** 在欢迎邮件中加入用户 ID 可能不是常规做法，但这是一个简单的方式，用来演示如何在邮件中包含*动态数据*——而不是只有静态内容。

定义和管理这封邮件内容有多种不同的方法，但一种方便且灵活的方式是使用 `html/template` 包提供的 Go 模板功能。

如果你正在跟着操作，先在项目目录中创建一个新的 `internal/mailer/templates` 文件夹，然后添加一个 `user_welcome.tmpl` 文件。就像这样：

```bash
$ mkdir -p internal/mailer/templates
$ touch internal/mailer/templates/user_welcome.tmpl
```

在这个文件中，我们将定义三个*命名模板*，作为欢迎邮件的一部分：

- 一个 `"subject"` 模板，包含邮件的主题行。
- 一个 `"plainBody"` 模板，包含邮件正文的纯文本版本。
- 一个 `"htmlBody"` 模板，包含邮件正文的 HTML 版本。

请继续更新 `internal/mailer/templates/user_welcome.tmpl` 文件，加入这些模板的内容：

```
File: internal/mailer/templates/user_welcome.tmpl

{{define "subject"}}Welcome to Greenlight!{{end}}

{{define "plainBody"}}
Hi,

Thanks for signing up for a Greenlight account. We're excited to have you on board!

For future reference, your user ID number is {{.ID}}.

Thanks,

The Greenlight Team
{{end}}

{{define "htmlBody"}}
<!doctype html>
<html>

<head>
    <meta name="viewport" content="width=device-width" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>

<body>
    <p>Hi,</p>
    <p>Thanks for signing up for a Greenlight account. We're excited to have you on board!</p>
    <p>For future reference, your user ID number is {{.ID}}.</p>
    <p>Thanks,</p>
    <p>The Greenlight Team</p>
</body>

</html>
{{end}}
```

如果你读过 *Let's Go*，这些模板语法和结构对你来说应该非常熟悉，这里我们不再赘述细节。但基本上：

- 我们使用 `{{define "..."}}...{{end}}` 标签定义了三个*命名模板*。
- 你可以通过 `.` 字符（称为*点*）在这些模板中渲染动态数据。在下一章中，我们会将 `User` 结构体作为动态数据传递给模板，这样我们就可以在模板中使用 `{{.ID}}` 标签渲染用户 ID。

> **注意：** 如果你需要频繁修改邮件文本，或者希望让用户能自行编辑这些邮件，那么把这些模板以字符串形式存储在数据库中可能更合适。但我觉得像我们这样把它们存在文件里，是一种更简单的方式，也是大多数项目不错的起点。

## 发送欢迎邮件

现在我们已经写好了欢迎邮件的内容，让我们来创建发送邮件的代码。

发送邮件时，我们*可以*使用标准库中的 Go `net/smtp` 包。但遗憾的是，它已经被冻结了好几年，不支持在更高级的使用场景中可能需要的一些功能，比如添加附件。

因此，我建议使用第三方包 `go-mail/mail` 来发送邮件。它经过了充分测试，文档完善，API 清晰易用。

如果你在跟着编码，请使用 `go get` 下载这个包的 `v2.3.0` 版本：

```
$ go get github.com/go-mail/mail/v2@v2.3.0
go: downloading github.com/go-mail/mail/v2 v2.3.0
go: downloading gopkg.in/alexcesaro/quotedprintable.v3 v3.0.0-20150716171945-2caba252f4dc
go get: added github.com/go-mail/mail/v2 v2.3.0
go get: added gopkg.in/alexcesaro/quotedprintable.v3 v3.0.0-20150716171945-2caba252f4dc
```

## 创建邮件辅助工具

在本章中，我们不会把发送欢迎邮件的所有代码都写进 `registerUserHandler`，而是创建一个新的 `internal/mailer` 包，把解析邮件模板和发送邮件的逻辑封装起来。

除此之外，我们还会使用 Go 1.16 的新增嵌入文件功能，这样以后构建二进制文件时，邮件模板文件将会*内置于二进制文件中*。这非常方便，因为这意味着我们不必再把这些模板文件单独部署到生产服务器上。

要演示这是如何工作的，最直接的方式可能就是直接看代码，然后边看边讲解细节。

我们先创建一个新的 `internal/mailer/mailer.go` 文件：

```bash
$ touch internal/mailer/mailer.go
```

然后继续添加以下代码：

```
File: internal/mailer/mailer.go

package mailer

import (
    "bytes"
    "embed"
    "html/template"
    "time"

    "github.com/go-mail/mail/v2"
)

// Below we declare a new variable with the type embed.FS (embedded file
system) to hold
// our email templates. This has a comment directive in the format
`//go:embed <path>`
// IMMEDIATELY ABOVE it, which indicates to Go that we want to store the
contents of the
// ./templates directory in the templateFS embedded file system variable.
// // ↓↓↓

//go:embed "templates"
var templateFS embed.FS

// Define a Mailer struct which contains a mail.Dialer instance (used to
connect to a
// SMTP server) and the sender information for your emails (the name and
address you
// want the email to be from, such as "Alice Smith <alice@example.com>").
type Mailer struct {
    dialer *mail.Dialer
    sender string
}

func New(host string, port int, username, password, sender string) Mailer {
    // Initialize a new mail.Dialer instance with the given SMTP server
settings. We
    // also configure this to use a 5-second timeout whenever we send an
email.
    dialer := mail.NewDialer(host, port, username, password)
    dialer.Timeout = 5 * time.Second

    // Return a Mailer instance containing the dialer and sender information.
    return Mailer{
        dialer: dialer,
        sender: sender,
    }
}

// Define a Send() method on the Mailer type. This takes the recipient email address
// as the first parameter, the name of the file containing the templates, and any
// dynamic data for the templates as an interface{} parameter.
func (m Mailer) Send(recipient, templateFile string, data interface{}) error
{
    // Use the ParseFS() method to parse the required template file from the embedded
    // file system.
    tmpl, err := template.New("email").ParseFS(templateFS,
    "templates/"+templateFile)
    if err != nil {
        return err
    }

    // Execute the named template "subject", passing in the dynamic data and storing the
    // result in a bytes.Buffer variable.
    subject := new(bytes.Buffer)
    err = tmpl.ExecuteTemplate(subject, "subject", data)
    if err != nil {
        return err
    }

    // Follow the same pattern to execute the "plainBody" template and store the result
    // in the plainBody variable.
    plainBody := new(bytes.Buffer)
    err = tmpl.ExecuteTemplate(plainBody, "plainBody", data)
    if err != nil {
        return err
    }
}
```



// And likewise with the "htmlBody" template.
htmlBody := new(bytes.Buffer)
err = tmpl.ExecuteTemplate(htmlBody, "htmlBody", data)
if err != nil {
    return err
}

// Use the mail.NewMessage() function to initialize a new mail.Message instance.
// Then we use the SetHeader() method to set the email recipient, sender and subject
// headers, the SetBody() method to set the plain-text body, and the AddAlternative()
// method to set the HTML body. It's important to note that AddAlternative() should
// always be called *after* SetBody().
msg := mail.NewMessage()
msg.SetHeader("To", recipient)
msg.SetHeader("From", m.sender)
msg.SetHeader("Subject", subject.String())
msg.SetBody("text/plain", plainBody.String())
msg.AddAlternative("text/html", htmlBody.String())

// Call the DialAndSend() method on the dialer, passing in the message to send. This
// opens a connection to the SMTP server, sends the message, then closes the
// connection. If there is a timeout, it will return a "dial tcp: i/o timeout"
// error.
err = m.dialer.DialAndSend(msg)
if err != nil {
    return err
}

return nil
}

## 使用嵌入式文件系统

在我们继续之前，让我们花一点时间更详细地讨论嵌入式文件系统，因为初次接触时有一些地方可能会让人困惑。

-   你只能在包级别的全局变量上使用 `//go:embed` 指令，而不能在函数或方法内部使用。如果你尝试在函数或方法中使用它，编译时会得到错误 `"go:embed cannot apply to var inside func"`。
-   当你使用指令 `//go:embed "<path>"` 创建嵌入式文件系统时，路径应*相对于包含该指令的源代码文件*。因此在我们的例子中，`//go:embed "templates"` 嵌入的是 `internal/mailer/templates` 目录下的内容。
-   嵌入式文件系统的根目录是包含 `//go:embed` 指令的目录。因此，在我们的例子中，要获取 `user_welcome.tmpl` 文件，我们需要在嵌入式文件系统中从 `templates/user_welcome.tmpl` 检索它。
-   路径不能包含 `.` 或 `..` 元素，也不能以 `/` 开头或结尾。这实际上限制了你只能嵌入与包含 `//go:embed` 指令的源代码位于同一目录（或其子目录）中的文件。
-   如果路径指向的是一个目录，则该目录中的所有文件都会被递归嵌入，但名称以 `.` 或 `_` 开头的文件除外。如果你想包含这些文件，应在路径中使用 `*` 通配符，例如 `//go:embed "templates/*"`。
-   你可以在一条指令中指定多个目录和文件。例如：`//go:embed "images" "styles/css" "favicon.ico"`。
-   路径分隔符应始终使用正斜杠，即使在 Windows 机器上也是如此。

## 使用我们的邮件助手

现在我们的邮件助手包已经就绪，我们需要将它连接到 `cmd/api/main.go` 文件中的其余代码。具体来说，我们需要做两件事：

-   调整我们的代码，使其接受 SMTP 服务器的配置设置作为命令行标志。
-   初始化一个新的 `Mailer` 实例，并通过 `application` 结构体将其提供给我们的处理器。

如果你在跟着操作，请确保使用上一章中你自己的 Mailtrap SMTP 服务器设置作为此处命令行标志的默认值——而不是我在下面代码中使用的确切值。

文件：cmd/api/main.go

```go
package main
```

```go
import (
    "context"
    "database/sql"
    "flag"
    "os"
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/jsonlog"
    "greenlight.alexedwards.net/internal/mailer" // New import

    _ "github.com/lib/pq"
)

const version = "1.0.0"

// Update the config struct to hold the SMTP server settings.
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
}
```

```go
// Update the application struct to hold a new Mailer instance.
type application struct {
    config config
    logger *jsonlog.Logger
    models data.Models
    mailer mailer.Mailer
}
```

```go
func main() {
    var cfg config

    flag.IntVar(&cfg.port, "port", 4000, "API server port")
    flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

    flag.StringVar(&cfg.db.dsn, "db-dsn", os.Getenv("GREENLIGHT_DB_DSN"), "PostgreSQL DSN")

    flag.IntVar(&cfg.db.maxOpenConns, "db-max-open-conns", 25, "PostgreSQL max open connections")
    flag.IntVar(&cfg.db.maxIdleConns, "db-max-idle-conns", 25, "PostgreSQL max idle connections")
    flag.StringVar(&cfg.db.maxIdleTime, "db-max-idle-time", "15m", "PostgreSQL max connection idle time")

    flag.BoolVar(&cfg.limiter.enabled, "limiter-enabled", true, "Enable rate limiter")
    flag.Float64Var(&cfg.limiter.rps, "limiter-rps", 2, "Rate limiter maximum requests per second")
    flag.IntVar(&cfg.limiter.burst, "limiter-burst", 4, "Rate limiter maximum burst")

    // Read the SMTP server configuration settings into the config struct, using the
    // Mailtrap settings as the default values. IMPORTANT: If you're following along,
    // make sure to replace the default values for smtp-username and smtp-password

// with your own Mailtrap credentials.
flag.StringVar(&cfg.smtp.host, "smtp-host", "smtp.mailtrap.io", "SMTP host")
flag.IntVar(&cfg.smtp.port, "smtp-port", 25, "SMTP port")
flag.StringVar(&cfg.smtp.username, "smtp-username", "0abf276416b183", "SMTP username")
flag.StringVar(&cfg.smtp.password, "smtp-password", "d8672aa2264bb5", "SMTP password")
flag.StringVar(&cfg.smtp.sender, "smtp-sender", "Greenlight <no-reply@greenlight.alexedwards.net>", "SMTP sender")

flag.Parse()

logger := jsonlog.New(os.Stdout, jsonlog.LevelInfo)

db, err := openDB(cfg)
if err != nil {
    logger.PrintFatal(err, nil)
}
defer db.Close()

logger.PrintInfo("database connection pool established", nil)

// Initialize a new Mailer instance using the settings from the command line
// flags, and add it to the application struct.
app := &application{
    config: cfg,
    logger: logger,
    models: data.NewModels(db),
    mailer: mailer.New(cfg.smtp.host, cfg.smtp.port, cfg.smtp.username, cfg.smtp.password, cfg.smtp.sender),
}

err = app.serve()
if err != nil {
    logger.PrintFatal(err, nil)
}
}
```

...
然后，我们需要做的最后一件事是更新 `registerUserHandler`，让它真正发送邮件，我们可以这样做：

```go
File: cmd/api/users.go

package main

...

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
    ... // Nothing above here needs to change.

    // Call the Send() method on our Mailer, passing in the user's email address,
    // name of the template file, and the User struct containing the new user's data.
    err = app.mailer.Send(user.Email, "user_welcome.tmpl", user)
    if err != nil {
        app.serverErrorResponse(w, r, err)
        return
    }

    err = app.writeJSON(w, http.StatusCreated, envelope{"user": user}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

好了，让我们来试一试！

运行应用程序，然后在另一个终端中使用 `curl` 注册一个新用户，邮箱地址为 `bob@example.com`：

```
$ BODY='{"name": "Bob Jones", "email": "bob@example.com", "password": "pa55word"}'
$ curl -w '\nTime: %{time_total}\n' -d "$BODY" localhost:4000/v1/users
{
  "user": {
    "id": 3,
    "created_at": "2021-04-11T20:26:22+02:00",
    "name": "Bob Jones",
    "email": "bob@example.com",
    "activated": false
  }
}

Time: 2.331957
```

**注意：** 我再次使用了 `-w` 标志来显示请求完成所用的总时间，在我的例子中约为 2.3 秒。对于一个 HTTP 请求来说，这已经算是相当长的时间了；在下一章中，我们将通过在后台 goroutine 中发送欢迎邮件来加快这一过程。





## 在 Mailtrap 中查看邮件

如果你一直跟着操作并使用 Mailtrap SMTP 服务器凭据，那么返回你的账户时，应该会看到 Demo 收件箱中现在有一封发送给 bob@example.com 的欢迎邮件，如下所示：

![](img/30f9221bfc265d52b544dd595ca099de_490_0.png)

如果你愿意，还可以点击 Text 标签查看邮件的纯文本版本，点击 Raw 标签查看包含邮件头的完整邮件。

总而言之，我们在本章中涵盖了大量内容。但我们构建的模式的好处在于它易于扩展。如果将来我们要从应用程序中发送其他邮件，只需在 `internal/mailer/templates` 文件夹中添加一个包含邮件内容的额外文件，然后像这里一样从 handlers 中发送即可。

## 附加信息

## 重试邮件发送尝试

如果你愿意，可以通过向 `Mailer.Send()` 方法添加一些基本的“重试”功能，使邮件发送过程更加健壮。例如：

```go
func (m Mailer) Send(recipient, templateFile string, data interface{}) error
{
    ...

    // Try sending the email up to three times before aborting and returning
    the final
    // error. We sleep for 500 milliseconds between each attempt.
    for i := 1; i <= 3; i++ {
        err = m.dialer.DialAndSend(msg)
        // If everything worked, return nil.
        if nil == err {
            return nil
        }

        // If it didn't work, sleep for a short time and retry.
        time.Sleep(500 * time.Millisecond)
    }
    return err
}
```

**提示：** 在上面的代码中，我们使用 `if nil == err` 子句来检查发送是否成功，而不是 `if err == nil`。它们在功能上是等价的，但将 `nil` 放在子句的第一项会使它在视觉上更醒目，并且不太可能与更常见的 `if err != nil` 子句混淆。

这个重试功能是对我们代码相对简单的补充，但有助于在遇到瞬时网络问题时提高邮件成功发送的概率。如果你在后台进程中发送邮件（就像我们在下一章中要做的那样），你可能会希望将这里的休眠时间设得更长一些，因为它不会对客户端产生实质性影响，并且为瞬时问题的解决留出更多时间。

第 14.4 章

## 发送后台邮件

正如我们在上一章中简要提到的，从 `registerUserHandler` 方法发送欢迎邮件会为客户端的总请求/响应往返增加大量延迟。

减少这种延迟的一种方法是在 *后台 goroutine* 中发送邮件。这将有效地将发送邮件的任务与 `registerUserHandler` 中的其余代码“解耦”，并且意味着我们可以在不等待邮件发送完成的情况下向客户端返回 HTTP 响应。

最简单的做法是，我们可以调整 handler，使其在后台 goroutine 中执行邮件发送，如下所示：

File: cmd/api/users.go

package main
...

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
...
    // Launch a goroutine which runs an anonymous function that sends the welcome email.
```go
go func() {
    err = app.mailer.Send(user.Email, "user_welcome.tmpl", user)
    if err != nil {
        // Importantly, if there is an error sending the email then we use the
        // app.logger.PrintError() helper to manage it, instead of the
        // app.serverErrorResponse() helper like before.
        app.logger.PrintError(err, nil)
    }
}()

    // Note that we also change this to send the client a 202 Accepted status code.
    // This status code indicates that the request has been accepted for processing, but
    // the processing has not been completed.
    err = app.writeJSON(w, http.StatusAccepted, envelope{"user": user}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

这段代码现在执行时，会启动一个新的“后台” goroutine 用于发送欢迎邮件。这个后台 goroutine 中的代码将与 `registerUserHandler` 中的后续代码 *并发* 执行，这意味着我们不再需要等待邮件发送完成后再向客户端返回 JSON 响应。很可能，后台 goroutine 会在 `registerUserHandler` 返回后仍然执行相当长的时间。

这里我想强调几点：

-   我们使用 `app.logger.PrintError()` 帮助函数来管理后台 goroutine 中的任何错误。这是因为当我们遇到错误时，客户端可能已经通过 `writeJSON()` 帮助函数收到了 `202 Accepted` 响应。
-   请注意，我们不想使用 `app.serverErrorResponse()` 帮助函数来处理后台 goroutine 中的任何错误，因为那将导致我们尝试写入第二个 *HTTP 响应*，并在运行时从 `http.Server` 收到 `"http: superfluous response.WriteHeader call"` 错误。
-   在后台 goroutine 中运行的代码对 `user` 和 `app` 变量形成了一个 *闭包*。需要注意的是，这些“被闭包捕获的”变量 *并不限定于后台 goroutine 的作用域*，这意味着你对它们所做的任何更改都会反映在代码库的其余部分。关于这一点的简单示例，请参见下面的 [示例代码](#)。

在我们的例子中，我们没有以任何方式更改这些变量的值，所以这种行为不会给我们带来任何问题。但记住这一点很重要。

好的，让我们试一试！

重启 API，然后继续注册另一个新用户，邮箱地址为 `carol@example.com`。如下所示：

```
$ BODY='{"name": "Carol Smith", "email": "carol@example.com", "password": "pa55word"}'
$ curl -w '\nTime: %{time_total}\n' -d "$BODY" localhost:4000/v1/users
```

```
{
  "user": {
    "id": 4,
    "created_at": "2021-04-11T21:21:12+02:00",
    "name": "Carol Smith",
    "email": "carol@example.com",
    "activated": false
  }
}

Time: 0.268639
```

这一次，你应该会看到返回响应所需的时间快得多——就我而言，是 0.27 秒，而之前是 2.33 秒。

如果你查看你的 Mailtrap 收件箱，应该会看到发送给 `carol@example.com` 的邮件已正确送达。如下所示：

恢复，使用与我们 `recoverPanic()` 中间件类似的模式。

我来演示一下。

重新打开你的 `cmd/api/users.go` 文件，并按如下方式更新 `registerUserHandler`：

File: cmd/api/users.go

package main

import (
    "errors"
    "fmt" // New import
    "net/http"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator"
)

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
    ...

    // Launch a background goroutine to send the welcome email.
    go func() {
        // Run a deferred function which uses recover() to catch any panic,
        and log an
        // error message instead of terminating the application.
        defer func() {
            if err := recover(); err != nil {
                app.logger.PrintError(fmt.Errorf("%s", err), nil)
            }
        }()
        // Send the welcome email.
        err = app.mailer.Send(user.Email, "user_welcome.tmpl", user)
        if err != nil {
            app.logger.PrintError(err, nil)
        }
    }()

    err = app.writeJSON(w, http.StatusAccepted, envelope{"user": user}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}

## 使用辅助函数

如果你需要在应用程序中执行大量后台任务，反复编写相同的 panic 恢复代码可能会变得很繁琐——而且你可能完全忘记包含它。

为了帮助处理这种情况，可以创建一个简单的辅助函数来封装 panic 恢复逻辑。如果你在跟着操作，请打开你的 `cmd/api/helpers.go` 文件，并创建一个新的 `background()` 辅助方法，如下所示：

File: cmd/api/helpers.go

package main

...



// The background() helper accepts an arbitrary function as a parameter.
func (app *application) background(fn func()) {
    // Launch a background goroutine.
    go func() {
        // Recover any panic.
        defer func() {
            if err := recover(); err != nil {
                app.logger.PrintError(fmt.Errorf("%s", err), nil)
            }
        }()
        // Execute the arbitrary function that we passed as the parameter.
        fn()
    }()
}

这个 `background()` 辅助函数利用了 Go 具备一等函数（first-class functions）的特性，这意味着函数可以被*赋值给变量*，也可以*作为参数传递给其他函数*。

在本例中，我们设计的 `background()` 辅助函数接受任何签名为 `func()` 的函数作为参数，并将其存储在变量 `fn` 中。随后它会启动一个后台 goroutine，使用一个延迟函数来恢复任何 panic 并记录错误，然后通过调用 `fn()` 来执行该函数。

现在基础工作已经就绪，让我们像下面这样更新 `registerUserHandler` 来使用它：

文件：cmd/api/users.go

```go
package main

import (
    "errors"
    "net/http"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator"
)

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
    ...

    // Use the background helper to execute an anonymous function that sends the welcome email.
    app.background(func() {
        err = app.mailer.Send(user.Email, "user_welcome.tmpl", user)
        if err != nil {
            app.logger.PrintError(err, nil)
        }
    })

    err = app.writeJSON(w, http.StatusAccepted, envelope{"user": user}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

让我们确认一下这仍然有效。重启 API，然后用电子邮件地址 dave@example.com 创建另一个新用户：

## 欢迎来到 Greenlight！

收件箱 > 演示收件箱 > 欢迎来到 Greenlight！

发件人：Greenlight <no-reply@greenlight.alexedwards.net>
收件人：<dave@example.com>
显示邮件头

- HTML
- HTML 源文件
- 文本
- 原始内容
- 垃圾邮件分析
- 检查 HTML
- 技术信息

- 欢迎来到 Greenlight！
  收件人：<dave@example.com>
  几秒钟前
- 欢迎来到 Greenlight！
  收件人：<carol@example.com>
  12 分钟前
- 欢迎来到 Greenlight！
  收件人：<bob@example.com>
  1 小时前

你好，

感谢你注册 Greenlight 账户。我们很高兴你的加入！

供你日后参考，你的用户 ID 是 5。

谢谢，
Greenlight 团队

点击此处升级你的限额

计数器加 1。然后你可以监控计数器，当它变为零时，你就知道所有后台 goroutine 都已执行完成。

让我们快速看一个独立的示例，演示 `sync.WaitGroup` 在实际中是如何工作的。

```go
package main

import (
    "fmt"
    "sync"
)

func main() {
    // Declare a new WaitGroup.
    var wg sync.WaitGroup

    // Execute a loop 5 times.
    for i := 1; i <= 5; i++ {
        // Increment the WaitGroup counter by 1, BEFORE we launch the
        // background routine.
        wg.Add(1)

        // Launch the background goroutine.
        go func() {
            // Defer a call to wg.Done() to indicate that the background
            // goroutine has
            // completed when this function returns. Behind the scenes this
            // decrements
            // the WaitGroup counter by 1 and is the same as writing
            wg.Add(-1).
```
```
defer wg.Done()

    fmt.Println("hello from a goroutine")
    }()
}

    // Wait() blocks until the WaitGroup counter is zero --- essentially
blocking until all
    // goroutines have completed.
    wg.Wait()

    fmt.Println("all goroutines finished")
}
```

如果你运行上面的代码，你会看到输出如下：

```
hello from a goroutine
hello from a goroutine
hello from a goroutine
hello from a goroutine
hello from a goroutine
all goroutines finished
```

这里需要强调的一点是，我们在启动后台 goroutine 之前立即使用 `wg.Add(1)` 递增计数器。如果我们在后台 goroutine 内部调用 `wg.Add(1)`，就会存在竞态条件，因为 `wg.Wait()` 可能在计数器递增之前就被调用。

## 修复我们的应用程序

让我们更新应用程序，引入一个 `sync.WaitGroup` 来协调我们的优雅关闭和后台 goroutine。

我们将从 `cmd/api/main.go` 文件开始，编辑 `application` 结构体，使其包含一个新的 `sync.WaitGroup`。操作如下：

文件：cmd/api/main.go

```go
package main

import (
    "context"
    "database/sql"
    "flag"
    "os"
    "sync" // New import
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/jsonlog"
    "greenlight.alexedwards.net/internal/mailer"

    _ "github.com/lib/pq"
)

...

// Include a sync.WaitGroup in the application struct. The zero-value for a
// sync.WaitGroup type is a valid, useable, sync.WaitGroup with a 'counter'
// value of 0,
// so we don't need to do anything else to initialize it before we can use
// it.
type application struct {
```
```
config config
logger *jsonlog.Logger
models data.Models
mailer mailer.Mailer
wg     sync.WaitGroup
}
...
```

接下来，我们前往 `cmd/api/helpers.go` 文件，更新 `app.background()` 辅助函数，使得每次启动后台 goroutine 之前递增 `sync.WaitGroup` 计数器，并在其完成时递减。

操作如下：

文件：cmd/api/helpers.go

```go
package main

...

func (app *application) background(fn func()) {
    // Increment the WaitGroup counter.
    app.wg.Add(1)

    // Launch the background goroutine.
    go func() {
        // Use defer to decrement the WaitGroup counter before the goroutine returns.
        defer app.wg.Done()

        defer func() {
```
```
"env":  app.config.env,
})

err := srv.ListenAndServe()
if !errors.Is(err, http.ErrServerClosed) {
    return err
}

err = <-shutdownError
if err != nil {
    return err
}

app.logger.PrintInfo("stopped server", map[string]string{
    "addr": srv.Addr,
})

return nil
}
```

要尝试一下，请重启 API，然后立即向 `POST /v1/users` 端点发送请求，紧接着发送一个 `SIGTERM` 信号。例如：

```
$ BODY='{"name": "Edith Smith", "email": "edith@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/users & pkill -SIGTERM api &
```

当你这样做时，你的服务器日志应该类似于下面的输出：

```text
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-15T15:06:50Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-15T15:06:50Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
{"level":"INFO","time":"2021-04-15T15:07:06Z","message":"caught signal","properties":{"signal":"terminated"}}
{"level":"INFO","time":"2021-04-15T15:07:06Z","message":"completing background tasks","properties":{"addr":":4000"}}
{"level":"INFO","time":"2021-04-15T15:07:08Z","message":"stopped server","properties":{"addr":":4000"}}
```

请注意，日志中先写入了**“completing background tasks”**消息，然后暂停了几秒钟让后台邮件发送完成，最后才出现**“stopped server”**消息，你看到了吗？

这很好地说明了优雅关闭过程如何一直等待欢迎邮件发送完成（在我的例子中大约需要两秒钟），然后才最终终止应用程序。

## 第 15 章

### 用户激活

目前，用户可以通过我们的 *Greenlight* API 注册账户，但我们并不确定他们在注册时提供的电子邮件地址*实际上是否属于他们*。

因此，在本节中，我们将构建相应功能，通过在欢迎邮件中包含“账户激活”说明，来确认用户使用的是他们自己的真实电子邮件地址。

设置激活步骤有几个原因，但主要好处是它为机器人增加了额外的验证门槛，并有助于防止人们使用虚假电子邮件地址或不属于自己的电子邮件地址进行恶意注册。

为了让你提前了解整体流程，账户激活过程如下：

- 1. 在新用户注册过程中，我们会创建一种加密安全的随机*激活令牌*，该令牌无法被猜测。
- 2. 随后，我们会将这个激活令牌的哈希值存储在一个新的 tokens 表中，同时存储新用户的 ID 和令牌的过期时间。
- 3. 我们会将原始（未哈希的）激活令牌通过欢迎邮件发送给用户。




4. 用户随后将其令牌提交到新的 `PUT /v1/users/activated` 端点。
5. 如果令牌的哈希存在于 `tokens` 表中且未过期，则我们将相关用户的 `activated` 状态更新为 `true`。
6. 最后，我们将从 `tokens` 表中删除激活令牌，以防止其再次被使用。

在本书的这一节中，你将学习如何：

- 实现一个安全的“账户激活”工作流，用于验证新用户的电子邮件地址。
- 使用 Go 的 `crypto/rand` 和 `encoding/base32` 包生成密码学安全的随机令牌。
- 使用 `crypto/sha256` 包快速生成数据的哈希值。
- 实现数据库中跨表关系的工作模式，包括设置外键以及通过 SQL `JOIN` 查询检索相关数据。

```
File: migrations/000005_create_tokens_table.down.sql

DROP TABLE IF EXISTS tokens;
```

让我们快速浏览一下这个新的 tokens 表中的列并解释其用途。

- `hash` 列将包含激活令牌的 SHA-256 哈希值。需要强调的是，我们只会在数据库中存储激活令牌的哈希值——而不是激活令牌本身。

我们希望在存储令牌之前对其进行哈希处理，原因与我们对用户密码进行 bcrypt 处理相同——如果数据库被入侵或泄露，它提供了额外的保护层。因为我们的激活令牌将是一个高熵随机字符串（128 位）——而不是像典型用户密码那样低熵的东西——因此使用 SHA-256 这样快速的算法来创建哈希就足够了，而不是使用 bcrypt 这样慢的算法。
- `user_id` 列将包含与令牌关联的用户的 ID。我们使用 `REFERENCES user` 语法在 `users` 表的主键上创建外键约束，这确保 `user_id` 列中的任何值在 `users` 表中都有对应的 `id` 条目。

- 最后，`scope` 列将表示令牌可用于的 *目的*。稍后在书中我们还需要创建和存储 *身份验证令牌*，这些令牌的代码和存储需求与我们的激活令牌几乎完全相同。因此，而不是创建单独的表（以及与其交互的代码），我们将把它们存储在一个表中，并通过 `scope` 列中的值来限制令牌的使用目的。

好的，在这些解释之后，你应该能够使用以下命令执行“up”迁移：

```
$ migrate -path=./migrations -database=$GREENLIGHT_DB_DSN up
5/u create_tokens_table (21.568194ms)
```

## 创建安全的激活令牌

我们的激活过程的完整性取决于一个关键因素：我们发送到用户电子邮件地址的令牌的“不可猜测性”。如果令牌容易猜测或可以被暴力破解，那么攻击者即使无法访问用户的电子邮件收件箱，也可能激活用户的账户。

因此，我们希望令牌由 *密码学安全随机数生成器*（CSPRNG）生成，并且具有足够的熵（或 *随机性*），使其无法被猜测。在我们的例子中，我们将使用 Go 的 `crypto/rand` 包和 128 位（16 字节）的熵来创建激活令牌。

如果你跟随操作，请继续创建一个新的 `internal/data/tokens.go` 文件。这将作为未来几章中所有与创建和管理令牌相关的逻辑的存放位置。

```
$ touch internal/data/tokens.go
```

然后在这个文件中，让我们定义一个 `Token` 结构体（用于表示单个令牌的数据），以及一个 `generateToken()` 函数，我们可以用它来创建新令牌。

这是另一个最好直接进入代码并在过程中描述正在发生的事情的时候。

```
File: internal/data/tokens.go

```go
package data

import (
    "crypto/rand"
    "crypto/sha256"
    "encoding/base32"
    "time"
)

// Define constants for the token scope. For now we just define the scope "activation"
// but we'll add additional scopes later in the book.
const (
    ScopeActivation = "activation"
)

// Define a Token struct to hold the data for an individual token. This includes the
// plaintext and hashed versions of the token, associated user ID, expiry time and
// scope.
type Token struct {
    Plaintext string
    Hash      []byte
    UserID    int64
    Expiry    time.Time
    Scope     string
}
```
```

```
func generateToken(userID int64, ttl time.Duration, scope string) (*Token, error) {
    // Create a Token instance containing the user ID, expiry, and scope
    // information.
    // Notice that we add the provided ttl (time-to-live) duration parameter
    // to the
    // current time to get the expiry time?
    token := &Token{
        UserID: userID,
        Expiry: time.Now().Add(ttl),
        Scope:  scope,
    }

    // Initialize a zero-valued byte slice with a length of 16 bytes.
    randomBytes := make([]byte, 16)

    // Use the Read() function from the crypto/rand package to fill the byte
    // slice with
    // random bytes from your operating system's CSPRNG. This will return an
    // error if
    // the CSPRNG fails to function correctly.
    _, err := rand.Read(randomBytes)
    if err != nil {
        return nil, err
    }

    // Encode the byte slice to a base-32-encoded string and assign it to the
    // token
    // Plaintext field. This will be the token string that we send to the
    // user in their
    // welcome email. They will look similar to this:
    // Y3QMGX3PJ3WLRL2YRTQGQ6KRHU
    //
    // Note that by default base-32 strings may be padded at the end with the
    // =
    // character. We don't need this padding character for the purpose of our
    // tokens, so
    // we use the WithPadding(base32.NoPadding) method in the line below to
```

好的，让我们继续设置一个 `TokenModel` 类型，它封装了与 PostgreSQL `tokens` 表的数据库交互。我们将再次遵循与 `MovieModel` 和 `UsersModel` 非常相似的模式，并在其上实现以下三个方法：

- `Insert()` 用于在数据库中插入新的令牌记录。
- `New()` 将是一个快捷方法，它使用 `generateToken()` 函数创建一个新令牌，然后调用 `Insert()` 来存储数据。
- `DeleteAllForUser()` 用于删除特定用户具有特定范围的所有令牌。

我们还将创建一个新的 `ValidateTokenPlaintext()` 函数，它将检查未来客户端提供的明文令牌是否正好为 26 字节长。

再次打开 `internal/data/tokens.go` 文件，并添加以下代码：

```
File: internal/data/tokens.go

package data

import (
    "context" // New import
    "crypto/rand"
    "crypto/sha256"
    "database/sql" // New import
    "encoding/base32"
    "time"
)
```

```
```go
"greenlight.alexedwards.net/internal/validator" // New import
)
...

// Check that the plaintext token has been provided and is exactly 26 bytes long.
func ValidateTokenPlaintext(v *validator.Validator, tokenPlaintext string) {
    v.Check(tokenPlaintext != "", "token", "must be provided")
    v.Check(len(tokenPlaintext) == 26, "token", "must be 26 bytes long")
}

// Define the TokenModel type.
type TokenModel struct {
    DB *sql.DB
}

// The New() method is a shortcut which creates a new Token struct and then inserts the
// data in the tokens table.
func (m TokenModel) New(userID int64, ttl time.Duration, scope string) (*Token, error) {
    token, err := generateToken(userID, ttl, scope)
    if err != nil {
        return nil, err
    }

    err = m.Insert(token)
    return token, err
}

// Insert() adds the data for a specific token to the tokens table.
func (m TokenModel) Insert(token *Token) error {
    query := `
        INSERT INTO tokens (hash, user_id, expiry, scope)
        VALUES ($1, $2, $3, $4)`

    args := []interface{}{token.Hash, token.UserID, token.Expiry,
    token.Scope}
```



```
ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
defer cancel()

_, err := m.DB.ExecContext(ctx, query, args...)
return err
}

// DeleteAllForUser() deletes all tokens for a specific user and scope.
func (m TokenModel) DeleteAllForUser(scope string, userID int64) error {
    query := `
        DELETE FROM tokens
        WHERE scope = $1 AND user_id = $2`

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    _, err := m.DB.ExecContext(ctx, query, scope, userID)
    return err
}
```

最后，我们需要更新 `internal/data/models.go` 文件，以便将新的 `TokenModel` 包含在父级 `Models` 结构体中。示例如下：

```
File: internal/data/models.go

package data

...

type Models struct {
    Movies MovieModel
    Tokens TokenModel // Add a new Tokens field.
```

当需要密码学安全性时，例如在此处生成令牌或密钥时。

实际上，使用 `crypto/rand` 作为 *标准做法* 无疑是最好的选择。只有在你确定确定性 PRNG 可接受，并且确实需要 `math/rand` 更快的性能的特定场景下，才考虑使用 `math/rand`。

> **Note:** 如果你的 API 是网站的后端，那么你可以调整此邮件，让它要求用户点击一个链接，该链接会将他们带到你网站上的页面。他们可以 *然后* 在页面上点击一个按钮来‘确认激活’，这会向你的 API 执行 `PUT` 请求，从而真正激活用户。我们将在下一章更详细地介绍这种模式。

但现在，如果你正在跟随操作，请继续更新你的欢迎邮件模板以包含激活令牌，如下所示：

```
File: internal/mailer/templates/user_welcome.tmpl

{{define "subject"}}Welcome to Greenlight!{{end}}

{{define "plainBody"}}
Hi,

Thanks for signing up for a Greenlight account. We're excited to have you on board!

For future reference, your user ID number is {{.userID}}.

Please send a request to the `PUT /v1/users/activated` endpoint with the following JSON
body to activate your account:

{"token": "{{.activationToken}}"}

Please note that this is a one-time use token and it will expire in 3 days.

Thanks,
The Greenlight Team
{{end}}

{{define "htmlBody"}}
<!doctype html>
<html>

<head>
    <meta name="viewport" content="width=device-width" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>

<body>
    <p>Hi,</p>
    <p>Thanks for signing up for a Greenlight account. We're excited to have you on board!</p>
    <p>For future reference, your user ID number is {{.userID}}.</p>
    <p>Please send a request to the <code>PUT /v1/users/activated</code> endpoint with the
    following JSON body to activate your account:</p>
    <pre><code>
{"token": "{{.activationToken}}"}
    </code></pre>
    <p>Please note that this is a one-time use token and it will expire in 3 days.</p>
    <p>Thanks,</p>
    <p>The Greenlight Team</p>
</body>

</html>
{{end}}
```

接下来我们需要更新 `registerUserHandler` 以生成新的激活令牌，并将其作为动态数据连同用户 ID 一起传递给欢迎邮件模板。

示例如下：

```go
File: cmd/api/users.go

package main

import (
    "errors"
    "net/http"
    "time" // New import

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator"
)

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
    ...
    err = app.models.Users.Insert(user)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrDuplicateEmail):
            v.AddError("email", "a user with this email address already exists")
            app.failedValidationResponse(w, r, v.Errors)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }

    // After the user record has been created in the database, generate a new activation
    // token for the user.
    token, err := app.models.Tokens.New(user.ID, 3*24*time.Hour, data.ScopeActivation)
    if err != nil {
        app.serverErrorResponse(w, r, err)
        return
    }

    app.background(func() {
        // As there are now multiple pieces of data that we want to pass to our email
        // templates, we create a map to act as a 'holding structure' for the data. This
        // contains the plaintext version of the activation token for the user, along
        // with their ID.
        data := map[string]interface{}{
            "activationToken": token.Plaintext,
            "userID":          user.ID,
        }

        // Send the welcome email, passing in the map above as dynamic data.
        err = app.mailer.Send(user.Email, "user_welcome.tmpl", data)
        if err != nil {
            app.logger.PrintError(err, nil)
        }
    })

    err = app.writeJSON(w, http.StatusAccepted, envelope{"user": user}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

好的，让我们看看它是如何工作的…

重启应用程序，然后使用电子邮件地址 faith@example.com 注册一个新用户账户。类似于这样：

```
$ BODY='{"name": "Faith Smith", "email": "faith@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/users
{
  "user": {
    "id": 7,
    "created_at": "2021-04-15T20:25:41+02:00",
    "name": "Faith Smith",
    "email": "faith@example.com",
    "activated": false
  }
}
```

如果你再次打开 Mailtrap 收件箱，你现在应该会看到包含激活令牌的新欢迎邮件，如下所示：

greenlight=> SELECT * FROM tokens;

| 哈希 | 用户ID | 过期时间 | 范围 |
|------|---------|--------|-------|
| \x09bcb40206b25fe511bfe f4d56cbe8c4a141869fc29612fa984b371ef086f5f5 | 7 | 2021-04-18 20:25:41+02 | activation |

我们可以在这里看到激活令牌哈希显示为值：

```
09bcb40206b25fe511bfe f4d56cbe8c4a141869fc29612fa984b371ef086f5f5
```

正如我们之前提到的，`psql` 总是以十六进制编码的字符串形式显示 `bytea` 列中的值。所以我们在这里看到的是明文令牌 `P4B3URJZJ2NW5UPZC2OHN4H2NM` 的 SHA-256 哈希的 *十六进制编码*，该令牌已发送在欢迎邮件中。

> **Note:** 如果你愿意，可以通过将欢迎邮件中的明文激活令牌输入到此在线 SHA-256 哈希生成器中来验证这一点。你应该会看到结果与 PostgreSQL 数据库中的十六进制编码值相匹配。

同样请注意，`user_id` 的值为 7 对我们的 `faith@example.com` 用户是正确的，到期时间已正确设置为

## 激活用户

在本章中，我们将进入激活工作流程的实际激活用户的部分。但在编写任何代码之前，我想快速谈谈我们系统中用户和令牌之间的关系。

我们所拥有的在关系数据库术语中被称为 *一对多关系* —— 一个用户可能拥有多个令牌，但一个令牌只能属于一个用户。

当你有这种一对多关系时，你可能希望从两个不同的方向对关系执行查询。例如，在我们的情况下，我们可能希望：

- 检索与令牌关联的用户。
- 检索与用户关联的所有令牌。

为了在代码中实现这些查询，一个干净清晰的方法是更新你的数据库模型以包含如下一些额外方法：

```
UserModel.GetForToken(token)  → Retrieve the user associated with a token
TokenModel.GetAllForUser(user) → Retrieve all tokens associated with a user
```



这个方法的好处在于返回的实体与模型的主要职责保持一致：`UserModel` 方法返回的是用户，而 `TokenModel` 方法返回的是令牌。

## 创建 activateUserHandler

现在我们已经对如何在数据库模型中查询用户 ↔ 令牌关系有了一个非常高层次的想法，让我们开始构建激活用户的代码。

为此，我们需要在 API 中添加一个新的 `PUT /v1/users/activated` 端点：

| 方法 | URL 模式 | 处理程序 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用程序信息 |
| GET | /v1/movies | listMoviesHandler | 显示所有电影的详细信息 |
| POST | /v1/movies | createMovieHandler | 创建一部新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |
| PATCH | /v1/movies/:id | updateMovieHandler | 更新特定电影的详细信息 |
| DELETE | /v1/movies/:id | deleteMovieHandler | 删除特定电影 |
| POST | /v1/users | registerUserHandler | 注册新用户 |
| PUT | /v1/users/activated | activateUserHandler | 激活特定用户 |

工作流程如下：

- 1. 用户提交明文激活令牌（他们刚刚通过电子邮件收到的）到 `PUT /v1/users/activated` 端点。
- 2. 我们验证明文令牌以检查其是否符合预期格式，如有必要则向客户端发送错误消息。
- 3. 然后我们调用 `UserModel.GetForToken()` 方法来检索与提供的令牌关联的用户的详细信息。如果找不到匹配的令牌或已过期，我们向客户端发送错误消息。
- 4. 我们通过将用户记录上的 `activated = true` 来激活关联的用户并在数据库中更新它。
- 5. 我们从 `tokens` 表中删除用户的所有激活令牌。我们可以使用之前创建的 `TokenModel.DeleteAllForUser()` 方法来完成此操作。
- 6. 我们在 JSON 响应中发送更新后的用户详细信息。

让我们在 `cmd/api/users.go` 文件中开始并创建新的 `activateUserHandler` 来逐步完成这些步骤：

```
File: cmd/api/users.go
```

```
args := []interface{}{tokenHash[:], tokenScope, time.Now()}

var user User

ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
defer cancel()

// Execute the query, scanning the return values into a User struct. If
// no matching
// record is found we return an ErrRecordNotFound error.
err := m.DB.QueryRowContext(ctx, query, args...).Scan(
    &user.ID,
    &user.CreatedAt,
    &user.Name,
    &user.Email,
    &user.Password.hash,
    &user.Activated,
    &user.Version,
)
if err != nil {
    switch {
    case errors.Is(err, sql.ErrNoRows):
        return nil, ErrRecordNotFound
    default:
        return nil, err
    }
}

// Return the matching user.
return &user, nil
}
```

现在设置完成，接下来需要做的最后一件事是将 PUT /v1/users/activated 端点添加到 cmd/api/routes.go 文件中。如下所示：

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

    router.HandlerFunc(http.MethodGet, "/v1/movies", app.listMoviesHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.updateMovieHandler)
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.deleteMovieHandler)

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    // Add the route for the PUT /v1/users/activated endpoint.
    router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

    return app.recoverPanic(app.rateLimit(router))
}
```

顺便说一下，我应该快速解释一下我们为什么对该端点使用 PUT 而不是 POST，因为它具有幂等性。

如果客户端多次发送相同的 PUT /v1/users/activated 请求，第一次请求会成功（假设令牌有效），然后任何后续请求都会导致向客户端发送错误（因为令牌已被使用并从数据库中删除）。但重要的是，*在第一次请求之后，我们应用程序的状态（即数据库）不会发生变化。*

基本上，客户端多次发送相同请求不会产生应用程序状态的副作用，这意味着该端点是幂等的，使用 PUT 比 POST 更合适。

好吧，让我们重新启动 API 然后试试。

首先，尝试向 PUT /v1/users/activated 端点发送包含一些无效令牌的请求。你应该会得到相应的错误消息响应，如下所示：

```
$ curl -X PUT -d '{"token": "invalid"}' localhost:4000/v1/users/activated
{
  "error": {
    "token": "must be 26 bytes long"
  }
}

$ curl -X PUT -d '{"token": "ABCDEFGHIJKLMNOPQRSTUVWXYZ"}'
localhost:4000/v1/users/activated
{
  "error": {
    "token": "invalid or expired activation token"
  }
}
```

```
enter the following code:

--------------------
Y3QMGX3PJ3WLRL2YRTQGQ6KRHU
--------------------

Please note that this code will expire in 3 days and can only be used once.

Thanks,

The Greenlight Team
```

这种方法从根本上来说是简单且安全的——本质上你的网站只需提供一个表单来代表用户执行 PUT 请求，而不是让他们使用 curl 或其他工具手动执行。

注意：创建电子邮件中的链接时，不要依赖 r.Host 中的 Host 头来构造 URL，因为这会容易受到主机头注入攻击。URL 域名应硬编码或作为命令行标志在启动应用程序时传入。

另外，如果你不想让用户复制粘贴令牌，你可以让他们点击包含令牌的链接，该链接会带他们到你网站上的页面。类似于这样：

```
Hi,
```

```
Thanks for signing up for a Greenlight account. We're excited to have you on board!

For future reference, your user ID number is 123.

To activate your Greenlight account please click the following link:

h_t_t_p_s_:__/_e_x_a_m_p_l_e_._c_o_m/_u_s_e_r_s/_a_c_t_i_v_a_t_e?_t_o_k_e_n=_Y_3_Q_M_G_X_3_P_J_3_W_L_R_L_2_Y_R_T_Q_G_Q_6_K_R_H_U_

Please note that this link will expire in 3 days and can only be used once.

Thanks,

The Greenlight Team
```

此页面随后应显示一个按钮，上面写着类似“确认您的账户激活”的内容，并且网页上的一些 JavaScript 可以从 URL 中提取令牌，并在用户点击按钮时将其提交到你的 PUT /v1/users/activate API 端点。

如果你选择第二个选项，你还需要采取措施避免令牌在用户导航到不同站点时通过引用标头泄露。你可以使用 Referrer-Policy: Origin 头或 <meta name="referrer" content="origin"> HTML 标签来缓解此问题，尽管你应该意识到它并非被所有网络浏览器都支持（目前支持率约为 ~96%）。

不过，在所有情况下，无论电子邮件和工作流程在前端和用户体验方面看起来如何，我们已实现的后端 API 端点都是相同的且无需更改。

## SQL 查询时序攻击

值得指出的是，我们在 `UserModel.GetForToken()` 中使用的 SQL 查询理论上容易受到时序攻击，因为 PostgreSQL 对 `tokens.hash = $1` 条件的评估不是以恒定时间执行的。

```
SELECT users.id, users.created_at, users.name, users.email,
users.password_hash, users.activated, users.version
FROM users
INNER JOIN tokens
ON users.id = tokens.user_id
WHERE tokens.hash = $1      --<-- This is vulnerable to a timing attack
AND tokens.scope = $2
AND tokens.expiry > $3
```

虽然操作起来有点棘手，但理论上攻击者可以向我们的 `PUT /v1/users/activated` 端点发出数千个请求并分析平均响应时间中的微小差异，以构建数据库中哈希激活令牌值的图像。

但是，在我们的情况下，即使时序攻击成功，它也只会泄露数据库中的 *哈希* 令牌值——而不是明文

用户实际需要提交以激活其账户的令牌值。

因此，攻击者仍然需要利用暴力破解来找到一个 26 字符的字符串，而该字符串恰好与他们在时序攻击中发现的 SHA-256 哈希值相同。这是极其困难的，以现有技术根本不可行。

## 认证

在本书的这一部分，我们将探讨如何*验证*发往我们 API 的请求，以便确切地知道某个请求来自哪个用户。

> **请记住：** *认证*是确认*用户是谁*，而*授权*则是检查该用户是否有权限执行某项操作。

我们将：

-   列出我们可以采用的 API 认证方式，并讨论它们各自的优缺点。
-   实现一种有状态的基于令牌的认证模式，允许客户端用其用户凭据换取一个限时的认证令牌，以标识其身份。

### HTTP 基本认证

要判断*谁在向你的 API 发起请求*，也许最简单的方式就是使用 HTTP 基本认证。

使用这种方法时，客户端在每次请求中包含一个 `Authorization` 头，其中携带其凭据。凭据需要采用 `username:password` 格式并进行 base-64 编码。因此，例如，要以 `alice@example.com:pa55word` 身份进行认证，客户端会发送以下请求头：

```
Authorization: Basic YWxpY2VAZXhhbXBsZS5jb206cGE1NXdvcmQ=
```

在你的 API 中，你可以使用 Go 的 `Request.BasicAuth()` 方法从这个请求头中提取凭据，并在继续处理请求之前验证它们是否正确。

HTTP 基本认证的一大优点是它对客户端来说非常简单。客户端只需在每次请求中发送相同的请求头即可——而且大多数编程语言、Web 浏览器以及 `curl` 和 `wget` 等工具都开箱即用地支持 HTTP 基本认证。

当你的 API 没有“真正的”用户账户，但你想要一种快速简便的方式来限制访问或防止被窥探时，它通常很有用。

对于拥有“真正的”用户账户（尤其是密码经过哈希处理）的 API 来说，它就不太合适了。将客户端提供的密码与（缓慢的）哈希密码进行比较，是一种有意为之的高成本操作，而在使用 HTTP 基本认证时，你需要在每个请求中都进行这种检查。这会给你的 API 服务器带来大量额外工作，并显著增加响应延迟。

但即便如此，如果你的 API 流量非常低，而且响应速度对你来说并不重要，基本认证仍然是一个不错的选择。

### 令牌认证

*令牌认证*（有时也称为*持有者令牌认证*）的总体思路如下：

-   1. 客户端向你的 API 发送一个包含其凭据（通常是用户名或电子邮件地址以及密码）的请求。
-   2. API 验证凭据是否正确，生成一个代表该用户的*持有者令牌*，并将其发送回用户。令牌在一段时间后过期，之后用户需要再次提交其凭据以获取新令牌。
-   3. 对于随后对 API 的请求，客户端会在 `Authorization` 请求头中包含该令牌，如下所示：

当客户端在后续请求中返回令牌时，你的 API 可以在数据库中查找该令牌，检查它是否已过期，并检索相应的用户 ID 以确定请求来自哪个用户。

这样做的一大优点是，你的 API 对令牌保持控制——通过从数据库中删除令牌或将其标记为已过期，可以很容易地按令牌或按用户撤销令牌。

从概念上讲，它也很简单且稳健——安全性来自令牌是一个“不可猜测”的值，这就是为什么为令牌使用高熵、加密安全的随机值非常重要。

那么，缺点是什么呢？

除了令牌认证通常给客户端带来的固有复杂性之外，很难找到太多可批评之处。也许需要数据库查询是一个缺点——但在大多数情况下，你*反正*都需要进行数据库查询来检查用户的激活状态或检索关于他们的其他信息。

### 无状态令牌认证

相比之下，无状态令牌将用户 ID 和过期时间编码在*令牌本身*中。令牌经过加密签名以防止篡改，并且（在某些情况下）经过加密以防止内容被读取。

有几种不同的技术可用于创建无状态令牌。将信息编码在 JWT（JSON Web Token）中可能是最广为人知的方法，但 PASETO、Branca 和 nacl/secretbox 也是可行的替代方案。尽管这些技术的实现细节不同，但就认证而言，它们的总体优缺点相似。

使用无状态令牌进行认证的主要卖点是，编码和解码令牌的工作可以在内存中完成，而且识别用户所需的全部信息都包含在令牌本身中。无需执行数据库查询即可知道请求来自哪个用户。

无状态令牌的主要缺点是，它们一旦签发，就很难被撤销。

在紧急情况下，你可以通过更改用于签署令牌的密钥来有效地撤销所有令牌（迫使所有用户重新认证），或者另一种变通方法是在数据库中维护一个被撤销令牌的黑名单（尽管这会破坏无状态令牌的“无状态”特性）。

> **注意：** 你通常应避免在无状态令牌中存储额外信息，例如用户的激活状态或权限，并将其作为*授权*检查的依据。在令牌的生命周期内，编码进令牌的信息可能会变得过时，与你系统中的真实数据失去同步——而依赖过时数据

-   然后，你的 API 将授权码发送到身份提供者提供的另一个端点。他们验证授权码，如果有效，他们会向你发送一个包含 *ID 令牌* 的 JSON 响应。
-   这个 ID 令牌本身就是一个 JWT。你需要验证并解码这个 JWT，以获取实际用户信息，包括电子邮件地址、姓名、出生日期、时区等。
-   既然你已经知道用户是谁，就可以实现有状态或无状态的身份验证令牌模式，这样就不必为每个后续请求都经历整个过程。

与我们看过的所有其他方案一样，使用 OpenID Connect 也有其优缺点。最大的优点是，你不需要自己持久化存储用户信息或密码。最大的缺点是它相当复杂——尽管有一些辅助包（如 `coreos/go-oidc`）能够很好地掩盖这种复杂性，并提供一个简单的接口供你接入 OpenID Connect 工作流。

同样重要的是要指出，使用 OpenID Connect 要求你的所有用户在身份提供者处拥有账户，而且“认证和同意”步骤需要通过 Web 浏览器进行人工交互——如果你的 API 是网站的后端，这大概没问题；但如果它是一个以其他计算机程序为客户端的“独立”API，就不太理想了。

-   相比之下，API 密钥可能更适合“通用”API，因为它们是永久性的，对于开发人员来说，在应用程序和脚本中使用起来也更简单。

在本书的其余部分，我们将使用*有状态身份验证令牌*模式来实现身份验证。就我们的情况而言，我们已经在我们*激活令牌*相关工作的一部分中构建了大量所需逻辑。

> **注意：** 虽然我真的不建议使用 JWT，除非你需要某种形式的*委托认证*，但我知道它们在开发者社区中占有很大份额，而且常常被更广泛地使用。
> 
> 因此，我在书的末尾还附了一个附录，解释如何将 *Greenlight* API 调整为使用带有 JWT 的无状态身份验证令牌模式。




## 生成身份验证令牌

在本章中，我们将专注于为新的 `POST/v1/tokens/authentication` 端点构建代码，该端点将允许客户端用其凭据（电子邮件地址和密码）交换有状态的身份验证令牌。

> **注意：** 为了简洁，而不是在本书其余部分重复“有状态身份验证令牌”一词，从现在开始我们将简单地将其称为用户的 *身份验证令牌*。

在高层次上，交换用户凭据以获取身份验证令牌的过程将如下工作：

- 1. 客户端向新的 `POST/v1/tokens/authentication` 端点发送包含其凭据（电子邮件和密码）的 JSON 请求。
- 2. 我们根据电子邮件查找用户记录，并检查提供的密码是否为该用户的正确密码。如果不是，则我们发送错误响应。
- 3. 如果密码正确，我们将使用我们的 `app.models.Tokens.New()` 方法生成一个过期时间为 24 小时且范围为 `"authentication"` 的令牌。
- 4. 我们将此身份验证令牌以 JSON 响应正文的形式发送回客户端。

让我们在 `internal/data/tokens.go` 文件中开始。

```json
{
  "token": "X3ASTT2CDAN66BACKSCI4SU7SI",
  "expiry": "2021-01-18T13:00:25.648511827+01:00"
}
```

## 构建端点

现在让我们深入本章的核心并设置新的 `POST/v1/tokens/authentication` 端点所需的所有代码。完成时，我们的 API 路由将如下所示：

| 方法 | URL 模式 | 处理程序 | 操作 |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | 显示应用程序信息 |
| GET | /v1/movies | listMoviesHandler | 显示所有电影的详细信息 |
| POST | /v1/movies | createMovieHandler | 创建新电影 |
| GET | /v1/movies/:id | showMovieHandler | 显示特定电影的详细信息 |
| PATCH | /v1/movies/:id | updateMovieHandler | 更新特定电影的详细信息 |
| DELETE | /v1/movies/:id | deleteMovieHandler | 删除特定电影 |
| POST | /v1/users | registerUserHandler | 注册新用户 |
| PUT | /v1/users/activated | activateUserHandler | 激活特定用户 |
| POST | /v1/tokens/authentication | createAuthenticationTokenHandler | 生成新的身份验证令牌 |

如果你跟随操作，请继续创建新的 `cmd/api/tokens.go` 文件：

```
$ touch cmd/api/tokens.go
```

并且在这个新文件中我们将添加 `createAuthenticationTokenHandler` 的代码。

本质上，我们希望此处理程序*交换用户的电子邮件地址和密码以获取身份验证令牌*，如下所示：

```
File: cmd/api/tokens.go

package main

import (
    "errors"
    "net/http"
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator"
)
```

```
func (app *application) createAuthenticationTokenHandler(w http.ResponseWriter, r *http.Request) {
    // Parse the email and password from the request body.
    var input struct {
        Email     string `json:"email"`
        Password string `json:"password"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    // Validate the email and password provided by the client.
    v := validator.New()

    data.ValidateEmail(v, input.Email)
    data.ValidatePasswordPlaintext(v, input.Password)

    if !v.Valid() {
        app.failedValidationResponse(w, r, v.Errors)
        return
    }

    // Lookup the user record based on the email address. If no matching user was
    // found, then we call the app.invalidCredentialsResponse() helper to send a 401
    // Unauthorized response to the client (we will create this helper in a moment).
    user, err := app.models.Users.GetByEmail(input.Email)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrRecordNotFound):
            app.invalidCredentialsResponse(w, r)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }

    // Check if the provided password matches the actual password for the user.
    match, err := user.Password.Matches(input.Password)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }

    message := "invalid authentication credentials"
    app.errorResponse(w, r, http.StatusUnauthorized, message)
}
```

最后，我们需要在应用程序路由中包含 POST /v1/tokens/authentication 端点。如下所示：

```
File: cmd/api/routes.go

package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck", app.healthcheckHandler)

    router.HandlerFunc(http.MethodGet, "/v1/movies", app.listMoviesHandler)
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.createMovieHandler)
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id", app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id", app.updateMovieHandler)
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id", app.deleteMovieHandler)

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated", app.activateUserHandler)

    // Add the route for the POST /v1/tokens/authentication endpoint.
    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication", app.createAuthenticationTokenHandler)

    return app.recoverPanic(app.rateLimit(router))
}
```

```
"error": "invalid authentication credentials"
}
```

在继续之前，让我们快速查看 PostgreSQL 数据库中的 `tokens` 表，以检查身份验证令牌是否已创建。

```
$ psql $GREENLIGHT_DB_DSN
Password for user greenlight:
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256,
compression: off)
Type "help" for help.

greenlight=> SELECT * FROM tokens WHERE scope = 'authentication';
\x4390d2ff4af7346dd4238ffccb8a5b18e8c3af9aa8cf57852895ad0f8ee2c50d |     1 | 2021-04-17 11:03:37+02 | authentication
```

看起来不错。我们可以看到令牌与 ID 为 1 的用户相关联（如果你一直跟随操作，这将是用户 `alice@example.com`），并且具有正确的范围和过期时间。

## 附加信息

### Authorization 头部

偶尔你可能会遇到其他 API 或教程，其中身份验证令牌会以 `Authorization` 头部形式发送回客户端，而不是像本章中那样在响应正文中。

你*可以*这样做，在大多数情况下它可能工作正常。但重要的是要意识到你正在做出对 HTTP 规范的*蓄意违反*：`Authorization` 是一个*请求*头部，而不是响应头部。

## 验证请求

现在我们的客户端有一种方法可以用凭据交换身份验证令牌，让我们看看如何使用该令牌来*验证它们*，以便我们确切知道请求来自哪个用户。

本质上，一旦客户端拥有身份验证令牌，我们将期望他们在后续所有请求中将其包含在 `Authorization` 头部中，如下所示：

```
Authorization: Bearer IEYZQUBEMPPAKPOAWTPV6YJ6RM
```

当我们收到这些请求时，我们将使用新的 `authenticate()` 中间件方法执行以下逻辑：

- 如果身份验证令牌无效，则我们将向客户端发送 `401 Unauthorized` 响应和错误消息，让他们知道其令牌格式错误或无效。
- 如果身份验证令牌有效，我们将查找用户详细信息并将其添加到 *request context*。
- 如果根本未提供 `Authorization` 头部，则我们将改为将 *anonymous user* 的详细信息添加到请求上下文中。




*姓名、电子邮件或密码。*

我们还在 `User` 结构体上实现了 `IsAnonymous()` 方法，因此每当我们有一个 `User` 实例时，就可以轻松检查它是否是 `AnonymousUser` 实例。 例如：

```go
data.AnonymousUser.IsAnonymous() // → Returns true

otherUser := &data.User{}
otherUser.IsAnonymous()           // → Returns false
```

## 读取和写入请求上下文

在创建 `authenticate()` 中间件本身之前，另一个设置步骤与 *在请求上下文中存储用户详细信息* 有关。

我们在 *Let’s Go* 中详细讨论了请求上下文是什么以及如何使用它，如果其中任何内容让你感到不熟悉，我建议在继续之前重新阅读书中的该部分。 但作为快速提醒：

- 我们的应用程序处理的每个 `http.Request` 都嵌入了 `context.Context`，我们可以在请求的生命周期内使用它来存储包含任意数据的键/值对。 在这种情况下，我们希望存储包含当前用户信息的 `User` 结构体。
- 存储在请求上下文中的任何值都具有 `interface{}` 类型。 这意味着在从请求上下文检索值后，在使用它之前需要将其断言回原始类型。
- 使用自己的自定义类型作为请求上下文键是良好的实践。 这有助于防止你的代码与也使用请求上下文存储信息的任何第三方包之间的命名冲突。

为此，让我们创建一个新的 `cmd/api/context.go` 文件，其中包含一些用于从请求上下文读取/写入 `User` 结构体的辅助方法。

如果你跟着操作，请继续创建新文件：

```bash
$ touch cmd/api/context.go
```

然后添加以下代码：

```go
File: cmd/api/context.go

package main

import (
    "context"
    "net/http"

    "greenlight.alexedwards.net/internal/data"
)
```

```go
type contextKey string

// Convert the string "user" to a contextKey type and assign it to the
userContextKey
// constant. We'll use this constant as the key for getting and setting user
information
// in the request context.
const userContextKey = contextKey("user")

// The contextSetUser() method returns a new copy of the request with the
provided
// User struct added to the context. Note that we use our userContextKey
constant as the
// key.
func (app *application) contextSetUser(r *http.Request, user *data.User) *http.Request {
    ctx := context.WithValue(r.Context(), userContextKey, user)
    return r.WithContext(ctx)
}

// The contextGetUser() retrieves the User struct from the request context.
The only
// time that we'll use this helper is when we logically expect there to be
User struct
// value in the context, and if it doesn't exist it will firmly be an
'unexpected' error.
// As we discussed earlier in the book, it's OK to panic in those
circumstances.
func (app *application) contextGetUser(r *http.Request) *data.User {
    user, ok := r.Context().Value(userContextKey).(*data.User)
    if !ok {
        panic("missing user value in request context")
    }

    return user
}
```

```go
http.ResponseWriter, r *http.Request) {
    w.Header().Set("WWW-Authenticate", "Bearer")

    message := "invalid or missing authentication token"
    app.errorResponse(w, r, http.StatusUnauthorized, message)
}
```

> **注意：** 我们在这里包含 `WWW-Authenticate: Bearer` 头是为了帮助通知或提醒客户端，我们期望他们使用 bearer token 进行身份验证。

最后，我们需要在处理器链中添加 `authenticate()` 中间件。 我们希望在 *所有* 请求上使用此中间件 —— 在我们的 panic 恢复和速率限制中间件之后，但在路由器之前。

请相应地更新 `cmd/api/routes.go` 文件：

```go
File: cmd/api/routes.go

package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)
}
```

**提示：** 如果你在此处收到错误响应，请确保在第二次请求中使用来自第一次请求的正确身份验证令牌。

相比之下，你也可以尝试发送一些带有无效身份验证令牌或格式错误的 Authorization 头的请求。 在这些情况下，你应该会收到 401 Unauthorized 响应，如下所示：

```
$ curl -i -H "Authorization: Bearer XXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
localhost:4000/v1/healthcheck
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Vary: Authorization
Www-Authenticate: Bearer
Date: Fri, 16 Apr 2021 10:23:06 GMT
Content-Length: 56

{
  "error": "invalid or missing authentication token"
}

$ curl -i -H "Authorization: INVALID" localhost:4000/v1/healthcheck
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Vary: Authorization
Www-Authenticate: Bearer
Date: Fri, 16 Apr 2021 10:23:26 GMT
Content-Length: 56

{
  "error": "invalid or missing authentication token"
}
```

## 需要用户激活

正如我们刚才提到的，就授权而言，我们要做的第一件事是限制对我们的 `/v1/movies**` 端点的访问 —— 这样只有经过身份验证（非匿名）的用户并且已激活其账户的用户才能访问。

执行这类检查是某些中间件的理想任务，因此让我们开始创建一个新的 `requireActivatedUser()` 中间件方法来处理此事。 在此中间件中，我们希望从请求上下文中提取 `User` 结构体，然后检查 `IsAnonymous()` 方法和 `Activated` 字段以确定请求是否应继续。

具体来说：

- 如果用户是匿名的，我们应发送 `401 Unauthorized` 响应并显示错误消息说 “`you must be authenticated to access this resource`”。
- 如果用户不是匿名的（即他们已成功通过身份验证，我们知道他们是谁），但他们未 *激活*，我们应发送 `403 Forbidden` 响应并显示错误消息说 “`your user account must be activated to access this resource`”。

文件: cmd/api/middleware.go

```go
package main

...

func (app *application) requireActivatedUser(next http.HandlerFunc) http.HandlerFunc {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Use the contextGetUser() helper that we made earlier to retrieve the user
        // information from the request context.
        user := app.contextGetUser(r)

        // If the user is anonymous, then call the authenticationRequiredResponse() to
        // inform the client that they should authenticate before trying again.
        if user.IsAnonymous() {
            app.authenticationRequiredResponse(w, r)
            return
        }

        // If the user is not activated, use the inactiveAccountResponse() helper to
        // inform them that they need to activate their account.
        if !user.Activated {
            app.inactiveAccountResponse(w, r)
            return
        }

        // Call the next handler in the chain.
        next.ServeHTTP(w, r)
    })
}
```

这里请注意，我们的 `requireActivatedUser()` 中间件与其他我们在本书中构建的中间件的签名略有不同。 而不是接受和返回 `http.Handler`，它接受和返回 `http.HandlerFunc`。

这是一个小的改动，但它使得可以直接用此中间件包装我们的 `/v1/movie**` 处理器函数，而无需进行任何进一步的转换。

请按如下方式更新 `cmd/api/routes.go` 文件以执行此操作：

```go
File: cmd/api/routes.go

package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)

    // Use the requireActivatedUser() middleware on our five /v1/movies**
endpoints.
    router.HandlerFunc(http.MethodGet, "/v1/movies",
app.requireActivatedUser(app.listMoviesHandler))
    router.HandlerFunc(http.MethodPost, "/v1/movies",
app.requireActivatedUser(app.createMovieHandler))
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",

```
app.requireActivatedUser(app.showMovieHandler)
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.requireActivatedUser(app.updateMovieHandler))
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.requireActivatedUser(app.deleteMovieHandler))

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication",
app.createAuthenticationTokenHandler)

    return app.recoverPanic(app.rateLimit(app.authenticate(router)))
}
```

## 演示

好吧，让我们试试这些更改！

我们将开始以匿名用户身份调用 GET /v1/movies/:id 端点。执行此操作时，你现在应该会收到 401 Unauthorized 响应，如下所示：

```
$ curl -i localhost:4000/v1/movies/1
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Vary: Authorization
Www-Authenticate: Bearer
Date: Fri, 16 Apr 2021 15:59:33 GMT
Content-Length: 66

{
"error": "you must be authenticated to access this resource"
}
```

接下来，让我们尝试以拥有账户但尚未激活的用户身份发出请求。如果你一直跟着做，你应该能够使用 `alice@example.com` 用户来执行此操作，如下所示：

```
$ BODY='{"email": "alice@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/tokens/authentication
{
    "authentication_token": {
        "token": "204YHHWDHVWWDNKN2UZR722BU",
        "expiry": "2021-04-17T18:03:09.598843181+02:00"
    }
}

$ curl -i -H "Authorization: Bearer 204YHHWDHVWWDNKN2UZR722BU"
localhost:4000/v1/movies/1
HTTP/1.1 403 Forbidden
Content-Type: application/json
Vary: Authorization
Date: Fri, 16 Apr 2021 16:03:45 GMT
Content-Length: 76

{
    "error": "your user account must be activated to access this resource"
}
```

太好了，我们可以看到这现在会从我们新的 `inactiveAccountResponse()` 辅助函数返回 `403 Forbidden` 响应。

最后，让我们尝试以已激活用户身份发出请求。

如果你正在跟随编码，你可能想快速连接到你的 PostgreSQL 数据库并 double-check 哪些用户已经激活。

```
$ psql $GREENLIGHT_DB_DSN
psql (13.2 (Ubuntu 13.2-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256,
compression: off)
Type "help" for help.

greenlight=> SELECT email FROM users WHERE activated = true;
        email
--------------------
 faith@example.com
(1 row)
```

在我的例子中，唯一已激活的用户是 faith@example.com，所以让我们以他们的身份尝试发出请求。当以已激活用户身份发出请求时，我们 requireActivatedUser() 中间件中的所有检查都会通过，你应该会得到成功的响应。类似于这样：

```
$ BODY='{"email": "faith@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/tokens/authentication
{
  "authentication_token": {
    "token": "ZFIKQ344EYM5KEP6JL2RHL RPJQ",
    "expiry": "2021-04-17T18:04:57.513348573+02:00"
  }
}

$ curl -H "Authorization: Bearer ZFIKQ344EYM5KEP6JL2RHL RPJQ"
localhost:4000/v1/movies/1
{
  "movie": {
    "id": 1,
    "title": "Moana",
    "year": 2016,
    "runtime": "107 mins",
    "genres": [
      "animation",
      "adventure"
    ],
    "version": 1
  }
}
```

## 分割中间件

目前我们有一个中间件执行两项检查：首先检查用户是否已通过身份验证（不是匿名），其次检查他们是否已激活。

但可以想象一种场景，你只想检查用户是否已通过身份验证，而不关心他们是否已激活。为此，你可能希望引入额外的 requireAuthenticatedUser() 中间件以及当前的 requireActivatedUser() 中间件。

然而，这两个中间件之间会存在一些重叠，因为它们都会检查用户是否已通过身份验证。避免这种重复的一种巧妙方法是

如果你只有几个端点需要执行授权检查，那么与其使用中间件，通常在相关处理器内部执行检查会更容易。例如：

```
func (app *application) exampleHandler(w http.ResponseWriter, r *http.Request) {
    user := app.contextGetUser(r)

    if user.IsAnonymous() {
        app.authenticationRequiredResponse(w, r)
        return
    }

    if !user.Activated {
        app.inactiveAccountResponse(w, r)
        return
    }

    // The rest of the handler logic goes here...
}
```

| 方法 | URL 模式 | 所需权限 |
|---|---|---|
| GET | /v1/movies/:id | movies:read |
| PATCH | /v1/movies/:id | movies:write |
| DELETE | /v1/movies/:id | movies:write |
| POST | /v1/users | - |
| PUT | /v1/users/activated | - |
| POST | /v1/tokens/authentication | - |

## 权限与用户之间的关系

权限与用户之间的关系是 *多对多* 关系的绝佳示例。一个用户可能拥有 *许多权限*，同一个权限也可能属于 *许多用户*。

在像 PostgreSQL 这样的关系数据库中管理多对多关系的经典方法是创建两个实体之间的 *连接表*。我会快速解释其工作原理。

假设我们将用户数据存储在 `users` 表中，其结构如下：

| id | email | ... |
|---|---|---|

| id | email | ... |
|---|---|---|
| 1 | alice@example.com | ... |
| 2 | bob@example.com | ... |

我们的权限数据存储在 `permissions` 表中，如下所示：

| id | code |
|---|---|
| 1 | movies:read |
| 2 | movies:write |

然后我们可以创建一个名为 `users_permissions` 的连接表来存储有关 *哪些用户拥有哪些权限* 的信息，如下所示：

| user_id | permission_id |
|---|---|
| 1 | 1 |
| 2 | 1 |
| 2 | 2 |

在上面的示例中，用户 `alice@example.com`（用户 ID `1`）仅拥有 `movies:read`（权限 ID `1`）权限，而 `bob@example.com`（用户 ID `2`）同时拥有 `movies:read` 和 `movies:write` 权限。

就像我们在书中前面看到的一对多关系一样，你可能希望在数据库模型中从两侧查询这种关系。例如，在你的数据库模型中，你可能希望创建以下方法：

```
PermissionModel.GetAllForUser(user)      → Retrieve all permissions for a user
UserModel.GetAllForPermission(permission) → Retrieve all users with a specific permission
```

## 创建 SQL 迁移

让我们将此付诸实践，并创建一个 SQL 迁移，在我们的数据库中创建新的 `permissions` 和 `users_permissions` 表，遵循我们刚才描述的模式。

继续运行以下命令来创建迁移文件：

```
$ migrate create -seq -ext .sql -dir ./migrations add_permissions
/home/alex/Projects/greenlight/migrations/000006_add_permissions.up.sql
/home/alex/Projects/greenlight/migrations/000006_add_permissions.down.sql
```

然后将以下 SQL 语句添加到‘up’迁移文件中：

```
File: migrations/000006_add_permissions.up.sql
```

```
CREATE TABLE IF NOT EXISTS permissions (
    id bigserial PRIMARY KEY,
    code text NOT NULL
);

CREATE TABLE IF NOT EXISTS users_permissions (
    user_id bigint NOT NULL REFERENCES users ON DELETE CASCADE,
    permission_id bigint NOT NULL REFERENCES permissions ON DELETE CASCADE,
    PRIMARY KEY (user_id, permission_id)
);

-- Add the two permissions to the table.
INSERT INTO permissions (code)
VALUES
    ('movies:read'),
    ('movies:write');
```

这里有几件重要的事情需要指出：

- PRIMARY KEY (user_id, permission_id) 行在我们的 users_permissions 表上设置了一个复合主键，其中主键由 users_id 和 permission_id 两列组成。将此设置为主键本质上意味着相同的用户/权限组合在表中只能出现一次且不能重复。
- 在创建 users_permissions 表时，我们使用 REFERENCES user 语法来针对 users 表的主键创建外键约束，这确保 user_id 列中的任何值在 users 表中都有对应的条目。同样，我们使用 REFERENCES permissions 语法

为确保 permission_id 列在 permissions 表中有对应的条目。

我们还需要在 'down' 迁移文件中添加必要的 DROP TABLE 语句，如下所示：

```
File: migrations/000006_add_permissions.down.sql

DROP TABLE IF EXISTS users_permissions;
DROP TABLE IF EXISTS permissions;
```

完成之后，请继续运行迁移：

```
$ migrate -path ./migrations -database $GREENLIGHT_DB_DSN up
6/u add_permissions (22.74009ms)
```

## 英特尔

Core i5-6300U Processor

6M 缓存，最高 3.00 GHz

FC-BGA14C, Tray

### 产品规格

Intel® Core™ i5-6300U Processor (6M Cache, up to 3.00 GHz)

FC-BGA14C, Tray

### 基本信息

| 项目 | 值 |
| --- | --- |
| 状态 | 已发布 |
| 发布日期 | Q4'15 |
| 处理器编号 | i5-6300U |
| 核心数 | 2 |
| 线程数 | 4 |
| 时钟速度 | 2.40 GHz |
| 最大睿频频率 | 3.00 GHz |
| 缓存 | 6 MB Intel® Smart Cache |
| 总线速度 | 4 GT/s |
| TDP | 15 W |

### 补充信息

| 项目 | 值 |
| --- | --- |
| 是否提供嵌入式选项 | 否 |

### 内存规格

| 项目 | 值 |
| --- | --- |
| 最大内存大小（取决于内存类型） | 32 GB |
| 内存类型 | DDR4-1866, DDR3L-1600, LPDDR3-1866 |
| 内存通道数 | 2 |
| 最大内存通道数 | 2 |

## 规格

在此查询中，我们使用 INNER JOIN 子句将 permissions 表连接到 users_permissions 表，然后再次使用它将该表连接到 users 表。然后我们使用 WHERE 子句过滤结果，仅保留与特定用户 ID 相关的行。

让我们继续设置新的 PermissionModel。首先创建一个新的 internal/data/permissions.go 文件：

```
$ touch internal/data/permissions.go
```

然后添加以下代码：

```
File: internal/data/permissions.go

package data

import (
    "context"
    "database/sql"
    "time"
)

// Define a Permissions slice, which we will use to hold the permission codes (like
// "movies:read" and "movies:write") for a single user.
type Permissions []string

// Add a helper method to check whether the Permissions slice contains a
```

```
defer rows.Close()

var permissions Permissions

for rows.Next() {
    var permission string

    err := rows.Scan(&permission)
    if err != nil {
        return nil, err
    }

    permissions = append(permissions, permission)
}
if err = rows.Err(); err != nil {
    return nil, err
}

return permissions, nil
}
```

然后我们需要做的最后一件事是将 `PermissionModel` 添加到父 `Model` 结构体中，以便我们的处理程序和中间件可以使用它。像这样：

```
File: internal/data/models.go

package data

...

type Models struct {
    Movies      MovieModel
    Permissions PermissionModel // Add a new Permissions field.
}
```

## 检查权限

现在我们的 PermissionModel 已经设置好，让我们看看如何使用它来限制对 API 端点的访问。

从概念上讲，我们在这里需要做的事情并不复杂。

- 我们将创建一个新的 `requirePermission()` 中间件，它接受一个特定的权限代码（如 `"movies:read"`）作为参数。
- 在此中间件中，我们将从请求上下文中检索当前用户，并调用 `app.models.Permissions.GetAllForUser()` 方法（我们刚刚创建的）来获取其权限的切片。
- 然后我们可以检查切片是否包含所需的特定权限代码。如果不包含，我们应该向客户端发送 `403 Forbidden` 响应。

为了实践这一点，让我们首先为发送 `403 Forbidden` 响应创建一个新的 `notPermittedResponse()` 辅助函数。像这样：

```
File: cmd/api/errors.go

package main

...

func (app *application) notPermittedResponse(w http.ResponseWriter, r *http.Request) {
    message := "your user account doesn't have the necessary permissions to access this resource"
    app.errorResponse(w, r, http.StatusForbidden, message)
}
```

然后让我们前往 `cmd/api/middleware.go` 文件并创建新的 `requirePermission()` 中间件方法。

我们将设置它，使 `requirePermission()` 中间件自动包装我们现有的 `requireActivatedUser()` 中间件，而后者——不要忘记——包装我们的 `requireAuthenticatedUser()` 中间件。

这很重要——这意味着当我们使用 `requirePermission()` 中间件时，我们实际上会执行 *三个检查*，这些检查共同确保请求来自 *经过身份验证（非匿名）、已激活的用户，并且具有特定权限。*

让我们继续在 `cmd/api/middleware.go` 文件中创建它，如下所示：

```
File: cmd/api/middleware.go

package main

...

// Note that the first parameter for the middleware function is the
// permission code that we require the user to have.
func (app *application) requirePermission(code string, next http.HandlerFunc) http.HandlerFunc {
    fn := func(w http.ResponseWriter, r *http.Request) {
        // Retrieve the user from the request context.
        user := app.contextGetUser(r)

        // Get the slice of permissions for the user.
        permissions, err := app.models.Permissions.GetAllForUser(user.ID)
        if err != nil {
            app.serverErrorResponse(w, r, err)
            return
        }

        // Check if the slice includes the required permission. If it doesn't, then
        // return a 403 Forbidden response.
        if !permissions.Include(code) {
            app.notPermittedResponse(w, r)
            return
        }

        // Otherwise they have the required permission so we call the next
        // handler in the chain.
        next.ServeHTTP(w, r)
    }

    // Wrap this with the requireActivatedUser() middleware before returning it.
    return app.requireActivatedUser(fn)
}
```

```
app.requirePermission("movies:write", app.deleteMovieHandler)

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated", app.activateUserHandler)

    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication", app.createAuthenticationTokenHandler)

    return app.recoverPanic(app.rateLimit(app.authenticate(router)))
}
```

## 演示

展示其实际效果有点尴尬，因为，如果你一直跟着做，我们数据库中目前没有任何用户的权限设置。

为了帮助演示此新功能，让我们打开 `psql` 并添加一些权限。具体来说，我们将：

- 激活用户 `alice@example.com`。
- 为 *所有* 用户授予 "movies:read" 权限。
- 为用户 `faith@example.com` 授予 "movies:write" 权限。

如果你跟着做，打开你的 `psql` 提示符：

```
$ psql $GREENLIGHT_DB_DSN
Password for user greenlight:
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

greenlight=>
```

并执行以下语句：

```
-- Set the activated field for alice@example.com to true.
UPDATE users SET activated = true WHERE email = 'alice@example.com';

-- Give all users the 'movies:read' permission
INSERT INTO users_permissions
SELECT id, (SELECT id FROM permissions WHERE code = 'movies:read') FROM
users;

-- Give faith@example.com the 'movies:write' permission
INSERT INTO users_permissions
VALUES (
    (SELECT id FROM users WHERE email = 'faith@example.com'),
    (SELECT id FROM permissions WHERE  code = 'movies:write')
);

-- List all activated users and their permissions.
SELECT email, array_agg(permissions.code) as permissions
FROM permissions
INNER JOIN users_permissions ON users_permissions.permission_id =
permissions.id
INNER JOIN users ON users_permissions.user_id = users.id
WHERE users.activated = true
GROUP BY email;
```

完成后，你应该会看到当前已激活用户及其权限的列表，类似于这样：

| email | permissions |
| --- | --- |
| alice@example.com | {movies:read} |
| faith@example.com | {movies:read,movies:write} |

(2 rows)

> 注意：在该最终 SQL 查询中，我们使用聚合函数 `array_agg()` 和 `GROUP BY` 子句将与每个电子邮件地址关联的权限作为数组输出。

现在我们的用户已分配了一些权限，我们准备尝试了。

首先，让我们尝试以 `alice@example.com` 的身份向我们的 `GET /v1/movies/1` 和 `DELETE /v1/movies/1` 端点发出一些请求。第一个请求应该能正确工作，但第二个请求应该会失败，因为用户没有必要的 `movies:write` 权限。

```
$ BODY='{"email": "alice@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/tokens/authentication
{
  "authentication_token": {
    "token": "OPFXEPOYZWMGNWXWKYIMEGATU",
    "expiry": "2021-04-17T20:49:39.963768416+02:00"
  }
```



## 授予权限

我们的权限模型和授权中间件现在运行良好。但是——目前——当新用户注册账户时，他们*没有任何权限*。在本章中，我们将更改这一点，以便新用户在默认情况下会自动*授予*"movies:read"权限。

## 更新权限模型

为了向用户授予权限，我们需要更新我们的 `PermissionModel` 以包含一个 `AddForUser()` 方法，该方法将*为特定用户的一个或多个权限代码*添加到我们的数据库中。想法是我们可以在处理程序中像这样使用它：

```
// Add the "movies:read" and "movies:write" permissions for the user with ID = 2.
app.models.Permissions.AddForUser(2, "movies:read", "movies:write")
```

在幕后，我们需要插入此数据的 SQL 语句如下所示：

```sql
INSERT INTO users_permissions
SELECT $1, permissions.id FROM permissions WHERE permissions.code = ANY($2)
```

在此查询中，`$1` 参数将是用户的 ID，而 `$2` 参数将是*PostgreSQL 数组*，其中包含我们想要为用户添加的权限代码，如 `{'movies:read', 'movies:write'}`。

这里发生的事情是，第二行的 `SELECT ...` 语句创建了一个‘临时’表，其行由用户 ID *以及数组中权限代码对应的 ID* 组成。然后我们将此临时表的内容插入到我们的 `user_permissions` 表中。

让我们继续在 `internal/data/permissions.go` 文件中创建 `AddForUser()` 方法：

```go
File: internal/data/permissions.go

package data

import (
    "context"
    "database/sql"
    "time"

    "github.com/lib/pq" // New import
)

...
```

```
// Add the provided permission codes for a specific user. Notice that we're using a
// variadic parameter for the codes so that we can assign multiple
// permissions in a
// single call.
func (m PermissionModel) AddForUser(userID int64, codes ...string) error {
    query := `
        INSERT INTO users_permissions
        SELECT $1, permissions.id FROM permissions WHERE permissions.code =
ANY($2)`

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    _, err := m.DB.ExecContext(ctx, query, userID, pq.Array(codes))
    return err
}
```

## 更新注册处理程序

现在就位了，让我们更新我们的 registerUserHandler，以便新用户在注册时自动获得 movies:read 权限。如下所示：

```go
File: cmd/api/users.go

package main

...

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
    var input struct {
}
    return
}

// Add the "movies:read" permission for the new user.
err = app.models.Permissions.AddForUser(user.ID, "movies:read")
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

token, err := app.models.Tokens.New(user.ID, 3*24*time.Hour,
data.ScopeActivation)
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

app.background(func() {
    data := map[string]interface{}{{
        "activationToken": token.Plaintext,
        "userID":          user.ID,
    }}

    err = app.mailer.Send(user.Email, "user_welcome.tmpl", data)
    if err != nil {
        app.logger.PrintError(err, nil)
    }
})

err = app.writeJSON(w, http.StatusAccepted, envelope{"user": user}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
...
```

让我们通过使用电子邮件地址 grace@example.com 注册一个全新的用户来检查它是否正常工作：

```
$ BODY='{"name": "Grace Smith", "email": "grace@example.com", "password": "pa55word"}'
$ curl -d "$BODY" localhost:4000/v1/users
{
  "user": {
    "id": 8,
    "created_at": "2021-04-16T21:32:56+02:00",
    "name": "Grace Smith",
    "email": "grace@example.com",
    "activated": false
  }
}
```

如果打开 psql，您应该能够通过运行以下 SQL 查询来查看他们是否具有 movies:read 权限：

```sql
SELECT email, code FROM users
INNER JOIN users_permissions ON users.id = users_permissions.user_id
INNER JOIN permissions ON users_permissions.permission_id = permissions.id
WHERE users.email = 'grace@example.com';
```

如下所示：

```
$ psql $GREENLIGHT_DB_DSN
Password for user greenlight:
```

```
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

greenlight=> SELECT email, code FROM users
greenlight-> INNER JOIN users_permissions ON users.id =
users_permissions.user_id
greenlight-> INNER JOIN permissions ON users_permissions.permission_id =
permissions.id
greenlight-> WHERE users.email = 'grace@example.com';
```

| 电子邮件 | 代码 |
|---|---|
| grace@example.com | movies:read |

(1 行)

理解 origin 是什么很重要，因为所有 Web 浏览器都实现了名为 *同源策略* 的安全机制。浏览器实现此策略的方式存在一些很小的差异，但总体而言：

- 一个源上的网页可以在其 HTML 中*嵌入*来自另一个源的某些类型资源——包括图像、CSS 和 JavaScript 文件。例如，在你的网页中这样做是可以的：
- 一个源上的网页可以向不同源*发送*数据。例如，网页中的 HTML 表单提交数据到不同源是可以的。
- 但是一个源上的网页*不*允许从不同源*接收*数据。

```
<img src="http://anotherorigin.com/example.png" alt="example image">
```

这里的关键是最后一点：同源策略防止另一个源上的（可能恶意的）网站*读取*（可能保密的）来自你网站的信息。

必须强调的是，跨源*发送数据*并未被同源策略阻止，尽管它也可能很危险。事实上，这就是 CSRF 攻击之所以可能的原因，也是我们需要采取额外步骤来防止它们的原因——比如使用 `SameSite` cookie 和 CSRF 令牌。

作为开发者，你最有可能遇到同源策略的情况是在浏览器中运行的 JavaScript 发起跨源请求时。

例如，假设你有一个位于 `https://foo.com` 的网页，其中包含一些前端 JavaScript 代码。如果此 JavaScript 尝试向 `https://bar.com/data.json`（不同源）发出 HTTP 请求，则请求将被发送并由 `bar.com` 服务器处理，但用户的 Web 浏览器将*阻止响应*，以便来自 `https://foo.com` 的 JavaScript 代码无法看到它。

总体而言，同源策略是一个极其有用的安全保障。但虽然在一般情况下它很好，但在某些情况下你可能希望放宽它。

例如，如果你有一个位于 `api.example.com` 的 API 和一个运行在 `www.example.com` 上的受信任的 JavaScript 前端应用程序，那么你可能希望允许来自受信任的 `www.example.com` 域的跨源请求访问你的 API。

或者你可能有一个完全开放的公共 API，并且希望允许跨源请求*来自任何地方*，以便其他开发者可以轻松地将其集成到自己的网站中。

幸运的是，大多数现代 Web 浏览器允许你通过在 API 响应上设置 `Access-Control` 头来允许或禁止对你的 API 的特定跨源请求。我们将在本书接下来的几章中详细解释如何做到这一点以及这些头的工作原理。

```go
package main

import (
    "flag"
    "log"
    "net/http"
)

// Define a string constant containing the HTML for the webpage. This
consists of a <h1>
// header tag, and some JavaScript which fetches the JSON from our GET
/v1/healthcheck
// endpoint and writes it to inside the <div id="output"></div> element.
const html = `
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
</head>
<body>
    <h1>Simple CORS</h1>
    <div id="output"></div>
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
            );
        });
    </script>
</body>
</html>`

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


受信任的来源：

```
$ go run ./cmd/api -cors-trusted-origins="http://localhost:9000"
{"level":"INFO","time":"2021-04-17T16:48:55Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-17T16:48:55Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

当这两者都在运行时，打开你的网页浏览器并访问 http://localhost:9000。如果你查看开发者工具中的控制台日志，应该会看到类似如下的消息：

> 跨域请求被阻止：同源策略禁止读取位于 http://localhost:4000/v1/tokens/authentication 的远程资源。（原因：根据 CORS 预检响应中的 `Access-Control-Allow-Headers` 请求头，不允许 `content-type` 请求头）。

![](img/30f9221bfc265d52b544dd595ca099de_667_0.png)

这里有趣的是预检请求的请求头。根据你使用的浏览器不同，它们可能会略有差异，但大致应该像这样：

```
Accept: */*
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.5
Access-Control-Request-Headers: content-type
Access-Control-Request-Method: POST
Cache-Control: no-cache
Connection: keep-alive
Host: localhost:4000
Origin: http://localhost:9000
Pragma: no-cache
Referer: http://localhost:9000/
```

`Origin` 请求头，以及一个 `Access-Control-Request-Method` 请求头。如果这些部分中有任何一项缺失，我们就知道这不是一个预检请求。

一旦我们确定这是一个预检请求，我们需要发送一个 `200 OK` 响应，并附带一些特殊的请求头，让浏览器知道真正的请求是否可以继续。这些请求头是：

- 一个 `Access-Control-Allow-Origin` 响应头，其值反映预检请求的 `Origin` 请求头（和上一章一样）。
- 一个 `Access-Control-Allow-Methods` 请求头，列出可以在对该 URL 的真正的跨域请求中使用的 HTTP 方法。
- 一个 `Access-Control-Allow-Headers` 请求头，列出可以包含在真正的跨域请求中的请求头。

在我们的例子中，我们可以设置以下响应头，以允许 *所有端点* 的跨域请求：

```
Access-Control-Allow-Origin: <reflected trusted origin>
Access-Control-Allow-Methods: OPTIONS, PUT, PATCH, DELETE
Access-Control-Allow-Headers: Authorization, Content-Type
```

**重要：** 在响应预检请求时，不需要在 `Access-Control-Allow-Methods` 请求头中包含 CORS 安全方法 `HEAD`、`GET` 或 `POST`。同样，

> > 也不需要将禁止的或 CORS 安全的请求头包含在 `Access-Control-Allow-Headers` 中。

当 Web 浏览器收到这些请求头时，它会将这些值与它希望在真正的请求中使用的方法和请求头（不区分大小写）进行比较。如果方法或任何请求头不被允许，浏览器就会阻止真正的请求。

## 更新我们的中间件

让我们付诸行动，更新我们的 `enableCORS()` 中间件，使它能够拦截并响应任何预检请求。具体来说，我们想要：

- 1. 在所有响应上设置一个 `Vary: Access-Control-Request-Method` 请求头，因为响应会根据请求中是否存在该请求头而有所不同。
- 2. 检查请求是否是预检跨域请求。如果不是，那么我们应该让请求正常继续。
- 3. 否则，如果它是一个预检跨域请求，那么我们应该按照上面的描述添加 `Access-Control-Allow-Method` 和 `Access-Control-Allow-Headers` 请求头。

继续更新 `cmd/api/middleware.go` 文件，如下所示：

```
File: `cmd/api/middleware.go`
```

```
package main

...

func (app *application) enableCORS(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Header().Add("Vary", "Origin")

        // Add the "Vary: Access-Control-Request-Method" header.
        w.Header().Add("Vary", "Access-Control-Request-Method")

        origin := r.Header.Get("Origin")

        if origin != "" && len(app.config.cors.trustedOrigins) != 0 {
            for i := range app.config.cors.trustedOrigins {
                if origin == app.config.cors.trustedOrigins[i] {
                    w.Header().Set("Access-Control-Allow-Origin", origin)

                    // Check if the request has the HTTP method OPTIONS and
                    // contains the
                    // "Access-Control-Request-Method" header. If it does,
                    // then we treat
                    // it as a preflight request.
                    if r.Method == http.MethodOptions &&
                        r.Header.Get("Access-Control-Request-Method") != "" {
                        // Set the necessary preflight response headers, as
                        // discussed
                        // previously.
                        w.Header().Set("Access-Control-Allow-Methods",
                            "OPTIONS, PUT, PATCH, DELETE")
                        w.Header().Set("Access-Control-Allow-Headers",
                            "Authorization, Content-Type")

                        // Write the headers along with a 200 OK status and
                        // return from
                        // the middleware with no further action.
                        w.WriteHeader(http.StatusOK)
                        return
                    }
                }
            }
        }
    })
}
```

```
pool established"}
{"level":"INFO","time":"2021-04-17T17:23:05Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

然后在浏览器中再次打开 [http://localhost:9000](http://localhost:9000)。这次你应该会看到向 POST `/v1/tokens/authentication` 发起的跨域 `fetch()` 请求成功，并且现在你在响应中会得到一个身份验证令牌。类似于这样：

![](img/30f9221bfc265d52b544dd595ca099de_673_0.png)

**注意：** 如果你查看预检请求的详细信息，应该会看到我们新的 CORS 请求头已经设置在预检响应上，如上图红色箭头所示。

预检缓存，因此如果你返回了错误的请求头，用户将会一直使用这些错误的请求头，直到缓存过期。

如果你想完全禁用缓存，可以将值设置为 `-1`：

```
Access-Control-Max-Age: -1
```

同样重要的是，要知道浏览器可能会对请求头的缓存时间施加一个硬性上限。MDN 文档指出：

- *Firefox 将此上限设为 24 小时（86400 秒）。*
- *Chromium（v76 之前）上限为 10 分钟（600 秒）。*
- *Chromium（从 v76 开始）上限为 2 小时（7200 秒）。*

## 预检通配符

如果你的 API 很复杂或者变化很快，那么为预检响应维护一个硬编码的方法和请求头白名单可能会很麻烦。你可能心想：*我只想允许所有的 HTTP 方法和请求头用于跨域请求。*

在这种情况下，`Access-Control-Allow-Methods` 和 `Access-Control-Allow-Headers` 请求头都允许你使用一个通配符 * 字符，就像这样：

```
Access-Control-Allow-Methods: *
Access-Control-Allow-Headers: *
```

但使用这些通配符有一些重要的注意事项：

- 目前只有 74% 的浏览器支持这些请求头中的通配符。任何不支持它们的浏览器都会阻止预检请求。
- `Authorization` 请求头不能使用通配符。相反，你需要在请求头中显式地包含它，比如 `Access-Control-Allow-Headers: Authorization, *`。
- 带凭证的请求（带有 cookie 或 HTTP 基本认证的请求）不支持通配符。对于这些请求，`*` 字符将被视为字面字符串 `"*"`，而不是通配符。





## 指标

当你的应用程序在生产环境中运行并承受真实流量时——或者你在进行有针对性的负载测试时——你可能会希望深入了解它的运行情况以及资源使用情况。

例如，你可能想回答这样一些问题：

- 我的应用程序使用了多少内存？这个数字随时间如何变化？
- 当前有多少个 goroutine 在使用中？这个数字随时间如何变化？
- 有多少数据库连接正在使用，有多少处于空闲状态？我需要调整连接池设置吗？
- 成功 HTTP 响应与客户端及服务器错误的比率是多少？错误率是否高于正常水平？

深入了解这些信息可以帮助你做出硬件和配置设置方面的选择，并作为潜在问题（如内存泄漏）的早期预警信号。

为了协助实现这一点，Go 的标准库包含了 `expvar` 包，它使你在运行时轻松整理和查看不同的应用程序指标。

在本节中你将学习：

```
)

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
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.requirePermission("movies:write", app.deleteMovieHandler))

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication",
app.createAuthenticationTokenHandler)

    // 注册一个新的 GET /debug/vars 端点，指向 expvar 处理器。
    router.Handler(http.MethodGet, "/debug/vars", expvar.Handler())

    return
app.recoverPanic(app.enableCORS(app.rateLimit(app.authenticate(router))))
}
```

![](img/30f9221bfc265d52b544dd595ca099de_682_0.png)

我们可以看到，这里的 JSON 当前包含两个顶级条目："`cmdline`" 和 "`memstats`"。让我们快速讨论一下它们代表什么。

"`cmdline`" 条目包含一个用于运行应用程序的命令行参数数组，以程序名开头。这本质上是对 `os.Args` 变量的 JSON 表示，如果你想知道启动应用程序时使用了哪些非默认设置，它会很有用。

"`memstats`" 条目包含内存使用情况的“瞬间”快照，由 `runtime.MemStats()` 函数返回。所有值的文档和描述可以在这里找到，但最重要的有：

## 创建自定义指标

expvar 处理器暴露的默认信息是一个好的开始，但我们还可以通过在 JSON 响应中暴露一些额外的自定义指标来使它更有用。

为了说明这一点，我们将从非常简单的开始，首先在 JSON 中暴露我们的应用程序版本号。如果你不记得的话，版本号当前在主文件 main.go 中被定义为字符串常量 "1.0.0"。

实现这一点的代码分为两个基本步骤：首先我们需要向 expvar 包注册一个自定义变量，然后我们需要为这个变量本身设置值。用一行代码来表示，大致如下：

```
expvar.NewString("version").Set(version)
```

第一部分——expvar.NewString("version")——创建一个新的 expvar.String 类型，然后发布它，使其以 "version" 的名称出现在 expvar 处理器的 JSON 响应中，然后返回一个指向它的指针。接着我们使用它的 Set() 方法来给这个指针分配一个实际的值。

还有另外两件事需要注意：

```
...

func main() {
    ...

    // 在 expvar 处理器中发布一个新的 "version" 变量，包含我们的应用程序
    // 版本号（当前为常量 "1.0.0"）。
    expvar.NewString("version").Set(version)

    app := &application{
        config: cfg,
        logger: logger,
        models: data.NewModels(db),
        mailer: mailer.New(cfg.smtp.host, cfg.smtp.port, cfg.smtp.username,
    cfg.smtp.password, cfg.smtp.sender),
    }

    err = app.serve()
    if err != nil {
        logger.PrintFatal(err, nil)
    }
}

...
```

如果你重启 API 并在浏览器中再次访问 http://localhost:4000/debug/vars，你现在应该能在 JSON 中看到一个 "version": "1.0.0" 条目。

类似于这样：

![](img/30f9221bfc265d52b544dd595ca099de_687_0.png)

> **注意：** 在上面的代码中，我们使用了 `expvar.NewString()` 函数来在 `expvar` 处理器中注册并发布一个字符串。但 Go 还提供了其他几种常见数据类型的函数：`NewFloat()`、`NewInt()` 和 `NewMap()`。所有这些函数的工作方式都非常相似，我们将在下一章中使用它们。

## 动态指标

有时候，你可能需要调用其他代码——或进行某种预处理——来生成必要的信息才能发布指标。为了帮助实现这一点，有一个

```
File: cmd/api/main.go

package main

import (
    "context"
    "database/sql"
    "expvar"
    "flag"
    "os"
    "runtime" // 新增导入
    "strings"
    "sync"
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/jsonlog"
    "greenlight.alexedwards.net/internal/mailer"

    _ "github.com/lib/pq"
)

...

func main() {
    ...

    expvar.NewString("version").Set(version)

    // 发布当前活跃的 goroutine 数量。
    expvar.Publish("goroutines", expvar.Func(func() interface{} {
        return runtime.NumGoroutine()
    }))

    // 发布数据库连接池的统计信息。
    expvar.Publish("database", expvar.Func(func() interface{} {
        return db.Stats()
    }))

```

![](img/30f9221bfc265d52b544dd595ca099de_691_0.png)

在我的例子中，我可以看到应用程序当前有 8 个活跃的 goroutine，数据库连接池处于“初始”状态，目前只有一个空闲连接（这是我们的代码在启动时调用 `db.PingContext()` 时创建的）。

如果你愿意，你可以使用像 `hey` 这样的工具来向你的应用程序生成一些请求，看看这些数字在负载下如何变化。例如，你可以向 `POST /v1/tokens/authentication` 端点发送一批请求（该端点较慢且开销较大，因为它要检查 bcrypt 哈希密码），如下所示：

```
$ BODY='{"email": "alice@example.com", "password": "pa55word"}'
$ hey -d "$BODY" -m "POST" http://localhost:4000/v1/tokens/authentication
```

```
Status code distribution:
[201] 200 responses
```

> **重要提示：** 在运行此命令之前，请确保你的 API 已通过 `-limiter-enabled=false` 命令行标志关闭了速率限制器，否则 `hey` 工具将会收到大量 `429 Too Many Requests` 响应。

如果你在 `hey` 工具运行期间访问 `GET /debug/vars` 端点，你应该会看到你的应用程序指标现在看起来大不相同了：

![](img/30f9221bfc265d52b544dd595ca099de_693_0.png)

## 请求级指标

在本章中，我们将创建一些新的中间件，为我们的应用程序记录自定义的*请求级*指标。我们将从记录以下三件事开始：

- 接收到的请求总数。
- 发送的响应总数。
- 处理所有请求所用的总（累积）时间，以微秒为单位。

所有这些值都是整数，因此我们将能够使用 `expvar.NewInt()` 函数将这些指标注册到 `expvar` 包中。

让我们直接进入代码，创建一个新的 `metrics()` 中间件方法，它初始化必要的 `expvar` 变量，然后在我们每次处理请求时更新它们。如下所示：

```
File: cmd/api/middleware.go

package main

import (
    "errors"
    "expvar" // 新增导入
    "fmt"
)
```




```go
"net"
"net/http"
"strings"
"sync"
"time"

"greenlight.alexedwards.net/internal/data"
"greenlight.alexedwards.net/internal/validator"

"golang.org/x/time/rate"
)
...
```

func (app *application) metrics(next http.Handler) http.Handler {
    // Initialize the new expvar variables when the middleware chain is first built.
    totalRequestsReceived := expvar.NewInt("total_requests_received")
    totalResponsesSent := expvar.NewInt("total_responses_sent")
    totalProcessingTimeMicroseconds :=
    expvar.NewInt("total_processing_time_us")

    // The following code will be run for every request...
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Record the time that we started to process the request.
        start := time.Now()

        // Use the Add() method to increment the number of requests received by 1.
        totalRequestsReceived.Add(1)

        // Call the next handler in the chain.
        next.ServeHTTP(w, r)

        // On the way back up the middleware chain, increment the number of responses
        // sent by 1.
        totalResponsesSent.Add(1)
```
```go
// Calculate the number of microseconds since we began to process the
request,
    // then increment the total processing time by this amount.
    duration := time.Now().Sub(start).Microseconds()
    totalProcessingTimeMicroseconds.Add(duration)
})
}
```

完成之后，我们需要更新 `cmd/api/routes.go` 文件以包含新的 `metrics()` 中间件，放在链的开头。如下所示：

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

    router.HandlerFunc(http.MethodGet, "/v1/movies",
    app.requirePermission("movies:read", app.listMoviesHandler))
    router.HandlerFunc(http.MethodPost, "/v1/movies",
    app.requirePermission("movies:write", app.createMovieHandler))
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
    app.requirePermission("movies:read", app.showMovieHandler))
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
```
```
app.requirePermission("movies:write", app.updateMovieHandler))
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.requirePermission("movies:write", app.deleteMovieHandler))

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication",
app.createAuthenticationTokenHandler)

    router.Handler(http.MethodGet, "/debug/vars", expvar.Handler())

    // Use the new metrics() middleware at the start of the chain.
    return
app.metrics(app.recoverPanic(app.enableCORS(app.rateLimit(app.authenticate(router)))))
}
```

好的，让我们试试。继续运行 API，但这次禁用速率限制：

```
$ go run ./cmd/api -limiter-enabled=false
{"level":"INFO","time":"2021-04-18T09:06:05Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T09:06:05Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

当你在浏览器中访问 localhost:4000/debug/vars 时，你现在应该会看到 JSON 响应中包含了以下项目：

![](img/30f9221bfc265d52b544dd595ca099de_702_0.png)

让我们在负载下试试，并再次使用 hey 向 POST /v1/tokens/authentication 端点发送一些请求。

首先重新启动 API：

```
$ go run ./cmd/api -limiter-enabled=false
{"level":"INFO","time":"2021-04-18T09:18:36Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T09:18:36Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

然后使用 hey 生成负载，如下所示：

```
DNS-lookup: 0.0005 secs, 0.0000 secs, 0.0047 secs
req write: 0.0001 secs, 0.0000 secs, 0.0012 secs
resp wait: 2.4293 secs, 1.6787 secs, 3.0293 secs
resp read: 0.0000 secs, 0.0000 secs, 0.0001 secs

Status code distribution:
  [201] 200 responses
```

完成后，如果你在浏览器中刷新 `localhost:4000/debug/vars`，你的指标现在应该看起来像这样：

![](img/30f9221bfc265d52b544dd595ca099de_704_0.png)

根据 `total_processing_time_us` 和 `total_responses_sent` 的值，我们可以计算出每个请求的平均处理时间约为 2.4 秒

（请记住，此端点故意设计得很慢且计算成本高，因为我们需要验证 bcrypt 加密的用户密码。）

```
481455830 µs / 201 reqs = 2395303 µs/req = 2.4 s/req
```

这与 `hey` 的结果摘要中显示的数据一致，后者给出的平均响应时间为 2.4302 秒。`hey` 的数据是完整往返时间，因此它总是会稍高一些，因为它包含了网络延迟以及 `http.Server` 处理请求所需的时间。

## 附加信息

### 计算额外指标

基于 `GET` `/debug/vars` 响应中的这些信息，你还可以推导出一些额外的有趣指标。例如...

- 正在进行的“活动”请求数：

```
total_requests_received - total_responses_sent
```

- 每秒接收到的平均请求数（在对 `GET /debug/vars` 端点的 A 次调用和 B 次调用之间）：
- 每个请求的平均处理时间（在对 `GET /debug/vars` 端点的 A 次调用和 B 次调用之间）：

```
(total_requests_received_B - total_requests_received_A) / (timestamp_B - timestamp_A)
```

```
(total_processing_time_us_B - total_processing_time_us_A) /
(total_requests_received_B - total_requests_received_A)
```

## 记录 HTTP 状态码

除了记录发送的响应的总数外，我们还可以更进一步，扩展我们的 `metrics()` 中间件，以开始统计我们的响应具体有哪些 HTTP 状态码。

这样做的棘手之处在于在我们的 `metrics()` 中间件中找出 *响应具有什么 HTTP 状态码*。不幸的是，Go 并没有让这变得容易——没有内置的方法可以检查 `http.ResponseWriter` 以查看将发送给客户端的状态码。

事实上的变通方法是创建你自己的 `http.ResponseWriter` 自定义实现，该实现记录 HTTP 状态码的副本以供将来访问。但这样做可能相当脆弱且笨拙——有几个边缘情况需要警惕，并且如果使用任何“额外”的 ResponseWriter 接口（如 `http.Flusher` 和 `http.Hijacker`）可能会导致问题。

而不是自己制作自定义的 `http.ResponseWriter` 实现，我强烈推荐使用第三方 `httpsnoop` 包。它小巧专注，没有额外的依赖，并且可以非常轻松地记录每个响应的 HTTP 状态码和大小，以及每个请求的总体处理时间。

如果你跟着做，请继续下载它，如下所示：

// the cumulative processing time.
    totalProcessingTimeMicroseconds.Add(metrics.Duration.Microseconds())

    // Use the Add() method to increment the count for the given status code by 1.
    // Note that the expvar map is string-keyed, so we need to use the strconv.Itoa()
    // function to convert the status code (which is an integer) to a string.
    totalResponsesSentByStatus.Add(strconv.Itoa(metrics.Code), 1)
  })
}
```

好吧，让我们试试。再次运行 API，但这次 *保持速率限制启用*。如下所示：

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-18T10:09:09Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T10:09:09Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

然后再次使用 hey 对 POST /v1/tokens/authentication 端点生成一些负载。这应该会导致少量成功的 201 Created 响应，但由于触发了速率限制，会有更多 429 Too Many Requests 响应。

```
$ BODY='{"email": "alice@example.com", "password": "pa55word"}'
$ hey -d "$BODY" -m "POST" http://localhost:4000/v1/tokens/authentication
```



## 第 20 章. 构建、版本控制和质量控制

本书的这一部分我们将把关注点从编写代码转移到 *管理与维护* 项目上，并采取措施帮助自动化常见任务并为 API 部署做准备。

具体来说，你将学习如何：

- 使用 makefile 自动化项目中的常见任务，例如创建和执行迁移。
- 使用 `go vet` 和 `staticcheck` 工具对代码进行质量控制检查。
- 引入第三方包，以防它们将来不可用。
- 构建并运行应用程序的可执行二进制文件，减少其大小，并为不同平台交叉编译二进制文件。
- 在构建二进制文件时将版本号和构建时间嵌入到应用程序中。
- 利用 Git 在构建过程中生成自动版本号。

```
> choco install make
```

### 一个简单的 makefile

现在 make 工具已安装在你的系统上，让我们创建 makefile 的第一个迭代。我们先从简单开始，然后逐步构建。

makefile 本质上是一个文本文件，其中包含一个或多个 make 工具可以运行的规则。每个规则都有一个目标，并包含一个按顺序执行的命令序列，当规则运行时会执行这些命令。一般来说，makefile 规则具有以下结构：

```
# comment (optional)
target:
	command
	command
	...
```

**重要：** 请注意 makefile 规则中的每个命令都必须以制表符字符开头，**而不是空格**。如果你恰好以 PDF 格式阅读本文，片段中制表符会显示为单个空格字符，但请确保在自己的代码中使用制表符字符。

如果你一直跟着做，你应该已经在项目目录的根部有一个空的 `Makefile`。让我们开始创建一个执行 `go run ./cmd/api` 命令来运行我们的 API 应用程序的规则。像这样：

```
File: Makefile

run:
	go run ./cmd/api
```

确保 `Makefile` 已保存，然后你可以通过从终端运行 `$ make <target>` 来执行特定的规则。

让我们继续调用 `make run` 来启动 API：

```
$ make run
go run ./cmd/api
{"level":"INFO","time":"2021-04-18T10:38:26Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T10:38:26Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

太好了，运行成功。当我们输入 `make run` 时，make 工具会在当前目录中查找名为 `Makefile` 或 `makefile` 的文件，然后执行与 `run` 目标关联的命令。

需要指出的一点是——默认情况下 `make` 会在终端输出中回显命令。我们可以在上面的代码中看到这一点，其中输出的第一行是回显的命令 `go run ./cmd/api`。如果你愿意，可以通过在命令前加上 `@` 字符来禁止回显命令。

### 环境变量

当我们执行一个 `make` 规则时，在 make 启动时可用的每个环境变量都会被转换为具有相同名称和值的 *make 变量*。然后我们可以使用 `${VARIABLE_NAME}` 语法在 makefile 中访问这些变量。

为了说明这一点，让我们创建两个额外的规则——用于连接数据库的 `psql` 规则和用于执行数据库迁移的 `up` 规则。如果你一直跟着做，这两个规则都需要访问来自你的 `GREENLIGHT_DB_DSN` 环境变量的数据库 DSN 值。

继续更新你的 `Makefile` 以包含这两个新规则，如下所示：

```
File: Makefile

run:
	go run ./cmd/api

psql:
	psql ${GREENLIGHT_DB_DSN}

up:
	@echo 'Running up migrations...'
	migrate -path ./migrations -database ${GREENLIGHT_DB_DSN} up
```

注意这里我们在 up 规则中使用了 @ 字符，以防止 echo 命令本身在运行时被回显。

好吧，让我们通过运行 `make up` 来执行数据库迁移试试：

```
$ make up
Running up migrations...
migrate -path ./migrations -database postgres://greenlight:pa55word@localhost/greenlight up
no change
```

你应该能从这里的输出中看到，你的 `GREENLIGHT_DB_DSN` 环境变量的值已成功传递并在 make 规则中使用。如果你一直跟着做，不应该有待应用的迁移，因此它应该成功退出且无进一步操作。

我们在这里也开始看到使用 makefile 的好处——能够输入 `make up` 比记住并使用执行 ‘up’ 迁移的完整命令要好得多。

```
psql:
	psql ${GREENLIGHT_DB_DSN}

migration:
	@echo 'Creating migration files for ${name}...'
	migrate create -seq -ext=.sql -dir=./migrations ${name}

up:
	@echo 'Running up migrations...'
	migrate -path ./migrations -database ${GREENLIGHT_DB_DSN} up
```

如果你使用 `name=create_example_table` 参数执行此新规则，你应该会看到以下输出：

```
$ make migration name=create_example_table
Creating migration files for create_example_table ...
migrate create -seq -ext=.sql -dir=./migrations create_example_table
/home/alex/Projects/greenlight/migrations/000007_create_example_table.up.sql
/home/alex/Projects/greenlight/migrations/000007_create_example_table.down.sql
```

你现在在 migrations 文件夹中还会有两个名为 `create_example_table` 的空迁移文件。像这样：

```
$ ls ./migrations/
000001_create_movies_table.down.sql
000001_create_movies_table.up.sql
000002_add_movies_check_constraints.down.sql
000002_add_movies_check_constraints.up.sql
000003_add_movies_indexes.down.sql
000003_add_movies_indexes.up.sql
000004_create_users_table.down.sql
000004_create_users_table.up.sql
000005_create_tokens_table.down.sql
000005_create_tokens_table.up.sql
000006_add_permissions.down.sql
000006_add_permissions.up.sql
000007_create_example_table.down.sql
000007_create_example_table.up.sql
```

如果你跟着做，我们实际上不会使用这两个新的迁移文件，所以请随意删除它们：

```
$ rm migrations/000007*
```

**注意：** makefile 中的变量名区分大小写，因此 `foo`、`FOO` 和 `Foo` 都引用不同的变量。`make` 文档建议对仅在 makefile 中用于内部目的的变量名使用小写字母，而在其他情况下使用大写变量名。

### 命名空间化目标

随着 makefile 的不断增长，你可能想要开始 *命名空间化* 你的目标名称，以在规则之间提供一些区分并帮助组织文件。例如，在一个大型 makefile 中，与其使用目标名称 `up`，不如将其命名为 `db/migrations/up` 更清晰。

我建议使用 `/` 字符作为命名空间分隔符，而不是句点、连字符或 `:` 字符。事实上，`:` 字符应严格避免在目标名称中使用，因为它在使用 *目标先决条件* 时可能会导致问题（我们稍后会介绍）。

让我们更新我们的目标名称以使用一些合理的命名空间，如下所示：

```make
File: Makefile

run/api:
	go run ./cmd/api

db/psql:
	psql ${GREENLIGHT_DB_DSN}

db/migrations/new:
	@echo 'Creating migration files for ${name}...'
	migrate create -seq -ext=.sql -dir=./migrations ${name}

db/migrations/up:
	@echo 'Running up migrations...'
	migrate -path ./migrations -database ${GREENLIGHT_DB_DSN} up
```

你应该能够通过在运行 `make` 时输入完整的目标名称来执行规则。例如：

```bash
$ make run/api
go run ./cmd/api
{
  "level": "INFO",
  "time": "2021-04-18T10:50:23Z",
  "message": "database connection pool established"
}
{
  "level": "INFO",
  "time": "2021-04-18T10:50:23Z",
  "message": "starting server",
  "properties": {"addr": ":4000", "env": "development"}
}
```

使用 `/` 字符作为命名空间分隔符的一个不错的特性是，你可以在终端输入目标名称时获得制表符补全。例如，如果你输入 `make db/migrations/` 然后按键盘上的制表键，该命名空间下的剩余目标将被列出。像这样：

```
$ make db/migrations/
new  up
```

### 先决条件目标和请求确认

我在本章开头给出的 makefile 规则的通用语法是一个轻微的简化，因为也可以指定 *先决条件* 目标。

```
target: prerequisite-target-1 prerequisite-target-2 ...
	command
	command
	...
```



当你为规则指定先决条件目标时，对应先决条件目标的命令将在执行实际目标命令*之前*运行。

利用此功能在执行我们的 `db/migrations/up` 规则*之前*向用户请求*确认继续*。

为此，我们将创建一个新的 `confirm` 目标，它会询问用户 `Are you sure? [y/N]`，如果未输入 `y` 则以错误退出。然后我们将把这个新的 `confirm` 目标用作 `db/migrations/up` 的先决条件。

继续按如下方式更新你的 `Makefile`：

```
File: Makefile

# Create the new confirm target.
confirm:
    @echo -n 'Are you sure? [y/N] ' && read ans && [ ${ans:-N} = y ]

run/api:
    go run ./cmd/api

db/psql:
    psql ${GREENLIGHT_DB_DSN}

db/migrations/new:
    @echo 'Creating migration files for ${name}...'
    migrate create -seq -ext=.sql -dir=./migrations ${name}

# Include it as prerequisite.
db/migrations/up: confirm
```

相比之下，让我们再次尝试同样的操作，但在请求确认时输入其他字母。这次，`make` 应该在*不*执行 `db/migrations/up` 规则中的任何内容的情况下退出。示例如下：

```
$ make db/migrations/up
Are you sure? [y/N] n
make: *** [Makefile:3: confirm] Error 1
```

像这样将 `confirm` 规则用作先决条件目标是一个非常不错的可复用模式。只要你有一个会执行破坏性或危险操作的 makefile 规则，现在就可以直接将 `confirm` 包含为先决条件目标来向用户请求确认继续。

## 显示帮助信息

我们可以做的一件小事来让 makefile 更友好，就是加入一些注释和帮助功能。具体来说，我们将为 makefile 中的每个规则加上以下格式的注释：

```
## <example target call>: <help text>
```

然后我们将创建一个新的 `help` 规则，它会解析 makefile 本身，使用 `sed` 从注释中提取帮助文本，将其格式化为表格然后显示给用户。

如果你在跟随操作，请继续更新你的 Makefile，使其看起来像这样：

```
File: Makefile

## help: print this help message
help:
    @echo 'Usage:'
    @sed -n 's/^##//p' ${MAKEFILE_LIST} | column -t -s ':' |  sed -e 's/^/ /'

confirm:
    @echo -n 'Are you sure? [y/N] ' && read ans && [ ${ans:-N} = y ]

## run/api: run the cmd/api application
run/api:
    go run ./cmd/api

## db/psql: connect to the database using psql
db/psql:
    psql ${GREENLIGHT_DB_DSN}

## db/migrations/new name=$1: create a new database migration
db/migrations/new:
    @echo 'Creating migration files for ${name}...'
    migrate create -seq -ext=.sql -dir=./migrations ${name}

## db/migrations/up: apply all up database migrations
db/migrations/up: confirm
    @echo 'Running up migrations...'
    migrate -path ./migrations -database ${GREENLIGHT_DB_DSN} up
```

> **注意：** `MAKEFILE_LIST` 是一个特殊变量，其中包含 `make` 正在解析的 makefile 的名称。

如果现在执行 `help` 目标，你应该会得到一个列出所有可用目标及其对应帮助文本的响应。类似于这样：

```
$ make help
Usage:
  help                          print this help message
  run/api                       run the cmd/api application
  db/psql                       connect to the database using psql
  db/migrations/new name=$1     create a new database migration
  db/migrations/up              apply all up database migrations
```

我还应指出，将 `help` 规则放在 `Makefile` 的最前面是有意为之的。如果你运行 `make` 而不*指定目标*，它将默认执行文件中的第一个规则。

因此，这意味着如果你尝试在不指定目标的情况下运行 `make`，现在会显示帮助信息，如下所示：

```
$ make
Usage:
  help                          print this help message
  run/api                       run the cmd/api application
  db/psql                       connect to the database using psql
```

| db/migrations/new name=$1 | 创建新的数据库迁移 |
| db/migrations/up | 应用所有上行数据库迁移 |

## 伪目标

在本章中，我们一直使用 `make` 来执行*操作*，但 `make` 的另一个而且可以说主要是用途是帮助在磁盘上创建文件，其中*目标名称是文件名称*由规则创建。

如果你主要像我们一样使用 `make` 来执行操作，那么如果项目目录中存在*与目标名称相同的路径*的文件，就会产生问题。

如果你愿意，可以通过在项目目录根部创建一个名为 `./run/api` 的文件来演示此问题，如下所示：

```bash
$ mkdir run && touch run/api
```

然后如果你执行 `make run/api`，而不是启动我们的 API 应用程序，你会得到以下消息：

```bash
$ make run/api
make: 'run/api' is up to date.
```

因为磁盘上已经存在 `./run/api` 文件，`make` 工具认为该规则已经执行过，因此返回我们上面看到的消息而不采取任何进一步操作。

为了解决这个问题，我们可以将 makefile 目标声明为伪目标：

> 伪目标并不是真正的文件名；它只是一个用于执行的规则的名称。

要将目标声明为伪目标，可以将其设为特殊 `.PHONY` 目标的先决条件。语法如下所示：

```
.PHONY: target
target: prerequisite-target-1 prerequisite-target-2 ...
    command
    command
    ...
```

让我们继续更新我们的 `Makefile`，使所有规则都有伪目标，如下所示：

```
File: Makefile

## help: print this help message
.PHONY: help
help:
    @echo 'Usage:'
    @sed -n 's/^##//p' ${MAKEFILE_LIST} | column -t -s ':' | sed -e 's/^/ /'
```

你可能会认为只有在文件名冲突时才需要将目标声明为伪目标，但在实践中*在目标实际上是伪目标时未将其声明为伪目标*可能导致错误或令人困惑的行为。例如，想象一下将来有人在项目目录根部不知情地创建了一个名为 `confirm` 的文件。这意味着我们的 `confirm` 规则永远不会被执行，进而会导致危险或破坏性规则在未经确认的情况下被执行。

为了避免此类错误，如果你有一个执行操作而不是创建文件的 makefile 规则，最好养成将其声明为伪目标的习惯。

如果你在跟随操作，可以继续删除我们刚刚创建的 `run` 目录的内容。如下所示：

```bash
$ rm -rf run/
```

总的来说，这进展得不错。我们的 makefile 开始包含一些有用的功能，我们将在本书接下来的几章中继续添加更多功能。

尽管这是我们在本次构建中做的最后几件事之一，但在开始项目时在项目目录根部创建 makefile 通常是我做的*第一*件事。我发现使用 makefile 处理常见任务有助于在开发过程中节省打字和思维开销，而且——从长远来看——它在你长时间中断后返回项目时充当有用的入口点和提醒，说明事物的工作方式。

相反，我们可以更新 makefile，以便将 `GREENLIGHT_DB_DSN` 环境变量中的 DSN 值作为规则的一部分传入。如果你在跟随操作，请继续按如下方式更新 `run/api` 规则：

```
File: Makefile

...

## run/api: run the cmd/api application
.PHONY: run/api
run/api:
    go run ./cmd/api -db-dsn=${GREENLIGHT_DB_DSN}

...
```

这是一个小的改动，但非常不错，因为它意味着*我们应用程序的默认配置值不再取决于运行环境*。在运行时传递的命令行标志值是我们配置应用程序设置的*唯一*机制，并且项目文件中仍然没有硬编码的机密信息。

在开发期间运行我们的应用程序仍然很方便——我们只需要输入 `make run/api`，如下所示：

```
$ make run/api
go run ./cmd/api -db-dsn=postgres://greenlight:pa55word@localhost/greenlight
```

{"level":"INFO","time":"2021-04-18T11:17:49Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T11:17:49Z","message":"starting server","properties":{"addr":":4000","env":"development"}}

**提示：** 如果你不喜欢在输入 `make run/api` 时 DSN 值（包含密码）显示在屏幕上，请记住，你可以在 makefile 中使用 `@` 字符来抑制该命令的回显。

## 使用 .envrc 文件

如果你愿意，也可以*移除* `$HOME/.profile` 或 `$HOME/.bashrc` 文件中的 `GREENLIGHT_DB_DSN` 环境变量，改为将其存储在项目根目录下的 `.envrc` 文件中。

如果你在跟着操作，请创建一个新的 `.envrc` 文件，如下所示：

```
$ touch .envrc
```

```
File: .envrc

export GREENLIGHT_DB_DSN=postgres://greenlight:pa55word@localhost/greenlight
```

然后，你可以使用像 `direnv` 这样的工具自动将 `.envrc` 文件中的变量加载到当前 shell 中，或者，你也可以在 `Makefile` 顶部添加一条 `include` 命令来加载它们。就像这样：

```
File: Makefile

# Include variables from the .envrc file
include .envrc

## help: print this help message
.PHONY: help
help:
    @echo 'Usage:'
    @sed -n 's/^##//p' ${MAKEFILE_LIST} | column -t -s ':' | sed -e 's/^/ /'
...
```

这种方法在需要频繁修改环境变量的项目中特别方便，因为这意味着你只需编辑 `.envrc` 文件，而无需在每次更改后重启计算机或运行 `source`。

这种方法的另一个好处是，如果你在同一台机器上处理多个项目，它可以在变量之间提供一定程度的隔离。

**重要：** 如果你使用这种方法，并且你的 `.envrc` 文件包含任何机密信息，你必须小心不要将该文件提交到版本控制系统（如 Git 或 Mercurial）。

在几个章节后，我们将开始使用 Git 对代码库进行版本控制，所以让我们先发制人地添加一条忽略规则，确保 `.envrc` 文件永远不会被提交。

```
$ echo '.envrc' >> .gitignore
```

## 代码质量控制

在本章中，我们将重点向 `Makefile` 添加一个 `audit` 规则，以自动检查、测试和整理我们的代码库。具体来说，该规则将：

- 使用 `go mod tidy` 命令，从 `go.mod` 和 `go.sum` 文件中剪除任何未使用的依赖，并添加任何缺失的依赖。
- 使用 `go mod verify` 命令，检查你计算机上的依赖（位于你的模块缓存中，即 `$GOPATH/pkg/mod`）在下载后是否未被更改，以及它们是否与 `go.sum` 文件中的加密哈希匹配。运行此命令有助于确保所使用依赖确实是你期望的确切版本。
- 使用 `go fmt ./...` 命令，按照 Go 标准格式化项目目录中的所有 `.go` 文件。这将“就地”重新格式化文件，并输出任何已更改文件的名称。
- 使用 `go vet ./...` 命令检查项目目录中的所有 `.go` 文件。`go vet` 工具运行各种*分析器*，对你的代码执行静态分析，并警告你可能存在问题但编译器无法发现的内容——例如不可达代码、不必要的赋值和格式错误的构建标签。
- 使用 `go test -race -vet=off ./...` 命令运行项目目录中的所有测试。默认情况下，`go test` 在运行任何测试之前会自动执行一小部分 `go vet` 检查，因此为了避免重复，我们将使用 `-vet=off` 标志将其关闭。`-race` 标志启用 Go 的[竞态检测器](#)，这有助于在测试运行期间发现某些类别的竞态条件。
- 使用第三方 `staticcheck` 工具执行一些额外的[静态分析检查](#)。

如果你在跟着操作，此时你需要在你的机器上安装 `staticcheck` 工具。最简单的方法是运行 `go install` 命令，如下所示：

```shell
$ go install honnef.co/go/tools/cmd/staticcheck@latest
go: downloading honnef.co/go/tools v0.1.3
go: downloading golang.org/x/tools v0.1.0
go: downloading github.com/BurntSushi/toml v0.3.1
go: downloading golang.org/x/sys v0.0.0-20210119212857-b64e53b001e4
go: downloading golang.org/x/xerrors v0.0.0-20200804184101-5ec99f83aff1
go: downloading golang.org/x/mod v0.3.0
$ which staticcheck
/home/alex/go/bin/staticcheck
```

> **注意：** 如果 `which` 命令没有找到任何内容，请检查你的 `$GOPATH/bin` 目录是否在你的系统路径中。如果你不确定 `$GOPATH` 目录在哪里，可以在终端中运行 `go env GOPATH` 来查看。

安装完成后，让我们继续在 makefile 中创建一个新的 audit 规则。与此同时，我们还要添加一些注释块，以帮助组织并阐明我们不同的 makefile 规则的目的，如下所示：

```
File: Makefile

include .envrc

#
================================================================================
====== #
# HELPERS
#
================================================================================
====== #

## help: print this help message
.PHONY: help
help:
    @echo 'Usage:'
    @sed -n 's/^##//p' ${MAKEFILE_LIST} | column -t -s ':' |  sed -e 's/^/ /'

.PHONY: confirm
confirm:
    @echo -n 'Are you sure? [y/N] ' && read ans && [ $${ans:-N} = y ]

#
================================================================================
====== #
# DEVELOPMENT
#
================================================================================
====== #
```

```
## run/api: run the cmd/api application
.PHONY: run/api
run/api:
    go run ./cmd/api -db-dsn=${GREENLIGHT_DB_DSN}

## db/psql: connect to the database using psql
.PHONY: db/psql
db/psql:
    psql ${GREENLIGHT_DB_DSN}

## db/migrations/new name=$1: create a new database migration
.PHONY: db/migrations/new
db/migrations/new:
    @echo 'Creating migration files for ${name}...'
    migrate create -seq -ext=.sql -dir=./migrations ${name}

## db/migrations/up: apply all up database migrations
.PHONY: db/migrations/up
db/migrations/up: confirm
    @echo 'Running up migrations...'
    migrate -path ./migrations -database ${GREENLIGHT_DB_DSN} up

#
================================================================================
====== #
# QUALITY CONTROL
#
================================================================================
====== #

## audit: tidy dependencies and format, vet and test all code
.PHONY: audit
audit:
    @echo 'Tidying and verifying module dependencies...'
    go mod tidy
    go mod verify
    @echo 'Formatting code...'
    go fmt ./...
```

```
@echo 'Vetting code...'
go vet ./...
staticcheck ./...
@echo 'Running tests...'
go test -race -vet=off ./...
```

现在完成了，你所需要做的就是在将任何代码更改提交到版本控制系统或构建任何二进制文件之前，输入 make audit 来运行这些检查。

让我们试一试。如果你一直在仔细跟着操作，输出应该与以下内容非常相似：

```
$ make audit
Tidying and verifying module dependencies...
go mod tidy
go: finding module for package gopkg.in/mail.v2
go: downloading gopkg.in/mail.v2 v2.3.1
go: found gopkg.in/mail.v2 in gopkg.in/mail.v2 v2.3.1
go mod verify
all modules verified
Formatting code...
go fmt ./...
Vetting code...
go vet ./...
staticcheck ./...
Running tests...
go test -race -vet=off ./...
?       greenlight.alexedwards.net/cmd/api          [no test files]
?       greenlight.alexedwards.net/cmd/examples/cors/preflight  [no test files]
?       greenlight.alexedwards.net/cmd/examples/cors/simple      [no test files]
?       greenlight.alexedwards.net/internal/data          [no test files]
```

```
?  greenlight.alexedwards.net/internal/jsonlog  [no test files]
?  greenlight.alexedwards.net/internal/mailer  [no test files]
?  greenlight.alexedwards.net/internal/validator  [no test files]
```

看起来不错。`go mod tidy` 命令导致需要下载一些额外的包，但除此之外，所有检查都顺利完成，没有问题。

## 附加信息

## 测试

我们在第一本 *Let's Go* 书中非常详细地讨论了测试主题，同样的原则在这里也适用。如果你愿意，可以随时重新阅读 *Let's Go* 的测试章节，并在你的 API 中重新实现一些相同的模式。例如，你可能想尝试：

- 为 `GET /v1/healthcheck` 端点创建一个端到端测试，以验证响应头和响应体是否符合预期。
- 为 `rateLimit()` 中间件创建一个单元测试，以确认它在一定数量的请求后发送 `429 Too Many Requests` 响应。
- 使用测试数据库实例创建一个端到端集成测试，该测试确认 `authenticate()` 和


`requirePermission()` 中间件能正确协同工作，以允许或拒绝访问特定端点。

## 模块代理与依赖本地化（Vendoring）

在 Go 代码中使用第三方包的一个风险是，包仓库可能不再可用。例如，`httprouter` 包在我们的应用程序中扮演着核心角色，如果作者决定从 GitHub 上删除它，我们将不得不手忙脚乱地寻找替代品。

（我并不是说 `httprouter` 会发生这种情况——只是用它举例！）

幸运的是，Go 提供了两种方法可以降低这种风险：*模块代理和依赖本地化（vendoring）*。

### 模块代理

从版本 1.13 开始，Go 默认支持*模块代理*（也称为*模块镜像*）。这些服务会从原始权威仓库（例如 GitHub、GitLab 或 Bitbucket 上的仓库）镜像源代码。

在机器上运行 `go env` 命令，可以打印 Go 操作环境的设置。输出应该类似这样：

```
$ go env
GO111MODULE=""
GOARCH="amd64"
GOBIN=""
GOCACHE="/home/alex/.cache/go-build"
GOENV="/home/alex/.config/go/env"
GOEXE=""
GOFLAGS=""
GOHOSTARCH="amd64"
GOHOSTOS="linux"
GOINSECURE=""
GOMODCACHE="/home/alex/go/pkg/mod"
GONOPROXY=""
GONOSUMDB=""
GOOS="linux"
GOPATH="/home/alex/go"
GOPRIVATE=""
GOPROXY="https://proxy.golang.org,direct"
GOROOT="/usr/local/go"
GOSUMDB="sum.golang.org"
GOTMPDIR=""
GOTOOLDIR="/usr/local/go/pkg/tool/linux_amd64"
GCCGO="gccgo"
AR="ar"
CC="gcc"
CXX="g++"
CGO_ENABLED="1"
GOMOD="/home/alex/Projects/greenlight/go.mod"
CGO_CFLAGS="-g -O2"
CGO_CPPFLAGS=""
CGO_CXXFLAGS="-g -O2"
CGO_FFLAGS="-g -O2"
CGO_LDFLAGS="-g -O2"
PKG_CONFIG="pkg-config"
GOGCCFLAGS="..."
```

这里需要关注的是 `GOPROXY` 设置，它包含一个以逗号分隔的模块镜像列表。默认情况下，其值如下：

```
GOPROXY="https://proxy.golang.org,direct"
```

我们看到的 URL `https://proxy.golang.org` 指向一个由 Google 的 Go 团队维护的*模块镜像*，其中包含数万个开源 Go 包的源代码副本。

每当你使用 `go` 命令获取包时——无论是通过 `go get` 还是某个 `go mod *` 命令——它都会首先尝试从这个镜像检索源代码。

如果镜像已经存储了所需包和版本号的源代码副本，它会立即以 zip 文件形式返回该代码。否则，如果尚未存储，镜像将尝试从权威仓库获取代码，代理转发给你，并存储以供将来使用。

如果镜像根本无法获取代码，那么它将返回错误响应，`go` 工具将回退到直接从权威仓库获取副本（感谢 `GOPROXY` 设置中的 `direct` 指令）。

使用模块镜像作为第一个获取位置有几个好处：

- `https://proxy.golang.org` 模块镜像*通常*会长期存储包，从而在原始仓库从互联网上消失时提供一定程度的保护。
- 一旦存储在 `https://proxy.golang.org` 模块镜像中，就无法覆盖或删除包。这有助于防止包作者（或攻击者）发布具有*相同版本号*的修改版本时可能出现的任何 bug 或问题。
- 从 `https://proxy.golang.org` 镜像获取模块通常比从权威仓库获取要快得多。

在大多数情况下，我通常建议保持 `GOPROXY` 设置为默认值。

但如果你不想使用 Google 提供的模块镜像，或者你处于阻止它的防火墙后面，还有其他替代方案，例如 https://goproxy.io 和微软提供的 https://athens.azurefd.net，你可以尝试。或者你甚至可以使用开源 Athens 和 goproxy 项目托管自己的模块镜像。

例如，如果你想切换到使用 `https://goproxy.io` 作为主要镜像，然后回退到使用 `https://proxy.golang.org` 作为次要镜像，再回退到直接获取，你可以像这样更新你的 `GOPROXY` 设置：

```bash
$ export GOPROXY=https://goproxy.io,https://proxy.golang.org,direct
```

或者如果你想完全禁用模块镜像，只需将值设置为 `direct`，像这样：

```
$ export GOPROXY=direct
```

### 依赖本地化（Vendoring）

Go 的模块镜像功能很棒，我推荐使用。但它并不是所有开发者和所有项目的银弹。

例如，也许你不想使用 Google 或其他第三方提供的模块镜像，但也不想承担托管自己的镜像的开销。或者你可能需要在没有网络访问的环境中例行工作。在这些场景中，你可能仍然希望降低依赖消失的风险，但使用模块镜像不可能或不吸引人。

你还应该注意，默认的 `proxy.golang.org` 模块镜像并不绝对保证会永远存储模块副本。从 FAQ 中：

> > *proxy.golang.org 不会永远保存所有模块。这有很多原因，但一个原因是如果 proxy.golang.org 无法检测到合适的许可证。在这种情况下，只有临时缓存的模块副本会*
> *被提供，如果模块从原始来源被删除并变得过时，它可能会不可用。*

此外，如果你需要在 5 年或 10 年后回到一个“冷”代码库，`proxy.golang.org` 模块镜像仍然可用吗？希望它会——但很难确定。

因此，出于这些原因，使用 `go mod vendor` 命令对项目依赖进行*依赖本地化*仍然是一种明智的做法。以这种方式进行依赖本地化，基本上会将第三方包的源代码完整副本存储在项目中的一个 *vendor* 文件夹中。

让我们演示如何做到这一点。我们将首先调整 `Makefile`，添加一个新的 `vendor` 规则，该规则调用 `go mod tidy`、`go mod verify` 和 `go mod vendor` 命令，如下所示：

```
File: Makefile

...

#
================================================================================
====== #
# QUALITY CONTROL
#
================================================================================
====== #

## audit: tidy and vendor dependencies and format, vet and test all code
.PHONY: audit
audit: vendor
```

```make
@ echo 'Formatting code...'
go fmt ./...
@ echo 'Vetting code...'
go vet ./...
staticcheck ./...
@ echo 'Running tests...'
go test -race -vet=off ./...

## vendor: tidy and vendor dependencies
.PHONY: vendor
vendor:
    @echo 'Tidying and verifying module dependencies...'
    go mod tidy
    go mod verify
    @echo 'Vendoring dependencies...'
    go mod vendor
```

除了添加 `vendor` 规则之外，我们还做了其他一些更改：

- 我们从 `audit` 规则中移除了 `go mod tidy` 和 `go mod verify` 命令。
- 我们添加了 `vendor` 规则作为 `audit` 的前提条件，这意味着每次执行 `audit` 规则时它都会自动运行。

为了明确这里的幕后情况，让我们快速了解一下运行 `make vendor` 时会发生什么：

- `go mod tidy` 命令将确保 `go.mod` 和 `go.sum` 文件列出我们项目所需的所有依赖项（并且没有不必要的依赖项）。
- `go mod verify` 命令将验证模块缓存中存储的依赖项（位于机器上的 `$GOPATH/pkg/mod`）是否与 `go.sum` 文件中的加密哈希匹配。
- `go mod vendor` 命令会将必要的源代码从模块缓存复制到项目根目录中一个新的 `vendor` 目录中。

让我们尝试运行这个新的 vendor 规则，如下所示：

```
$ make vendor
Tidying and verifying module dependencies...
go mod tidy
go mod verify
all modules verified
Vendoring dependencies...
go mod vendor
```

完成后，你应该会看到创建了一个新的 `vendor` 目录，其中包含所有源代码的副本以及一个 `modules.txt` 文件。`vendor` 文件夹中的目录结构应该类似于这样：

```
$ tree -L 3 ./vendor/
./vendor/
├── github.com
│   ├── felixge
│   │   └── httpsnoop
│   └── go-mail
```




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




## ./... 模式

大多数 `go` 工具都支持 `./...` 通配符模式，例如 `go fmt ./...`、`go vet ./...` 和 `go test ./...`。此模式匹配当前目录和所有子目录，但排除 `vendor` *目录*。

一般来说，这很有用，因为它意味着我们不会不必要地格式化、检查或测试 `vendor` 目录中的代码——并且我们的 `make audit` 规则不会因为这些 vendored 包 *内部* 可能存在的问题而失败。

### 第 20.5 章。

## 构建二进制文件

目前我们一直使用 `go run` 命令（或最近的 `make run/api`）运行 API。但在本章中，我们将重点介绍如何*构建一个可执行二进制文件*，以便在无需安装 Go 工具链的情况下分发并在其他机器上运行。

构建二进制文件需要使用 `go build` 命令。简单示例的使用方式如下：

```bash
$ go build -o=./bin/api ./cmd/api
```

当我们运行此命令时，`go build` 会将 `cmd/api` 包（以及任何依赖包）*编译*为包含机器码的文件，然后将它们*链接*在一起形成可执行二进制文件。在上面的命令中，可执行二进制文件将输出到 `./bin/api`。

为方便起见，让我们在 makefile 中添加一个新的 `build/api` 规则来运行此命令，如下所示：

```
File: Makefile
```

```
$ ./bin/api -port=4040 -db-dsn=postgres://greenlight:pa55word@localhost/greenlight
{"level":"INFO","time":"2021-04-18T14:06:11Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T14:06:11Z","message":"starting server","properties":{"addr":":4040","env":"development"}}
```

### 减小二进制文件大小

如果仔细查看可执行二进制文件，您会发现其大小为 10470419 字节（约 10.5MB）。

```
$ ls -l ./bin/api
-rwxrwxr-x 1 alex alex 10470419 Apr 18 16:05 ./bin/api
```

> **注意：** 如果您跟随操作，您的二进制文件大小可能会略有不同。它取决于您的操作系统，以及您使用的 Go 的确切版本和第三方依赖项。

通过指示 Go 链接器从二进制文件中剥离 DWARF 调试信息和符号表，可以将二进制文件大小减少约 25%。我们可以在 go build 命令中使用链接器标志 -ldflags="-s" 来实现，如下所示：

```
File: Makefile

...
#
================================================================================
======= #
# BUILD
#
================================================================================
======= #

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
    @echo 'Building cmd/api...'
    go build -ldflags='-s' -o=./bin/api ./cmd/api
```

如果再次运行 `make build/api`，您现在应该会发现二进制文件的大小已减少到 8 MB 以下。

```
$ make build/api
Building cmd/api...
go build -ldflags='-s' -o=./bin/api ./cmd/api
$ ls -l ./bin/api
-rwxrwxr-x 1 alex alex 7618560 Apr 18 16:08 ./bin/api
```

需要注意的是，剥离 DWARF 信息和符号表会使使用 Delve 或 gdb 等工具调试可执行文件变得更加困难。但通常情况下，您并不经常需要这样做——而且 Rob Pike 甚至提出了一个[开放提案]，建议将来将省略 DWARF 信息作为链接器的默认行为。

### 交叉编译

默认情况下，`go build` 命令会输出适用于您*本地机器操作系统和架构*的二进制文件。但它也支持交叉编译，因此您可以生成适用于不同机器的二进制文件。如果您在一个操作系统上开发，在另一个操作系统上部署，这尤其有用。

要查看 Go 支持的所有操作系统/架构组合列表，您可以运行 `go tool dist list` 命令，如下所示：

```text
$ go tool dist list
aix/ppc64
android/386
android/amd64
android/arm
android/arm64
darwin/amd64
...
```

您可以通过在运行 `go build` 时设置 `GOOS` 和 `GOARCH` 环境变量来指定要创建二进制文件的操作系统和架构。例如：

```
$ GOOS=linux GOARCH=amd64 go build {args}
```

在本书的下一节中，我们将介绍如何在 Digital Ocean 托管的 Ubuntu Linux 服务器上部署可执行二进制文件。为此，我们需要一个专为运行在具有 `linux/amd64` 操作系统和架构组合的机器上而设计的二进制文件。

因此，让我们更新 `make build/api` 规则，使其创建两个二进制文件——一个用于本地机器，另一个用于部署到 Ubuntu Linux 服务器。

```
File: Makefile

...

#
================================================================================
====== #
# BUILD
#
================================================================================
====== #

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
    @echo 'Building cmd/api...'
    go build -ldflags='-s' -o=./bin/api ./cmd/api
```

```
GOOS=linux GOARCH=amd64 go build -ldflags='-s' -o=./bin/linux_amd64/api ./cmd/api
```

如果您跟随操作，请继续再次运行 `make build/api`。

您应该会看到现在创建了两个二进制文件——交叉编译的二进制文件位于 `./bin/linux_amd64` 目录下，如下所示：

```
$ make build/api
Building cmd/api...
go build -ldflags='-s' -o=./bin/api ./cmd/api
GOOS=linux GOARCH=amd64 go build -ldflags='-s' -o=./bin/linux_amd64/api ./cmd/api
$ tree ./bin
./bin
├── api
└── linux_amd64
    └── api
```

作为一般规则，您可能不希望将 Go 二进制文件与源代码一起提交到版本控制中，因为它们会显著增加存储库的大小。

因此，如果您跟随操作，让我们快速在 `.gitignore` 文件中添加一条额外的规则，指示 Git 忽略 `bin` 目录的内容。

```
$ echo 'bin/' >> .gitignore
$ cat .gitignore
.envrc
bin/
```

## 附加信息

### 构建缓存

需要注意的是，go build 命令会将构建输出缓存到 Go 构建缓存中。此缓存输出将在适当的未来构建中再次重用，这可以显著加快应用程序的整体构建时间。

如果您不确定构建缓存的位置，可以通过运行 go env GOCACHE 命令来检查：

```
$ go env GOCACHE
/home/alex/.cache/go-build
```

您还应注意，构建缓存不会自动检测代码通过 cgo 导入的 C 库的任何更改。因此，如果自上次构建以来您更改了 C 库，则在运行 `go build` 时需要使用 -a 标志强制重建所有包。或者，您也可以使用 `go clean` 清除缓存：

```
$ go build -a -o=/bin/foo ./cmd/foo      # Force all packages to be rebuilt
$ go clean -cache                      # Remove everything from the build cache
```

> **注意：** 如果您在非 `main` 包上运行 `go build`，构建输出将存储在构建缓存中以便重用，但不会生成可执行文件。

## 管理和自动化版本号

本书一开始，我们将应用程序的版本号硬编码为 cmd/api/main.go 文件中的常量 "1.0.0"。

在本章中，我们将采取措施使查看和管理此版本号变得更容易，并解释如何基于 Git 提交自动生成版本号并将其集成到应用程序中。

### 显示版本号

让我们首先更新我们的应用程序，以便可以通过使用 -version 命令行标志运行二进制文件来轻松检查版本号，如下所示：

```
$ ./bin/api -version
Version:      1.0.0
```

从概念上讲，实现起来相当直接。我们需要定义一个布尔版本命令行标志，检查此标志 on

启动之后，如有必要，打印版本号并退出应用程序。

如果你正在跟着做，请像这样更新你的 `cmd/api/main.go` 文件：

```
File: cmd/api/main.go

package main

import (
    "context"
    "database/sql"
    "expvar"
    "flag"
    "fmt" // New import
    "os"
    "runtime"
    "strings"
    "sync"
    "time"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/jsonlog"
    "greenlight.alexedwards.net/internal/mailer"

    _ "github.com/lib/pq"
)

const version = "1.0.0"

...

func main() {
    var cfg config
```

```
flag.IntVar(&cfg.port, "port", 4000, "API server port")
flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

flag.StringVar(&cfg.db.dsn, "db-dsn", "", "PostgreSQL DSN")

flag.IntVar(&cfg.db.maxOpenConns, "db-max-open-conns", 25, "PostgreSQL max open connections")
flag.IntVar(&cfg.db.maxIdleConns, "db-max-idle-conns", 25, "PostgreSQL max idle connections")
flag.StringVar(&cfg.db.maxIdleTime, "db-max-idle-time", "15m", "PostgreSQL max connection idle time")

flag.BoolVar(&cfg.limiter.enabled, "limiter-enabled", true, "Enable rate limiter")
flag.Float64Var(&cfg.limiter.rps, "limiter-rps", 2, "Rate limiter maximum requests per second")
flag.IntVar(&cfg.limiter.burst, "limiter-burst", 4, "Rate limiter maximum burst")

flag.StringVar(&cfg.smtp.host, "smtp-host", "smtp.mailtrap.io", "SMTP host")
flag.IntVar(&cfg.smtp.port, "smtp-port", 25, "SMTP port")
flag.StringVar(&cfg.smtp.username, "smtp-username", "0abf276416b183", "SMTP username")
flag.StringVar(&cfg.smtp.password, "smtp-password", "d8672aa2264bb5", "SMTP password")
flag.StringVar(&cfg.smtp.sender, "smtp-sender", "Greenlight <no-reply@greenlight.alexedwards.net>", "SMTP sender")

flag.Func("cors-trusted-origins", "Trusted CORS origins (space separated)", func(val string) error {
    cfg.cors.trustedOrigins = strings.Fields(val)
    return nil
})

// Create a new version boolean flag with the default value of false.
displayVersion := flag.Bool("version", false, "Display version and exit")
```

> **记住：** 布尔命令行标志*没有值*时会被解释为 `true`。所以使用 `-version` 运行我们的应用与使用 `-version=true` 运行是相同的。

## 包含构建时间

让我们进一步扩展，让 `-version` 标志强制我们的应用打印出版本号*以及*可执行二进制文件被构建的确切时间。类似这样：

```
$ ./bin/api -version
Version:      1.0.0
Build time:   2021-02-15T13:54:14+01:00
```

这是一个非常有趣的改动，因为构建时间是一个完全动态的值，*不受我们的应用代码控制*。在调用 `go build` 之前我们*无法预先*知道构建时间，因此它不能以常规方式在我们的源代码中定义。

为了实现这一点，我们需要使用 `go build` 的一个特殊功能——`-X` 链接器标志，它允许你在运行 `go build` 时将一个值赋值或“烧录”到一个变量中。具体来说，我们将在 makefile 中生成一个包含当前日期和时间的字符串，然后将其“烧录”到二进制文件中，作为 `make build/api` 规则的一部分。

我来演示一下。

打开 `cmd/api/main.go` 文件，并更新它以包含并打印一个新的 `buildTime` 变量，像这样：

```
File: cmd/api/main.go

package main

...

const version = "1.0.0"

// Create a buildTime variable to hold the executable binary build time. Note that this
// must be a string type, as the -X linker flag will only work with string
// variables.
var buildTime string

...

func main() {
    var cfg config

    flag.IntVar(&cfg.port, "port", 4000, "API server port")
    flag.StringVar(&cfg.env, "env", "development", "Environment (development|staging|production)")

    flag.StringVar(&cfg.db.dsn, "db-dsn", "", "PostgreSQL DSN")

    flag.IntVar(&cfg.db.maxOpenConns, "db-max-open-conns", 25, "PostgreSQL max open connections")
    flag.IntVar(&cfg.db.maxIdleConns, "db-max-idle-conns", 25, "PostgreSQL max idle connections")
    flag.StringVar(&cfg.db.maxIdleTime, "db-max-idle-time", "15m", "PostgreSQL max connection idle time")

    flag.BoolVar(&cfg.limiter.enabled, "limiter-enabled", true, "Enable rate limiter")
    flag.Float64Var(&cfg.limiter.rps, "limiter-rps", 2, "Rate limiter maximum requests per second")
    flag.IntVar(&cfg.limiter.burst, "limiter-burst", 4, "Rate limiter maximum burst")

    flag.StringVar(&cfg.smtp.host, "smtp-host", "smtp.mailtrap.io", "SMTP host")
    flag.IntVar(&cfg.smtp.port, "smtp-port", 25, "SMTP port")
    flag.StringVar(&cfg.smtp.username, "smtp-username", "0abf276416b183", "SMTP username")
    flag.StringVar(&cfg.smtp.password, "smtp-password", "d8672aa2264bb5", "SMTP password")
    flag.StringVar(&cfg.smtp.sender, "smtp-sender", "Greenlight <no-reply@greenlight.alexedwards.net>", "SMTP sender")

    flag.Func("cors-trusted-origins", "Trusted CORS origins (space separated)", func(val string) error {
        cfg.cors.trustedOrigins = strings.Fields(val)
        return nil
    })

    displayVersion := flag.Bool("version", false, "Display version and exit")

    flag.Parse()

    if *displayVersion {
        fmt.Printf("Version:\t%s\n", version)
        // Print out the contents of the buildTime variable.
        fmt.Printf("Build time:\t%s\n", buildTime)
        os.Exit(0)
    }

    ...
}
...
```

然后我们需要对 `Makefile` 做几处修改。具体来说，我们需要：

- 1. 使用 unix `date` 命令生成当前时间，并将其存储在一个 `current_time` 变量中。
- 2. 更新 `build/api` 规则，使用 `-X` 链接器标志将当前时间“烧录”到我们的 `main.buildTime` 变量中。

像这样：

```
File: Makefile

...

#
================================================================================
====== #
# BUILD
#
================================================================================
====== #

current_time = $(shell date --iso-8601=seconds)

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
	@echo 'Building cmd/api...'
	go build -ldflags='-s -X main.buildTime=${current_time}' -o=./bin/api ./cmd/api
	GOOS=linux GOARCH=amd64 go build -ldflags='-s -X main.buildTime=${current_time}' -o=./bin/linux_amd64/api ./cmd/api
```

如果你重新构建二进制文件并用 `-version` 标志运行它们，它们现在应该会在版本号旁边打印出它们被构建的确切时间。类似这样：

```
```
$ make build/api
Building cmd/api...
go build -ldflags='-s -X main.buildTime=2021-04-18T18:21:40+02:00' -o=./bin/api ./cmd/api
GOOS=linux GOARCH=amd64 go build -ldflags='-s -X main.buildTime=2021-04-18T18:21:40+02:00' -o=./bin/linux_amd64/api ./cmd/api

$ ./bin/api -version
Version:      1.0.0
Build time:   2021-04-18T18:21:40+02:00
```
```

请注意，如果你在*没有*烧录 `buildTime` 值的情况下执行应用程序，那么 `buildTime` 将保留应用程序代码中设置的默认值（在我们的例子中是空字符串 `""`）。例如，当使用 `go run` 时：

```
```
$ go run ./cmd/api -version
Version:      1.0.0
Build time:
```
```

我们的 Makefile 中的行变得有点长，所以让我们快速将链接器标志拆分成一个可复用的变量，像这样：

文件：Makefile

```
...
#
================================================================================
====== #
# BUILD
#
================================================================================
====== #

current_time = $(shell date --iso-8601=seconds)
linker_flags = '-s -X main.buildTime=${current_time}'

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
    @echo 'Building cmd/api...'
    go build -ldflags=${linker_flags} -o=./bin/api ./cmd/api
    GOOS=linux GOARCH=amd64 go build -ldflags=${linker_flags} -o=./bin/linux_amd64/api ./cmd/api
```

## 使用 Git 自动版本编号

如果你使用 Git 对源代码进行版本控制，那么可以扩展本章中讨论的思路，根据你的 Git 提交为你的应用程序创建*自动版本号*。



**重要：** 本书的这一部分只有在你使用 Git 时才真正相关。如果你不使用，那完全没问题，你可以毫无问题地跳到下一章。

否则，如果你正在跟随操作（并且尚未执行），请继续在项目目录的根目录初始化一个新的 Git 仓库：

```
$ git init
Initialized empty Git repository in /home/alex/Projects/greenlight/.git/
```

然后像这样创建一个包含项目目录中所有文件的新提交：

```
$ git add .
$ git commit -m "Initial commit"
```

如果你使用 `git log` 命令查看提交历史，你会看到此提交的 *哈希*。

```
$ git log
commit 0f8573aab79f3cbee17d39901d5cb200121c7ed1 (HEAD -> master)
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:29:48 2021 +0200

    Initial commit
```

在我的例子中，提交哈希是 `0f8573aab79f3cbee17d39901d5cb200121c7ed1` —— 但你的会是不同的值。

你也可以使用 `git describe` 命令来获取仓库当前状态的‘可读性’描述符。像这样：

```
$ git describe --always --dirty
0f8573a
```

在这种情况下，我们可以看到 `git describe` 返回的是 *提交哈希的缩写版本*。我们还使用了 `--dirty` 标志，这意味着如果仓库中有任何未提交的更改，描述符将以 "`-dirty`" 为后缀。例如 `0f8573a-dirty`。

让我们更新我们的项目，以便在构建可执行文件时，将 `git describe` 的输出作为应用程序的‘版本号’烧录到二进制文件中。

为此，我们首先需要做的就是将 `cmd/api/main.go` 文件中的 `version` 常量改为变量，因为无法将值‘烧录’到常量中。

```
File: cmd/api/main.go

package main

...

// Remove the hardcoded version number and make version a variable instead of a constant.
var (
    buildTime string
    version   string
)

...
```

然后让我们更新 Makefile，使用与构建时间相同的模式，将 git describe 输出烧录到应用程序的 version 变量中。像这样：

```
File: Makefile

...

#
================================================================================
====== #
# BUILD
#
================================================================================
====== #

current_time = $(shell date --iso-8601=seconds)
git_description = $(shell git describe --always --dirty)
linker_flags = '-s -X main.buildTime=${current_time} -X main.version=${git_description}'

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
    @echo 'Building cmd/api...'
    go build -ldflags=${linker_flags} -o=./bin/api ./cmd/api
    GOOS=linux GOARCH=amd64 go build -ldflags=${linker_flags} -o=./bin/linux_amd64/api ./cmd/api
```

在这一点上，让我们再次快速运行 `git describe`：

```
$ git describe --always --dirty
0f8573a-dirty
```

这个输出是有意义的——上一次提交的哈希是 `0f8573a...`，而 `-dirty` 后缀表示我们的仓库现在包含未提交的更改（自上次提交以来我们修改了 `cmd/api/main.go` 和 `Makefile` 文件）。

让我们提交这些最近的更改，再次运行 `make build/api`，然后检查二进制文件中的版本号。像这样：

```
$ git add .
$ git commit -m "Generate version number automatically"
[master 76c976a] Generate version number automatically
  2 files changed, 6 insertions(+), 7 deletions(-)
```

```
$ make build/api
Building cmd/api...
go build -ldflags='-s -X main.buildTime=2021-04-18T18:43:32+02:00 -X main.version=76c976a' -o=./bin/api ./cmd/api
GOOS=linux GOARCH=amd64 go build -ldflags='-s -X main.buildTime=2021-04-18T18:43:32+02:00 -X main.version=76c976a' -o=./bin/linux_amd64/api ./cmd/api

$ ./bin/api -version
Version:      76c976a
Build time:   2021-04-18T18:43:32+02:00
```

我们可以看到，我们的二进制文件现在报告它是从 *具有该提交哈希的仓库的干净版本* 76c976a 构建的。让我们将其与项目的 `git log` 输出进行交叉检查：

```
$ git log
commit 76c976a07d0fce3d813f3a4748574f81b1e24226 (HEAD -> master)
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:39:17 2021 +0200

    Generate version number automatically

commit 0f8573aab79f3cbee17d39901d5cb200121c7ed1
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:29:48 2021 +0200

    Initial commit
```

看起来不错——我们 Git 历史中的提交哈希与我们的应用程序版本号完全一致。这意味着我们现在可以轻松识别特定二进制文件包含的确切代码——我们只需要使用 `-version` 标志运行二进制文件，然后将其与 Git 仓库历史进行交叉引用即可。

## 使用 Git 标签

在某些项目中，你可能希望用标签注释某些 Git 提交，通常是为了表示正式的发布版本号。

为了说明这一点，让我们像这样将 `v1.0.0` 标签添加到我们最新的提交中：

```
$ git tag v1.0.0
$ git log
commit 76c976a07d0fce3d813f3a4748574f81b1e24226 (HEAD -> master, tag: v1.0.0)
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:39:17 2021 +0200

    Generate version number automatically

...
```

如果你以这种方式为提交添加标签，那么在调用 `git describe` 生成应用程序版本号时，使用 `--tags` 和 `--long` 标志是个好主意。这将强制输出采用以下格式：

```
{tag}-{number of additional commits}-g{abbreviated commit hash}
```

让我们快速看看这对我们的项目目前是什么样子的：

```bash
$ git describe --always --dirty --tags --long
v1.0.0-0-g76c976a
```

因此，在这种情况下，我们可以从版本号看出，仓库基于 `v1.0.0`，在其之上没有额外的提交，最新的提交哈希是 `76c976a`。前缀提交哈希的 `g` 字符代表‘git’，存在是为了帮助区分该哈希与其他版本控制系统生成的哈希。

让我们更新我们的 `Makefile`，在生成版本号时使用这些额外的标志，像这样：

```
File: Makefile

...

#
================================================================================
====== #
# BUILD
#
================================================================================
====== #

current_time = $(shell date --iso-8601=seconds)
git_description = $(shell git describe --always --dirty --tags --long)
linker_flags = '-s -X main.buildTime=${current_time} -X main.version=${git_description}'

...
```

然后继续提交此更改，重建二进制文件并检查版本号。你的输出应类似于这样：

```
$ git add .
$ git commit -m "Use --tags and --long flags when generating version number"
$ make build/api
$ ./bin/api -version
Version:      v1.0.0-1-gf27fd0f
Build time:   2021-04-18T18:54:05+02:00
```

版本号现已更改为 v1.0.0-1-gf27fd0f，表示二进制文件是使用来自提交 f27fd0f 的仓库代码构建的，该提交领先于 v1.0.0 标签 1 个提交。

在基础设施和架构方面，我们将在一台 Ubuntu Linux 服务器上运行所有内容。我们的技术栈将包括一个 PostgreSQL 数据库和 Greenlight API 的可执行二进制文件，其运行方式与本书迄今为止所见的大致相同。但除此之外，我们还将在 Greenlight API 前运行 Caddy 作为 *反向代理*。

使用 Caddy 有几个好处。它将自动为我们处理和终止 HTTPS 连接——包括通过 Let’s Encrypt 自动生成和管理 TLS 证书——我们还可以使用 Caddy 轻松限制对指标端点的互联网访问。

在本节中你将学习如何：

- 在 Digital Ocean 上部署一台运行 Ubuntu Linux 的服务器来托管你的应用程序。
- 自动化服务器配置——包括创建用户账户、配置防火墙和安装必要的软件。
- 自动化更新应用程序并将更改部署到服务器的过程。
- 如何使用 systemd 以非 root 用户身份将应用程序作为后台服务运行。
- 使用 Caddy 作为应用程序前面的反向代理来自动管理 TLS 证书并处理 HTTPS 连接。



## 创建 Digital Ocean Droplet

我们需要做的第一件事是在 Digital Ocean 上部署一台服务器来托管我们的应用程序。

严格来说，我们要部署的实际上是一个在 Digital Ocean 术语中称为 *droplet* 的 *virtual machine*。

如果你想跟随本书的这一阶段，你需要为 Digital Ocean 注册一个账户（如果你还没有）。在注册过程中，你将被提示确认你的电子邮件地址，然后使用信用卡/借记卡或 PayPal 向你的账户添加至少 5 美元的预付费额度。

完成注册并充值后，你应该会看到一个类似以下的介绍屏幕：

### 开始构建吧

节省时间，让我们为您配置一个适合常见起点的 Droplet：

- Node.JS 服务器
- Docker 服务器
- WordPress 网站
- django
- Python 服务器
- PHP (LAMP) 服务器
- Ubuntu 服务器

或在 App Platform 上部署你的应用程序或静态网站

部署你的源代码

跳过此步骤并前往控制面板

点击屏幕底部的“Skip this”链接以直接进入你的账户控制面板，其应如下所示：

![](img/30f9221bfc265d52b544dd595ca099de_796_0.png)

## 创建 SSH 密钥

为了登录你的 Digital Ocean 账户中的 droplets，你需要一个 *SSH keypair*。

> **建议：** 如果你不熟悉 SSH、SSH 密钥或 [公钥加密](...) 一般概念，那么我建议在继续之前先阅读 [本指南](...) 的前半部分以了解概况。

如果你已经有一个满意的 SSH keypair 用于此目的，那太好了，你可以跳到下一节。

但如果你没有，你需要使用本地机器上的 `ssh-keygen` 命令创建 keypair。类似这样：

```
$ ssh-keygen -t rsa -b 4096 -C "greenlight@greenlight.alexedwards.net" -f $HOME/.ssh/id_rsa_greenlight
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/alex/.ssh/id_rsa_greenlight
Your public key has been saved in /home/alex/.ssh/id_rsa_greenlight.pub
The key fingerprint is:
SHA256:/ii7Wo90BdsoaMU1UAajmd/5vBSeVmBRtf7QtoWw8YM
greenlight@greenlight.alexedwards.net
The key's randomart image is:
+-----[RSA 4096]-----+
|     ++= .....   |
|     = + . .   . |
|   + o . o o .   |
|   + . B . B o   |
|   o o S + E * + |
|   .   o = +   =o|
|     o o B     ..|
|     o.+ = .     |
|     ..++o o     |
+-----[SHA256]-----+
```

这将在你的 `$HOME/.ssh` 文件夹中生成两个新文件：

- `$HOME/.ssh/id_rsa_greenlight` 文件包含你的 *private key*。请务必妥善保管，因为任何有权访问它的人都可以冒充你。

![](img/30f9221bfc265d52b544dd595ca099de_801_0.png)

屏幕随后应更新以确认你的 SSH 密钥已成功添加，如下所示：

![](img/30f9221bfc265d52b544dd595ca099de_802_0.png)

## 创建 Droplet

现在你已经在账户中添加了有效的 SSH 密钥，是时候真正创建 droplet 了。

有几种方法可以做到这一点。可以通过 Digital Ocean API 或使用官方命令行工具以编程方式完成，如果你需要创建或管理大量服务器，我建议使用这些方法。

或者，你也可以通过 Digital Ocean 网站上的控制面板手动创建 droplet。这是我们在本书中采用的方法，部分原因是它作为一次性操作足够简单...

![](img/30f9221bfc265d52b544dd595ca099de_804_0.png)

下一步是选择一个与 droplet 所需技术规格相匹配的计划。在这种情况下我们将选择 **Basic Regular Intel with SSD** 计划，价格为 **$5/month**，这将为我们提供一台具有 1GB RAM、25GB 磁盘空间以及每月 1000GB 出站数据传输的虚拟机（入站数据传输不受限制）。

![](img/30f9221bfc265d52b544dd595ca099de_805_0.png)

下一个选项允许我们为 droplet 添加块存储。这本质上是一个与 droplet 无关的存储卷，充当本地硬盘，可以在不同的 droplet 之间移动。我们现在不需要它，所以你可以跳过此部分。

之后我们需要选择 droplet 将物理托管的数据中心。我将选择 New York 3，但如果你喜欢也可以选择其他位置。

![](img/30f9221bfc265d52b544dd595ca099de_806_0.png)

之后我们可以为 droplet 选择一些免费的“附加”功能。在我们的例子中我们将选择 Monitoring，这将允许你稍后在 Digital Ocean 控制面板中查看各种 droplet 统计信息（如 CPU、内存和磁盘使用）的图表——你还可以设置警报，如果资源使用超过某个阈值。

![](img/30f9221bfc265d52b544dd595ca099de_807_0.png)

在 Authentication 部分，确保选择 SSH keys 作为身份验证方法，并且你刚刚上传的 SSH 密钥已被选中。

然后我们进入最终的配置选项。

![](img/30f9221bfc265d52b544dd595ca099de_808_0.png)

我们现在只需要 **one droplet**，所以你可以将其保留为默认值。

你还应该为 droplet 添加一个 **hostname**。其中之一，hostname 在 Digital Ocean 控制面板中用作 droplet 的主要标识符，并且当你稍后通过 SSH 登录 droplet 进行管理时也会看到它。因此，你应该选择一个合理且易于识别的名称。我将使用主机名 `greenlight-production`，但你也可以使用其他名称。

为你的 droplet 添加标签是完全可选的，但如果你经常使用 Digital Ocean，它们可以成为帮助过滤和管理 droplet 的有用方式。我在这里使用标签 `greenlight` 和 `production`。

然后最后你可以选择支付额外 20% 的费用来启用自动 droplet 备份。如果你选择此选项，Digital Ocean 将每周对你的 droplet 进行一次‘快照’并保存 4 周。你可以通过控制面板将 droplet 恢复到其快照状态（如果需要）。是否启用备份完全取决于你——但这是一个简单且无忧的安全网。

一切设置好后，继续点击屏幕底部的 **Create Droplet** 按钮。你应该会看到一个进度条，显示 droplet 正在为你设置，几分钟后 droplet 应该就可以上线使用了。

![](img/30f9221bfc265d52b544dd595ca099de_809_0.png)

此时最重要的是记下 droplet 的 IP 地址，在我的例子中是 45.55.49.87。

如果你愿意，也可以点击 droplet 主机名以查看有关 droplet 的更详细信息（包括监控统计信息）并在需要时进行进一步的配置和管理更改。

![](img/30f9221bfc265d52b544dd595ca099de_810_0.png)

好了，droplet 设置好后，是时候见证真相的时刻了！

打开一个新的终端窗口并尝试使用 droplet IP 地址以 root 用户身份通过 SSH 连接到 droplet。像这样...

```
$ ssh root@45.55.49.87
The authenticity of host '45.55.49.87 (45.55.49.87)' can't be established.
ECDSA key fingerprint is SHA256:HWGdr4i2xF0you3GlRcvOVY/pqJ45pwLXhKWAjq4ahw.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '45.55.49.87' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-51-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

 System information as of Sun Apr 18 19:02:59 UTC 2021

 System load:  0.0               Users logged in:       0
 Usage of /:   5.9% of 24.06GB   IPv4 address for eth0: 45.55.49.87
 Memory usage: 21%               IPv4 address for eth0: 10.17.0.5
 Swap usage:  0%                IPv4 address for eth1: 10.108.0.2
 Processes:    103

126 updates can be installed immediately.
60 of these updates are security updates.
To see these additional updates run: apt list --upgradable

The programs included with the Ubuntu system are free software:
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

root@greenlight-production:~#
```



> **注意：** 这是你第一次使用 SSH 连接到此 Droplet 时，你会收到一条“无法建立主机真实性”的消息。在这种情况下这是正常的，只需输入 `yes` 继续。如果你的 SSH 密钥受密码短语保护，你可能还会被提示输入它。

太好了，看起来运行正常。我们的 Ubuntu Linux Droplet 已启动并运行，并且我们已成功以 `root` 用户通过 SSH 连接到它。

你可以继续输入 `exit` 来终止 SSH 连接并返回到本地机器的终端，如下所示：

```
root@greenlight-production:~# exit
logout
Connection to 45.55.49.87 closed.
```

## 服务器配置和安装软件

现在我们的 Ubuntu Linux Droplet 已成功部署，我们需要做一些维护工作来保护服务器并使其准备就绪。与其手动操作，本章我们将创建一个可重复使用的脚本来自动化这些设置任务。

> **注意：** 本章我们将使用常规的 bash 脚本来执行设置任务，但如果你习惯使用 Ansible 等配置管理工具，也可以随意使用它来实现相同的设置流程。

总体而言，我们希望设置脚本执行以下操作：

- 更新服务器上的所有软件包，包括应用安全更新。
- 设置服务器时区（就我而言，我将设置为 `America/New_York`）并安装所有区域设置的支持。
- 在服务器上创建 `greenlight` 用户，我们可以用它进行日常维护和运行 API 应用（而不是使用功能强大的 `root` 用户账户）。我们应该

```bash
$ mkdir -p remote/setup
$ touch remote/setup/01.sh
```

然后添加以下代码：

```bash
File: remote/setup/01.sh

#!/bin/bash
set -eu

#
====================================================================
======= #
# VARIABLES
#
====================================================================
======= #

# Set the timezone for the server. A full list of available timezones can be found by
# running timedatectl list-timezones.
TIMEZONE=America/New_York

# Set the name of the new user to create.
USERNAME=greenlight

# Prompt to enter a password for the PostgreSQL greenlight user (rather than hard-coding
# a password in this script).
read -p "Enter password for greenlight DB user: " DB_PASSWORD

# Force all output to be presented in en_US for the duration of this script. This avoids
# any "setting locale failed" errors while this script is running, before we have
# installed support for all locales. Do not change this setting!
export LC_ALL=en_US.UTF-8

#
==============================================================================
====== #
# SCRIPT LOGIC
#
==============================================================================
====== #

# Enable the "universe" repository.
add-apt-repository --yes universe

# Update all software packages. Using the --force-confnew flag means that
configuration
# files will be replaced if newer ones are available.
apt update
apt --yes -o Dpkg::Options::="--force-confnew" upgrade

# Set the system timezone and install all locales.
timedatectl set-timezone ${TIMEZONE}
apt --yes install locales-all

# Add the new user (and give them sudo privileges).
useradd --create-home --shell "/bin/bash" --groups sudo "${USERNAME}"

# Force a password to be set for the new user the first time they log in.
passwd --delete "${USERNAME}"
chage --lastday 0 "${USERNAME}"

# Copy the SSH keys from the root user to the new user.
rsync --archive --chown=${USERNAME}:${USERNAME} /root/.ssh /home/${USERNAME}

# Configure the firewall to allow SSH, HTTP and HTTPS traffic.
ufw allow 22
ufw allow 80/tcp
ufw allow 443/tcp
ufw --force enable

# Install fail2ban.
apt --yes install fail2ban

# Install the migrate CLI tool.
curl -L https://github.com/golang-migrate/migrate/releases/download/v4.14.1/migrate.linux-amd64.tar.gz | tar xzv
mv migrate.linux-amd64 /usr/local/bin/migrate

# Install PostgreSQL.
apt --yes install postgresql

# Set up the greenlight DB and create a user account with the password
entered earlier.
sudo -i -u postgres psql -c "CREATE DATABASE greenlight"
sudo -i -u postgres psql -d greenlight -c "CREATE EXTENSION IF NOT EXISTS citext"
sudo -i -u postgres psql -d greenlight -c "CREATE ROLE greenlight WITH LOGIN PASSWORD '${DB_PASSWORD}'"

# Add a DSN for connecting to the greenlight database to the system-wide
environment
# variables in the /etc/environment file.
echo "GREENLIGHT_DB_DSN='postgres://greenlight:${DB_PASSWORD}@localhost/greenlight'" >> /etc/environment

# Install Caddy (see https://caddyserver.com/docs/install#debian-ubuntu-raspbian).
apt --yes install -y debian-keyring debian-archive-keyring apt-transport-https
curl -L https://dl.cloudsmith.io/public/caddy/stable/gpg.key | sudo apt-key add -
curl -L https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt | sudo tee -a /etc/apt/sources.list.d/caddy-stable.list
apt update
apt --yes install caddy
```

> 当你使用 SSH 密钥进行身份验证时，基于密码的访问。请选择 `keep the local version currently installed` 然后 `<Ok>` 继续。

几分钟后，脚本应成功完成，Droplet 将重新启动——这也会让你断开 SSH 连接。

## 以 greenlight 用户连接

等待一分钟让重启完成后再试，尝试以 `greenlight` 用户通过 SSH 连接到 Droplet。这应该能正常工作（并且你在上一章中创建的 SSH 密钥对应用于验证连接）*但你将被提示设置密码。*

```
$ ssh greenlight@45.55.49.87
You are required to change your password immediately (administrator enforced)
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-72-generic x86_64)

* Documentation:  https://help.ubuntu.com
* Management:    https://landscape.canonical.com
* Support:       https://ubuntu.com/advantage

  System information as of Sun Apr 18 15:51:33 EDT 2021

  System load:    0.0              Users logged in:     0
  Usage of /:     9.2% of 24.06GB  IPv4 address for eth0: 45.55.49.87
  Memory usage:   20%              IPv4 address for eth0: 10.17.0.5
```

如果重新以 greenlight 用户连接，一切现在应该正常工作，你应该能够在 Droplet 上执行命令。如下所示：

```
$ ssh greenlight@45.55.49.87
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-65-generic x86_64)

...

greenlight@greenlight-production:~$ whoami
greenlight
```

在我们连接到 Droplet 的同时，让我们快速查看一下并检查一些关键功能是否按预期工作。

首先让我们通过使用 -version 标志运行它来检查 migrate 二进制文件是否已下载并且位于系统路径中。如果一切正常，这应该会像这样打印 migrate 版本号：

```
greenlight@greenlight-production:~$ migrate -version
4.14.1
```

接下来让我们验证 PostgreSQL 是否正在运行，并且我们可以使用 GREENLIGHT_DB_DSN 环境变量中的 DSN 连接到它：

```
greenlight@greenlight-production:~$ psql $GREENLIGHT_DB_DSN
psql (12.6 (Ubuntu 12.6-0ubuntu0.20.04.1))
```

```
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256,
compression: off)
Type "help" for help.

greenlight=> exit
```

最后，让我们通过调用 `systemctl status caddy` 来检查 Caddy 是否正在运行，以查看 Caddy 后台服务的状况。你需要在这里使用 `sudo` 以 `root` 身份运行此命令。

```
greenlight@greenlight-production:~$ sudo systemctl status caddy
● caddy.service - Caddy
    Loaded: loaded (/lib/systemd/system/caddy.service; enabled; vendor preset: enabled)
    Active: active (running) since Sun 2021-04-18 15:23:32 EDT; 37min ago
    Docs: https://caddyserver.com/docs/
  Main PID: 586 (caddy)
    Tasks: 7 (limit: 1136)
    Memory: 37.6M
    CGroup: /system.slice/caddy.service
            └─586 /usr/bin/caddy run --environ --config /etc/caddy/Caddyfile

Apr 18 15:23:33 greenlight-production caddy[586]: USER=caddy
Apr 18 15:23:33 greenlight-production caddy[586]:
INVOCATION_ID=2e2dc35c3cf44786b7103847fd9a9ad8
...
```

你应该会看到 Caddy 服务的状态为 `active (running)`——这证实 Caddy 运行成功。



```
...
#
================================================================================
====== #
# PRODUCTION
#
================================================================================
====== #

production_host_ip = '45.55.49.87'

## production/connect: connect to the production server
.PHONY: production/connect
production/connect:
    ssh greenlight@${production_host_ip}
```

一旦设置完成，你就可以在需要时通过简单输入 `make production/connect` 来连接你的 Droplet：

```
$ make production/connect
ssh greenlight@'45.55.49.87'
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-65-generic x86_64)
...

greenlight@greenlight-production:~$
```

## 附加信息

## Droplet 配置的未来更改

如果你需要对 Droplet 配置或设置进行进一步更改，可以创建一个额外的 `remote/setup/02.sh` 脚本，然后按以下方式执行它：

```
$ rsync -rP --delete ./remote/setup greenlight@45.55.49.87:~
$ ssh -t greenlight@45.55.49.87 "sudo bash /home/greenlight/setup/02.sh"
```

## 部署和执行迁移

此时我们的 Droplet 已配置好所需的所有软件和用户账户，因此让我们继续部署和运行我们的 API 应用的过程。

从高层次来看，我们的部署流程将包括三个操作：

- 1. 将应用程序二进制文件和 SQL 迁移文件复制到 Droplet。
- 2. 在 Droplet 上的 PostgreSQL 数据库上执行迁移。
- 3. 以 *background service* 的形式启动应用程序二进制文件。

目前我们只关注步骤 1 和 2，并在下一章处理将我们的应用程序作为 *background service* 运行的问题。

让我们开始在 Makefile 中创建一个新的 `make production/deploy/api` 规则，我们将使用它来自动执行这两个步骤。如下所示：

```
File: Makefile
```

```
...
#
================================================================================
====== #
# PRODUCTION
#
================================================================================
====== #

production_host_ip = "45.55.49.87"

## production/connect: connect to the production server
.PHONY: production/connect
production/connect:
    ssh greenlight@${production_host_ip}

## production/deploy/api: deploy the api to production
.PHONY: production/deploy/api
production/deploy/api:
    rsync -rP --delete ./bin/linux_amd64/api ./migrations greenlight@${production_host_ip}:~
    ssh -t greenlight@${production_host_ip} 'migrate -path ~/migrations -database $$GREENLIGHT_DB_DSN up'
```

让我们快速分析一下这个新规则在做什么。

首先，它使用 rsync 命令将 ./bin/linux_amd64/api 可执行二进制文件（专门为 Linux 构建的那个）和 ./migrations 文件夹复制到 Droplet 上 greenlight 用户的主目录中。

然后它使用带有 -t 标志的 ssh 命令，以 greenlight 用户身份在我们的 Droplet 上运行这些数据库迁移，使用以下命令：

```
'migrate -path ~/migrations -database $$GREENLIGHT_DB_DSN up'
```

因为 $ 字符在 Makefile 中有特殊含义，所以我们在上面的命令中通过在前面加上额外的美元字符 $$ 来 *转义它*。这意味着实际在 Droplet 上运行的命令将是 `'migrate -path ~/migrations -database $GREENLIGHT_DB_DSN up'`，并且迁移将 *使用 Droplet 环境变量* `GREENLIGHT_DB_DSN` 运行。

还需要注意的是，我们用单引号将此命令括起来。如果使用双引号，它将是一个 *interpreted string*，我们需要使用额外的转义字符 \ 像这样：

```
"migrate -path ~/migrations -database \$$GREENLIGHT_DB_DSN up"
```

好吧，让我们试试这个！

继续执行我们刚刚创建的 `make production/deploy/api` 规则。你应该会看到所有文件都成功复制（这可能需要一两分钟，具体取决于你的连接速度），然后迁移将被应用到你的数据库。如下所示：

```
$ make production/deploy/api
rsync -rP --delete ./bin/linux_amd64/api ./migrations greenlight@"45.55.49.87":~
sending incremental file list
api
        7,618,560 100%  119.34kB/s    0:01:02 (xfr#1, to-chk=13/14)
migrations/
migrations/000001_create_movies_table.down.sql
        28 100%   27.34kB/s    0:00:00 (xfr#2, to-chk=11/14)
migrations/000001_create_movies_table.up.sql
        286 100%  279.30kB/s    0:00:00 (xfr#3, to-chk=10/14)
migrations/000002_add_movies_check_constraints.down.sql
        198 100%  193.36kB/s    0:00:00 (xfr#4, to-chk=9/14)
migrations/000002_add_movies_check_constraints.up.sql
        289 100%  282.23kB/s    0:00:00 (xfr#5, to-chk=8/14)
migrations/000003_add_movies_indexes.down.sql
        78 100%   76.17kB/s    0:00:00 (xfr#6, to-chk=7/14)
migrations/000003_add_movies_indexes.up.sql
        170 100%  166.02kB/s    0:00:00 (xfr#7, to-chk=6/14)
migrations/000004_create_users_table.down.sql
        27 100%   26.37kB/s    0:00:00 (xfr#8, to-chk=5/14)
migrations/000004_create_users_table.up.sql
        294 100%  287.11kB/s    0:00:00 (xfr#9, to-chk=4/14)
migrations/000005_create_tokens_table.down.sql
        28 100%   27.34kB/s    0:00:00 (xfr#10, to-chk=3/14)
migrations/000005_create_tokens_table.up.sql
        203 100%   99.12kB/s    0:00:00 (xfr#11, to-chk=2/14)
migrations/000006_add_permissions.down.sql
        73 100%   35.64kB/s    0:00:00 (xfr#12, to-chk=1/14)
migrations/000006_add_permissions.up.sql
        452 100%  220.70kB/s    0:00:00 (xfr#13, to-chk=0/14)
ssh -t greenlight@"45.55.49.87" 'migrate -path ~/migrations -database $GREENLIGHT_DB_DSN up'
```

```
1/u create_movies_table (11.782733ms)
2/u add_movies_check_constraints (23.109006ms)
3/u add_movies_indexes (30.61223ms)
4/u create_users_table (39.890662ms)
5/u create_tokens_table (48.659641ms)
6/u add_permissions (58.23243ms)
Connection to 45.55.49.87 closed.
```

让我们快速连接到我们的 Droplet 并验证一切是否正常工作。

```
$ make production/connect
ssh greenlight@'45.55.49.87'
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-65-generic x86_64)
...
greenlight@greenlight-production:~$ ls -R
.:
api  migrations

./migrations:
000001_create_movies_table.down.sql
000001_create_movies_table.up.sql
000002_add_movies_check_constraints.down.sql
000002_add_movies_check_constraints.up.sql
000003_add_movies_indexes.down.sql
000003_add_movies_indexes.up.sql
000004_create_users_table.down.sql
000004_create_users_table.up.sql
000005_create_tokens_table.down.sql
000005_create_tokens_table.up.sql
000006_add_permissions.down.sql
000006_add_permissions.up.sql
```

80 因为 Caddy 已经在使用它，所以我们将改用不受限制的端口 4000。

如果你一直跟着操作，Droplet 上的端口 4000 目前应该被防火墙规则阻止，因此我们需要暂时放宽限制以允许传入请求。继续像这样操作：

```
greenlight@greenlight-production:~$ sudo ufw allow 4000/tcp
Rule added
Rule added (v6)
```

然后使用以下命令启动 API：

```
greenlight@greenlight-production:~$ ./api -port=4000 -db-dsn=$GREENLIGHT_DB_DSN -env=production
{"level":"INFO","time":"2021-04-19T07:10:55Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-19T07:10:55Z","message":"starting server","properties":{"addr":":4000","env":"production"}}
```

此时你应该能够在你的网络浏览器中访问 http://<your_droplet_ip>:4000/v1/healthcheck 并从健康检查端点获得成功的响应，类似于这样：

![](img/30f9221bfc265d52b544dd595ca099de_834_0.png)

最后，返回到你的 SSH 终端窗口并按 Ctrl+C 停止 Droplet 上的 API 运行。你应该会看到它优雅地关闭，如下所示：

```
greenlight@greenlight-production:~$ /home/greenlight/api -port=4000 -db-dsn=$GREENLIGHT_DB_DSN -env=production
{"level":"INFO","time":"2021-04-19T07:10:55Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-19T07:10:55Z","message":"starting server","properties":{"addr":":4000","env":"production"}}
^C{"level":"INFO","time":"2021-04-19T07:13:23Z","message":"caught signal","properties":{"signal":"interrupt"}}
{"level":"INFO","time":"2021-04-19T07:13:23Z","message":"completing background tasks","properties":{"addr":":4000"}}
{"level":"INFO","time":"2021-04-19T07:13:23Z","message":"stopped server","properties":{"addr":":4000"}}
```



## 将 API 作为后台服务运行

现在我们知道 API 可执行文件在生产 droplet 上运行正常，下一步是将其配置为 *后台服务* 运行，包括在 droplet 重启时自动启动。

有几种不同的工具可以用来实现此目的，但在本书中我们将使用 systemd —— 这是一组用于管理服务的工具，随 Ubuntu（以及许多其他 Linux 发行版）一起提供。

为了将我们的 API 应用作为后台服务运行，我们首先需要创建一个单元文件，该文件会告知 systemd 如何以及何时运行该服务。

如果你在跟随操作，请回到本地机器上的终端窗口，并在项目目录中创建一个新的 `remote/production/api.service` 文件：

```
$ mkdir remote/production
$ touch remote/production/api.service
```

然后添加以下标记：

```
File: remote/production/api.service

[Unit]
# Description is a human-readable name for the service.
Description=Greenlight API service

# Wait until PostgreSQL is running and the network is "up" before starting
the service.
After=postgresql.service
After=network-online.target
Wants=network-online.target

# Configure service start rate limiting. If the service is (re)started more
than 5 times
# in 600 seconds then don't permit it to start anymore.
StartLimitIntervalSec=600
StartLimitBurst=5

[Service]
# Execute the API binary as the greenlight user, loading the environment
variables from
# /etc/environment and using the working directory /home/greenlight.
Type=exec
User=greenlight
Group=greenlight
EnvironmentFile=/etc/environment
WorkingDirectory=/home/greenlight
ExecStart=/home/greenlight/api -port=4000 -db-dsn=${GREENLIGHT_DB_DSN} -env=production

# Automatically restart the service after a 5-second wait if it exits with a
non-zero
# exit code. If it restarts more than 5 times in 600 seconds, then the rate
limit we
# configured above will be hit and it won't be restarted anymore.
Restart=on-failure
RestartSec=5

[Install]
# Start the service automatically at boot time (the 'multi-user.target'
describes a boot
# state when the system will accept logins).
WantedBy=multi-user.target
```

现在单元文件已经设置好，下一步是在我们的 droplet 上安装此单元文件并启动服务。基本上我们需要做三件事：

- 1. 要‘安装’该文件，我们需要将其复制到 droplet 上的 `/etc/systemd/system/` 文件夹中。
- 2. 然后我们需要在 droplet 上运行 `systemctl enable api` 命令，使 `systemd` 意识到新的单元文件，并在 droplet 重启时自动启用该服务。
- 3. 最后，我们需要运行 `systemctl restart api` 来启动服务。

这三项任务都需要使用 `sudo` 运行。

让我们更新 makefile，以包含一个新的 `production/configure/api.service` 规则来为我们自动化这些任务。如下所示：

```
File: Makefile

...
#
================================================================================
# PRODUCTION
#
================================================================================

production_host_ip = '45.55.49.87'

...

## production/configure/api.service: configure the production systemd
api.service file
.PHONY: production/configure/api.service
production/configure/api.service:
    rsync -P ./remote/production/api.service greenlight@${production_host_ip}:~
    ssh -t greenlight@${production_host_ip} '\
        sudo mv ~/api.service /etc/systemd/system/ \
        && sudo systemctl enable api \
        && sudo systemctl restart api \
    '
```

> **注意：** 要将单元文件复制到 `/etc/systemd/system/` 文件夹（该文件夹由我们 droplet 上的 `root` 用户拥有），我们需要先将其复制到 `greenlight` 用户的主目录中，然后使用 `sudo mv` 命令将其移动到最终位置。

保存 makefile，然后继续运行此新规则。当...时你应该会被提示输入 `greenlight` 用户的密码

```
dsn=postgres://greenlight:pa55word1234@localhost/greenlight -env=production

Apr 19 03:24:35 greenlight-production systemd[1]: Starting Greenlight API service...
Apr 19 03:24:35 greenlight-production systemd[1]: Started Greenlight API service.
Apr 19 03:24:35 greenlight-production api[6997]:
{"level":"INFO","time":"2021-04-19T07:24:35Z", ...}
Apr 19 03:24:35 greenlight-production api[6997]:
{"level":"INFO","time":"2021-04-19T07:24:35Z", ...}
```

太好了！这证实了我们的 `api` 服务已成功在后台运行，并且在我这里，它的 PID（进程 ID）为 6997。

出于兴趣，让我们也快速列出 `greenlight` 用户的正在运行的进程：

```
greenlight@greenlight-production:~$ ps -U greenlight
    PID TTY          TIME CMD
    6997 ?        00:00:00 api
    7043 ?        00:00:00 systemd
    7048 ?        00:00:00 (sd-pam)
    7117 ?        00:00:00 sshd
    7118 pts/0    00:00:00 bash
    7148 pts/0    00:00:00 ps
```

这与预期一致——我们可以在这里看到 PID 为 6997 的 `api` 进程，这证实了确实是我们的 `greenlight` 用户在运行 `api` 二进制文件。

最后，让我们从外部视角检查一下，并再次尝试向我们的 healthcheck 端点发出请求，可以使用浏览器或 `curl`。你应该会得到如下所示的成功响应：

```
$ curl 45.55.49.87:4000/v1/healthcheck
{
  "status": "available",
  "system_info": {
    "environment": "production",
    "version": "v1.0.0-1-gf27fd0f"
  }
}
```

## 重启后重新启动

在我们复制 systemd 单元文件后，通过在 makefile 中运行 `systemctl enable api` 命令，我们的 API 服务应该在 droplet 重启后自动启动。

如果你愿意，可以自己验证这一点。在通过 SSH 连接到 droplet 的同时，继续重启它（确保你连接到的是 droplet，不要意外重启本地机器！）。

```
greenlight@greenlight-production:~$ sudo reboot
greenlight@greenlight-production:~$ Connection to 45.55.49.87 closed by remote host.
Connection to 45.55.49.87 closed.
make: *** [Makefile:91: production/connect] Error 255
```

等待一分钟，让重启完成并让 droplet 重新上线。然后你应该能够重新连接并使用 `systemctl status` 检查服务是否再次运行。如下所示：

```
$ make production/connect
greenlight@greenlight-production:~$ sudo systemctl status api.service
[sudo] password for greenlight:
● api.service - Greenlight API service
    Loaded: loaded (/etc/systemd/system/api.service; enabled; vendor preset: enabled)
    Active: active (running) since Mon 2021-04-19 03:36:26 EDT; 16s ago
    Main PID: 774 (api)
    Tasks: 5 (limit: 1136)
    Memory: 8.7M
    CGroup: /system.slice/api.service
            └─774 /home/greenlight/api -port=4000 -db-dsn=postgres://greenlight:pa55word1234@localhost/greenlight -env=production

Apr 19 03:36:26 greenlight-production systemd[1]: Starting Greenlight API service...
Apr 19 03:36:26 greenlight-production systemd[1]: Started Greenlight API service.
Apr 19 03:36:26 greenlight-production api[774]: {"level":"INFO","time":"2021-04-19T07:36:26Z", ...}
Apr 19 03:36:26 greenlight-production api[774]: {"level":"INFO","time":"2021-04-19T07:36:26Z", ...}
```

## 禁用端口 4000

如果你一直在按照本书本节的步骤操作，让我们撤销之前所做的临时防火墙更改，并再次禁止端口 4000 的流量。

```
greenlight@greenlight-production:~$ sudo ufw delete allow 4000/tcp
Rule deleted
Rule deleted (v6)
greenlight@greenlight-production:~$ sudo ufw status
Status: active

| 目标 | 操作 | 来源 |
|---|---|---|
| 22 | 允许 | 任何地方 |
| 80/tcp | 允许 | 任何地方 |
| 443/tcp | 允许 | 任何地方 |
| 22 (v6) | 允许 | 任何地方 (v6) |
| 80/tcp (v6) | 允许 | 任何地方 (v6) |
| 443/tcp (v6) | 允许 | 任何地方 (v6) |
```

## 附加信息

### 在受限端口上监听

如果你不打算在反向代理后面运行应用程序，并且想直接在端口 80 或 443 上监听请求，你需要设置单元文件，使服务具有 `CAP_NET_BIND_SERVICE` 能力（这将允许它绑定到受限端口）。例如：



`cmd/api/main.go` 文件 — 包含你的 Mailtrap 收件箱的 SMTP 凭据。在正常情况下，你也希望将生产环境的 SMTP 凭据作为此命令的一部分设置在单元文件中。

## 附加单元文件选项

Systemd 单元文件提供了大量的配置选项，而本章我们才刚刚触及皮毛。有关更多信息，《Understanding Systemd Units and Unit Files》文章是一个很好的概述，你也可以在手册页中找到全面（尽管很密集）的信息。

还有这个 gist，详细介绍了可用于加固服务的各种安全选项。

## 使用 Caddy 作为反向代理

我们现在处于 Greenlight API 应用已作为后台服务在我们的 Droplet 上运行并监听端口 4000 上的 HTTP 请求的状态。同时，Caddy 也作为后台服务运行并监听端口 80 上的 HTTP 请求。

因此，设置生产环境下一步是配置 Caddy 作为反向代理，将其收到的任何 HTTP 请求转发到我们的 API。

配置 Caddy 最简单的方法是创建一个 Caddyfile —— 其中包含一系列描述我们希望 Caddy 执行的操作的规则。如果你跟着操作，请在项目目录中创建一个新的 remote/production/Caddyfile 文件：

```
$ touch remote/production/Caddyfile
```

然后添加以下内容，确保将 IP 地址替换为你自己的 Droplet 地址：

```
File: remote/production/Caddyfile

http://45.55.49.87 {
    reverse_proxy localhost:4000
}
```

仅凭外观你大概就能猜到，这个规则告诉 Caddy 我们希望它监听发往 45.55.49.87 的 HTTP 请求，然后充当反向代理，将请求转发到本地机器的端口 4000（我们的 API 在此监听）。

> **提示：** Caddyfile 有 *很多* 可用的设置，我们将在本章 iler... 但如果你计划在自己的生产项目中使用 Caddy，那么我建议阅读官方 Caddyfile 文档，其非常出色。

下一步我们需要做的是将此 Caddyfile 上传到我们的 Droplet 并重新加载 Caddy 使更改生效。

为此，让我们更新 makefile 以包含一个新的 `production/configure/caddyfile` 规则。这将遵循我们在上一章中用于上传 `api.service` 文件时使用的大致相同模式，但我们将改为将 Caddyfile 复制到服务器上的 `/etc/caddy/Caddyfile`。

像这样：

```
File: Makefile

#
================================================================================
====== #
# PRODUCTION
#
================================================================================
====== #

production_host_ip = '45.55.49.87'

...

## production/configure/caddyfile: configure the production Caddyfile
.PHONY: production/configure/caddyfile
production/configure/caddyfile:
    rsync -P ./remote/production/Caddyfile greenlight@${production_host_ip}:~
    ssh -t greenlight@${production_host_ip} '\
        sudo mv ~/Caddyfile /etc/caddy/ \
        && sudo systemctl reload caddy \
    '
```

做出该更改后，请继续运行该规则将 Caddyfile 部署到生产环境：

```
$ make production/configure/caddyfile
rsync -P ./remote/production/Caddyfile greenlight@"45.55.49.87":~
sending incremental file list
Caddyfile
               53 100%    0.00kB/s    0:00:00 (xfr#1, to-chk=0/1)
ssh -t greenlight@"45.55.49.87" '\
```
```bash
sudo mv ~/Caddyfile /etc/caddy/ \
&& sudo systemctl reload caddy \
'
[sudo] password for greenlight:
Connection to 45.55.49.87 closed.
```

你应该会看到 Caddyfile 已成功复制，并且重新加载在没有任何错误的情况下干净地执行。

此时，你可以在网页浏览器中访问 http://<your_droplet_ip>/v1/healthcheck，你会发现请求已从 Caddy 成功转发到我们的 API。如下所示：

![](img/30f9221bfc265d52b544dd595ca099de_851_0.png)

## 阻止访问应用程序指标

在浏览器中，让我们导航到显示应用程序指标的 GET /debug/vars 端点。你应该会看到类似这样的响应：

![](img/30f9221bfc265d52b544dd595ca099de_852_0.png)

如我们之前提到的，将此敏感信息公开访问并不是一个好主意。

幸运的是，通过在我们的 Caddyfile 中添加一个新的 respond 指令，就很容易阻止对此的访问，如下所示：

```
File: remote/production/Caddyfile

http://45.55.49.87 {
  respond /debug/* "Not Permitted" 403
  reverse_proxy localhost:4000
}
```

通过这个新指令，我们指示 Caddy 对所有 URL 路径以 /debug/ 开头的请求发送 403 Forbidden 响应。

继续将此更改再次部署到生产环境，并在网页浏览器中刷新页面，你会发现它现在已被阻止。

```
$ make production/configure/caddyfile
```

![](img/30f9221bfc265d52b544dd595ca099de_854_0.png)

尽管指标不再公开可访问，但你仍可以通过 SSH 连接到 Droplet 并向 http://localhost:4000/debug/vars 发出请求来访问它们。

```
$ make production/connect
greenlight@greenlight-production:~$ curl http://localhost:4000/debug/vars
{
"cmdline": ..., 
"database": ..., 
"goroutines": 7, 
"memstats": ..., 
"timestamp": 1618820037, 
"total_processing_time_µs": 1305, 
"total_requests_received": 8, 
"total_responses_sent": 7, 
"total_responses_sent_by_status": {"200": 3, "404": 4}, 
}
```

```
"version": "v1.0.0-1-gf27fd0f"
}
```

或者，你可以打开一个 SSH 隧道到 Droplet，并使用你 *本地机器* 上的网页浏览器查看它们。例如，你可以通过运行以下命令在 Droplet 上的端口 `4000` 与本地机器上的端口 `9999` 之间打开一个 SSH 隧道（确保将 *两个* IP 地址都替换为你自己的 Droplet IP）：

```
$ ssh -L :9999:45.55.49.87:4000 greenlight@45.55.49.87
```

在该隧道处于活动状态时，你应该能够在网页浏览器中访问 [http://localhost:9999/debug/vars](http://localhost:9999/debug/vars) 并看到你的应用程序指标，如下所示：

![](img/30f9221bfc265d52b544dd595ca099de_856_0.png)

## 使用域名

对于部署的下一步，我们将配置 Caddy，以便可以通过域名访问我们的 Droplet，而不是需要使用 IP 地址。

如果你想跟随此步骤，你需要拥有一个域名并能够更新该域名的 DNS 记录。如果你没有可用的域名，那么你可以通过 Freenom 服务获取一个免费域名。

我将在此示例代码中使用域名 greenlight.alexedwards.net，但如果你在跟随操作，请将其替换为你自己的域名。

你需要做的第一件事是配置域名的 DNS 记录，使其包含指向 Droplet IP 地址的 A 记录。所以在我的例子中，DNS 记录看起来像这样：

```
A    greenlight.alexedwards.net    45.55.49.87
```

> 注意：如果不确定如何更改 DNS 记录，你的域名注册商应提供指导和文档。

一旦 DNS 记录就位，下一步任务是更新 Caddyfile 以使用你的域名而不是 Droplet 的 IP 地址。请按如下方式将其替换（请记住将 greenlight.alexedwards.net 替换为你自己的域名）：

```
File: remote/production/Caddyfile

http://greenlight.alexedwards.net {
  respond /debug/* "Not Permitted" 403
  reverse_proxy localhost:4000
}
```

然后再次将 Caddyfile 重新部署到你的 Droplet：

```
$ make production/configure/caddyfile
```

完成后，你现在应该能够通过在浏览器中访问 http://<your_domain_name>/v1/healthcheck 来通过域名访问 API：

![](img/30f9221bfc265d52b544dd595ca099de_858_0.png)

## 启用 HTTPS



现在我们已经设置好了域名，可以用上 Caddy 的一个主打功能：*自动 HTTPS*。

Caddy 会自动通过 Let’s Encrypt 为你的域名处理 TLS 证书的签发和续期，同时将所有 HTTP 请求重定向到 HTTPS。它的设置非常简单，非常稳健，让你无需再手动跟踪证书续期。

要启用这一功能，我们只需要更新我们的 `Caddyfile`，让它看起来像这样：

```
File: remote/production/Caddyfile

# Set the email address that should be used to contact you if there is a problem with
# your TLS certificates.
{
  email you@example.com
}

# Remove the http:// prefix from your site address.
greenlight.alexedwards.net {
  respond /debug/* "Not Permitted" 403
  reverse_proxy localhost:4000
}
```

这是最后一次，请将这个 Caddyfile 更新部署到你的 droplet……

```
$ make production/configure/caddyfile
```

然后，当你在 Web 浏览器中刷新页面时，你应该会发现它被自动重定向到该页面的 HTTPS 版本。

![](img/30f9221bfc265d52b544dd595ca099de_860_0.png)

> **重要提示：** 如果刷新页面时出现错误，请等待几秒钟后再试一次。Caddy 有时可能需要一点时间才能完成首次证书设置。

如果你使用的是 Firefox，还可以按 `Ctrl+i` 在浏览器中查看页面信息。它看起来应该类似这样：

![](img/30f9221bfc265d52b544dd595ca099de_861_0.png)

从中我们可以看出，连接已成功使用 TLS 1.3 和 TLS_AES_128_GCM_SHA256 密码套件进行加密。

最后，如果你愿意，可以使用 curl 尝试向应用程序发出 HTTP 请求。你应该会看到它返回一个 308 Permanent Redirect，指向该应用程序的 HTTPS 版本，如下所示：

```
$ curl -i http://greenlight.alexedwards.net
HTTP/1.1 308 Permanent Redirect
Connection: close
Location: https://greenlight.alexedwards.net/
Server: Caddy
Date: Mon, 19 Apr 2021 08:36:20 GMT
Content-Length: 0
```

第 22 章。

## 附录

- 管理密码重置
- 创建额外的激活令牌
- 使用 JSON Web 令牌进行身份验证
- JSON 编码细微差别
- JSON 解码细微差别
- 请求内容超时

## 管理密码重置

如果你正在构建的 API 面向公众用户，那么你很可能会希望加入用户在忘记密码时重置密码的功能。

为了在你的 API 中支持这一点，你可以添加以下两个端点：

| 方法 | URL 模式 | 处理器 | 操作 |
|---|---|---|---|
| POST | /v1/tokens/password-reset | createPasswordResetTokenHandler | 生成一个新的密码重置令牌 |
| PUT | /v1/users/password | updateUserPasswordHandler | 更新指定用户的密码 |

并实现如下工作流：

- 1. 客户端向 `POST /v1/tokens/password-reset` 端点发送请求，其中包含想要重置密码的用户的电子邮件地址。
- 2. 如果 `users` 表中存在具有该电子邮件地址的用户，*并且该用户已通过激活确认了其电子邮件地址*，则生成一个加密安全的高熵随机令牌。
- 3. 将此令牌的哈希值与用户 ID 以及该令牌的较短（30-60 分钟）过期时间一起存储在 `tokens` 表中。
- 4. 通过电子邮件将原始（未哈希的）令牌发送给用户。
- 5. 如果该电子邮件地址的所有者没有请求密码重置令牌，他们可以忽略这封电子邮件。
- 6. 否则，他们可以将该令牌连同新密码一起提交到 `PUT /v1/users/password` 端点。如果该令牌的哈希值存在于 `tokens` 表中且尚未过期，则生成新密码的 bcrypt 哈希并更新该用户的记录。
- 7. 删除该用户所有现有的密码重置令牌。

在我们的代码库中，你可以通过创建一个新的 `password-reset` 令牌作用域来实现此工作流：

```
File: internal/data/tokens.go

```go
package data

...

const (
    ScopeActivation      = "activation"
    ScopeAuthentication = "authentication"
    ScopePasswordReset  = "password-reset"
)

...
```
```

```
v.AddError("email", "no matching email address found")
    app.failedValidationResponse(w, r, v.Errors)
default:
    app.serverErrorResponse(w, r, err)
}
    return
}

// Return an error message if the user is not activated.
    if !user.Activated {
        v.AddError("email", "user account must be activated")
        app.failedValidationResponse(w, r, v.Errors)
        return
    }

// Otherwise, create a new password reset token with a 45-minute expiry time.
    token, err := app.models.Tokens.New(user.ID, 45*time.Minute,
data.ScopePasswordReset)
    if err != nil {
        app.serverErrorResponse(w, r, err)
        return
    }

// Email the user with their password reset token.
app.background(func() {
    data := map[string]interface{}{
        "passwordResetToken": token.Plaintext,
    }

    // Since email addresses MAY be case sensitive, notice that we are sending this
    // email using the address stored in our database for the user --- not to the
    // input.Email address provided by the client in this request.
    err = app.mailer.Send(user.Email, "token_password_reset.tmpl", data)
    if err != nil {
        app.logger.PrintError(err, nil)
    }
}
```

```
```go
})

// Send a 202 Accepted response and confirmation message to the client.
env := envelope{"message": "an email will be sent to you containing password reset instructions"}

err = app.writeJSON(w, http.StatusAccepted, env, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```
```

```
File: cmd/api/users.go

package main

...

// Verify the password reset token and set a new password for the user.
func (app *application) updateUserPasswordHandler(w http.ResponseWriter, r *http.Request) {
    // Parse and validate the user's new password and password reset token.
    var input struct {
        Password     string `json:"password"`
        TokenPlaintext string `json:"token"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    v := validator.New()
```
```

```
data.ValidatePasswordPlaintext(v, input.Password)
data.ValidateTokenPlaintext(v, input.TokenPlaintext)

if !v.Valid() {
    app.failedValidationResponse(w, r, v.Errors)
    return
}

// Retrieve the details of the user associated with the password reset token,
// returning an error message if no matching record was found.
user, err := app.models.Users.GetForToken(data.ScopePasswordReset,
input.TokenPlaintext)
if err != nil {
    switch {
    case errors.Is(err, data.ErrRecordNotFound):
        v.AddError("token", "invalid or expired password reset token")
        app.failedValidationResponse(w, r, v.Errors)
    default:
        app.serverErrorResponse(w, r, err)
    }
    return
}

// Set the new password for the user.
err = user.Password.Set(input.Password)
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

// Save the updated user record in our database, checking for any edit conflicts as
// normal.
err = app.models.Users.Update(user)
if err != nil {
    switch {
    case errors.Is(err, data.ErrEditConflict):
        app.editConflictResponse(w, r)
```

```
default:
    app.serverErrorResponse(w, r, err)
}
    return
}

    // If everything was successful, then delete all password reset tokens
    for the user.
    err = app.models.Tokens.DeleteAllForUser(data.ScopePasswordReset,
    user.ID)
    if err != nil {
        app.serverErrorResponse(w, r, err)
        return
    }

    // Send the user a confirmation message.
    env := envelope{"message": "your password was successfully reset"}

    err = app.writeJSON(w, http.StatusOK, env, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

你还应该创建一个 `internal/mailer/templates/token_password_reset.tmpl` 文件，其中包含密码重置电子邮件的邮件模板，类似于这样：

```
File: internal/mailer/templates/token_password_reset.tmpl

{{define "subject"}}Reset your Greenlight password{{end}}

{{define "plainBody"}}
```


```text
Hi,

Please send a `PUT /v1/users/password` request with the following JSON body to set a new password:

{"password": "your new password", "token": "{{.passwordResetToken}}"}

Please note that this is a one-time use token and it will expire in 45 minutes. If you need another token please make a `POST /v1/tokens/password-reset` request.

Thanks,

The Greenlight Team
{{end}}

{{define "htmlBody"}}
<!doctype html>
<html>
    <head>
        <meta name="viewport" content="width=device-width" />
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    </head>
    <body>
        <p>Hi,</p>
        <p>Please send a <code>PUT /v1/users/password</code> request with the following JSON body to set a new password:</p>
        <pre><code>
        {"password": "your new password", "token": "{{.passwordResetToken}}"}
        </code></pre>
        <p>Please note that this is a one-time use token and it will expire in 45 minutes.
        If you need another token please make a <code>POST /v1/tokens/password-reset</code> request.</p>
        <p>Thanks,</p>
        <p>The Greenlight Team</p>
    </body>
</html>
{{end}}
```

并将必要的路由添加到 cmd/api/routes.go 文件中：

```go
File: cmd/api/routes.go

package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck", app.healthcheckHandler)

    router.HandlerFunc(http.MethodGet, "/v1/movies", app.requirePermission("movies:read", app.listMoviesHandler))
    router.HandlerFunc(http.MethodPost, "/v1/movies", app.requirePermission("movies:write", app.createMovieHandler))
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id", app.requirePermission("movies:read", app.showMovieHandler))
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id", app.requirePermission("movies:write", app.updateMovieHandler))
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id", app.requirePermission("movies:write", app.deleteMovieHandler))

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated", app.activateUserHandler)

    // Add the PUT /v1/users/password endpoint.
    router.HandlerFunc(http.MethodPut, "/v1/users/password", app.updateUserPasswordHandler)

    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication", app.createAuthenticationTokenHandler)

    // Add the POST /v1/tokens/password-reset endpoint.
    router.HandlerFunc(http.MethodPost, "/v1/tokens/password-reset", app.createPasswordResetTokenHandler)

    router.Handler(http.MethodGet, "/debug/vars", expvar.Handler())

    return app.metrics(app.recoverPanic(app.enableCORS(app.rateLimit(app.authenticate(router)))))
}
```

一旦所有这些都就绪，你应该能够通过以下请求来请求新的密码重置令牌：

```text
$ curl -X POST -d '{"email": "alice@example.com"}' localhost:4000/v1/tokens/password-reset
{
  "message": "an email will be sent to you containing password reset instructions"
}
```

然后你可以通过发送包含邮件中收到的令牌的请求来启动实际的密码更改。例如：

```text
$ BODY='{"password": "your new password", "token": "Y7QCRZ7FWOWYLXLAOC2VYOLIPY"}'
$ curl -X PUT -d "$BODY" localhost:4000/v1/users/password
```

```text
{
  "message": "your password was successfully reset"
}
```

## 附加信息

### Web 应用程序工作流程

就像我们之前看到的激活工作流程一样，如果你的 API 是网站的后端（而不是完全独立的服务），你可以调整此密码重置工作流程，使其对用户更直观。

例如，你可以要求用户在网站上的表单中输入令牌以及新密码，并使用一些 JavaScript 将表单内容提交到你的 `PUT /v1/users/password` 端点。支持此工作流程的电子邮件可能如下所示：

```text
Hi,

To reset your password please visit https://example.com/users/password and enter the following secret code along with your new password:

-----------------------
Y7QCRZ7FWOWYLXLAOC2VYOLIPY
--------------------------

Please note that this code will expire in 45 minutes. If you need another code please visit https://example.com/tokens/password-reset.

Thanks,

The Greenlight Team
```

另外，如果你不希望用户复制粘贴令牌，你可以要求他们点击包含令牌的链接，该链接会将他们带到你网站上的页面。类似这样：

```text
Hi,

To reset your password please click the following link:

https://example.com/users/password?token=Y7QCRZ7FWOWYLXLAOC2VYOLIPY

Please note that this link will expire in 45 minutes. If you need another password reset link please visit https://example.com/tokens/password-reset.

Thanks,

The Greenlight Team
```

此页面随后可以显示一个表单，用户在其中输入新密码，然后网页上的一些 JavaScript 应该从 URL 中提取令牌并将其与新密码一起提交到 `PUT /v1/users/password` 端点。同样，如果你选择第二个选项，你需要采取措施避免令牌在引用标头中泄露。

### 第 22.2 章. 创建额外的激活令牌

你可能还想为你的 API 添加一个独立的端点来生成激活令牌。这在用户未能及时激活账户或从未收到欢迎邮件的情况下会很有用。

在本附录中，我们将快速介绍执行此操作的代码，并添加以下端点：

| 方法 | URL 模式 | 处理程序 | 操作 |
|--------|-------------|---------|--------|
| POST | /v1/tokens/activation | createActivationTokenHandler | 生成新的激活令牌 |

createActivationTokenHandler 处理程序的代码应如下所示：

```go
File: cmd/api/tokens.go

...

func (app *application) createActivationTokenHandler(w http.ResponseWriter, r *http.Request) {
    // Parse and validate the user's email address.
    var input struct {
        Email string `json:"email"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    v := validator.New()

    if data.ValidateEmail(v, input.Email); !v.Valid() {
        app.failedValidationResponse(w, r, v.Errors)
        return
    }

    // Try to retrieve the corresponding user record for the email address. If it can't
    // be found, return an error message to the client.
    user, err := app.models.Users.GetByEmail(input.Email)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrRecordNotFound):
            v.AddError("email", "no matching email address found")
            app.failedValidationResponse(w, r, v.Errors)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }

    // Return an error if the user has already been activated.
    if user.Activated {
        v.AddError("email", "user has already been activated")
        app.failedValidationResponse(w, r, v.Errors)
        return
    }
}
```

你还需要创建一个 `internal/mailer/templates/token_activation.tmpl` 文件，其中包含必要的电子邮件模板，类似于以下内容：

```text
File: internal/mailer/templates/token_activation.tmpl

{{define "subject"}}Activate your Greenlight account{{end}}

{{define "plainBody"}}
Hi,

Please send a `PUT /v1/users/activated` request with the following JSON body to activate your account:

{"token": "{{.activationToken}}"}

Please note that this is a one-time use token and it will expire in 3 days.

Thanks,

The Greenlight Team
{{end}}

{{define "htmlBody"}}
<!doctype html>
<html>
    <head>
        <meta name="viewport" content="width=device-width" />
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    </head>
    <body>
        <p>Hi,</p>
        <p>Please send a <code>PUT /v1/users/activated</code> request with the following JSON body to activate your account:</p>
        <pre><code>
        {"token": "{{.activationToken}}"}
```



```html
</code></pre>
    <p>Please note that this is a one-time use token and it will expire in 3 days.</p>
    <p>Thanks,</p>
    <p>The Greenlight Team</p>
  </body>
</html>
{{end}}
```

并更新 cmd/api/routes.go 文件以包含新的端点：

```go
File: cmd/api/routes.go

package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck", app.healthcheckHandler)

    router.HandlerFunc(http.MethodGet, "/v1/movies",
        app.requirePermission("movies:read", app.listMoviesHandler))
    router.HandlerFunc(http.MethodPost, "/v1/movies",
        app.requirePermission("movies:write", app.createMovieHandler))
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
        app.requirePermission("movies:read", app.showMovieHandler))
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
        app.requirePermission("movies:write", app.updateMovieHandler))
    router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
        app.requirePermission("movies:write", app.deleteMovieHandler))

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated",
        app.activateUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/password",
        app.updateUserPasswordHandler)

    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication",
        app.createAuthenticationTokenHandler)
    // Add the POST /v1/tokens/activation endpoint.
    router.HandlerFunc(http.MethodPost, "/v1/tokens/activation",
        app.createActivationTokenHandler)
    router.HandlerFunc(http.MethodPost, "/v1/tokens/password-reset",
        app.createPasswordResetTokenHandler)

    router.Handler(http.MethodGet, "/debug/vars", expvar.Handler())

    return app.metrics(app.recoverPanic(app.enableCORS(app.rateLimit(app.authenticate(router)))))
}
```

现在这些都已就位，用户可以通过提交其电子邮件地址来请求新的激活令牌，如下所示：

```sh
$ curl -X POST -d '{"email": "bob@example.com"}' localhost:4000/v1/tokens/activation
{
    "message": "an email will be sent to you containing activation instructions"
}
```

令牌将通过电子邮件发送给他们，然后他们可以将令牌提交到 `PUT /v1/users/activated` 端点进行激活，与收到欢迎邮件中的令牌时的方式完全相同。

如果你实现这样的端点，需要注意的是，这会允许用户在任何时候同时拥有多个有效的激活令牌‘在进行中’。这没问题——但你只需确保用户成功激活后删除该用户 *所有* 的激活令牌（不仅仅是他们使用的令牌）。

同样，如果你的 API 是网站的后端，那么你可以通过使用我们之前讨论过的同类模式来调整电子邮件和工作流程，使其更直观。

## 使用 JSON Web Token 进行身份验证

在本附录中，我们将把 API 的身份验证流程切换为使用 JSON Web Token（JWT）。

**重要：** 对于这个特定应用程序，使用 JWT 与我们当前的‘有状态令牌’方法相比没有任何好处。JWT 方法更复杂，最终需要相同数量的数据库查询，而且我们失去了撤销令牌的能力。因此，在这里使用它们并没有多大意义。但我仍然想出于两个原因解释这种模式：

- JWT 拥有很大的关注度，作为开发者，你很可能会遇到使用它们进行身份验证的现有代码库，或者外部因素迫使你使用它们。
- 了解它们的工作原理是值得的，以防你需要实现需要 *委托身份验证* 的 API，而这 *正是* 它们有用的场景。

> **注意：** 如果你完全是 JWT 新手，我建议阅读 [JSON Web Token 简介](...) 文章作为入门。

正如我们在书中简要解释的那样，JWT 是一种 *无状态令牌*。它们包含一组 *声明*，这些声明使用对称或非对称签名算法签名，然后使用 base-64 编码。在我们的例子中，我们将使用 JWT 来携带包含已验证用户 ID 的 *主题* 声明。

有几个不同的包可用于在 Go 中相对简单地处理 JWT。在大多数情况下，`pascaldekloe/jwt` 包是不错的选择——它具有清晰简单的 API，并且默认设计为避免一些主要的 JWT 安全漏洞。

如果你想跟随操作，请像这样安装它：

```sh
$ go get github.com/pascaldekloe/jwt@v1.10.0
```

使用 JWT 时需要考虑的第一件事之一是签名算法的选择。

如果你的 JWT 将被 *不同于* 创建它的应用程序消费，那么通常应使用 ECDSA 或 RSA 等非对称密钥算法。‘创建’应用程序使用其私钥对 JWT 进行签名，而‘消费’应用程序使用相应的公钥验证签名。而如果你的 JWT 将被 *创建它的同一应用程序* 消费，那么合适的选择是像 HMAC-SHA256 这样使用随机密钥的（更简单、更快的）对称密钥算法。这就是我们将为 API 使用的方法。

因此，要使 JWT 身份验证正常工作，你首先需要在 `.envrc` 文件中添加用于签名 JWT 的密钥。例如：

```sh
File: .envrc

export GREENLIGHT_DB_DSN=postgres://greenlight:pa55word@localhost/greenlight
export JWT_SECRET=pei3einoh0Beem6uM6Ungohn2heiv5lah1ael4joopie5JaigeikoozaoTew2Eh6
```

**注意：** 你的密钥应为密码学安全的随机字符串，其底层熵至少为 32 字节（256 位）。

然后你需要更新 `Makefile`，在启动应用程序时将密钥作为命令行标志传入，如下所示：

```make
File: Makefile

...
# ============================================================================ #
# DEVELOPMENT
# ============================================================================ #

## run/api: run the cmd/api application
.PHONY: run/api
run/api:
    @go run ./cmd/api -db-dsn=${GREENLIGHT_DB_DSN} -jwt-secret=${JWT_SECRET}

...
```

接下来你需要编辑 `cmd/api/main.go` 文件，以便从命令行标志解析 JWT 密钥到 `config` 结构体中：

```go
File: cmd/api/main.go

package main

...

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
        host      string
        port      int
        username string
        password string
        sender    string
    }
    cors struct {
        trustedOrigins []string
    }
    jwt struct {
        secret string // Add a new field to store the JWT signing secret.
    }
}
...
func main() {
    var cfg config

    ...

    // Parse the JWT signing secret from the command-line flag. Notice that we leave the
    // default value as the empty string if no flag is provided.
    flag.StringVar(&cfg.jwt.secret, "jwt-secret", "", "JWT secret")

    displayVersion := flag.Bool("version", false, "Display version and exit")

    flag.Parse()

    ...
}
...
```

```go
data.ValidatePasswordPlaintext(v, input.Password)

if !v.Valid() {
    app.failedValidationResponse(w, r, v.Errors)
    return
}

user, err := app.models.Users.GetByEmail(input.Email)
if err != nil {
    switch {
    case errors.Is(err, data.ErrRecordNotFound):
        app.invalidCredentialsResponse(w, r)
    default:
        app.serverErrorResponse(w, r, err)
    }
    return
}

match, err := user.Password.Matches(input.Password)
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

if !match {
    app.invalidCredentialsResponse(w, r)
    return
}

// Create a JWT claims struct containing the user ID as the subject, with an issued
// time of now and validity window of the next 24 hours. We also set the issuer and
// audience to a unique identifier for our application.
var claims jwt.Claims
claims.Subject = strconv.FormatInt(user.ID, 10)
claims.Issued = jwt.NewNumericTime(time.Now())
claims.NotBefore = jwt.NewNumericTime(time.Now())
claims.Expires = jwt.NewNumericTime(time.Now().Add(24 * time.Hour))
```




```go
claims.Issuer = "greenlight.alexedwards.net"
claims.Audiences = []string{"greenlight.alexedwards.net"}

// Sign the JWT claims using the HMAC-SHA256 algorithm and the secret key from the
// application config. This returns a []byte slice containing the JWT as a base64-encoded string.
jwtBytes, err := claims.HMACSign(jwt.HS256,
[]byte(app.config.jwt.secret))
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

// Convert the []byte slice to a string and return it in a JSON response.
err = app.writeJSON(w, http.StatusCreated,
envelope{"authentication_token": string(jwtBytes)}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
...
```

请继续引入新的 `github.com/pascaldekloe/jwt` 依赖，并按如下方式运行 API：

```sh
$ make vendor
$ make run/api
```

然后，当你使用有效的电子邮件地址和密码向 `POST /v1/tokens/authentication` 端点发起请求时，现在应该会收到一个包含 JWT 的响应，如下所示（为便于阅读，添加了换行）：

```sh
$ curl -X POST -d '{"email": "faith@example.com", "password": "pa55word"}'
localhost:4000/v1/tokens/authentication
{
    "authentication_token":
"eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJncmVlbmxpZ2h0LmFsFsZXhlZHDcm
RzLm5ldCIsInN1YiI6IjciLCJhdWQiOlsiz3JlZW5saWdodC5hbGV4ZWR3YXJkcy5uZXQiXSwizXh
wIjoxNj
E4OTM4MjY0L jgxOTIwNSwib mJmIjoxNjE4ODUxOD Y0L jgxOTIwNSwiaWF0IjoxNjE4ODUxOD Y0L jg
xOTIwND
    h9.zNK1bJPl5rIr_Yvjy0XuimJwaC3KgPqmW2M1u5RvgeA"
}
```

如果你好奇，可以解码 base64 编码的 JWT 数据。你应该会看到声明的内容与你预期相符，类似于这样：

```json
{"alg":"HS256"}{"iss":"greenlight.alexedwards.net","sub":"7","aud":
["greenlight.alexedwards.net"],
"exp":1618938264.819205,"nbf":1618851864.819205,"iat":1618851864.819204}...
```

接下来，你需要更新 `authenticate()` 中间件，使其接受 `Authorization: Bearer <jwt>` 请求头中的 JWT，验证 JWT，并从 `subject` 声明中提取用户 ID。

当我们说“验证 JWT”时，实际上指的是以下四件事：

- 检查 JWT 的签名是否与 JWT 内容匹配（基于我们的密钥）。这将确认令牌没有被客户端篡改。
- 检查当前时间是否在 JWT 的“not before”和“expires”时间之间。
- 检查 JWT 的“issuer”是否为 `"greenlight.alexedwards.net"`。
- 检查 `"greenlight.alexedwards.net"` 是否在 JWT 的“audiences”中。

请继续按如下方式更新 `authenticate()` 中间件：

```go
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
)
```

```go
"github.com/felixge/httpsnoop"
"github.com/pascaldekloe/jwt" // New import
"github.com/tomasen/realip"
"golang.org/x/time/rate"
)

...
```

```go
func (app *application) authenticate(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Header().Add("Vary", "Authorization")

        authorizationHeader := r.Header.Get("Authorization")

        if authorizationHeader == "" {
            r = app.contextSetUser(r, data.AnonymousUser)
            next.ServeHTTP(w, r)
            return
        }

        headerParts := strings.Split(authorizationHeader, " ")
        if len(headerParts) != 2 || headerParts[0] != "Bearer" {
            app.invalidAuthenticationTokenResponse(w, r)
            return
        }

        token := headerParts[1]

        // Parse the JWT and extract the claims. This will return an error if
        // the JWT contents doesn't match the signature (i.e. the token has been
        // tampered with) or the algorithm isn't valid.
        claims, err := jwt.HMACCheck([]byte(token),
        []byte(app.config.jwt.secret))
        if err != nil {
            app.invalidAuthenticationTokenResponse(w, r)
            return
        }
    }
```

```go
// Check if the JWT is still valid at this moment in time.
if !claims.Valid(time.Now()) {
    app.invalidAuthenticationTokenResponse(w, r)
    return
}

// Check that the issuer is our application.
if claims.Issuer != "greenlight.alexedwards.net" {
    app.invalidAuthenticationTokenResponse(w, r)
    return
}

// Check that our application is in the expected audiences for the JWT.
if !claims.AcceptAudience("greenlight.alexedwards.net") {
    app.invalidAuthenticationTokenResponse(w, r)
    return
}

// At this point, we know that the JWT is all OK and we can trust the data in
// it. We extract the user ID from the claims subject and convert it from a
// string into an int64.
userID, err := strconv.ParseInt(claims.Subject, 10, 64)
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

// Lookup the user record from the database.
user, err := app.models.Users.Get(userID)
if err != nil {
    switch {
    case errors.Is(err, data.ErrRecordNotFound):
        app.invalidAuthenticationTokenResponse(w, r)
    default:
        app.serverErrorResponse(w, r, err)
    }
```

```go
}
return
}

// Add the user record to the request context and continue as normal.
r = app.contextSetUser(r, user)

next.ServeHTTP(w, r)
})
}
```

最后，要让这一切正常工作，你需要创建一个新的 `UserModel.Get()` 方法，根据其 ID 从数据库中检索用户详细信息。

```go
File: internal/data/users.go

package data

...

func (m UserModel) Get(id int64) (*User, error) {
    query := `
        SELECT id, created_at, name, email, password_hash, activated, version
        FROM users
        WHERE id = $1`

    var user User

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    err := m.DB.QueryRowContext(ctx, query, id).Scan(
        &user.ID,
```

```go
&user.CreatedAt,
&user.Name,
&user.Email,
&user.Password.hash,
&user.Activated,
&user.Version,
)

if err != nil {
    switch {
    case errors.Is(err, sql.ErrNoRows):
        return nil, ErrRecordNotFound
    default:
        return nil, err
    }
}

return &user, nil
}
```

现在，你应该能够向受保护的端点之一发起请求，并且只有当请求在 Authorization 头中包含有效的 JWT 时，请求才会成功。例如：

```sh
$ curl -H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJncmlbmxpZ..." localhost:4000/v1/movies/2
{
    "movie": {
        "id": 2,
        "title": "Black Panther",
        "year": 2018,
        "runtime": "134 mins",
        "genres": [
            "sci-fi",

"action",
    "adventure"
],
    "version": 2
}
}

$ curl -H "Authorization: Bearer INVALID" localhost:4000/v1/movies/2
{
    "error": "invalid or missing authentication token"
}
```

> **注意：** 由于 JWT 是 base64 编码的，你可能会发现更改 JWT 中的最后一个字符后，它仍然会被接受为有效。这是正常的，详细原因可参见 StackOverflow 帖子以及此 GitHub issue。

如果你计划将使用 JWT 的系统投入生产，我还建议你花时间阅读并充分理解以下两篇文章：

- JWT 安全最佳实践
- JSON Web Token 库中的关键漏洞

### 第22.4章

## JSON 编码的细微差别

### Nil 切片和空切片的编码方式不同

在 Go 中，Nil 切片将被编码为 JSON 的 `null` 值，而空（但非 nil）切片将被编码为空的 JSON 数组。例如：

```go
var nilSlice []string
emptySlice := []string{}

m := map[string][]string{
    "nilSlice": nilSlice,
    "emptySlice": emptySlice,
}
```

将编码为以下 JSON：

```json
{"emptySlice":[],"nilSlice":null}
```

### 对零值结构体使用 omitempty 无效

`omitempty` 结构体标签指令永远不会认为结构体是空的——即使所有结构体字段都为零值，并且你也对这些字段使用了 `omitempty`。它始终会以对象的形式出现在编码后的 JSON 中。例如，以下结构体：

```go
s := struct {
    Foo struct {
        Bar string `json:",omitempty"`
    } `json:",omitempty"`
}{}
```

将编码为以下 JSON：

```json
{"Foo":{}}
```

长期存在一个讨论更改此行为的提案，但 Go 1 兼容性承诺意味着这种情况不太可能很快发生。相反，你可以通过将该字段设置为指向结构体的指针来绕过此问题，因为 `omitempty` 会将 nil 指针视为空。例如：

```go
s := struct {
    Foo *struct {
        Bar string `json:",omitempty"`
    } `json:",omitempty"`
}{}
```

 和 [/content] 之间。我们已经在开头和结尾加了。

注意：原文中在 [content] 之后没有空行，我们也没有。

现在，最终输出。[content]
将编码为如下所示的空 JSON 对象：

```
{}
```

## 在零值 time.Time 上使用 omitempty 不起作用

在零值 `time.Time` 字段上使用 `omitempty` 不会在 JSON 对象中隐藏它。这是因为 `time.Time` 类型在幕后是一个结构体，并且如上所述，`omitempty` 从不认为结构体是空的。相反，字符串 `"0001-01-01T00:00:00Z"` 会出现在 JSON 中（这是对零值 `time.Time` 调用 `MarshalJSON()` 方法返回的值）。例如，以下结构体：

```
s := struct {
    Foo time.Time `json:",omitempty"`
}{}
```

将编码为如下 JSON：

```
{"Foo":"0001-01-01T00:00:00Z"}
```

## 结构体标签不支持非 ASCII 标点字符

当使用结构体标签来更改 JSON 对象中的键时，任何包含非 ASCII 标点字符的标签都将被忽略。值得注意的是，这意味着你不能在结构体标签中使用短破折号或长破折号，以及大多数货币符号。例如，以下结构体：

```
s := struct {
    CostUSD string `json:"cost $"` // This is OK.
    CostEUR string `json:"cost €"` // This contains the non-ASCII punctuation character
    // € and will be ignored.
}{
    CostUSD: "100.00",
    CostEUR: "100.00",
}
```

将编码为以下 JSON（请注意，重命名 CostEUR 键的结构体标签已被忽略）：

```
{"cost $":"100.00","CostEUR":"100.00"}
```

## 整数、time.Time 和 net.IP 值可用作映射键

可以将整数作为映射键来编码映射。在生成的 JSON 中，整数将自动转换为字符串（因为 JSON 对象中的键必须始终是字符串）。例如，以下映射：

```
m := map[int]string{
  123: "foo",
  456_000: "bar",
}
```

将编码为如下 JSON：

```
{"123":"foo","456000":"bar"}
```

此外，实现了 `encoding.TextMarshaler` 接口的映射键也受支持。这意味着你也可以开箱即用地将 `time.Time` 和 `net.IP` 值用作映射键。例如，以下映射：

```
t1 := time.Now()
t2 := t1.Add(24 * time.Hour)

m := map[time.Time]string{
  t1: "foo",
  t2: "bar",
}
```

将编码为类似于以下的 JSON：

```
{"2009-11-10T23:00:00Z":"foo","2009-11-11T23:00:00Z":"bar"}
```

## 字符串中的尖括号和与号会被转义

如果字符串包含尖括号 `<` 或 `>`，则在编码为 JSON 时，这些字符将被转义为 Unicode 字符代码 `\u003c` 和 `\u003e`。同样，`&` 字符将被转义为 `\u0026`。这是为了防止某些 Web 浏览器意外地将 JSON 响应解释为 HTML。例如，以下切片：

```
s := []string{
    "<foo>",
    "bar & baz",
}
```

将编码为如下 JSON：

```
["\u003cfoo\u003e","bar \u0026 baz"]
```

如果你想防止这些字符被转义，你需要使用一个带有 `SetEscapeHTML(false)` 的 `json.Encoder` 实例来执行编码。

## 浮点数尾随的零会被移除

当编码一个小数部分以零结尾的浮点数时，任何尾随的零都不会出现在 JSON 中。例如：

```
s := []float64{
    123.0,
    456.100,
    789.990,
}
```

将编码为如下 JSON：

```
[123,456.1,789.99]
```

## 使用预计算的 JSON

如果你有一个包含“预计算”或“预编码”JSON 的字符串或 `[]byte` 切片，默认情况下，Go 在编码时会像对待任何其他字符串或 `[]byte` 切片一样对待它。这意味着字符串将被转义并编码为 JSON 字符串，而字节切片将被编码为 base-64 JSON 字符串。例如，以下结构体：

```
m := struct {
    Person string
}{
    Person: `{"name": "Alice", "age": 21}`,
}
```

将编码为：

```
{"Person":"{\"name\": \"Alice\", \"age\": 21}"}
```

如果你想不加任何修改地插入预计算的 JSON，你需要将预计算的 JSON 值转换为 `json.RawMessage` 类型。然后 Go 会将其直接插入到其余 JSON 中。例如：

```
m := struct {
    Person json.RawMessage
}{
    Person: json.RawMessage(`{"name": "Alice", "age": 21}`),
}
```

将编码为如下 JSON：

```
```json
{"Person":{"name":"Alice","age":21}}
```
```

> **重要**：使用 `json.RawMessage` 时要小心，确保预计算的值包含有效的 JSON，否则在尝试编码父对象时会出错。如果你需要在运行时检查这一点，可以使用 `json.Valid()` 函数。

## MarshalText 回退

如果一个类型*没有* `MarshalJSON()` 方法，但*确实有* `MarshalText()` 方法（因此它实现了 `encoding.TextMarshaler` 接口），那么 Go 在 JSON 编码期间将回退到调用该方法，并将结果表示为 JSON 字符串。

例如，如果你运行以下代码：

```
```go
type myFloat float64

func (f myFloat) MarshalText() ([]byte, error) {
    return []byte(fmt.Sprintf("%.2f", f)), nil
}

func main() {
    f := myFloat(1.0/3.0)

    js, err := json.Marshal(f)
}
```
```

```
if err != nil {
    log.Fatal(err)
}

fmt.Printf("%s", js)
}
```

它将把 `MarshalText()` 的返回值作为 JSON 字符串打印出来：

```
"0.33"
```

## 使用 MarshalJSON 时接收者很重要

我们在本书前面已经提到过这一点，但确实值得强调，因为它经常让人措手不及。如果你在自定义类型上实现了 `MarshalJSON()` 方法，并且 `MarshalJSON()` 方法使用指针接收者，那么它只会在你编码指向自定义类型的指针时被使用。对于任何自定义类型的值，它将被完全忽略。

如果你在 Go playground 上运行这段代码，就能看到实际效果。

除非你特别想要这种行为，否则我建议养成总是为 `MarshalJSON()` 方法使用值接收者的习惯，就像我们在本书中所做的那样。

```
fmt.Printf("tooShortArray: %v\n", tooShortArray)
fmt.Printf("tooLongArray: %v\n", tooLongArray)
```

将打印出：

```
tooShortArray: [1 2]
tooLongArray: [1 2 3 0]
```

## 部分 JSON 解码

如果你有大量 JSON 输入需要处理，但只需要其中的一小部分，通常可以利用 `json.RawMessage` 类型来帮助处理。例如：

```
// Let's say that the only thing we're interested in is processing the
// "genres" array in
// the following JSON object
js := `{"title": "Top Gun", "genres": ["action", "romance"], "year": 1986}`

// Decode the JSON object to a map[string]json.RawMessage type. The
json.RawMessage
// values in the map will retain their original, un-decoded, JSON values.
var m map[string]json.RawMessage

err := json.NewDecoder(strings.NewReader(js)).Decode(&m)
if err != nil {
    log.Fatal(err)
}

// We can then access the JSON "genres" value from the map and decode it as

| JSON 类型 | ⇒ | interface{} 的底层 Go 类型 |
|---|---|---|
| JSON 布尔值 | ⇒ | bool |
| JSON 字符串 | ⇒ | string |
| JSON 数字 | ⇒ | float64 |
| JSON 数组 | ⇒ | []interface{} |
| JSON 对象 | ⇒ | map[string]interface{} |
| JSON 空值 | ⇒ | nil |

解码为 `interface{}` 类型在以下情况下很有用：

- 你事先不知道你要解码的确切内容。
- 你需要解码包含不同 JSON 类型项的 JSON 数组。
- JSON 对象中的键/值对并不总是包含相同 JSON 类型的值。

例如，考虑以下代码：

```
// This JSON array contains both JSON string and JSON boolean types.
js := `["foo", true]`

// Decode the JSON into a []interface{} slice.
var s []interface{}

err := json.NewDecoder(strings.NewReader(js)).Decode(&s)
```

```
```go
if err != nil {
    log.Fatal(err)
}

// The first value in the slice will have the underlying Go type string, the
second will
// have the underlying Go type bool. We can then type assert them and print
them out
// the values along with their underlying type.
fmt.Printf("item: 0; type: %T; value: %v\n", s[0], s[0].(string))
fmt.Printf("item: 1; type: %T; value: %v\n", s[1], s[1].(bool))
```
```

这将打印出：

```
```
item: 0; type: string; value: foo
item: 1; type: bool; value: true
```
```

## 将 JSON 数字解码为 `interface{}`

如上表所示，当你将 JSON 数字解码为 `interface{}` 类型时，该值的底层类型将是 `float64`——即使它在原始 JSON 中是整数。例如：

```
```go
js := `10` // This JSON number is an integer.

var n interface{}

err := json.NewDecoder(strings.NewReader(js)).Decode(&n)
if err != nil {
    log.Fatal(err)
```




```
}

fmt.Printf("type: %T; value: %v\n", n, n)
```

## 将打印：

```
type: float64; value: 10
```

如果你想将值作为整数获取（而不是 `float64`），你应该在解码之前对你的 `json.Decoder` 实例调用 `UseNumber()` 方法。这将导致所有 JSON 数字被解码为底层类型 `json.Number` 而不是 `float64`。

`json.Number` 类型随后提供了一个 `Int64()` 方法，你可以调用它来将数字作为 `int64` 获取，或者 `String()` 方法来将数字作为 `string` 获取。例如：

```
js := `10`

var n interface{}

dec := json.NewDecoder(strings.NewReader(js))
dec.UseNumber() // Call the UseNumber() method on the decoder before using it.
err := dec.Decode(&n)
if err != nil {
    log.Fatal(err)
}
```

```go
// Type assert the interface{} value to a json.Number, and then call the
Int64() method
// to get the number as a Go int64.
nInt64, err := n.(json.Number).Int64()
if err != nil {
    log.Fatal(err)
}

// Likewise, you can use the String() method to get the number as a Go
string.
nString := n.(json.Number).String()

fmt.Printf("type: %T; value: %v\n", n, n)
fmt.Printf("type: %T; value: %v\n", nInt64, nInt64)
fmt.Printf("type: %T; value: %v\n", nString, nString)
```

这将打印出：

```text
type: json.Number; value: 10
type: int64; value: 10
type: string; value: 10
```

## 结构体标签指令

使用结构体标签 `json:"-"` 在结构体字段上会导致在解码 JSON 时将其 *忽略*，即使 JSON 输入中包含对应的键/值对。例如：

```go
js := `{"name": "alice", "age": 21}`
```

## 请求上下文超时

作为本书中用于管理数据库超时的模式的替代方案，我们本可以在处理器中使用请求上下文作为父上下文创建带超时的上下文——然后将上下文传递给数据库模型。

大致来说，模式如下：

```go
func (app *application) exampleHandler(w http.ResponseWriter, r *http.Request) {
    ...
    // Create a context.Context with a one-second timeout deadline and which has the
    // request context as the 'parent'.
    ctx, cancel := context.WithTimeout(r.Context(), time.Second)
    defer cancel()

    // Pass the context on to the Get() method.
    example, err := app.models.Example.Get(ctx, id)
    if err != nil {
        switch {
        case errors.Is(err, data.ErrNotFound):
            app.notFoundResponse(w, r)
        default:
            app.serverErrorResponse(w, r, err)
        }
        return
    }
}
```

```
...
}
```

在很多方面，这样做被认为是一种良好的实践。允许上下文在你的应用程序中“流动”通常是一个好主意，而且这种方法也更灵活——无论谁在调用数据库模型，都可以轻松控制超时持续时间，而不必总是使用数据库模型设定的固定持续时间。

但使用请求上下文作为父上下文会引入大量额外的复杂性。

需要注意的关键是，如果客户端关闭其 HTTP 连接，则 *请求上下文将被取消*。根据 `net/http` 文档：

> 对于传入的服务器请求，[请求] 上下文会在客户端连接关闭时、请求被取消（使用 HTTP/2）或 ServeHTTP 方法返回时被取消。

如果我们使用请求上下文作为父上下文，那么此取消信号将传递到我们的数据库驱动程序 `pq`，正在运行的 SQL 查询将被终止，其方式与上下文超时时完全相同。重要的是，这意味着我们会收到与数据库查询超时时相同的 `pq: canceling statement due to user request` 错误消息。

一方面这是积极的一面——如果没有剩余客户端可以返回响应，我们不妨取消 SQL 查询并释放资源。

另一方面，我们会在两种截然不同的场景中收到相同的错误消息：

- 当数据库查询花费的时间过长时，在这种情况下我们希望将其记录为错误。
- 当客户端关闭连接时——这可能由于许多无害的原因发生，例如用户关闭浏览器标签页或终止进程。从我们应用程序的角度来看，这 *真的* 不是错误，我们可能希望忽略它或将其记录为警告。

幸运的是，通过在上下文上调用 `ctx.Err()` 方法，*是可以* 区分这两种场景的。如果上下文被取消（由于客户端关闭连接），则 `ctx.Err()` 将返回错误 `context.Canceled`。如果达到超时，则它将返回 `context.DeadlineExceeded`。如果同时达到截止时间和上下文被取消，则 `ctx.Err()` 将返回先发生的那个。

还需要注意的是，如果客户端在查询被 `sql.DB` 排队时关闭连接，你可能会收到 `context.Canceled` 错误，同样 `Scan()` 也可能返回 `context.Canceled` 错误。

综合起来，一个合理的管理方式是在我们的
数据库模型中检查错误 `pq: canceling statement due to user request`，并在返回之前用 `ctx.Err()` 的错误将其包装。例如：

```
func (m ExampleModel) Get(ctx context.Context, id int64) (*Example, error) {
    query := `SELECT ... FROM examples WHERE id = $1`

    var example Example

    err := m.DB.QueryRowContext(ctx, query, id).Scan(...)

    if err != nil {
        switch {
        case err.Error() == "pq: canceling statement due to user request":
            // Wrap the error with ctx.Err().
            return nil, fmt.Errorf("%v: %w", err, ctx.Err())
        case errors.Is(err, sql.ErrNoRows):
            return nil, ErrNotFound
        default:
            return nil, err
        }
    }

    return &example, nil
}
```

然后在你的处理器中，你可以使用 `errors.Is()` 检查数据库模型返回的错误是否等于（或包装）`context.Canceled`，并相应地处理它。

```
func (app *application) exampleHandler(w http.ResponseWriter, r *http.Request) {
    ...
}
```

```go
ctx, cancel := context.WithTimeout(r.Context(), 3*time.Second)
defer cancel()

example, err := app.models.Example.Get(ctx, id)
if err != nil {
    switch {
    // If the error is equal to or wraps context.Canceled, then return
    // without taking
    // any further action.
    case errors.Is(err, context.Canceled):
        return
    case errors.Is(err, data.ErrNotFound):
        app.notFoundResponse(w, r)
    default:
        app.serverErrorResponse(w, r, err)
    }
    return
}

...
}
```

除了这种额外的错误处理之外，你还需要注意使用后台 goroutine 时的影响。请记住我之前引用的关于请求上下文取消的内容：

> *对于传入的服务器请求，[请求] 上下文会在 ... ServeHTTP 方法返回时被取消。*

这意味着，如果你从请求上下文派生上下文，则在后台 goroutine 中使用该上下文的任何 SQL 查询都将在初始请求的 HTTP 响应发送时被取消！如果你不希望出现这种情况（你可能确实不希望），那么你
无论如何都需要使用 `context.Background()` 为后台 goroutine 创建一个全新的上下文。

因此，总结一下，使用请求上下文作为数据库超时的父上下文会增加相当多的行为复杂性，并引入你和任何在代码库上工作的人都需要了解的细微差别。你必须问：*值得吗？*

对于大多数应用程序的大多数端点来说，这可能不值得。例外可能是在资源经常接近饱和点运行的应用程序，或执行运行缓慢或计算成本非常高的 SQL 查询的特定端点。在这些情况下，当客户端消失时积极取消查询可能会产生有意义的积极影响，从而使权衡值得。

