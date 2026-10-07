
遗漏。这可能会导致各种数据损坏 bug。

关于调度语义有许多细小的细节，因此为了学习这些，请阅读第 14 章中标题为《Go 调度》的几篇文章。

## 6.2 并发基础

从一个需要编排的简单并发问题开始。

列表 6.1

```go
func init() {
    runtime.GOMAXPROCS(1)
}
```

对 `GOMAXPROCS` 的调用被用于将 Go 程序作为单线程 Go 程序运行。此程序将是单线程的，并且有一个 P/M 来执行所有的 Goroutine。该函数首字母大写，是因为它也是一个环境变量。此函数将覆盖该变量。

列表 6.2

```go
g := runtime.GOMAXPROCS(0)
```

当我为容器配置设置 CPU 配额时，这个函数是一个重要的函数。当传递 `0` 时，会报告 Go 程序将要使用的线程数。我必须确保该数字与我在容器化环境中可用的操作系统线程数匹配。如果数字不相等，Go 程序的运行效果可能不会像原本那样好。我可能想使用环境变量或此调用来匹配它们。

列表 6.3

```go
func main() {
    var wg sync.WaitGroup
    wg.Add(2)

    go func() {
        lowercase()
        wg.Done()
    }()

    go func() {
        uppercase()
        wg.Done()
    }()

    fmt.Println("Waiting To Finish")
    wg.Wait()
    fmt.Println("\nTerminating Program")
}
```

这个程序必须解决一个编排问题。在保证创建的两个 Goroutine 先完成它们的工作之前，主 Goroutine 不能让 `main` 函数返回。`WaitGroup` 是处理不需要在 Goroutine 之间传递数据的编排问题的完美工具。这里的信号通过一个 API 实现，该 API 允许 Goroutine 等待其他 Goroutine 发出完成的信号。

在这段代码中，构造了一个 `WaitGroup` 并设置其零值状态，然后立即调用 `Add` 方法将 `WaitGroup` 设置为 `2`，这将与要创建的 Goroutine 数量匹配。当我预先知道将创建多少 Goroutine 时，我应该调用一次 `Add` 并传入该数字。如果我不知道（例如在流式服务中），那么调用 `Add(1)` 是可以的。

调用的最后是 `Wait`。`Wait` 阻塞主 Goroutine 防止函数返回。当 `main` 函数返回时，Go 程序会被极其果断地关闭。这就是为什么用适当的保证来管理编排非常重要。`Wait` 调用将阻塞直到 `WaitGroup` 被设回 `0`。

在程序的中间，我有两个 Goroutine 的创建过程。

# 列表 6.4

```go
func main() {

    go func() {
        lowercase()
        wg.Done()
    }

    go func() {
        uppercase()
        wg.Done()
    }

}
```

字面量函数是通过 `go` 关键字声明并执行的。在此时，我正在告诉 Go 调度器并发执行这些函数。以一种未定义的顺序执行它们。在每个 Goroutine 的实现内部都是对 `Done` 的调用。该调用会将 `WaitGroup` 减 1。一旦两个 `Done` 调用都完成，`WaitGroup` 将从 `2` 变为 `0`，然后主 Goroutine 将被允许从 `Wait` 调用中解除阻塞，终止程序。

# 列表 6.5

```go
func main() {
    var wg sync.WaitGroup
    wg.Add(2)

    go func() {
        lowercase()
        wg.Done()
    }()

    ...
}
```

这种编排模式的一个重要部分是将 `Add` 和 `Done` 调用保持在同一视线范围内。尽量不要将 `WaitGroup` 作为一个函数参数，导致这些调用丢失。这有助于减少 bug。

# 列表 6.6

```text
Output:
Start Goroutines
Waiting To Finish
A B C D E F G H I J K L M N O Q R S T U V W X Y Z A B C D E F G H I J K L M N O Q R S T U V W X Y Z A B C D E F G H I J K L M N O Q R S T U V W X Y Z a c d e f g h i j k l m n o q r s t u v w x z
Terminating Program
```

当我构建并运行这个程序时，我看到这个程序是并发运行的。创建的第二个 Goroutine 被先调度了。它完成了工作，然后另一个 Goroutine 运行。下一次我运行这个程序时，不能保证我看到相同的输出。这个程序中唯一的保证是，在最后一个 Goroutine 完成之前程序不会终止。即使我运行这个程序 100 次并看到相同的输出，也不能保证它会再次发生。这极有可能，但不是保证。

# 列表 6.7

```go
func main() {
    ...
    fmt.Println("Waiting To Finish")
    wg.Wait()
    fmt.Println("\nTerminating Program")
}
```

如果我忘记调用 `Done`，程序会发生什么？由于 `Wait` 会导致死锁。

# 列表 6.8

```go
func main() {
    var wg sync.WaitGroup
    wg.Add(2)

    go func() {
        lowercase()
        wg.Done()
    }()

    go func() {
        uppercase()
        wg.Done()
    }()
}
```

```text
Output:
Start Goroutines
Waiting To Finish
A B C D E F G H I J K L M N O Q R S T U V W X Y Z A B C D E F G H I J K L M N O Q R S T U V W X Y Z A B C D E F G H I J K L M N O Q R S T U V W X Y Z a c d e f g h i j k l m n o q r s t u v w x z
Terminating Program
```

当我构建并运行这个程序时，我看到这个程序是并发运行的。创建的第二个 Goroutine 被先调度了。它完成了工作，然后另一个 Goroutine 运行。下一次我运行这个程序时，不能保证我看到相同的输出。这个程序中唯一的保证是，在最后一个 Goroutine 完成之前程序不会终止。即使我运行这个程序 100 次并看到相同的输出，也不能保证它会再次发生。这极有可能，但不是保证。

# 列表 6.9

```go
func main() {
    var wg sync.WaitGroup
    wg.Add(1)

    go func() {
        lowercase()
        // wg.Done()
    }()

    ...
}
```

```text
Output:
Start Goroutines
Waiting To Finish
fatal error: all goroutines are asleep - deadlock!

goroutine 1 [sem]:
sync.(*WaitGroup).Wait()
    /usr/local/go/src/sync/waitgroup.go:62 +0x...
main.main()

goroutine 6 [running]:
main.func1
    /path/to/main.go:12
```

```go
func main() {
    var wg sync.WaitGroup
    wg.Add(2)

    go func() {
        lowercase()
        wg.Done()
    }()

    go func() {
        uppercase()
        // wg.Done()
    }()

    ...
}
```
