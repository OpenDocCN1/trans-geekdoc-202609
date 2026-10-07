
![](img/8be06d78925d0d5a2d2ade851e9bad63_303_0.png)

# 协作式调度器

正如我们在第一篇文章中讨论的，OS 调度器是一个抢占式调度器。本质上，这意味着你无法预测调度器在任何给定时间会做什么。内核正在做出决策，一切是非确定性的。运行在操作系统之上的应用程序对内核内部的调度没有控制权，除非它们利用了原子指令（atomic instructions）和互斥锁（mutex-cells）等同步原语。

https://en.wikipedia.org/wiki/Linearizability
https://en.wikipedia.org/wiki/Lock_(computer_science)

Go 调度器是 Go runtime 的，而 Go runtime 被构建在你的应用程序中。这意味着 Go 调度器运行在用户空间，位于内核之上。

https://en.wikipedia.org/wiki/User_space

Go 调度器的当前实现是一个抢占式调度器。

https://en.wikipedia.org/wiki/Preemption_(computing)

你无法预测 Go 调度器将做什么。这是因为该调度器的决策权并不在开发者手中，也不在 Go runtime 手中。理解调度器是非确定性的很重要。

# Goroutine 状态

与线程（Threads）一样，Goroutine 有相同的三个高级状态。这些状态决定了 Go 调度器对任何给定 Goroutine 的角色。Goroutine 可以处于三种状态之一：等待（Waiting）、可运行（Runnable）或运行（Running）。

**Waiting（等待）**：意味着 Goroutine 已停止并正在等待某些内容以便继续。这可能是因为等待操作系统（系统调用）或同步调用（原子和互斥锁操作）。这类延迟是性能低下的的根源。

**Runnable（可运行）**：意味着 Goroutine 想要获得 M 的时间来执行其分配的指令。如果你有大量的 Goroutine 需要时间，那么 Goroutine 必须等待更才能获得时间。此外，随着更多 Goroutine 竞争时间，任何给定 Goroutine 获得的时间都会缩短。这种调度延迟也可能是性能低下的的原因之一。

**Running（运行）**：意味着 Goroutine 已放置在 M 上并正在执行其指令。与应用程序的工作正在进行。这是大家等待的结果。

# 上文切换

Go 调度器需要定义良好的、发生在代码安全点（safe points）的用户空间事件来进行上下文切换。这些事件和安全点体现在函数调用内部或指令之间。

你的 Go 程序中发生了几类事件，它们允许调度器做出调度决策。这并不意味着它总是发生在这些事件上，而是意味着调度器获得了机会。

这些事件是：

- 使用 `go` 关键字
- 垃圾回收（Garbage collection）
- 系统调用
- 同步与编排（Synchronization and Orchestration）

# `go` 关键字的使用

`go` 关键字是创建 Goroutine 的方式。一旦创建了新的 Goroutine，就会赋予调度器做出调度决策的机会。

# 垃圾回收

由于 GC 使用自己的一组 Goroutine 运行，这些 Goroutine 需要 M 的时间来运行。这导致 GC 产生了大量的调度混乱。然而，调度器对于 Goroutine 在做什么非常智能，并将将利用这种智能来做出聪明的决策。一个聪明的决策是将想要碰堆的 Goroutine 与不碰堆的 Goroutine 进行上下文切换。当 GC 运行时，会做出许多调度决策。

# 系统调用

如果一个 Goroutine 发起的系统调用会导致 M 阻塞，有时调度器能够将 Goroutine 从 M 上切换下来，并将一个新的 Goroutine 切换到同一个 M 上。然而，有时需要一个新的 M 来继续执行排在 P 队列中的 Goroutine。其工作原理将在下一节中详细解释。

# 同步与编排

如果原子、互斥锁或通道操作会导致 Goroutine 阻塞，调度器可以切换一个新的 Goroutine 来运行。一旦该 Goroutine 再次运行，它可以被重新入队并最终切换回 M 上。

# 异步系统调用

当你运行的操作系统具有异步处理系统调用的能力时，可以使用名为网络轮询器（network poller）的东西来更高效地处理系统调用。这是通过使用 kqueue (MacOS)、epoll (Linux) 或 iocp (Windows) 实现的。
