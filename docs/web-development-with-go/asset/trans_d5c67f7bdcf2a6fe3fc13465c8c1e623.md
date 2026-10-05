

## 3.1. 使用 IF/ELSE 语句进行路由

如果你的服务器已经在运行，在看到更改之前，你需要通过按下 `ctrl + e` 来停止它。停止服务器后，再次运行它。

```
$ go run main.go
```

框 3.2. 动态重载

如果你对学习动态重载感兴趣，请查看 Go fresh - github.com/pilu/fresh

一旦服务器重启，访问 localhost:3000/contact，你将看到你的联系页面。然后访问 localhost:3000，你将看到你的主页。

如果你跳转到另一个路径会发生什么？尝试一下 - 跳转到一个我们没有定义的路径，例如 localhost:3000/something。你应该会看到一个空白页。这看起来很奇怪。

当用户访问我们未定义的页面时，最佳实践是返回 404 状态码，并告诉用户我们找不到他们寻找的页面。为了实现这一点，我们正在通过添加一个额外的 `else` 语句来更新我们的处理函数。更新后的代码如列表 3.2 所示。

### 列表 3.2：创建 404 页面

```go
func handlerFunc(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "text/html")
    if r.URL.Path == "/" {
        fmt.Fprint(w, "<h1>Welcome to my awesome site!</h1>")
    } else if r.URL.Path == "/contact" {
        fmt.Fprint(w, "<p>To get in touch, please send an email " +
        "to <a href=\"mailto:support@enslocked.com\">" + 
        "support@enslocked.com</a></a></p>")
    } else {
        w.WriteHeader(http.StatusNotFound)
        fmt.Fprint(w, "<h1>We could not find the page you " + \
        "were looking for :(</h1>" +
        "<p>Please email us if you keep being sent to an " + \
        "invalid page.</p>")
    }
}
```

现在如果我们重启服务器并访问一个不存在的页面，我们将得到类似图 3.1 所示的错误消息。

图 3.1：我们新的 404 页面

在添加任何新代码之前，让我们快速回顾一下代码中发生了什么。

首先，我们从 `Request` 对象获取 URL，它返回一个 *url.URL*。这个结构体有一个名为 `Path` 的字段，用于返回 URL 的路径。例如，如果 URL 是 http://lenslocked.com/docs/abc，那么 `Path` 就是 `/docs/abc`。这里唯一的异常是空路径始终被设置为 `/`，即根路径。

一旦我们获取了路径，就使用它来决定渲染哪个页面。当用户访问根路径 (/) 时，我们返回欢迎页面。当用户访问我们的联系页面 (/contact) 时，我们返回一个包含如何联系我们信息的页面。

如果这两个标准都不满足，我们就会写入 404 HTTP 状态码，然后向响应写入器写入错误消息。`NotFound` 变量实际上只是代表 HTTP 状态码 404 的常量，而 `WriteHeader` 方法是在 Go 中写入 HTTP 状态码的一种方法。

> 框 3.3. 导出常用常量
> 如上所述，`http.StatusNotFound` 实际上只是一个表示 404 状态码的常量。这并不是绝对必要的，你可以在代码中将其替换为 404，但包通常会导出 `StatusNotFound` 常量，以便代码更易于阅读和维护。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 完成版 - book.usegolang.com/3.1
- 更改 - book.usegolang.com/3.1-diff

## 3.2 流行的路由器

现在我们已经有了基础路由，我们将查看改进和简化应用程序的方法。具体来说，我们将探索开源路由器，并选择其中一个在我们的项目中使用。

### 3.2.1 net/http.ServeMux

我们将查看的第一个路由器是 Go 标准库的一部分。`net/http.ServeMux` 是一个非常直观的路由器，它非常容易使用，对于简单的 Web 应用程序效果非常好。

遗憾的是这个包在功能上稍显不足，许多功能最终是我们最终需要自己编写的。例如，`ServeMux` 没有提供一种方便的方法来定义 URL 参数，而我们将在后面的章节中用到它。

