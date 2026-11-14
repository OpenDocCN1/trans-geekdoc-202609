
# 并发爬虫

## 基于计数器的解决方案

```go
func main() {
    worklist := make(chan []string)
    var n int // number of pending sends to worklist

    // Start with the command-line arguments.
    n++
    go func() { worklist <- os.Args[1:] }()

    // Crawl the web concurrently.
    seen := make(map[string]bool)
    for ; n > 0; n-- {
        list := <-worklist
        for _, link := range list {
            if !seen[link] {
                seen[link] = true
                n++
                go func(link string) {
                    worklist <- crawl(link)
                }(link)
            }
        }
    }
}
```

在此版本中，计数器 `n` 跟踪尚未发生的对 `worklist` 的发送次数。每当我们知道某个项目需要发送到 `worklist` 时，我们就增加 `n`：在发送初始命令行参数之前增加一次，并在每次启动爬虫 goroutine 时再次增加。当 `n` 降为零时主循环终止，因为没有更多工作要做。

现在并发爬虫的运行速度比 [第 5.6 节](#part0048.html#id-anonymousfunctions) 中的广度优先爬虫快约 20 倍，没有错误，并且如果完成任务则正确终止。

## 固定 Goroutine 池解决方案

下面的程序展示了解决过度并发问题的另一种方案。此版本使用没有计数信号量的原始 `crawl` 函数，但从 20 个长期运行的爬虫 goroutine 中调用它，从而确保最多有 20 个 HTTP 请求同时处于活动状态。

[点击此处查看代码图像](#part0138_split_035.html#id243pro01_r)

gopl.io/ch8/crawl3

```go
func main() {
    worklist := make(chan []string)  // lists of URLs, may have duplicates
    unseenLinks := make(chan string) // de-duplicated URLs

    // Add command-line arguments to worklist.
    go func() { worklist <- os.Args[1:] }()

    // Create 20 crawler goroutines to fetch each unseen link.
    for i := 0; i < 20; i++ {
        go func() {
            for link := range unseenLinks {
                foundLinks := crawl(link)
                go func() { worklist <- foundLinks }()
            }
        }()
    }

    // The main goroutine de-duplicates worklist items
    // and sends the unseen ones to the crawlers.
    seen := make(map[string]bool)
    for list := range worklist {
        for _, link := range list {
            if !seen[link] {
                seen[link] = true
                unseenLinks <- link
            }
        }
    }
}
```

爬虫 goroutine 都由同一个通道 `unseenLinks` 提供数据。主 goroutine 负责去重它从 `worklist` 接收到的项目，然后将每个未见过的项目通过 `unseenLinks` 通道发送给爬虫 goroutine。

`seen` 映射被*限制*在主 goroutine 内部；也就是说，它只能被该 goroutine 访问。与其他形式的信息隐藏一样，限制有助于我们推断程序的正确性。例如，局部变量不能在声明它们的函数外部通过名称提及；不“逃逸”（[§2.3.4](#part0023.html#id-escaping)）出函数的变量不能从该函数外部访问；对象的封装字段只能通过该对象的方法访问。在所有情况下，信息隐藏都有助于限制程序各部分之间的意外交互。

`crawl` 发现的链接从专用 goroutine 发送到 `worklist` 以避免死锁。

为了节省空间，我们在此示例中未解决终止问题。

### 练习

**练习 8.6：** 为并发爬虫添加深度限制。即，如果用户设置 `-depth=3`，则只获取最多通过三个链接可达的 URL。

**练习 8.7：** 编写一个并发程序，创建一个网站的本地镜像，获取每个可达页面并将其写入本地磁盘上的目录。只应获取原始域名内的页面（例如 `golang.org`）。镜像页面中的 URL 应根据需要进行更改，以便它们指向镜像页面，而不是原始页面。

# 8.7 使用 `select` 进行多路复用

下面的程序为火箭发射进行倒计时。`time.Tick` 函数返回一个通道，它定期向该通道发送事件，充当节拍器。每个事件的值是一个时间戳，但其送达这一事实比时间戳本身更有趣。

[点击此处查看代码图像](#part0138_split_036.html#id244pro01_r)

gopl.io/ch8/countdown1

```go
func main() {
    fmt.Println("Commencing countdown.")
    tick := time.Tick(1 * time.Second)
    for countdown := 10; countdown > 0; countdown-- {
        fmt.Println(countdown)
        <-tick
    }
    launch()
}
```

现在让我们添加在倒计时期间按回车键中止发射序列的功能。首先，我们启动一个 goroutine 尝试从标准输入读取单个字节，如果成功，则在名为 `abort` 的通道上发送一个值。

[点击此处查看代码图像](#part0138_split_037.html#id244pro02_r)

gopl.io/ch8/countdown2

```go
abort := make(chan struct{})
go func() {
    os.Stdin.Read(make([]byte, 1)) // read a single byte
    abort <- struct{}{}
}()
```

现在倒计时循环的每次迭代都需要等待两个通道之一上的事件到达：如果一切正常（NASA 行话中的“nominal”）则是定时器通道，如果有“异常”则是中止事件。我们不能只从每个通道接收，因为我们先尝试的任何操作都会阻塞直到完成。我们需要*多路复用*这些操作，为此我们需要 `select` 语句。

```go
select {
case <-ch1:
    // ...
case x := <-ch2:
    // ...use x...
case ch3 <- y:
    // ...
default:
    // ...
}
```

上面展示了 `select` 语句的一般形式。像 `switch` 语句一样，它有若干 `case` 和一个可选的 `default`。每个 `case` 指定一个*通信*（在某个通道上的发送或接收操作）和一个关联的语句块。接收表达式可以单独出现，如第一个 `case`，也可以在短变量声明中出现，如第二个 `case`；第二种形式允许你引用接收到的值。

`select` 等待直到某个 `case` 的通信可以继续进行。然后它执行该通信并执行该 `case` 关联的语句；其他通信不会发生。没有 `case` 的 `select`，即 `select{}`，会永远等待。

让我们回到火箭发射程序。`time.After` 函数立即返回一个通道，并启动一个新 goroutine 在指定时间后向该通道发送单个值。下面的 `select` 语句等待两个事件中的第一个到达：要么是中止事件，要么是表示 10 秒已过的事件。如果 10 秒内没有中止，则继续发射。

[点击此处查看代码图像](#part0138_split_038.html#id245pro01_r)

```go
func main() {
    // ...create abort channel...

    fmt.Println("Commencing countdown.  Press return to abort.")
    select {
    case <-time.After(10 * time.Second):
        // Do nothing.
    case <-abort:
        fmt.Println("Launch aborted!")
        return
    }
    launch()
}
```

下面的例子更微妙。通道 `ch` 的缓冲区大小为 1，交替为空和满，因此只有一个 `case` 可以继续：`i` 为偶数时发送，`i` 为奇数时接收。它总是打印 `0 2 4 6 8`。

[点击此处查看代码图像](#part0138_split_039.html#id245pro02_r)

```go
ch := make(chan int, 1)
for i := 0; i < 10; i++ {
    select {
    case x := <-ch:
        fmt.Println(x) // "0" "2" "4" "6" "8"
    case ch <- i:
    }
}
```

如果多个 `case` 都准备好，`select` 会随机选择一个，这确保了每个通道都有平等的被选中机会。增加前一个例子的缓冲区大小会使其输出变得非确定性，因为当缓冲区既不满也不空时，`select` 语句形象地说就是抛硬币决定。
