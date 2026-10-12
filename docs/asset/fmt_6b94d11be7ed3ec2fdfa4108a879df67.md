
```go
close(e.ready) // broadcast ready condition

} else {

    // This is a repeat request for this key.

    memo.mu.Unlock()

    <-e.ready // wait for ready condition

}

return e.res.value, e.res.err

}
```

对 `Get` 的调用现在涉及获取保护 `cache` 映射的互斥锁，在映射中查找指向现有 `entry` 的指针，如果未找到则分配并插入一个新的 `entry`，然后释放锁。如果存在现有的 `entry`，其值不一定已经就绪——另一个 goroutine 可能仍在调用缓慢的函数 `f`——因此调用 goroutine 必须在读取 `entry` 的 `result` 之前等待该 `entry` 的“就绪”条件。它通过从 `ready` 通道读取值来实现这一点，因为此操作会阻塞直到通道关闭。

如果不存在现有的 `entry`，则通过将一个新的“未就绪” `entry` 插入映射，当前 goroutine 就负责调用缓慢函数、更新 `entry`，并通过关闭通道向可能（届时）正在等待它的其他 goroutine 广播新 `entry` 的就绪状态。

请注意，`entry` 中的变量 `e.res.value` 和 `e.res.err` 在多个 goroutine 之间共享。创建 `entry` 的 goroutine 设置它们的值，其他 goroutine 在“就绪”条件广播后读取它们的值。尽管被多个 goroutine 访问，但不需要互斥锁。`ready` 通道的关闭 *happens before* 任何其他 goroutine 接收广播事件，因此第一个 goroutine 中对这些变量的写入 *happens before* 后续 goroutine 对它们的读取。不存在数据竞争。

我们的并发、重复抑制、非阻塞缓存已完成。

上述 `Memo` 的实现使用互斥锁来保护由每个调用 `Get` 的 goroutine 共享的映射变量。将这种设计与另一种设计进行对比很有趣，在另一种设计中，映射变量被限制在一个*监控 goroutine* 中，`Get` 的调用者必须向其发送消息。

`Func`、`result` 和 `entry` 的声明保持不变：

```go
// Func is the type of the function to memoize.

type Func func(key string) (interface{}, error)

// A result is the result of calling a Func.

type result struct {

    value interface{}

    err   error

}

type entry struct {

    res   result

    ready chan struct{} // closed when res is ready

}

```

然而，`Memo` 类型现在由一个通道 `requests` 组成，`Get` 的调用者通过它与监控 goroutine 通信。该通道的元素类型是 `request`。使用此结构，`Get` 的调用者向监控 goroutine 发送键（即备忘函数的参数）和另一个通道 `response`，当结果可用时应通过该通道发回。此通道将仅传递单个值。

```go
// A request is a message requesting that the Func be applied to key.

type request struct {

    key      string

    response chan<- result // the client wants a single result

}

type Memo struct{ requests chan request }

// New returns a memoization of f.  Clients must subsequently call Close.

func New(f Func) *Memo {

    memo := &Memo{requests: make(chan request)}

    go memo.server(f)

    return memo

}

func (memo *Memo) Get(key string) (interface{}, error) {

    response := make(chan result)

    memo.requests <- request{key, response}

    res := <-response

    return res.value, res.err

}

func (memo *Memo) Close() { close(memo.requests) }

```

上面的 `Get` 方法创建一个响应通道，将其放入请求中，发送给监控 goroutine，然后立即从中接收。

`cache` 变量被限制在监控 goroutine `(*Memo).server` 中，如下所示。监控循环读取请求，直到 `Close` 方法关闭请求通道。对于每个请求，它查询缓存，如果未找到则创建并插入一个新的 `entry`。

```go
func (memo *Memo) server(f Func) {

    cache := make(map[string]*entry)

    for req := range memo.requests {

        e := cache[req.key]

        if e == nil {

            // This is the first request for this key.

            e = &entry{ready: make(chan struct{})}

            cache[req.key] = e

            go e.call(f, req.key) // call f(key)

        }

        go e.deliver(req.response)

    }

}

func (e *entry) call(f Func, key string) {

    // Evaluate the function.

    e.res.value, e.res.err = f(key)

    // Broadcast the ready condition.

    close(e.ready)

}

func (e *entry) deliver(response chan<- result) {

    // Wait for the ready condition.

    <-e.ready

    // Send the result to the client.

    response <- e.res

}

```

以类似于基于互斥锁版本的方式，对给定键的首次请求负责在该键上调用函数 `f`，将结果存储在 `entry` 中，并通过关闭 `ready` 通道广播 `entry` 的就绪状态。这由 `(*entry).call` 完成。

对同一键的后续请求在映射中找到现有的 `entry`，等待结果就绪，并通过响应通道将结果发送给调用 `Get` 的客户端 goroutine。这由 `(*entry).deliver` 完成。`call` 和 `deliver` 方法必须在各自的 goroutine 中调用，以确保监控 goroutine 不会停止处理新请求。

