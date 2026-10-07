

# 图 12.4

![](img/8be06d78925d0d5a2d2ade851e9bad63_239_0.png)

堆图中用两种颜色（或色调）表示。橙色（较深色调）代表微秒级堆上正在使用的内存量。绿色（较浅色调）代表根据该部分内存再次被堆使用的时间，预测下一次何时触发 GC（垃圾回收）。

# 图 12.5

![](img/8be06d78925d0d5a2d2ade851e9bad63_239_1.png)

这就是为什么当橙色区域到达绿色区域顶部时，GC 区域会出现一条线。每条线代表发生过一次 GC。顺便说一下，圆点是此处列出的堆信息的选择点。

由于绿色区域在整个程序运行期间保持一致的直线，我可以选择任何橙色点来查看堆的最大尺寸，该尺寸为 4MB 内存。

如果我想更清楚地了解这个数字，可以使用 GDEBUG 并重新运行程序。

# 列表 12.8

```
$ time GDEBUG=gctrace=1 ./trace > .out

gc 1 @01.06s 0%: 0.020+0.024+0.025 ms clock, 0.32+0.18/0.12+0.39 ms cpu,
4->4o MB, 5 MB goal, 16 P
gc 2 @00.29s 0%: 0.030+0.023+0.002 ms clock, 0.49+0.15/0.17+0.001+0.037 ms cpu, 4->4o MB, 5 MB goal, 16 P
gc 3 @08.04s 0%: 0.033+0.026+0.019 ms clock, 0.52+0.15/0.059+0.31 ms cpu, 4->4o MB, 5 MB goal, 16 P
gc 73 @82.79s 0%: 0.043+0.046+0.040 ms clock, 0.70+0.24/0.18/0.25+0.65 ms cpu, 4->4o MB, 5 MB goal, 16 P
gc 74 @82.80s 0%: 0.043+0.035+0.002 ms clock, 0.69+0.28/0.37+0.16+0.042 ms cpu, 4->4o MB, 5 MB goal, 16 P
gc 75 @82.814s 0%: 0.032+0.028+0.017 ms clock, 0.52+0.20/0.26+0.026+0.28 ms cpu, 4->4o MB, 5 MB goal, 16 P
```

2021/05/12 15:17:24 Searching 4000 files, found presiden 2800 times.

果如其然，堆保持在 4MB，且所有内存都是瞬态的，每次 GC 导致存活值数量为零。正我在跟踪（trace）中看到的。

我真正需要的是关于 GC 的更多信息。不是关乎某一次 GC，而是关乎所有需要发生的 GC。我可以通过选择工具并双击任何蓝线来获取这些信息。

# 图 12.6

| 已选中 275 个项目。 | 切片 (275) |
| 名称 | 墙钟时长 (Wall Duration) | 自有时间 (Self time) | 平均墙钟时长 | 出现次数 |
| :--- | :--- | :--- | :--- | :--- |
| GC | 106,639,993 ns | 106,639,993 ns | 387,72 ns | 275 |

- 选择开始
  - 15,245,706 ns
- 选择范围
- 开始
- CPU 持续时间
- 持续
- CPU 自有时间

这些数字有助于确定 GC 在程序执行过程中做了多少工作。有了这些数字，我对比程序的性能有了一个基准。

## 表 12.1

| | 单次 |
| :--- | :--- |
| 运行时间 | 2670ms |
| 顶部内存 | 4 MB |
| GC 发生次数 | 275 |
| GC 平均持续时间 | 387us |
| GC 墙钟时长 | 106ms |
| GC 耗时 | 4% |

有了基准数字，我仍然不知道如何加速程序。也许查看图表的更大部分会有帮助？

图 12.7

- Proc 0
- Proc 1
- Proc 2
- Proc 3

![](img/8be06d78925d0d5a2d2ade851e9bad63_239_1.png)

如果我更仔细地查看跟踪的这一部分，就能发现问题。程序任何时候只使用一个逻辑处理器来执行工作。然而，如果我将算法改为使用机器上所有的核心，应该会有帮助。

## 12.4 扇出 (Fan-Out)

可以使用的一种并发模式是扇出（fan-out）模式。这种模式的想法是为每个需要处理的文件创建一个 Goroutine，并让调度器管理所有的逻辑处理器。我可以扇出这些 Goroutine，因为工作的顺序并不重要。重要的是完成了所有工作。

# 列表 12.9

```go
func freqConcurrent(topic string, docs []string) {
    var found int

    g := len(docs)                << ADDED
    var wg sync.WaitGroup      << ADDED
    wg.Add(g)                   << ADDED

    for _, doc := range docs {
        .
    }

    wg.Wait()                   << ADDED
    return
}
```

为了开始，我需要添加代码使得 `freq` 函数在所有工作完成之前不返回。这通过使用 WaitGroup 实现最好。首先识别需要创建的 Goroutine 数量（即 `docs` 的长度），将该数字加入 WaitGroup，并在函数末尾等待 WaitGroup 归零。

# 列表 12.0

```go
func freqConcurrent(topic string, docs []string) int {
    var found int

    g := len(docs)
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

## 12.5 缓存友好 (Cache Friendly)

问题出在 `found` 变量上。技术上，它是对于访问内存的 4k Goroutine 来说的全局变量。虽然使用 `atomic` 包有助于序列化访问，但我机器上执行 Goroutine 的每个核心都会接收并操作 `found` 变量的副本。一旦任何核心内部的任何副本被增加，它就会将所有其他核心中的所有副本标记为脏。

当下一个 Goroutine 尝试增加其副本时，如果该副本被标记为脏，就需要从主内存中拉取新的副本。这将导致内存抖动，减慢一切速度。为了缓解抖动，我需要每个 Goroutine 使用局部变量来计算找到词的次数。然而，在 Goroutine 终止之前，它必须将其局部变量的结果加到全局变量。对于当前的算法，这意味着我们将抖动从 28k 次减少到了 4k 次。不是完美，但好得多。

