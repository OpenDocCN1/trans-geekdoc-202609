
然而，它完成任务仍然耗时太长。没有理由阻止对 `walkDir` 的所有调用并发执行，从而利用磁盘系统的并行性。下面是 `du` 的第三个版本，它为每次 `walkDir` 调用创建一个新的 goroutine。它使用 `sync.WaitGroup`（[§8.5](#ebook_split_080.html#id-loopinginparallel)）来统计仍在活动的 `walkDir` 调用次数，并使用一个额外的 goroutine 在计数器降为零时关闭 `fileSizes` 通道。

[点击此处查看代码图像](#ch08_images.html#id250pro01_r)

gopl.io/ch8/du3

```
func main() {
    // ...确定根目录...

    // 并行遍历文件树的每个根目录。
    fileSizes := make(chan int64)
    var n sync.WaitGroup
    for _, root := range roots {
        n.Add(1)
        go walkDir(root, &n, fileSizes)
    }
    go func() {
        n.Wait()
        close(fileSizes)
    }()
    // ...select 循环...
}
```

[点击此处查看代码图像](#ch08_images.html#id250pro02_r)

```
func walkDir(dir string, n *sync.WaitGroup, fileSizes chan<- int64) {
    defer n.Done()
    for _, entry := range dirents(dir) {
        if entry.IsDir() {
            n.Add(1)
            subdir := filepath.Join(dir, entry.Name())
            go walkDir(subdir, n, fileSizes)
        } else {
            fileSizes <- entry.Size()
        }
    }
}
```

由于该程序在峰值时会创建成千上万个 goroutine，我们必须修改 `dirents` 以使用计数信号量，防止其一次性打开太多文件，就像我们在 [8.6 节](#ebook_split_081.html#id-exampleconcurrentwebcrawler) 中为网络爬虫所做的那样：

[点击此处查看代码图像](#ch08_images.html#id250pro02_01_r)

```
// sema 是一个计数信号量，用于限制 dirents 中的并发性。
var sema = make(chan struct{}, 20)

// dirents 返回目录 dir 的条目。
func dirents(dir string) []os.FileInfo {
    sema <- struct{}{}        // 获取令牌
    defer func() { <-sema }() // 释放令牌
    // ...
```

此版本比前一个版本快几倍，尽管不同系统之间的差异很大。

**练习 8.9：** 编写一个 `du` 版本，计算并定期显示每个 `root` 目录的单独总计。

## 8.9 取消

有时我们需要指示一个 goroutine 停止它正在做的事情，例如，在 Web 服务器代表已断开连接的客户端执行计算时。

没有任何方法让一个 goroutine 直接终止另一个 goroutine，因为那样会留下所有共享变量处于未定义状态。在火箭发射程序（[§8.7](#ebook_split_082.html#id-multiplexingwithselect)）中，我们向一个名为 `abort` 的通道发送了单个值，倒计时 goroutine 将其解释为请求自行停止。但如果我们需要取消两个 goroutine，或者任意数量的 goroutine 怎么办？

一种可能性是在 `abort` 通道上发送与要取消的 goroutine 数量相同的事件。然而，如果其中一些 goroutine 已经自行终止，我们的计数就会过大，导致发送操作卡住。另一方面，如果这些 goroutine 又衍生出了其他 goroutine，我们的计数就会过小，导致某些 goroutine 无法感知到取消。一般来说，很难知道在任何给定时刻有多少个 goroutine 在为我们工作。此外，当一个 goroutine 从 `abort` 通道接收值时，它会消费该值，导致其他 goroutine 无法看到它。对于取消操作，我们需要一种可靠的机制，通过通道*广播*事件，以便许多 goroutine 能在事件发生时*看到*它，并且事后也能知道它*已经*发生。

回想一下，通道关闭且已发送的值被接收完毕后，后续的接收操作会立即进行，产生零值。我们可以利用这一点创建一个广播机制：不要在通道上发送值，*关闭*它。

我们可以通过几个简单的更改为上一节的 `du` 程序添加取消功能。首先，我们创建一个取消通道，该通道永远不发送值，但其关闭表示程序该停止工作了。我们还定义了一个工具函数 `cancelled`，它在被调用的瞬间检查或*轮询*取消状态。

[点击此处查看代码图像](#ch08_images.html#id251pro01_r)

gopl.io/ch8/du4

```
var done = make(chan struct{})

func cancelled() bool {
    select {
    case <-done:
        return true
    default:
        return false
    }
}
```

接下来，我们创建一个从标准输入读取的 goroutine，标准输入通常连接到终端。一旦读取到任何输入（例如，用户按下回车键），该 goroutine 通过关闭 `done` 通道来广播取消信号。

[点击此处查看代码图像](#ch08_images.html#id252pro01_r)

```
// 当检测到输入时取消遍历。
go func() {
    os.Stdin.Read(make([]byte, 1)) // 读取单个字节
    close(done)
}()
```

现在我们需要让 goroutine 对取消做出响应。在主 goroutine 中，我们向 select 语句添加第三个 case，尝试从 `done` 通道接收。如果选中此 case，函数会返回，但在返回之前，它必须先耗尽 `fileSizes` 通道，丢弃所有值，直到通道关闭。这样做是为了确保任何活跃的 `walkDir` 调用能够运行完成，而不会因向 `fileSizes` 发送值而卡住。

[点击此处查看代码图像](#ch08_images.html#id252pro02_r)

```
for {
    select {
    case <-done:
        // 耗尽 fileSizes 以允许现有 goroutine 完成。
        for range fileSizes {
            // 什么都不做。
        }
        return
    case size, ok := <-fileSizes:
        // ...
    }
}
```

`walkDir` goroutine 在开始时轮询取消状态，如果状态已设置则直接返回而不做任何事情。这使得取消事件后创建的所有 goroutine 变为空操作：

[点击此处查看代码图像](#ch08_images.html#id252pro03_r)

```
func walkDir(dir string, n *sync.WaitGroup, fileSizes chan<- int64) {
    defer n.Done()
    if cancelled() {
        return
    }
    for _, entry := range dirents(dir) {
        // ...
    }
}
```

在 `walkDir` 的循环内再次轮询取消状态可能会有益处，以避免在取消事件后创建 goroutine。取消涉及权衡；更快的响应通常需要对程序逻辑进行更侵入式的更改。确保取消事件后不再发生任何昂贵操作可能需要更新代码中的许多位置，但通常只需在几个关键位置检查取消即可获得大部分收益。

对该程序进行少量性能分析显示，瓶颈在于 `dirents` 中获取信号量令牌。下面的 `select` 使该操作可取消，并将程序的典型取消延迟从数百毫秒降低到几十毫秒：

[点击此处查看代码图像](#ch08_images.html#id253pro01_r)

```
func dirents(dir string) []os.FileInfo {
    select {
    case sema <- struct{}{}: // 获取令牌
    case <-done:
        return nil // 已取消
    }
    defer func() { <-sema }() // 释放令牌

    // ...读取目录...
}
```
