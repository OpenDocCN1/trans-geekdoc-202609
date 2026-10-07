

```go
package main

import (
    github.com/gorilla/mux
    ...
)
```

# 使用 gorilla/mux

为了增加一点趣味性，让我们使用 gorilla/mux 创建一个处理器，根据正则表达式来匹配传入的产品 ID 的请求。如果产品 ID 长度为单个数字，则我们匹配成功，并将其路由到相应的页面。如果不是，我们将其路由到错误页面。

首先，我们需要导入 gorilla/mux 模块，我们按照正常的方式进行操作：

```
import (
    ...
    github.com/gorilla/mux
)
```

接下来，我们需要切换到 gorilla/mux 而不是它默认的 `DefaultServeMux`：

```go
func main() {
    router = mux.NewRouter()
}
```

完成这一步后，我们就可以使用熟悉的处理器函数了，但在路由的语境下，并可以使用 gorilla/mux 提供的额外功能，例如使用正则表达式搜索 URL 参数：

```go
router.HandleFunc("/product/id:[0-9]+", pageHandler)
```

该行代码创建了一个处理器，它尝试匹配以 `/product/` 开头并跟着一个零到九数字的 URL，我们将其称为 `id`。如果匹配成功，将调用 `pageHandler` 函数。

在我们的 `pageHandler` 函数中，我们需要验证 `HandleFunc` 匹配到的精确字符串。我们使用 Gorilla 的 `mux.Vars` 函数来实现此，将请求作为单个参数传入，并返回一个路由变量映射。我们可以通过其名称——`id`——来引用我们感兴趣的路由变量。

在获取产品 ID 后，我们可以接着检查是否有匹配的 HTML 页面。Go 的 `os` 模块提供了 `Stat` 和 `IsNotExist` 函数来帮助我们。如果文件存在于服务器上，我们使用 `http.ServeFile` 将其发送到浏览器。如果它不存在，我们将返回另一个页面，告诉用户该产品无效。

代码列表 6 显示了完整的代码。

```go
package main

import (
    "log"
    "net/http"
    "os"

    "github.com/gorilla/mux"
)

func pageHandler(w http.ResponseWriter, r *http.Request) {
    vars := mux.Vars(r)
    productID := vars["id"]
    log.Printf("Product ID:%v\n", productID)

    fileName := productID + ".html"

    if _, err := os.Stat(fileName); os.IsNotExist(err) {
        log.Printf("no such product")
        fileName = "invalid.html"
    }

    http.ServeFile(w, r, fileName)
}

func main() {
    router := mux.NewRouter()
    router.HandleFunc("/product/{id:[0-9]+}", pageHandler)
    http.Handle("/", router)
    http.ListenAndServe(":8999", nil)
}
```

这仅仅是 gorilla/mux 功能冰冰一角。例如，你可以针对以下内容进行匹配：

- 路径前缀：
`router.PathPrefix("/products/")`

- HTTP 方法：
`router.Methods("GET", "POST")`

- URL 方案：
`router.Schemes("https")`

- Header 值（例如，请求是否为 AJAX 请求？）：
```
router.Headers("X-Requested-With", "XMLHttpRequest")
```

- 查询值：
```
router.Queries("key", "value")
```

- 你定义的自定义匹配函数：
```
router.MatcherFunc(func(r *http.Request, match *RouteMatch) bool {
  // 执行操作
}
```

你可以通过链式函数调用在一个路由中组合多个匹配器：

```go
router.HandleFunc("/products", productHandler)
Host("www.example.com")
Methods("GET")
Schemes("https")
```

或者，你可以使用子路由将多个路由分组在一起。例如，以下代码查找 `www.example.com` 的主机映射，但只有当在主机上匹配成功时，它才会检查子路由：

```go
router := mux.NewRouter()
subrouter := route.Host("www.example.com").Subrouter
```

```go
// 注册子路由
subrouter.HandleFunc("/products", AllProductsHandler)
subrouter.HandleFunc("/products/{name}", ProductHandler)
subrouter.HandleFunc("/reviews/{category}/{id:[0-9]+}"), ReviewsHandler
```

> gorilla/mux 是 DefaultServeMux 非常强大的替代方案，值得研究。你可以在 http://www.gorillatool.org/pkg/mux 了解更多信息。

当然，由于 Gorilla 是一个如此庞大的生态系统，如果你不喜欢 Gorilla，还有许多其他选择。我偏喜欢 Gorilla 是因为它很容易理解，而且它总是能执行我要求它做的任何事情。

其他流行的第三方路由器包括：

- httrouter：轻量且快速，但功能不如 Gorilla。例如，你不能在路由中包含正则表达式。
- httpremux：一个灵活的、基于树的 HTTP 路由器，受 httrouter 启发。
- Pat：简单易且非常流行。如果你是熟悉 Sinatra 和 Rails 的 Ruby 开发者，你会发现 Pat 的方法非常熟悉。

# 返回错误

事情并不总是如我们预期的那样运行。请求指向已不存在的页面，事物从一个地方移动到另一个，有时连接会中断。

HTTP 协议定义了 61 个状态码，以便我们判断请求是否成功。

以下是常见的状态码：

- 200 OK：成功！
- 404 Not Found：未找到。
- 301 Moved Permanently：永久重定向。
- 302 Moved Temporarily：临时重定向。
- 500 Internal Server Error：服务器内部错误。

net/http 包提供了各种函数供你报告错误。作为开发者，你可以传递 `ResponseWriter`、字符串消息和状态码来使用它。例如，在 Go 中使用：

```go
http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
    http.Error(w, "发生了了错误", http.StatusBadRequest)

# 访问数据

在上一章中，我们看到了 Go 如何接收请求并将其路由到不同的 URL。到目前为止，所有的响应都只是静态内容。在本章中，我们将学习如何让 Go 程序连接数据源。

## 获取数据库驱动

Go 允许你使用任何提供驱动程序的数据库。驱动程序列表可以在 https://github.com/go/wiki/Drivers 找到。

MySQL 是一个非常优秀的数据库，尽管它已经存在很久，但仍然非常受欢迎，因此我们将使用它。无论你选择哪种数据库，所需的步骤与所示相似或完全相同。

你可以从 http://www.mysql.com 下载社区版。Windows 安装程序中有此选项，而 Mac 和 Linux 需要手动安装。

如果你想跟随示例，请使用命令行连接到 MySQL 服务器，然后执行以下语句：

```
mysql> SOURCE /path/to/world.sql
```

你可以通过以下命令验证 "world" 数据库已安装：

当你安装了数据库服务器后，需要为它安装驱动。你可以通过 **get** 实现。我使用的是 **go-sql-driver** MySQL。

当我们将驱动导入到数据库服务器后，接下来需要在 **import** 语句中引用它和通用的 **database/sql** 包。注意我们在导入驱动前加了下划线 (_)。这告诉 Go 编译器我们引用的包是另一个包的补充——在例例中，是 **database/sql** 包。我们只使用它的初始化能力——即 Go 所说的“副作用”。

```go
import (
	"database/sql"
	"log"
	_ "github.com/go-sql-driver/mysql"
)
```

