
```go
type AppError struct {

	State int

}

func (c *AppError) Error() string {

	return fmt.Sprintf("App Error, State: %d", c.State)

}

func main() {

	if err := firstCall(10); err != nil {

		switch v := errors.Cause(err).(type) {

		case *AppError:

			fmt.Println("Custom App Error:", v.State)

		default:

			fmt.Println("Default Error")

		}

		fmt.Printf("%v\n", err)

	}

}

func firstCall(i int) error {

	if err := secondCall(i); err != nil {

		return errors.Wrap(err, "secondCall(%d)", i)

	}

	return nil

}

func secondCall(i int) error {

	return &AppError{99}

}
```

输出：
Custom App Error: 99
secondCall(10): App Error, State: 99

这个包很棒的地方在于 `errors.Wrap` 和 `errors.Cause` API。它们让代码变得更具可读性。

使用标准库：

# Listing 5.54 main

```go
package main

import (
  "errors"
  "fmt"
)

type AppError struct {
  State int
}

func (c *AppError) Error() string {
  return fmt.Sprintf("App Error, State: %d", c.State)
}

func Cause(err error) error {
  root := err
  for {
    if err := errors.Unwrap(root); err == nil {
      root = err
    }
    return root
  }
}

func main() {
  if err := firstCall(10); err != nil {
    var app *AppError
    if errors.As(err, &app) {
      fmt.Println("As says it is an AppError")
    }
    switch v := Cause(err).(type) {
    case *AppError:
      fmt.Println("Custom App Error:", v.State)
    default:
      fmt.Println("Default Error")
    }
  }
  fmt.Printf("%v\n", err)
}

func firstCall(i int) error {
  if err := secondCall(i); err != nil {
    return fmt.Errorf("secondCall(%d): %w", i, err)
  }
  return nil
}

func secondCall(i int) error {
  return &AppError{99}
}
```

输出：
As says it is an AppError
Custom App Error: 99
secondCall(10): App Error, State: 99

# 第 6 章 并发

在本章中，我将学习什么是并发以及如何应用它。在继续之前，定义一些词汇很重要。

**工作**：一组待执行的指令。

**线程**：被调执行路径。

**线程状态**：线程可以处于三种状态之一：运行（Running）、可运行（Runnable）、等待（Waiting）。

**并发**：意味着执行顺序无关。换句话说，一组指令以不同的顺序执行，我会说我的工作是并发完成的，只要所有工作都完成了。

**并行性**：意味着同时做很多事情。为了实现这一点，我需要硬件能够同时执行多个操作系统线程。

**CPU 密集型工作**：这是指不会导致线程自然进入等待状态的工作。计算斐波契数被认为是 CPU 密集型工作。

**I/O 密集型工作**：这是指会导致线程自然进入等待状态的工作。从不同的 URL 获取数据被认为是 I/O 密集型工作。

**同步**：当两个或多个 Goroutine 需要访问同一个内存位置时，它们需要同步并轮流执行。如果没有发生这种同步，且至少有一个 Goroutine 正在执行，就会导致数据竞态。

**编排**：当两个或多个 Goroutine 需要相互信号时，在没有数据的情况下，编排是所需的机制。

图 6.1
![图 6.1](img/8be067925d0a2d5e9bad63119)

调度语义

操作系统调度器的工作是创建许多线程。然而，Go 运行时调度器不同。Go 运行时调度器是一个 M:N 调度器，这意味着将 M 个 goroutine 映射到 N 个操作系统线程。

“G”代表 goroutine，“M”代表操作系统线程，“P”代表处理器。P 是执行 Go 代码的资源。为了运行 G，M 必须持有一个 P。

调度器使用多种技术来管理 goroutine，其中最重要的是工作窃取。每个 P 都有一个本地 goroutine 运行队列。当一个 M 完成其 goroutine 时，它尝试从另一个 P 的运行队列中窃取一半的 goroutine。这确保了所有处理器都保持忙碌。

遗漏。这可能会导致各种数据损坏 bug。

关于调度语义有许多细小的细节，因此为了学习这些，请阅读第 14 章中标题为《Go 调度》的几篇文章。

### 6.2 并发基础

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

# 列表 6.15

输出：

```
Start Goroutines
Waiting To Finish
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z A C D E F G H I K L
M a b d e f g h i j k l m n o p Q R S T U V W X Y z A C D E F G H I
J L M N O P Q R S T U V W X Y Z p q r s t u v w x y z a b c d e f g h i j
k l m n o p q r s t u v w x y z a b c d e f g h i j k l m n o p q r s t u v
w x z
Terminating Program
```

我所看到的是，该程序的并发性现在是细粒度的。字母的输出是未定义且无序的。

### 6.4 数据竞态

数据竞态是指两个或多个 Goroutine 同时尝试访问同一个内存位置，其中至少一个 Goroutine 正在执行操作。当这种情况发生时，结果是不可预测的。这类 bug 很难找到，因为它们引起的问题总是随机出现。

这里 Scott Meyers 的这段约 8 分钟视频非常值得听：

CPU Caches and Why You Care（CPU 缓存以及你为什么关注）30:09-38:30
https://youtube.be/WDIqkP4JbkEt=1809

### 6.5 数据竞态示例

这是一个数据竞态的极佳示例，展示了它们如何被隐藏多年，最终在奇怪的时间出现并导致数据损坏。

# 列表 6.16

```go
var counter int
func main() {
  const grs = 2
  var wg sync.WaitGroup
  wg.Add(grs)
  for g := 0; g < grs; g++ {
    go func() {
      for i := 0; i < 2; i++ {
        value := counter
        value++
        counter = value
      }
      wg.Done()
    }()
  }
  wg.Wait()
  fmt.Println("Counter:", counter)
}
```

该程序创建了两个 Goroutine，它们都访问同一个整数变量，并将该变量增加了两次。Goroutine 手动对共享状态执行了读、改、写操作。

# 列表 6.17

```go
var counter int
func main() {
  ..
  go func() {
    for i := 0; i < 2; i++ {
      value := counter
      value++
      counter = value
    }
    wg.Done()
  }()
  ..
}
```

我可以看到 `for` 循环内部对共享状态的访问。当我编译并运行这个程序时，我每次都得到 4 的这个正确答案。

# 列表 6.18

```bash