此示例表明，可以使用两种方法中的任一种——共享变量和锁，或通信顺序进程——来构建许多并发结构，而不会产生过度的复杂性。

在给定情况下，哪种方法更可取并不总是显而易见的，但了解它们如何对应是值得的。有时从一种方法切换到另一种方法可以使代码更简单。

**练习 9.3：** 扩展 `Func` 类型和 `(*Memo).Get` 方法，以便调用者可以提供一个可选的 `done` 通道，通过该通道他们可以取消操作（§8.9）。被取消的 `Func` 调用的结果不应被缓存。

## 9.8 Goroutines 和 Threads

在上一章中，我们说 goroutine 和操作系统（OS）线程之间的区别可以暂时忽略。虽然它们之间的差异本质上是定量的，但足够大的定量差异会变成定性差异，goroutine 和线程正是如此。现在是区分它们的时候了。

### 9.8.1 可增长的栈

每个操作系统线程都拥有一块固定大小的内存块（通常高达 2MB）作为其 `stack`（栈），这是保存正在进行或暂时挂起（因调用另一函数而挂起）的函数调用的局部变量的工作区。这种固定大小的栈同时存在“太大”和“太小”的问题。对于一个小型 goroutine（例如仅等待 `WaitGroup` 然后关闭一个 channel 的 goroutine）来说，2MB 的栈会造成巨大的内存浪费。Go 程序一次性创建数十万个 goroutine 并不罕见，若栈如此之大则无法实现。然而尽管栈很大，固定大小的栈对于最复杂和深度递归的函数来说仍不够用。更改固定大小可以提高空间效率并允许创建更多线程，或者支持更深的递归函数，但不能两者兼得。

相比之下，goroutine 启动时仅拥有一个小栈，通常为 2KB。与操作系统线程的栈一样，goroutine 的栈保存活跃和挂起函数调用的局部变量，但与操作系统线程不同的是，goroutine 的栈不是固定的；它会根据需要增长和收缩。goroutine 栈的大小限制可高达 1GB，比典型的固定大小线程栈大几个数量级，当然极少数 goroutine 会用那么多。

**练习 9.4：** 构建一个管道，用 channel 连接任意数量的 goroutine。在不耗尽内存的情况下，你能创建的最大管道阶段数是多少？一个值穿越整个管道需要多长时间？

### 9.8.2 Goroutine 调度

操作系统线程由操作系统内核调度。每隔几毫秒，硬件定时器就会中断处理器，导致一个名为 `scheduler`（调度器）的内核函数被调用。该函数挂起当前正在执行的线程并将其寄存器保存到内存中，查看线程列表并决定下一个该运行哪个线程，从内存恢复该线程的寄存器，然后恢复该线程的执行。因为操作系统线程由内核调度，从一个线程切换控制权到另一个线程需要完整的 `context switch`（上下文切换），即将一个用户线程的状态保存到内存，恢复另一个线程的状态，并更新调度器的数据结构。由于其较差的局部性和所需的大量内存访问，此操作很慢，并且历史上随着访问内存所需的 CPU 周期数增加，情况只会变得更糟。

Go 运行时包含自己的调度器，它使用一种称为 `m:n scheduling`（M:N 调度）的技术，因为它将 `m` 个 goroutine 多路复用（或调度）到 `n` 个操作系统线程上。Go 调度器的工作类似于内核调度器，但它只关注单个 Go 程序的 goroutine。

与操作系统的线程调度器不同，Go 调度器不是由硬件定时器定期调用的，而是由特定的 Go 语言结构隐式调用。例如，当 goroutine 调用 `time.Sleep` 或在 channel 或互斥锁操作中阻塞时，调度器会将其休眠并运行另一个 goroutine，直到该唤醒第一个 goroutine 为止。因为不需要切换到内核上下文，重新调度 goroutine 比重新调度线程廉价得多。

**练习 9.5：** 编写一个包含两个 goroutine 的程序，它们通过两个无缓冲 channel 以乒乓方式来回发送消息。该程序每秒能维持多少次通信？

### 9.8.3 `GOMAXPROCS`

Go 调度器使用一个名为 `GOMAXPROCS` 的参数来确定有多少个操作系统线程可以同时活跃地执行 Go 代码。其默认值是机器上的 CPU 数量，因此在拥有 8 个 CPU 的机器上，调度器会同时在最多 8 个操作系统线程上调度 Go 代码。(`GOMAXPROCS` 是 `m:n` 调度中的 `n`。) 正在睡眠或因通信而阻塞的 goroutine 完全不需要线程。因 I/O 或其他系统调用而阻塞或正在调用非 Go 函数的 goroutine 确实需要一个操作系统线程，但 `GOMAXPROCS` 不必为它们计数。

你可以使用 `GOMAXPROCS` 环境变量或 `runtime.GOMAXPROCS` 函数显式控制此参数。我们可以通过这个小程序看到 `GOMAXPROCS` 的效果，它打印无尽的 0 和 1 流：

```go
for {

    go fmt.Print(0)

    fmt.Print(1)

}
```

```bash
$ GOMAXPROCS=1 go run hacker-cliché.go
111111111111111111110000000000000000000011111...
```

