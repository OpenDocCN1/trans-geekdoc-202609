
```go
wantAuth := `Basic realm="Restricted"`
if gotAuth != wantAuth {
    t.Fatalf("WWW-Authenticate, want: %s, got: %s", wantAuth, gotAuth)
}
}
```

你可以克隆 Git 仓库并像这样运行测试：

```
mkdir -p $GOPATH/src/github.com/openfaas/
cd $GOPATH/src/github.com/openfaas/
git clone --depth=1 https://github.com/openfaas/faas-provider
cd faas-provider

go test -v ./auth/
=== RUN   Test_AuthWithValidPassword_Gives200
--- PASS: Test_AuthWithValidPassword_Gives200 (0.00s)
=== RUN   Test_AuthWithInvalidPassword_Gives403
--- PASS: Test_AuthWithInvalidPassword_Gives403 (0.00s)
=== RUN   Test_ReadFromCustomLocation_AndNames
--- PASS: Test_ReadFromCustomLocation_AndNames (0.00s)
=== RUN   Test_ReadFromCustomLocation_DefaultNames
--- PASS: Test_ReadFromCustomLocation_DefaultNames (0.00s)
PASS
ok      github.com/openfaas/faas-provider/auth  0.002s
```

## 第 7 章：使用 Goroutines 并发工作

在计算中，并发意味着能够同时处理多个任务，但不一定在完全相同的时间内对它们进行工作。这个概念经常与并行计算混淆，并行计算是指同时对多个任务取得进展的行为。

Go 对并发的解决方案是 Goroutines。文档将“goroutine”定义为：“由 Go 运行时管理的轻量级线程。”

为什么这很重要？操作系统（OS）线程通常创建和协调成本很高。Go 的方法被描述为“lightweight”线程，这意味着操作系统（OS）线程和 Goroutines 之间不一定存在 1:1 的关系，使其更快、更具可扩展性。

如果想深入了解 Goroutines 和同步技术，你可能也会喜欢 The Go Programming Language（Addison-Wesley）。

在本章中，我想介绍一些实用示例，展示你今天如何开始。我还会提到一个常见的陷阱，即使是最有经验的 Golang 程序员也可能遇到。

我们将涵盖：编写你的第一个 Goroutine、在循环中创建 Goroutines、通过 WaitGroups 同步、使用 Error groups 进行错误处理、使用通道并限制进行中的工作量。

### 使用 Goroutines 的简单示例

在这个示例中，我们有一个 printLater 函数，它模拟了一个运行缓慢的调用，慢到我们可能希望并发运行多个调用并在最后收集结果，而不是串行运行每个调用并等待更长时间。

```go
package main

import (
    "fmt"
    "os"
    "time"
)

func main() {
    printLater("Hello\n", time.Millisecond*100)
    printLater("World\n", time.Millisecond*100)
    printLater(os.Getenv("USER")+"\n", time.Millisecond*100)
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

运行此程序时，会得到以下输出，大约需要 300ms 执行：

```
$ go run main.go
Hello
World
alex
```

现在想象 printLater 方法实际上是之前从远程 HTTP 服务器获取和提取 JSON 的示例。我们可以通过使用 Goroutines 并发执行 HTTP 调用，将总运行时间从 300ms 优化到大约 100ms。

```go
package main

import (
    "fmt"
    "os"
    "time"
)

