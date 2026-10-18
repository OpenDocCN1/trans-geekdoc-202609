

```go
fmt.Printf("- %s = error: %s\n", k, v.Error.Error())
    } else {
        fmt.Printf("- %s = [%d] %d bytes\n", k, v.HTTPCode, v.HTTPLength)
    }
}
}
```

这是运行程序后的输出：

```text
$ go run .
- https://notfound.example.com/ = error: Get "https://notfound.example.com/": dial tcp:
  lookup notfound.example.com: no such host
- https://openfaas.com/ = [200] 32696 bytes
- https://inlets.dev/ = [200] 69805 bytes
```

你知道吗？sync.Mutex 会对对象施加独占锁，这意味着在锁释放之前，任何其他读写操作都无法进行。如果对象同时存在读者和写者，这可能会导致瓶颈。

sync.RWMutex 类型可以用作 sync.Mutex 的直接替代品，它允许任意数量的读者获取锁，或单个写者获取锁。

```go
package main

import (
    "sync"
)

func main() {
    lock := sync.RWMutex{}
    go readOperation(data, "key", &lock)
    go writeOperation(data, "key", "value", &lock)

    // Add synchronisation for the two routines here.
}

func readOperation(data map[string]string, key string, lock *sync.RWMutex) {
    lock.RLock()
    defer lock.RUnlock()
    fmt.Println(data["key"])
}

func writeOperation(data map[string]string, key, value string, lock *sync.RWMutex) {
    lock.Lock()
    defer lock.Unlock()
    data[key] = value
}
```

在这种情况下，读写操作可以同时发生，因为写锁不会阻塞读取值的函数。

这种模式在真实世界中的用例是什么？也许你有一个内存缓存，保存着活跃客户列表。该列表需要通过联网下载，这可能是一项开销很大的操作。随后，该列表会与 HTTP 服务器中的多个 Goroutine 或处理程序共享。读锁将用于访问数据，而写锁将由类似定时器或长时间运行的循环使用，以更新缓存中的条目。

第二种方法是让 Goroutine 直接输出数据，不共享类型。调用代码随后可以汇总结果，无需创建带锁的单独类型。你将在下面看到这种方法的示例：

```go
var uri string
flag.StringVar(&uri, "uri", "", "uri to fetch")
flag.Parse()

titleCh := make(chan string)
errorCh := make(chan error)

go titleOf(uri, titleCh, errorCh)

select {
case title := <-titleCh:
    fmt.Printf("Title: %s\n", title)
case err := <-errorCh:
    fmt.Printf("Error: %s\n", err.Error())
    os.Exit(1)
}
}

func titleOf(uri string, titleCh chan string, errCh chan error) {
    req, err := http.NewRequest(http.MethodGet, uri, nil)
    if err != nil {
        errCh <- err
        return
    }

    res, err := http.DefaultClient.Do(req)
    if err != nil {
        errCh <- err
        return
    }
    if res.Body != nil {
        defer res.Body.Close()

        res, _ := io.ReadAll(res.Body)
        for _, l := range strings.Split(string(res), "\n") {
            if strings.Contains(l, "<title>") {
                titleCh <- l
                return
            }
        }
    }

    errCh <- fmt.Errorf("no title found")
}
```

下面是一个运行工作负载的示例，包含三个不同的网站，然后是几个错误场景。

```text
$ go run . -uri https://inlets.dev
Title:   <title>Inlets - The Cloud Native Tunnel</title>

$ go run . -uri https://github.com/alexellis/
Title:   <title>alexellis (Alex Ellis) · GitHub</title>

$ go run .
Error: Get "": unsupported protocol scheme ""
exit status 1

$ go run . -uri https://gitzub.com
Error: Get "https://gitzub.com": dial tcp: lookup gitzub.com: no such host
exit status 1
```

## 使用上下文处理超时

现在，这里还存在另一个潜在问题。某些网站可能会挂起或无限期地保持连接打开。Go 提供了一个称为“context”（上下文）的概念，可以将其传递给使用外部资源的调用，就像上面的 HTTP 请求一样。

Context（上下文）会携带一个截止时间、一个取消信号以及其他值，跨过 API 边界。

你可以在这里查看 context 包的文档：context。

有些库函数允许通过参数传入 Context，但如果没有可用的 Context，你可以使用以下方法获取后台上下文：

```go
ctx := context.Background()
```

你也可能会看到使用 context.TODO() 的情况，这可以用于没有可用的上下文，或者不清楚该使用哪个上下文的时候。

它的 API 还提供了几个实用方法，用于定义取消策略：