虽然我们最终可以将此路由器封装在我们自己的类型中并添加我们需要的所有功能，但我不想花整本书都集中在 Web 应用程序的一个特定部分，而是选择了另一个选项。

### 3.2.2 github.com/julienschmidt/httrouter

`github.com/julienschmidt/httrouter` 是一个非常流行的路由器，我在许多其他教程和 Web 框架中见过它。它被用于流行的 Web 框架 Gin，我也自己使用这个路由器写过几篇博客文章。

我喜欢这个路由器的点是它非常关注简单、快速和高效。如果你查看它 Github 页面上的某些基准测试，你会发现它优于许多其他路由器。除了对快速的关注，它还支持命名 URL 参数以及基于所使用的 HTTP 请求方法进行路由。我们将在未来的章节中学习更多内容。

最终我决定不在本书中使用 `httrouter`，原因有两个。第一，该库要求如果你想访问任何路径参数，必须使用接收第三个参数的 `http handler` 处理函数。这种方法没有问题，但我担心它可能会让初学者感到困惑，因此我选择使用我们将要介绍的路由器 - `gorilla/mux.Router`。

### 3.2.3 github.com/gorilla/mux.Router

最后，我们将检查 `github.com/gorilla/mux.Router`。

一旦我们有了了 `，.，.  。。我们需要检查 `github.com/gorilla/mux.Router`。它支持接收第三个参数的 `http handler` 函数。

此外，`gorilla/mux` 是 Gorilla Toolkit 的一部分，我们以后会它。很多路由器，`gorilla/mux`  我们我们使用。。。。，，，，，，。。 ，，在在编写本书时，`gorilla/mux` 是一个非常好的选择。

### 3.2.4 关于其他路由器

有很多很棒的路由器，我没有提到，`gorilla/mux` 是其中最流行的之一。`gorilla/mux` 已经存在了很长时间，有着非常稳健的记录。

### 3.3 使用 gorilla/mux

当你使用 gorilla/mux 时，首先需要做的是安装该包。到目前我们只使用了标准库。如果你正在运行程序，请停止它（ctrl + c），然后在终端中输入。

| 列表 3.3：安装 gorilla/mux. |
| :--- |
| `$ go get -u github.com/gorilla/mux` |

这将下载该包，`-u` 选项将告诉 Go 获取最新版本。接下来我们需要准备好代码。

> 框 3.4. 如果你看到错误
> 在此期间你可能会遇到错误，因为你没有安装 git。如果是这种情况，我建议安装 git 并重启以解决该问题。
> https://git-scm.com/en/Starting-Installing

我们可以继续像 3.1 中那样用一个函数处理多个页面，但这非常难以维护。相反，我们将每个页面拆分为自己的函数，这样我们只需要告诉路由器根据用户访问的页面调用哪个函数。代码如列表 3.4 所示，并应添加到 main。

### 使用 GORILLA MUX 路由器

### 列表 3.4：拆分我们的处理器。

```go
func home(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "text/html")
    fmt.Fprint(w, "<h1>Welcome to our site!</h1>")
}

func contact(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "text/html")
    fmt.Fprint(w, "<p>To get in touch, please send an email " +
        "to <a href=\"mailto:support@enslocked.com\">" +
        "support@enslocked.com</a></a></p>")
}
```

现在你已经导入了 mux 包，我们可以在 main 函数中使用它。首先我们需要在源代码的顶部添加一个 import。

### 列表 3.5：导入 gorilla/mux。

```go
import (
    "fmt"
    "net/http"

    "github.com/gorilla/mux"
)
```

我们在这里做的是添加那行代码，告诉我们将使用 `gorilla/mux` 包。当导入第三方库时，你将使用像我们刚刚使用的那样的 URL。这通常是一个指向源码控制服务的链接，例如 github，但你之后会看到我们使用 lenslocked.com 域名来创建私有包。

现在你已经导入了 mux 包，我们可以在 main 中使用它。列表 3.6 中的代码将替换你当前 main 中的代码

