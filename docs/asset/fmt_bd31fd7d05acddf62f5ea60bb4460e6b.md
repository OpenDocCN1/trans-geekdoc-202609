
```go
var wg sync.WaitGroup

wg.Add(g)

for _, doc := range docs {

    go func(doc string) {     << ADDED

        defer wg.Done()        << ADDED

        ..

    }(doc)                   << ADDED

}

wg.Wait()

return

}
```

接下来，我将 `range` 循环内部内部的代码封装在 Goroutine 中，将每次迭代的文件传递给新的 Goroutine 以防止闭包 Bug。有了 Goroutine，我通过确保每个 Goroutine 在终止前调用 `wg.Done()` 来完成 WaitGroup。最后需要做的是处理文件时移除返回值。我可能会认为由于 WaitGroup 已到位这段代码已经好了，但如果我用竞争检测器运行这段代码会发生什么？

# 列表 12.11

```bash
$ go build -race

$ ./trace > t.out

=====================

WARNING: DATA RACE

Read at 0x00c15748 by goroutine 21:

main.freq.func()

/Users/bill/code/src/github.com/ardlanabs/gotraining/topics/go/

profiling/trace.go:103 +0x644

Previous write at 0x00c15748 by goroutine 66:

main.freq.func()

/Users/bill/code/src/github.com/ardlanabs/gotraining/topics/go/

profiling/trace.go:103 +0x65d
```

看起来我有数据竞争。输出的前两行显示在函数内部同一行代码上存在读取和一个之前的写入。103 行的代码是什么？

# 列表 12.12

```go
96 for _, item := range d.Channel.Items {
97     if strings.Contains(item.Title, topic) {
98         found++
99         continue
100     }
101 
102     if strings.Contains(item.Description, topic) {
103         found++
104     }
105 }
```

如果我给代码添加行号，可以看到它与 `found` 变量的增加有关。这段代码实际上在第 98 行再次使用，因此两行代码（98, 103）都包含数据竞争。

为了修复这个竞争，我需要将 `found` 变量的增加改为使用原子指令。为此我可以使用 `atomic` 包。

# 列表 12.12

```go
96 for _, item := range d.Channel.Items {
97     if strings.Contains(item.Title, topic) {
98         atomic.AddInt32(&found, 1)         << CHANGED
99         continue
100     }
101 
102     if strings.Contains(item.Description, topic) {
103         atomic.AddInt32(&found, 1)         << CHANGED
104     }
105 }
```

我替换了第 98 行和第 103 行使用 `atomic.AddInt32` 函数。问题是函数需要 `int32` 而不是 `int`，所以我需要再做两个更改。

# 列表 12.13

```go
func freq(topic string, docs []string) int {
    var found int32      << CHANGED
    .
    wg.Wait()
    return int(found)    << CHANGED
}
```

### 12.5 缓存友好 (Cache Friendly)

问题出在 `found` 变量上。技术上，它是对于访问内存的 4k Goroutine 来说的全局变量。虽然使用 `atomic` 包有助于序列化访问，但我机器上执行 Goroutine 的每个核心都会接收并操作 `found` 变量的副本。一旦任何核心内部的任何副本被增加，它就会将所有其他核心中的所有副本标记为脏。

当下一个 Goroutine 尝试增加其副本时，如果该副本被标记为脏，就需要从主内存中拉取新的副本。这将导致内存抖动，减慢一切速度。为了缓解抖动，我需要每个 Goroutine 使用局部变量来计算找到词的次数。然而，在 Goroutine 终止之前，它必须将其局部变量的结果加到全局变量。对于当前的算法，这意味着我们将抖动从 28k 次减少到了 4k 次。不是完美，但好得多。

# Listing 12.14

```go
func freq(topic string, docs []string) int {
    var found int32
    g := len(docs)
    var wg sync.WaitGroup
    wg.Add(g)
    for _, doc := range docs {
        go func(doc string) {
            var found int32                -- ADDED
            defer func() {                 -- CHANGED
                atomic.AddInt32(&found, lFound)  -- MOVED
                wg.Done()                   -- MOVED
            }()
            for _, item := range d.Channel.Items {
                if strings.Contains(item.Title, topic) {
                    lFound++                   -- CHANGED
                    continue
                }
                if strings.Contains(item.Description, topic) {
                    lFound++                   -- CHANGED
                }
            }
        }(doc)
    }
    wg.Wait()
    return int(found)
}
```

我添加了一个新变量 `lFound` 来表示每个 Goroutine 局部的找到计数变量。这意味着我可以从搜索主题匹配的循环内部移除 `atomic.AddInt32` 调用。由于我仍然需要更新全局变量 `found`，因此我在调用 `wg.Done()` 之前在 `defer` 中执行该操作。

## 12.6 扇出（Fan-Out）结果

在完成这些更改后，我可以尝试新的基于扇出的算法。

# Listing 12.15

```bash
$ go build

$ ./trace > t.out

2021/05/13 12:10:51 Search 4000 files, found 28000 times.

./trace > t.out 7.30s user 0.71s system 106% cpu 0.725 total
$ ./trace > t.out

2021/05/13 12:10:53 Search 4000 files, found 28000 times.

./trace > t.out 7.21s user 0.76s system 127% cpu 0.615 total
```

我已经从时间上看到性能提升了 2 秒。现在我可以查看追踪（trace）。

# 图 12.8

![](img/8be06d78925d0d5a2d2ade851e9bad63_246.png)

这是一个良好的信号，说明我机器上所有的 CPU 负载都在被使用。如果我向下滚动，将看到所有 16 个逻辑处理器都在使用中。我需要为这个算法收集所有的测量数据。

# 表 12.2

| 运行时 | 单线程 | 扇出 |
|---|---|---|
| | 270ms | 580ms |
| 顶部内存 | 4 Meg | 53 Meg |
| GC 次数 | 275 | 62 |
| GC 平均持续时间 | 387us | 4ms |
| GC 总持续时间 | 106ms | 250ms |
| GC 耗时 | 4% | 43% |

我看到有 2 秒的提升，但这是以 GC 消耗更多数量级内存为代价的。然而，由于配置（profile）变大，GC 的次数减少了。这个追踪中有几个很有有趣的方面。

# 图 12.9

![](img/8be06d78925d0d5a2d2ade851e9bad63_247.png)

我正在查看前 45ms 的时间，期间所有 4k Goroutine 都有机会运行并被调度器置于等待状态。我可以看到密集的上下文切换，以及 Setup（STW 终止）阶段是在 GC 中间开始的。这意味着在 GC 尝试停止所有工作以便开始标记阶段之前花费了约 19ms。在图中显示 GC 期间 Goroutine 的顶部区域，如果我扩展此视图的某个部分，将更清楚地看到上下文切换。

# 图 12.10

* 系统调用 (Syscalls)
* Proc 0
* Proc 1
* Proc 2

| 标题 | 事件(s) | 链接 |
|---|---|---|
| selected | main.freq.func1 | 入入流: go |
| User | 出出流: go |
| Start | 22,137 ns | 前序事件: 各种类型 |
| Wall Duration | 123,547 ns | 后续事件: 各种类型 |
| Self Time | 123,547 ns | 所有连接事件: 各种类型 |

```
main.freq.func1:

End Stack Trace runtime.gc.Start:132

runtime.mallocgc:116

runtime.growsize:224

io.ReadAll:631
```
