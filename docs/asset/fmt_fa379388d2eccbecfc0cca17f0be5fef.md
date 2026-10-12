
现在有两个临界区。goroutine 首先获取读锁，查询 map，然后释放锁。如果找到条目（常见情况），则返回该条目。如果未找到条目，goroutine 获取写锁。无法在不先释放共享锁的情况下将共享锁升级为独占锁，因此我们必须重新检查 `icons` 变量，以防另一个 goroutine 在此期间已将其初始化。

上述模式提供了更大的并发性，但比较复杂且容易出错。幸运的是，`sync` 包为一次性初始化问题提供了专门的解决方案：`sync.Once`。从概念上讲，`Once` 由一个互斥锁和一个记录初始化是否已发生的布尔变量组成；互斥锁保护布尔变量和客户端的数据结构。唯一的方法 `Do` 接受初始化函数作为参数。让我们用 `Once` 来简化 `Icon` 函数：

```go
var loadIconsOnce sync.Once

var icons map[string]image.Image

// Concurrency-safe.

func Icon(name string) image.Image {

    loadIconsOnce.Do(loadIcons)

    return icons[name]

}
```

每次调用 `Do(loadIcons)` 都会锁定互斥锁并检查布尔变量。在第一次调用中，变量为 false，`Do` 调用 `loadIcons` 并将变量设为 true。后续调用不执行任何操作，但互斥锁同步确保了 `loadIcons` 对内存（具体指 `icons`）的影响对所有 goroutine 可见。以这种方式使用 `sync.Once`，我们可以避免与其他 goroutine 共享变量，直到它们被正确构建。

**练习 9.2：** 重写 第 2.6.2 节 中的 `PopCount` 示例，使其在首次需要时使用 `sync.Once` 初始化查找表。（实际上，对于像 `PopCount` 这样小且高度优化的函数，同步的成本过高。）

## 9.6 竞争检测器

即使极其小心，也很容易犯并发错误。幸运的是，Go 运行时和工具链配备了一个复杂且易于使用的动态分析工具——*竞争检测器*。

只需在 `go build`、`go run` 或 `go test` 命令中添加 `-race` 标志。这会导致编译器构建应用程序或测试的修改版本，并添加额外的检测代码，有效记录执行期间发生的所有共享变量访问，以及读取或写入该变量的 goroutine 的标识。此外，修改后的程序还会记录所有同步事件，例如 `go` 语句、通道操作，以及对 `(*sync.Mutex).Lock`、`(*sync.WaitGroup).Wait` 等的调用。（完整的同步事件集由随语言规范附带的 *The Go Memory Model* 文档指定。）

竞争检测器研究这一事件流，寻找一种情况：一个 goroutine 读取或写入一个共享变量，而该变量最近一次是由另一个 goroutine 写入的，且两者之间没有插入同步操作。这表明对共享变量的并发访问，即数据竞争。该工具打印的报告包含变量的标识，以及读取 goroutine 和写入 goroutine 中活跃函数调用的堆栈。这通常足以定位问题。第 9.7 节 包含竞争检测器实际运行的示例。

竞争检测器报告实际执行的所有数据竞争。然而，它只能检测运行期间发生的竞争条件；无法证明竞争永远不会发生。为获得最佳效果，请确保测试使用并发来测试包。

由于额外的记账工作，启用竞争检测构建的程序运行需要更多时间和内存，但开销即使对许多生产任务也是可接受的。对于不常发生的竞争条件，让竞争检测器发挥作用可以节省数小时甚至数天的调试时间。

## 9.7 示例：并发非阻塞缓存

在本节中，我们将构建一个*并发非阻塞缓存*，这是一种解决实际并发程序中常见问题的抽象，而现有库无法很好地解决该问题。这是*备忘*函数的问题，即缓存函数结果，使其只需计算一次。我们的解决方案将是并发安全的，并避免基于单个锁保护整个缓存的设计所带来的争用。

我们将使用下面的 `httpGetBody` 函数作为我们可能想要备忘的函数类型的示例。它发起 HTTP GET 请求并读取响应体。调用此函数的开销相对较大，因此我们希望避免不必要的重复调用。

```go
func httpGetBody(url string) (interface{}, error) {

    resp, err := http.Get(url)

    if err != nil {

        return nil, err

    }

    defer resp.Body.Close()

    return ioutil.ReadAll(resp.Body)

}
```

