

# Go 性能分析与示例函数

## 性能分析概述

Go 支持多种性能分析，每种关注性能的不同方面，但它们都涉及记录一系列感兴趣的事件序列，每个事件都附带一个堆栈跟踪——即事件发生时刻活跃的函数调用栈。`go test` 工具内置了对多种性能分析的支持。

### CPU 性能分析

*CPU 性能分析* 标识出执行最耗费 CPU 时间的函数。每个 CPU 上当前正在运行的线程会被操作系统每隔几毫秒周期性地中断，每次中断在恢复正常执行前记录一个性能分析事件。

### 堆性能分析

*堆性能分析* 标识出负责分配最多内存的语句。性能分析库对内部内存分配例程的调用进行采样，因此平均每分配 512KB 内存就会记录一个性能分析事件。

### 阻塞性能分析

*阻塞性能分析* 标识出导致 goroutine 阻塞时间最长的操作，例如系统调用、通道发送和接收、以及获取锁。每当 goroutine 被这些操作之一阻塞时，性能分析库就会记录一个事件。

为测试代码收集性能分析数据只需启用以下标志之一即可。但请注意，同时使用多个标志时要小心：收集一种性能分析的机制可能会扭曲其他性能分析的结果。

```
$ go test -cpuprofile=cpu.out
$ go test -blockprofile=block.out
$ go test -memprofile=mem.out
```

为非测试程序添加性能分析支持也很简单，尽管具体做法在短命命令行工具和长期运行的服务器应用之间有所不同。性能分析在长期运行的应用中特别有用，因此 Go 运行时的性能分析功能可以通过 `runtime` API 在程序员控制下启用。

## 使用 `pprof` 分析性能数据

收集到性能分析数据后，我们需要使用 `pprof` 工具进行分析。它是 Go 发行版的标准组成部分，但因为它不是日常工具，所以通过 `go tool pprof` 间接访问。它有数十种功能和选项，但基本用法只需要两个参数：生成性能分析数据的可执行文件和性能分析日志。

为了使性能分析高效并节省空间，日志中不包含函数名；相反，函数通过其地址来标识。这意味着 `pprof` 需要可执行文件才能解读日志。虽然 `go test` 通常在测试完成后丢弃测试可执行文件，但启用性能分析时，它会将可执行文件保存为 `foo.test`，其中 `foo` 是被测试包的名称。

以下命令展示了如何收集并显示简单的 CPU 性能分析。我们选择了 `net/http` 包中的一个基准测试。通常最好对特定的、具有代表性的基准测试进行性能分析。对测试用例进行基准测试几乎从不具备代表性，这就是为什么我们使用过滤器 `-run=NONE` 来禁用它们。

```
$ go test -run=NONE -bench=ClientServerParallelTLS64 \
    -cpuprofile=cpu.log net/http
PASS
BenchmarkClientServerParallelTLS64-8  1000
   3141325 ns/op  143010 B/op  1747 allocs/op
ok      net/http       3.395s

$ go tool pprof -text -nodecount=10 ./http.test cpu.log
2570ms of 3590ms total (71.59%)
Dropped 129 nodes (cum <= 17.95ms)
Showing top 10 nodes out of 166 (cum >= 60ms)
    flat  flat%   sum%     cum   cum%
  1730ms 48.19% 48.19%  1750ms 48.75%  crypto/elliptic.p256ReduceDegree
   230ms  6.41% 54.60%   250ms  6.96%  crypto/elliptic.p256Diff
   120ms  3.34% 57.94%   120ms  3.34%  math/big.addMulVVW
   110ms  3.06% 61.00%   110ms  3.06%  syscall.Syscall
    90ms  2.51% 63.51%  1130ms 31.48%  crypto/elliptic.p256Square
    70ms  1.95% 65.46%   120ms  3.34%  runtime.scanobject
    60ms  1.67% 67.13%   830ms 23.12%  crypto/elliptic.p256Mul
    60ms  1.67% 68.80%   190ms  5.29%  math/big.nat.montgomery
    50ms  1.39% 70.19%    50ms  1.39%  crypto/elliptic.p256ReduceCarry
    50ms  1.39% 71.59%    60ms  1.67%  crypto/elliptic.p256Sum
```

`-text` 标志指定输出格式，本例中为文本表格，每行一个函数，按“最热”函数——即消耗 CPU 周期最多的函数——排在最前面。`-nodecount=10` 标志将结果限制为 10 行。对于明显的性能问题，这种文本格式可能足以定位原因。

该性能分析告诉我们，椭圆曲线加密对于这个特定 HTTPS 基准测试的性能至关重要。相比之下，如果性能分析主要由 `runtime` 包中的内存分配函数主导，那么减少内存消耗可能是值得的优化方向。

对于更微妙的问题，您可能更适合使用 `pprof` 的图形化显示之一。这些需要 GraphViz，可从 `www.graphviz.org` 下载。然后 `-web` 标志会渲染程序函数的有向图，并用 CPU 性能分析数字标注，通过颜色指示最热的函数。

我们在这里只是触及了 Go 性能分析工具的皮毛。要了解更多，请阅读 Go 博客上的“Profiling Go Programs”文章。

## 11.6 `Example` 函数

`go test` 特殊对待的第三种函数是示例函数，其名称以 `Example` 开头。它没有参数也没有返回值。这是一个为 `IsPalindrome` 编写的示例函数：

```
func ExampleIsPalindrome() {
    fmt.Println(IsPalindrome("A man, a plan, a canal: Panama"))
    fmt.Println(IsPalindrome("palindrome"))
    // Output:
    // true
    // false
}
```

![godoc 中 strings.Join 的交互式示例。](graphics/godoc-example.png)

**图 11.4.** `godoc` 中 `strings.Join` 的交互式示例。

示例函数有三个用途。首要的是文档记录：一个好的示例比文字描述能更简洁或直观地传达库函数的行为，特别是作为提醒或快速参考时。示例还可以演示属于同一 API 的多个类型和函数之间的交互，而文字文档必须始终附属于某个位置，如类型或函数声明，或整个包。与注释中的示例不同，示例函数是真实的 Go 代码，接受编译时检查，因此不会随着代码演进而过时失效。

根据 `Example` 函数的后缀，基于 Web 的文档服务器 `godoc` 将示例函数与其演示的函数或包关联起来，因此 `ExampleIsPalindrome` 会显示在 `IsPalindrome` 函数的文档中，而名为 `Example` 的示例函数则会与 `word` 包作为一个整体关联。

第二个用途是示例作为由 `go test` 运行的可执行测试。如果示例函数包含如上所示的最终 `// Output:` 注释，测试驱动程序将执行该函数，并检查其打印到标准输出的内容是否与注释中的文本匹配。

示例的第三个用途是动手实验。`golang.org` 上的 `godoc` 服务器利用 Go Playground 让用户在 Web 浏览器中编辑并运行每个示例函数，如图 11.4 所示。这通常是对特定函数或语言特性建立直观认识的最快途径。

本书最后两章将探讨 `reflect` 和 `unsafe` 包，极少 Go 程序员会经常使用它们——甚至更少的人*需要*使用它们。如果您还没有编写过任何实质性的 Go 程序，现在是个很好的时机。

# 12. 反射

