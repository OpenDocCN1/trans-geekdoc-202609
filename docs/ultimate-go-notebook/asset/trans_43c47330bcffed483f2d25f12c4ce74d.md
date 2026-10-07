

![](img/8be06d78925d0d5a2d2ade851e9bad63_321_0.png)

在图1中，你可以看到两个逻辑处理器（P）的示意图，它们各自连接到机器上独立的操作系统线程（M），而这些线程又对应独立的硬件线程（Core）。你可以看到两个 Goroutine（G1 和 G2）正在并行执行，同时在各自的 OS/硬件线程上执行指令。在每个逻辑处理器内部，三个 Goroutine 轮流共享各自的 OS 线程。所有这些 Goroutine 都在并发运行，按无顺序执行指令并共享 OS 线程的时间。

问题在于，有时利用并发而不使用并行反而会降低你的吞吐量。同样有趣的是，有时同时利用并发和并行带来的性能提升可能并不如你想象的那么大。

# 负载 (Workloads)

如何判断何时无序执行是可能的或合理的？理解你的问题所处理的负载类型是一个极佳的起点。在考虑并发时，有两种类型的负载需要理解：

- **CPU 密集型 (CPU-Bound)：** 这种负载永远不会产生 Goroutine 自然地在等待状态之间切换的情况。一个计算圆周率到第 N 位的线程就是那种不断进行计算的工作。

- **I/O 密集型 (I/O-Bound)：** 这种负载会使 Goroutine 自然地进入等待状态。这类工作包括通过网络请求资源访问、向操作系统进行系统调用，或等待事件发生。需要读取文件的 Goroutine 就是 I/O 密集型的。我会将导致 Goroutine 等待的同步事件（如互斥锁、原子操作）也包含在此类别中。

对于 **CPU 密集型负载**，你需要通过并行来利用并发。单个 OS/硬件线程处理多个 Goroutine 是低效的，因为 Goroutine 不会因为负载的原因自然地在等待状态间切换。Goroutine 的数量多于 OS/硬件线程会因为延迟开销（将 Goroutine 在 OS 线程上移入移出所需的时间）而减慢负载执行。上下文切换会为你的负载创建一个“停顿世界（Stop The World）”事件；在切换期间，你本可以执行的负载完全无法运行。

对于 **I/O 密集型负载**，你不需要并行即可使用并发。单个 OS/硬件线程就可以高效地处理多个 Goroutine；因为 Goroutine 会作为负载的一部分自然地在等待状态间切换。Goroutine 的数量多于 OS/硬件线程可以加速负载执行，因为 Goroutine 在 OS 线程上的移入切换延迟开销不会产生“停顿世界”事件。你的负载会自然停止，这允许不同的 Goroutine 高效地利用同一个 OS/硬件线程，而不是让该线程处于空闲。

如何知道每个硬件提供多少个 Goroutine 能获得最佳吞吐量？Goroutine 太少会导致更多空闲时间；Goroutine 太多会导致更多的上下文延迟时间。这是你需要去思考的问题，但超出了本文的讨论范围。

目前，重要的是回顾一些代码，以巩固你识别负载何时可以利用并发、何时不能、以及是否需要并行的能力。

# 加法计算 (Adding Numbers)

我们不需要复杂的代码来视觉化并理解这些语义。看下面这个名为 `add` 的函数，它计算一个整数集合的和。

列表 1

```go
36 func add(numbers []int) int {
37   var v int
38   for _, n := range numbers {
39     v += n
40   }
41   return v
42 }
```

在列表 1 的第 36 行，声明了一个名为 `add` 的函数，它接收一个整数集合并返回和。第 37 行定义的变量 `v` 用于存储和。然后第 38 行，函数线性遍历集合，并在第 39 行将每个数字加到当前总和上。最后在第 41 行，函数将最终总和返回给调用者。

问题：`add` 函数负载适合无序执行吗？我认为答案是肯定的。整数集合可以被分成更小的列表，这些列表可以并发处理。一旦所有较小列表都求了和，将这些和相加，即可得到与顺序执行版本相同的答案。

然而，另一个问题浮现在脑海：应该创建并独立处理多少个小列表才能获得最佳吞吐量？要回答这个问题，你必须知道执行的是什么种负载。`add` 函数执行的是 **CPU 密集型负载**，因为算法在执行纯数学计算，没有任何会导致 goroutine 进入等待状态。这意味着这意味着每个 OS/硬件线程使用一个 Goroutine 即可获得良好的吞吐量。列表 2 是是我 `add` 的并发版本。

列表 2

```go
func addConcurrent(goroutines int, numbers []int) int {
    var v int64
    totalNumbers := len(numbers)
    lastGoroutine := goroutines - 1
    stride := totalNumbers / goroutines

    var wg sync.WaitGroup
    wg.Add(goroutines)

    for i := 0; i < goroutines; i++ {
        go func(i int) {
            defer wg.Done()
            start := i * stride
            end := start + stride
            if i == lastGoroutine {
                end = totalNumbers
            }
            var lv int64
            for _, n := range numbers[start:end] {
                lv += int64(n)
            }
            atomic.AddInt64(&v, lv)
        }(i)
    }

    wg.Wait()
    return int(v)
}
```

*(注：由于原文后半部分存在大量重复和混乱，译文已根据代码逻辑进行了对对齐处理。)*