```bash
$ GOMAXPROCS=2 go run hacker-cliché.go
010101010101010101011001100101011010010100110...
```

在第一次运行中，最多只有一个 goroutine 同时执行。最初是打印 1 的主 goroutine。经过一段时间后，Go 调度器将其休眠并唤醒打印 0 的 goroutine，让它获得在操作系统线程上运行的机会。在第二次运行中，有两个操作系统线程可用，因此两个 goroutine 同时运行，以大致相同的速率打印数字。我们必须强调，许多因素都涉及 goroutine 调度，且运行时在不断演进，因此你的结果可能与上述结果不同。

**练习 9.6：** 测量计算密集型并行程序（参见练习 8.5）的性能如何随 `GOMAXPROCS` 变化。在你的计算机上最优值是多少？你的计算机有多少个 CPU？

### 9.8.4 Goroutine 没有标识

在大多数支持多线程的操作系统和编程语言中，当前线程都有独特的标识，可以作为普通值轻松获取，通常是整数或指针。这使得构建称为 `thread-local storage`（线程本地存储）的抽象变得容易，它本质上是一个以线程标识为键的全局映射，以便每个线程可以存储和检索独立于其他线程的值。

Goroutine 没有程序员可访问的标识概念。这是设计使然，因为线程本地存储容易被滥用。例如，在使用具有线程本地存储的语言实现的 Web 服务器中，许多函数通常通过查看该存储来查找关于当前正在为其工作的 HTTP 请求的信息。然而，就像过度依赖全局变量的程序一样，这可能导致不健康的“远程作用”，即函数的行为不仅由其参数决定，还由其运行所在的线程标识决定。因此，如果线程标识发生变化——例如征用一些工作线程来帮忙——该函数会神秘地表现异常。

Go 鼓励一种更简单的编程风格，即影响函数行为的参数是显式的。这不仅使程序更易读，还让我们可以自由地将给定函数的子任务分配给许多不同的 goroutine，而无需担心它们的标识。

你现在已经学习了编写 Go 程序所需的所有语言特性。在接下来的两章中，我们将退一步，审视一些支持大规模编程的实践和工具：如何将项目构建为一组包，以及如何获取、构建、测试、基准测试、剖析、文档化和共享这些包。

# 10. 包与 Go 工具

如今一个中等规模的程序可能包含 10,000 个函数。然而其作者只需考虑其中少数几个，甚至设计更少，因为绝大多数是由他人编写并通过 `packages`（包）提供复用的。

Go 自带 100 多个标准包，为大多数应用程序提供基础。Go 社区是一个包设计、共享、复用和改进的繁荣生态系统，发布了更多包，你可以在 `http://godoc.org` 找到可搜索的索引。在本章中，我们将展示如何使用现有包和创建新包。

## Go 工具与包系统

Go 还附带了 `go` 工具，这是一个复杂但易于使用的命令，用于管理 Go 包的工作区。从本书一开始，我们就一直在展示如何使用 `go` 工具来下载、构建和运行示例程序。在本章中，我们将探讨该工具的底层概念，并浏览其更多功能，包括打印文档和查询工作区中包的元数据。在下一章中，我们将探索其测试功能。

## 10.1 简介

任何包系统的目的都是将相关功能组合在一起，形成易于理解和更改的单元，且独立于程序的其他包，从而使大型程序的设计和维护变得切实可行。这种 `模块化` 使得包可以被不同的项目共享和重用，在组织内部分发，或向更广泛的世界提供。

每个包都定义了一个独特的名字空间来封装其标识符。每个名称都与特定的包相关联，这让我们可以为最常使用的类型、函数等选择简短、清晰的名称，而不会与程序的其他部分产生冲突。

包还通过控制哪些名称在包外可见或被导出，提供了 `封装`。限制包成员的可见性将辅助函数和类型隐藏在包的 API 之后，允许包维护者有信心地更改实现，而无需担心包外的代码会受到影响。限制可见性还隐藏了变量，以便客户端只能通过导出的函数来访问和更新它们，这些函数保护内部不变量或在并发程序中强制实施互斥。

当我们更改一个文件时，必须重新编译该文件的包，以及可能依赖它的所有包。Go 编译的速度明显快于大多数其他编译型语言，即使是从头构建也是如此。编译器速度快主要有三个原因。首先，所有导入必须在每个源文件的开头显式列出，因此编译器不必读取和处理整个文件来确定其依赖关系。其次，包的依赖关系形成一个有向无环图，因为没有循环，包可以单独编译，甚至可以并行编译。最后，已编译 Go 包的目标文件不仅记录了包本身的导出信息，还记录了其依赖项的导出信息。编译包时，编译器必须为每个导入读取一个目标文件，但无需查看这些文件之外的内容。

## 10.2 导入路径

每个包由一个称为其 `导入路径` 的唯一字符串标识。导入路径是出现在 `import` 声明中的字符串。

```go
import (

    "fmt"

    "math/rand"

    "encoding/json"

    "golang.org/x/net/html"
```
