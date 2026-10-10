
# Go Web 服务器示例

Go 的库使得编写响应客户端请求（如 `fetch` 发出的请求）的 Web 服务器变得很容易。在本节中，我们将展示一个最小化的服务器，它返回用于访问服务器的 URL 的路径组件。也就是说，如果请求是 `http://localhost:8000/hello`，响应将是 `URL.Path = "/hello"`。

[点击此处查看代码图像](#ch01_images.html#id019pro01_r)

gopl.io/ch1/server1

```
// Server1 is a minimal "echo" server.
package main

import (
    "fmt"
    "log"
    "net/http"
)

func main() {
    http.HandleFunc("/", handler) // each request calls handler
    log.Fatal(http.ListenAndServe("localhost:8000", nil))
}

// handler echoes the Path component of the requested URL.
func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "URL.Path = %q\n", r.URL.Path)
}
```

该程序只有短短几行，因为库函数完成了大部分工作。`main` 函数将处理函数连接到路径以 `/` 开头的传入 URL（即所有 URL），并启动一个在 8000 端口监听传入请求的服务器。请求被表示为 `http.Request` 类型的结构体，它包含许多相关字段，其中之一是传入请求的 URL。当请求到达时，它被传递给处理函数，该函数从请求 URL 中提取路径组件（`/hello`）并使用 `fmt.Fprintf` 将其作为响应发送回去。Web 服务器将在 [第 7.7 节](#ebook_split_066.html#id-httphandler) 中详细解释。

让我们在后台启动服务器。在 Mac OS X 或 Linux 上，在命令后添加 `&` 符号；在 Microsoft Windows 上，您需要在单独的命令窗口中运行不带 `&` 符号的命令。

[点击此处查看代码图像](#ch01_images.html#id019pro02_r)

```
$ go run src/gopl.io/ch1/server1/main.go &
```

然后我们可以从命令行发起客户端请求：

[点击此处查看代码图像](#ch01_images.html#id020pro01_r)

```
$ go build gopl.io/ch1/fetch
$ ./fetch http://localhost:8000
URL.Path = "/"
$ ./fetch http://localhost:8000/help
URL.Path = "/help"
```

或者，我们可以从 Web 浏览器访问服务器，如 [图 1.2](#ebook_split_017.html#id-figures-echoserver) 所示。

![回显服务器的响应。](graphics/echoserver.png)

**图 1.2.** 回显服务器的响应。

向服务器添加功能很容易。一个有用的添加是返回某种状态的特定 URL。例如，这个版本执行相同的回显，但也会计算请求数量；对 URL `/count` 的请求返回迄今为止的计数（不包括 `/count` 请求本身）：

[点击此处查看代码图像](#ch01_images.html#id020pro02_r)

gopl.io/ch1/server2

```
// Server2 is a minimal "echo" and counter server.
package main

import (
    "fmt"
    "log"
    "net/http"
    "sync"
)

var mu sync.Mutex
var count int

func main() {
    http.HandleFunc("/", handler)
    http.HandleFunc("/count", counter)
    log.Fatal(http.ListenAndServe("localhost:8000", nil))
}

// handler echoes the Path component of the requested URL.
func handler(w http.ResponseWriter, r *http.Request) {
    mu.Lock()
    count++
    mu.Unlock()
    fmt.Fprintf(w, "URL.Path = %q\n", r.URL.Path)
}

// counter echoes the number of calls so far.
func counter(w http.ResponseWriter, r *http.Request) {
    mu.Lock()
    fmt.Fprintf(w, "Count %d\n", count)
    mu.Unlock()
}
```

服务器有两个处理器，请求 URL 决定调用哪一个：对 `/count` 的请求调用 `counter`，所有其他请求调用 `handler`。以斜杠结尾的处理器模式匹配任何以该模式为前缀的 URL。在后台，服务器在单独的 goroutine 中为每个传入请求运行处理器，以便可以同时服务多个请求。然而，如果两个并发请求尝试同时更新 `count`，它可能不会一致地递增；该程序将有一个称为 *race condition*（竞态条件）的严重 Bug（[§9.1](#ebook_split_087.html#id-raceconditions)）。为了避免这个问题，我们必须确保一次最多只有一个 goroutine 访问该变量，这就是括住每次 `count` 访问的 `mu.Lock()` 和 `mu.Unlock()` 调用的目的。我们将在 [第 9 章](#ebook_split_086.html#id-concurrencywithsharedvariables) 中更仔细地研究带有共享变量的并发。

作为一个更丰富的示例，处理器函数可以报告它接收到的头部和表单数据，使服务器可用于检查和调试请求：

[点击此处查看代码图像](#ch01_images.html#id021pro01_r)

gopl.io/ch1/server3

```
// handler echoes the HTTP request.
func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "%s %s %s\n", r.Method, r.URL, r.Proto)
    for k, v := range r.Header {
        fmt.Fprintf(w, "Header[%q] = %q\n", k, v)
    }
    fmt.Fprintf(w, "Host = %q\n", r.Host)
    fmt.Fprintf(w, "RemoteAddr = %q\n", r.RemoteAddr)
    if err := r.ParseForm(); err != nil {
        log.Print(err)
    }
    for k, v := range r.Form {
        fmt.Fprintf(w, "Form[%q] = %q\n", k, v)
    }
}
```

这使用 `http.Request` 结构体的字段产生如下输出：

[点击此处查看代码图像](#ch01_images.html#id021pro02_r)

```
GET /?q=query HTTP/1.1
Header["Accept-Encoding"] = ["gzip, deflate, sdch"]
Header["Accept-Language"] = ["en-US,en;q=0.8"]
Header["Connection"] = ["keep-alive"]
Header["Accept"] = ["text/html,application/xhtml+xml,application/xml;..."]
Header["User-Agent"] = ["Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_5)..."]
Host = "localhost:8000"
RemoteAddr = "127.0.0.1:59911"
Form["q"] = ["query"]
```

注意 `ParseForm` 的调用是如何嵌套在 `if` 语句中的。Go 允许简单语句（如局部变量声明）位于 `if` 条件之前，这对于错误处理特别有用，正如本例所示。我们也可以写成：

```
err := r.ParseForm()
if err != nil {
    log.Print(err)
}
```

但合并语句更简短，并减少了变量 `err` 的作用域，这是一种良好的实践。我们将在 [第 2.7 节](#ebook_split_026.html#id-scope) 中定义作用域。

在这些程序中，我们已经看到了三种截然不同的类型被用作输出流。`fetch` 程序将 HTTP 响应数据复制到 `os.Stdout`（一个文件），`lissajous` 程序也是如此。`fetchall` 程序通过将响应复制到微不足道的接收器 `ioutil.Discard` 来丢弃响应（同时计算其长度）。而上面的 Web 服务器使用 `fmt.Fprintf` 写入 `http.ResponseWriter`，它代表 Web 浏览器。

尽管这三种类型在做什么的细节上有所不同，但它们都满足一个通用的 *interface*（接口），允许在需要输出流的任何地方使用它们中的任何一个。该接口称为 `io.Writer`，将在 [第 7.1 节](#ebook_split_060.html#id-interfacesascontracts) 中讨论。

Go 的接口机制是 [第 7 章](#ebook_split_059.html#id-interfaces) 的主题，但为了让您了解它的能力，让我们看看将 Web 服务器与 `lissajous` 函数结合是多么容易，以便将动画 GIF 写入 HTTP 客户端而不是标准输出。只需将这些行添加到 Web 服务器中：

[点击此处查看代码图像](#ch01_images.html#id022pro01_r)

```
handler := func(w http.ResponseWriter, r *http.Request) {
    lissajous(w)
}
http.HandleFunc("/", handler)
```

或者等价地：

[点击此处查看代码图像](#ch01_images.html#id022pro02_r)

```
http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
    lissajous(w)
})
```

紧接在上面的 `HandleFunc` 函数调用中的第二个参数是一个 *function literal*（函数字面量），即在其使用点定义的匿名函数。我们将在 [第 5.6 节](#ebook_split_047.html#id-anonymousfunctions) 中进一步解释它。