func main() {
    go func() {
        printLater("Hello\n", time.Millisecond*100)
    }()
    go func() {
        printLater("World\n", time.Millisecond*100)
    }()
    go func() {
        printLater(os.Getenv("USER")+"\n", time.Millisecond*100)
    }()
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

现在运行此程序时，它将在没有任何输出的情况下退出。这是因为 Goroutines 异步执行，因此需要与主程序的执行流程同步。

你可以通过使用通道，或标准库 sync 包中的其他一些原语来同步 Goroutines。WaitGroup 是我最喜欢的示例之一。

WaitGroup 的主要目的是阻塞并等待多个任务完成。

要使用 WaitGroup，首先使用任务数量调用 Add 函数，然后设置你的 Goroutines。在每个 Goroutine 内部，需要在完成时调用 Done。最后，在同步工作的函数中，调用 wg.Wait()，它将在那里阻塞执行，直到所有例程都调用了 Done 且未完成的任务设为 0。

```go
package main

import (
    "fmt"
    "os"
    "sync"
    "time"
)

func main() {
    wg := sync.WaitGroup{}
    wg.Add(3)

    go func() {
        defer wg.Done()
        printLater("Hello\n", time.Millisecond*100)
    }()
    go func() {
        defer wg.Done()
        printLater("World\n", time.Millisecond*100)
    }()
    go func() {
        defer wg.Done()
        printLater(os.Getenv("USER")+"\n", time.Millisecond*100)
    }()

    wg.Wait()
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

现在我们看到代码已完成，并打印所有消息。我们可以判断工作是并发执行的，因为消息似乎顺序错乱。

```
$ go run main.go
World
Hello
alex
```

此示例无法处理错误，需要注意的是，如果一个 Goroutine 调用 panic()，则整个应用程序将失败。我们将在稍后探讨两种错误处理方法。

### 避免 Goroutines 的常见错误

现在让我们探讨一个常见的 Goroutines 错误，我自己也时不时会犯。

现在你已经了解了定义和同步 Goroutines 的方法，引入循环会很诱人，有时也更高效。

```go
package main

import (
    "fmt"
    "sync"
    "time"
)

func main() {
    wg := sync.WaitGroup{}
    workItems := 5
    wg.Add(workItems)

    for i := 1; i <= workItems; i++ {
        go func() {
            defer wg.Done()
            printLater(
                fmt.Sprintf("Hello from %d\n", i),
                time.Millisecond*100)
        }()
    }

    wg.Wait()
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

现在运行示例：

```
$ go run ./
Hello from 6
Hello from 6
Hello from 6
Hello from 6
Hello from 6
```

注意消息对每个 5 个响应都显示 `Hello from 6`？循环捕获了 i 变量的最终值并将其用于每个 Goroutine。

为了解决这个问题，我们可以将 i 变量作为参数传递给 Goroutine，或者使用新的局部变量在闭包中捕获它。

以下是第一种方法：

```go
for i := 1; i <= workItems; i++ {
    go func(j int) {
        defer wg.Done()
        printLater(
            fmt.Sprintf("Hello from %d\n", j),
            time.Millisecond*100)
    }(i)
}
```

注意我们的 Goroutine 的签名如下所示更改：

```go
i := 1
go func(j int) {
    fmt.Printf("Value is: %d", j)
}(i)
```

在第二种方法中，我们定义一个新的局部变量 j 来捕获 i 的值：

```go
for i := 1; i <= workItems; i++ {
    j := i
    go func() {
        defer wg.Done()
        printLater(
            fmt.Sprintf("Hello from %d\n", j),
            time.Millisecond*100)
    }()
}
```

在这两种情况下，我们都会得到预期的输出：

```
Hello from 4
Hello from 3
Hello from 5
Hello from 1
Hello from 2
```

### 错误组

另一种并行同步工作的方式是通过 Golang 团队提供的非官方“errgroup”包。

在上面的示例中，这变得更有用，因为我们的任何 Goroutine 都可以返回错误并被捕获，而无需编写代码通过通道同步消息。

errgroup 不仅可以并发运行多个 Goroutine，还可以按流水线方式串行运行它们，在进入下一个任务之前检查每个任务的错误。

要使用一个 *error group*，导入 `"golang.org/x/sync/errgroup"` 包，然后使用 `g := errgroup.Group{}` 定义一个新的 errgroup，然后为每个工作项调用 `g.Go(func() error { })`。你会注意到 `g.Go()` 函数接受一个可以返回错误 的函数。如果没有错误，则返回 `nil`，否则返回错误，整个执行将退出并将错误冒泡到同步函数。

```go
package main

import (
    "fmt"
    "os"
    "time"

    "golang.org/x/sync/errgroup"
)

func main() {
    g := errgroup.Group{}
    g.Go(func() error {
        printLater("Hello\n", time.Millisecond*100)
        return nil
    })
    g.Go(func() error {
        // printLater("World\n", time.Millisecond*100)
        return fmt.Errorf("world failed")
    })
    g.Go(func() error {
        printLater(os.Getenv("USER")+"\n", time.Millisecond*100)
        return nil
```