```go
func WithCancel(parent Context) (ctx Context, cancel CancelFunc)
```

需要传入一个父上下文，当调用 cancel 函数时，任何正在进行的操作都必须停止，并应释放资源。

```go
func WithDeadline(parent Context, d time.Time) (Context, CancelFunc)
```

这个函数与 WithCancel 类似，不同的是它有一个截止时间/日期，在未来的某个时间点，操作应当被取消。这对于 HTTP 请求或访问外部系统时很有用。

```go
func WithTimeout(parent Context, timeout time.Duration) (Context, CancelFunc)
```

WithTimeout 函数也类似，但它提供了一个辅助函数，因此可以传入一个超时值，而不是未来的实际日期。

在下面的示例中，你将看到 WithTimeout 是如何工作的。

```go
package main

import (
  "context"
  "flag"
  "fmt"
  "io"
  "net/http"
  "os"
  "strings"
  "time"
)

func main() {
    var uri string
    var timeout time.Duration

    flag.StringVar(&uri, "uri", "", "uri to fetch")
    flag.DurationVar(&timeout, "timeout", time.Second*5, "timeout for HTTP client")

    flag.Parse()

    titleCh := make(chan string)
    errorCh := make(chan error)

    go titleOf(uri, timeout, titleCh, errorCh)

    select {
    case title := <-titleCh:
        fmt.Printf("Title: %s\n", title)
    case err := <-errorCh:
        fmt.Printf("Error: %s\n", err.Error())
        os.Exit(1)
    }
}

func titleOf(uri string, timeout time.Duration, titleCh chan string, errCh chan error) {
    ctx, cancel := context.WithTimeout(context.Background(), timeout)
    defer cancel()

    req, err := http.NewRequestWithContext(ctx, http.MethodGet, uri, nil)
    if err != nil {
        errCh <- err
        return
    }

    res, err := http.DefaultClient.Do(req)
    if err != nil {
        errCh <- err
        return
    }

    if res.Body != nil {
        defer res.Body.Close()
        res, _ := io.ReadAll(res.Body)
        for _, l := range strings.Split(string(res), "\n") {
            if strings.Contains(l, "<title>") {
                titleCh <- l
                return
            }
        }
    }

    errCh <- fmt.Errorf("no title found")
}
```

现在，让我们将超时设置得更激进一些，比如 10ms，并引入一个 flag，以便我们能够轻松配置该值。

```text
$ go run . -uri https://github.com/alexellis --timeout 10ms
Error: Get "https://github.com/alexellis": context deadline exceeded
exit status 1

$ go run . -uri https://github.com/alexellis --timeout 1000ms
Error: Get "https://github.com/alexellis": context deadline exceeded
exit status 1

$ go run . -uri https://github.com/alexellis --timeout 3000ms
Title:  <title>alexellis (Alex Ellis) · GitHub</title>
```

所以看起来，我们需要一个相当宽裕的超时时间，才能从英国的一台客户端获取我的 GitHub 个人资料。

## 限制并发任务

到目前为止，我们所看到的所有技术都不允许我们限制资源。在某些时候，你可能会超过某个限制，比如你的机器上允许的文件数或 HTTP 连接数，或者你的“数据库即服务”所允许的数据库连接数。

在这些情况下，考虑限制工作负载是很有用的。OpenFaaS CLI 中实现了一种类似的技术，用于构建、推送和部署函数。

默认情况下，并发级别为 1，但可以被覆盖，因此如果你需要构建 8 个函数，你可以让其中 4 个同时被处理。你可以将这种方法看作一个“窗口”，4 个 Goroutine 会启动，并接收 8 份工作中的 4 份。当进行中的工作降到 3 份时，剩余队列中的 4 件任务中的另一件将被处理，直到所有工作完成且没有剩余为止。

下面的模式更新了我们的 `titleOf` 方法，使其无需 channel 即可运行，并返回 `(string, error)` 形式的结果。

```go
func titleOf(uri string, timeout time.Duration) (string, error) {
    ctx, cancel := context.WithTimeout(context.Background(), timeout)
    defer cancel()

    req, err := http.NewRequestWithContext(ctx, http.MethodGet, uri, nil)
    if err != nil {
        return "", err
    }

    res, err := http.DefaultClient.Do(req)
    if err != nil {
        return "", err
    }

    if res.Body != nil {
        defer res.Body.Close()
        res, _ := io.ReadAll(res.Body)
        for _, l := range strings.Split(string(res), "\n") {
            if strings.Contains(l, "<title>") {
                return uri, nil
            }
        }
    }
}
```

