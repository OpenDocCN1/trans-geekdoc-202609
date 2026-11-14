

## 1.6 并发获取多个 URL

Go 语言最有趣、最新颖的特性之一是其对并发编程的支持。这是一个大话题，第 8 章和第 9 章专门讲解此内容，因此这里我们仅让您略窥 Go 语言主要并发机制——goroutine（协程）和 channel（通道）的门径。

接下来的程序 `fetchall` 与前一个示例一样，都是获取 URL 的内容，但它会并发获取多个 URL，因此该过程所花费的时间不会超过最耗时的那一次获取，而非所有获取时间之和。此版本的 `fetchall` 会丢弃响应内容，但会报告每个 URL 的大小和耗时：

**gopl.io/ch1/fetchall**

```go
// Fetchall 并行获取 URL 并报告其耗时和大小。
package main

import (
    "fmt"
    "io"
    "io/ioutil"
    "net/http"
    "os"
    "time"
)

func main() {
    start := time.Now()
    ch := make(chan string)
    for _, url := range os.Args[1:] {
        go fetch(url, ch) // 启动一个 goroutine
    }
    for range os.Args[1:] {
        fmt.Println(<-ch) // 从通道 ch 接收
    }
    fmt.Printf("%.2fs elapsed\n", time.Since(start).Seconds())
}

func fetch(url string, ch chan<- string) {
    start := time.Now()
    resp, err := http.Get(url)
    if err != nil {
        ch <- fmt.Sprint(err) // 向通道 ch 发送
        return
    }

    nbytes, err := io.Copy(ioutil.Discard, resp.Body)
    resp.Body.Close() // 避免资源泄漏
    if err != nil {
        ch <- fmt.Sprintf("while reading %s: %v", url, err)
        return
    }
    secs := time.Since(start).Seconds()
    ch <- fmt.Sprintf("%.2fs  %7d  %s", secs, nbytes, url)
}
```

以下是一个示例：

```bash
$ go build gopl.io/ch1/fetchall
$ ./fetchall https://golang.org http://gopl.io https://godoc.org
0.14s     6852  https://godoc.org
0.16s     7261  https://golang.org
0.48s     2475  http://gopl.io
0.48s elapsed
```

*goroutine* 是一种并发的函数执行。*channel* 是一种通信机制，允许一个 goroutine 将特定类型的值传递给另一个 goroutine。`main` 函数运行在一个 goroutine 中，而 `go` 语句则创建额外的 goroutine。

`main` 函数使用 `make` 创建了一个字符串通道。对于每个命令行参数，第一个 range 循环中的 `go` 语句会启动一个新的 goroutine，异步调用 `fetch` 以使用 `http.Get` 获取 URL。`io.Copy` 函数读取响应主体，并通过写入 `ioutil.Discard` 输出流将其丢弃。`Copy` 返回字节计数及发生的任何错误。随着每个结果的到达，`fetch` 会在通道 `ch` 上发送一行汇总信息。`main` 中的第二个 range 循环接收并打印这些行。

当一个 goroutine 尝试在通道上发送或接收时，它会阻塞，直到另一个 goroutine 尝试执行相应的接收或发送操作，此时值被传递，两个 goroutine 继续执行。在本例中，每个 `fetch` 都在通道 `ch` 上发送一个值（`ch <- 表达式`），而 `main` 接收所有这些值（`<-ch`）。让 `main` 完成所有打印工作，可确保每个 goroutine 的输出作为一个整体被处理，如果两个 goroutine 同时完成，不会出现交错输出的危险。

**练习 1.10：** 找一个产生大量数据的网站。通过连续运行两次 `fetchall` 来研究缓存机制，观察报告的时间是否有很大变化。每次获取的内容都相同吗？修改 `fetchall` 将其输出打印到文件中，以便进行检查。

**练习 1.11：** 尝试使用更长的参数列表运行 `fetchall`，例如 `alexa.com` 上提供的前一百万个网站样本。如果某个网站不响应，程序会如何表现？（第 8.9 节介绍了应对此类情况的机制。）

## 1.7 Web 服务器

Go 的库使得编写 Web 服务器变得轻而易举，它能响应像 `fetch` 发出的那些客户端请求。在本节中，我们将展示一个最小化的服务器，它返回用于访问服务器的 URL 的路径组件。也就是说，如果请求是 `http://localhost:8000/hello`，响应将是 `URL.Path = "/hello"`。

**gopl.io/ch1/server1**

```go
// Server1 是一个最小的“回显”服务器。
package main

import (
    "fmt"
    "log"
    "net/http"
)

func main() {
    http.HandleFunc("/", handler) // 每个请求调用 handler
    log.Fatal(http.ListenAndServe("localhost:8000", nil))
}

// handler 回显请求 URL 的 Path 组件。
func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "URL.Path = %q\n", r.URL.Path)
}
```

该程序只有短短几行，因为库函数完成了大部分工作。`main` 函数将处理函数与路径以 `/` 开头的传入 URL 关联起来（这涵盖了所有 URL），并启动一个服务器在端口 8000 上监听传入请求。请求被表示为 `http.Request` 类型的结构体，其中包含许多相关字段，其中之一是传入请求的 URL。当请求到达时，它被交给处理函数，该函数从请求 URL 中提取路径组件（`/hello`），并使用 `fmt.Fprintf` 将其作为响应发送回去。Web 服务器将在第 7.7 节中详细解释。

