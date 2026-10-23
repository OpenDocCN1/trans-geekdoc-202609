
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