最后一行隐藏了一个细微差别。`ReadAll` 返回两个结果，一个 `[]byte` 和一个 `error`，但由于它们可分别赋值给 `httpGetBody` 声明的返回类型——`interface{}` 和 `error`——我们可以直接返回调用结果而无需进一步处理。我们为 `httpGetBody` 选择此返回类型，使其符合缓存设计用于备忘的函数类型。

这是缓存的第一个草稿：

```go
// Package memo 提供了一个非并发安全的
// Func 类型函数的备忘录模式实现。
package memo

// Memo 缓存调用 Func 的结果。
type Memo struct {
    f     Func
    cache map[string]result
}

// Func 是要备忘的函数类型。
type Func func(key string) (interface{}, error)

type result struct {
    value interface{}
    err   error
}

func New(f Func) *Memo {
    return &Memo{f: f, cache: make(map[string]result)}
}

// 注意：非并发安全！
func (memo *Memo) Get(key string) (interface{}, error) {
    res, ok := memo.cache[key]
    if !ok {
        res.value, res.err = memo.f(key)
        memo.cache[key] = res
    }
    return res.value, res.err
}
```

`Memo` 实例持有要备忘的函数 `f`（类型为 `Func`）和缓存，缓存是一个从字符串到 `result` 的映射。每个 `result` 仅仅是调用 `f` 返回的那对结果——一个值和一个错误。随着设计的演进，我们将展示 `Memo` 的几种变体，但它们都将共享这些基本特征。

下面展示了一个如何使用 `Memo` 的示例。对于传入 URL 流中的每个元素，我们调用 `Get`，记录调用的延迟和返回的数据量：

```go
m := memo.New(httpGetBody)

for url := range incomingURLs() {

    start := time.Now()

    value, err := m.Get(url)

    if err != nil {

        log.Print(err)

    }

    fmt.Printf("%s, %s, %d bytes\n",

        url, time.Since(start), len(value.([]byte)))

}
```

我们可以使用 `testing` 包（主题见 第 11 章）系统地研究备忘录模式的效果。从下面的测试输出中，我们可以看到 URL 流包含重复项，并且虽然每个 URL 的第一次 `(*Memo).Get` 调用需要数百毫秒，但第二次请求在不到一毫秒的时间内返回了相同数量的数据。

```
$ go test -v gopl.io/ch9/memo1

=== RUN   Test

https://golang.org, 175.026418ms, 7537 bytes

https://godoc.org, 172.686825ms, 6878 bytes

https://play.golang.org, 115.762377ms, 5767 bytes

http://gopl.io, 749.887242ms, 2856 bytes

https://golang.org, 721ns, 7537 bytes

https://godoc.org, 152ns, 6878 bytes

https://play.golang.org, 205ns, 5767 bytes

http://gopl.io, 326ns, 2856 bytes

--- PASS: Test (1.21s)

PASS

ok  gopl.io/ch9/memo1   1.257s
```

此测试按顺序执行所有对 `Get` 的调用。

由于 HTTP 请求是并行化的绝佳机会，让我们修改测试，使其并发发起所有请求。测试使用 `sync.WaitGroup` 等待直到最后一个请求完成才返回。

```go
m := memo.New(httpGetBody)

var n sync.WaitGroup

for url := range incomingURLs() {

    n.Add(1)

    go func(url string) {

        start := time.Now()

        value, err := m.Get(url)

        if err != nil {

            log.Print(err)

        }

        fmt.Printf("%s, %s, %d bytes\n",

            url, time.Since(start), len(value.([]byte)))

        n.Done()

    }(url)

}

n.Wait()
```

测试运行得快多了，但遗憾的是它不太可能始终正确工作。我们可能会注意到意外的缓存未命中、返回错误值的缓存命中，甚至崩溃。

更糟的是，它很可能*有时*能正确工作，所以我们甚至可能注意不到它有问题。但如果我们使用 `-race` 标志运行它，竞态检测器（§9.6）通常会打印如下报告：

