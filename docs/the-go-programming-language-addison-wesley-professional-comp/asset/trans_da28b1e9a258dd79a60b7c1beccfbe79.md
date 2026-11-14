

## 9.5 使用 `sync.Once` 进行一次性初始化

```
func loadIcons() {
    icons = make(map[string]image.Image)
    icons["spades.png"] = loadIcon("spades.png")
    icons["hearts.png"] = loadIcon("hearts.png")
    icons["diamonds.png"] = loadIcon("diamonds.png")
    icons["clubs.png"] = loadIcon("clubs.png")
}
```

因此，发现 `icons` 非 nil 的 `goroutine` 不能假设该变量的初始化已完成。

确保所有 `goroutine` 都能观察到 `loadIcons` 的效果，最简单正确的方法是使用 `mutex` 进行同步：

[点击此处查看代码图像](#part0139_split_018.html#id269pro03_r)

```
var mu sync.Mutex // 保护 icons
var icons map[string]image.Image

// 并发安全。
func Icon(name string) image.Image {
    mu.Lock()
    defer mu.Unlock()
    if icons == nil {
        loadIcons()
    }
    return icons[name]
}
```

然而，强制对 `icons` 进行互斥访问的代价是，两个 `goroutine` 无法并发访问该变量，即使该变量已被安全初始化且永远不会再被修改。这提示我们使用 `multiple-readers lock`（多读者锁，即读写锁）：

[点击此处查看代码图像](#part0139_split_019.html#id270pro01_r)

```
var mu sync.RWMutex // 保护 icons
var icons map[string]image.Image

// 并发安全。
func Icon(name string) image.Image {
    mu.RLock()
    if icons != nil {
        icon := icons[name]
        mu.RUnlock()
        return icon
    }
    mu.RUnlock()

    // 获取排他锁
    mu.Lock()
    if icons == nil { // 注意：必须再次检查 nil
        loadIcons()
    }
    icon := icons[name]
    mu.Unlock()
    return icon
}
```

现在有两个临界区。`goroutine` 首先获取 `reader lock`（读锁），查询 map，然后释放锁。如果找到了条目（常见情况），则直接返回。如果未找到条目，`goroutine` 则获取 `writer lock`（写锁）。在不先释放 `shared lock`（共享锁）的情况下，无法将其升级为 `exclusive`（排他锁），因此我们必须重新检查 `icons` 变量，以防另一个 `goroutine` 在此期间已经将其初始化。

上述模式虽然提供了更大的并发性，但比较复杂，因此容易出错。幸运的是，`sync` 包为一次性初始化问题提供了专门的解决方案：`sync.Once`。从概念上讲，`Once` 由一个 `mutex` 和一个记录初始化是否已发生的 `boolean` 变量组成；`mutex` 同时保护 `boolean` 和客户端的数据结构。其唯一的方法 `Do` 接受初始化函数作为参数。让我们用 `Once` 来简化 `Icon` 函数：

[点击此处查看代码图像](#part0139_split_020.html#id271pro01_r)

```
var loadIconsOnce sync.Once
var icons map[string]image.Image

// 并发安全。
func Icon(name string) image.Image {
    loadIconsOnce.Do(loadIcons)
    return icons[name]
}
```

每次调用 `Do(loadIcons)` 都会锁定 `mutex` 并检查 `boolean` 变量。在第一次调用中，该变量为 false，`Do` 会调用 `loadIcons` 并将变量设为 true。后续调用什么也不做，但 `mutex` 的同步机制确保了 `loadIcons` 对内存（具体来说是 `icons`）的影响对所有 `goroutine` 可见。通过这种方式使用 `sync.Once`，我们可以避免与其他 `goroutine` 共享变量，直到它们被正确构建完成。

### 练习 9.2

重写 [2.6.2 节](#part0026.html#id-packageinitialization) 中的 `PopCount` 示例，使其在首次需要时使用 `sync.Once` 初始化查找表。（实际上，对于像 `PopCount` 这样又小又高度优化的函数，同步的成本是难以承受的。）

## 9.6 竞态检测器

即使极其小心，也很容易犯并发错误。幸运的是，`Go` 运行时和工具链配备了一个复杂且易于使用的动态分析工具——`race detector`（竞态检测器）。

只需在 `go build`、`go run` 或 `go test` 命令中添加 `-race` 标志。这会导致编译器构建应用程序或测试的修改版本，并添加额外的检测代码，有效地记录执行期间发生的所有共享变量访问，以及读或写该变量的 `goroutine` 的身份。此外，修改后的程序还会记录所有同步事件，例如 `go` 语句、`channel` 操作，以及对 `(*sync.Mutex).Lock`、`(*sync.WaitGroup).Wait` 等的调用。（完整的同步事件集由随语言规范附带的 `The Go Memory Model` 文档指定。）

竞态检测器研究这一事件流，寻找这样的情况：一个 `goroutine` 读或写一个共享变量，而该变量最近曾被另一个 `goroutine` 写入，且两者之间没有插入同步操作。这表明对共享变量存在并发访问，即 `data race`（数据竞争）。该工具会打印一份报告，包含变量的身份，以及读取 `goroutine` 和写入 `goroutine` 中活跃函数调用的堆栈。这通常足以定位问题。[9.7 节](#part0094.html#id-cache) 包含一个竞态检测器实际运行的示例。

竞态检测器会报告实际执行过的所有 `data races`。然而，它只能检测运行过程中发生的 `race conditions`（竞态条件）；它无法证明将来永远不会发生。为获得最佳效果，请确保您的测试在并发场景下覆盖您的包。

由于额外的记账工作，启用 `race detection`（竞态检测）构建的程序运行需要更多时间和内存，但这种开销即使对于许多生产任务也是可以容忍的。对于难以复现的 `race conditions`，让 `race detector` 发挥作用可以节省数小时甚至数天的调试时间。

## 9.7 示例：并发非阻塞缓存

在本节中，我们将构建一个 `concurrent non-blocking cache`（并发非阻塞缓存），这是一种抽象，解决了实际并发程序中常见但现有库未能很好解决的问题。这个问题是对函数进行 `memoizing`（备忘/记忆化），即缓存函数的结果，使其只需计算一次。我们的解决方案将是 `concurrency-safe`（并发安全）的，并将避免基于单一全局锁的缓存设计所带来的竞争。

我们将使用下面的 `httpGetBody` 函数作为我们可能想要备忘的函数类型的示例。它发起一个 `HTTP GET` 请求并读取响应体。调用此函数的开销相对较大，因此我们希望避免不必要的重复调用。

[点击此处查看代码图像](#part0139_split_021.html#id272pro01_r)

```
func httpGetBody(url string) (interface{}, error) {
    resp, err := http.Get(url)
    if err != nil {
        return nil, err
    }
    defer resp.Body.Close()
    return ioutil.ReadAll(resp.Body)
}
```

最后一行隐藏了一个细微的细节。`ReadAll` 返回两个结果，一个 `[]byte` 和一个 `error`，但由于它们可分别赋值给 `httpGetBody` 声明的结果类型——`interface{}` 和 `error`——我们可以直接返回调用结果而无需进一步处理。我们为 `httpGetBody` 选择这种返回类型，是为了使其符合我们的缓存设计所要备忘的函数类型。

这是缓存的第一个草稿：

[点击此处查看代码图像](#part0139_split_022.html#id272pro02_r)

`gopl.io/ch9/memo1`