```
$ go test -run=TestConcurrent -race -v gopl.io/ch9/memo1

=== RUN   TestConcurrent

...

WARNING: DATA RACE

Write by goroutine 36:

  runtime.mapassign1()

      ~/go/src/runtime/hashmap.go:411 +0x0

  gopl.io/ch9/memo1.(*Memo).Get()

      ~/gobook2/src/gopl.io/ch9/memo1/memo.go:32 +0x205

  ...

Previous write by goroutine 35:

  runtime.mapassign1()

      ~/go/src/runtime/hashmap.go:411 +0x0

  gopl.io/ch9/memo1.(*Memo).Get()

      ~/gobook2/src/gopl.io/ch9/memo1/memo.go:32 +0x205

...

Found 1 data race(s)

FAIL    gopl.io/ch9/memo1   2.393s
```

对 `memo.go:32` 的引用告诉我们，两个 goroutine 在没有任何中间同步的情况下更新了 `cache` map。`Get` 不是并发安全的：它存在数据竞争。

```go
28  func (memo *Memo) Get(key string) (interface{}, error) {

29      res, ok := memo.cache[key]

30      if !ok {

31          res.value, res.err = memo.f(key)

32          memo.cache[key] = res

33      }

34      return res.value, res.err

35  }
```

使缓存并发安全的最简单方法是使用基于监视器的同步。我们只需向 `Memo` 添加一个互斥锁，在 `Get` 开头获取锁，在 `Get` 返回前释放它，这样两个 `cache` 操作就发生在临界区内：

```go
// gopl.io/ch9/memo2

type Memo struct {

    f     Func

    mu    sync.Mutex // 保护 cache

    cache map[string]result

}

// Get 是并发安全的。

func (memo *Memo) Get(key string) (value interface{}, err error) {

    memo.mu.Lock()

    res, ok := memo.cache[key]

    if !ok {

        res.value, res.err = memo.f(key)

        memo.cache[key] = res

    }

    memo.mu.Unlock()

    return res.value, res.err

}
```

现在即使并发运行测试，竞态检测器也保持静默。遗憾的是，对 `Memo` 的这一更改抵消了我们之前的性能提升。由于在调用 `f` 期间持有锁，`Get` 将我们打算并行化的所有 I/O 操作串行化了。我们需要的是一个*非阻塞*缓存，即一个不会串行化对其备忘函数调用的缓存。

在下面的 `Get` 的下一个实现中，调用 goroutine 获取锁两次：一次用于查找，如果查找未返回结果，则第二次用于更新。在此期间，其他 goroutine 可以自由使用缓存。

```go
// gopl.io/ch9/memo3

func (memo *Memo) Get(key string) (value interface{}, err error) {

    memo.mu.Lock()

    res, ok := memo.cache[key]

    memo.mu.Unlock()

    if !ok {

        res.value, res.err = memo.f(key)

        // 在两个临界区之间，多个 goroutine

        // 可能会竞争计算 f(key) 并更新 map。

        memo.mu.Lock()

        memo.cache[key] = res

        memo.mu.Unlock()

    }

    return res.value, res.err

}
```

性能再次提升，但现在我们注意到某些 URL 被获取了两次。当两个或多个 goroutine 大约在同一时间为同一个 URL 调用 `Get` 时，就会发生这种情况。两者都查询缓存，发现那里没有值，然后都调用缓慢的函数 `f`。然后它们都用获得的结果更新 map。其中一个结果会被另一个覆盖。

理想情况下，我们希望避免这种冗余工作。此功能有时称为*重复抑制*。在下面的 `Memo` 版本中，每个 map 元素是一个指向 `entry` 结构体的指针。每个 `entry` 包含对函数 `f` 调用的备忘结果，如前所述，但它额外包含一个名为 `ready` 的通道。就在 `entry` 的 `result` 被设置后，该通道将被关闭，以*广播*（§8.9）给任何其他 goroutine，表明现在它们可以安全地从 `entry` 读取结果了。

```go
// gopl.io/ch9/memo4

type entry struct {

    res   result

    ready chan struct{} // closed when res is ready

}

func New(f Func) *Memo {

    return &Memo{f: f, cache: make(map[string]*entry)}

}

type Memo struct {

    f     Func

    mu    sync.Mutex // guards cache

    cache map[string]*entry

}

func (memo *Memo) Get(key string) (value interface{}, err error) {

    memo.mu.Lock()

    e := memo.cache[key]

    if e == nil {

        // This is the first request for this key.

        // This goroutine becomes responsible for computing

        // the value and broadcasting the ready condition.

        e = &entry{ready: make(chan struct{})}

        memo.cache[key] = e

        memo.mu.Unlock()

        e.res.value, e.res.err = memo.f(key)
```
