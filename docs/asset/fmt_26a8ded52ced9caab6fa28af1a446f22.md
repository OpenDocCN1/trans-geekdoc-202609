
`seen` 映射被限制在主 goroutine 内部；也就是说，它只能被该 goroutine 访问。与其他形式的信息隐藏一样，限制有助于我们推断程序的正确性。例如，局部变量不能在声明它们的函数外部通过名称提及；不会逃逸的变量不能从函数外部访问；对象的封装字段只能通过该对象的方法访问。在所有情况下，信息隐藏都有助于限制程序各部分之间的意外交互。

`crawl` 发现的链接通过一个专用的 goroutine 发送到 `worklist`，以避免死锁。

为节省篇幅，本示例未解决终止问题。

### 练习 8.6
为并发爬虫添加深度限制。即，如果用户设置 `-depth=3`，则仅获取最多通过三个链接可达的 URL。

### 练习 8.7
编写一个并发程序，创建一个网站的本地镜像，获取每个可达页面并将其写入本地磁盘上的目录。只应获取原始域名内的页面（例如 `golang.org`）。镜像页面中的 URL 应按需修改，使其指向镜像页面而非原始页面。

## 8.7 使用 `select` 进行多路复用

下面的程序执行火箭发射倒计时。`time.Tick` 函数返回一个通道，它会定期向该通道发送事件，表现得像节拍器一样。每个事件的值是一个时间戳，但其送达这一事实比时间戳本身更有趣。

点击此处查看代码图像

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

现在让我们增加一个功能：在倒计时期间按回车键可中止发射序列。首先，我们启动一个 goroutine 尝试从标准输入读取单个字节，如果成功，则向名为 `abort` 的通道发送一个值。

点击此处查看代码图像

gopl.io/ch8/countdown2

```go
abort := make(chan struct{})
go func() {
    os.Stdin.Read(make([]byte, 1)) // read a single byte
    abort <- struct{}{}
}()
```

现在，倒计时循环的每次迭代都需要等待两个通道之一的事件到达：如果一切正常（“nominal”，NASA 行话），则是定时器通道；如果出现“异常”，则是中止事件。我们不能直接从每个通道接收，因为我们先尝试的那种操作会阻塞直到完成。我们需要多路复用这些操作，为此我们需要 `select` 语句。

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

上图展示了 `select` 语句的一般形式。像 `switch` 语句一样，它包含若干 `case` 和一个可选的 `default`。每个 `case` 指定一个通信（对某个通道的发送或接收操作）和一个关联的语句块。接收表达式可以单独出现，如第一个 `case` 所示，也可以出现在短变量声明中，如第二个 `case` 所示；第二种形式允许你引用接收到的值。

`select` 会等待，直到某个 `case` 的通信操作可以进行。然后它执行该通信操作并运行该 `case` 关联的语句；其他的通信操作不会发生。没有 `case` 的 `select`，即 `select{}`，会永远等待。

让我们回到火箭发射程序。`time.After` 函数会立即返回一个通道，并启动一个新的 goroutine，在指定时间后向该通道发送单个值。下面的 `select` 语句等待两个事件中最先到达的一个：要么是中止事件，要么是表示 10 秒已过的事件。如果 10 秒内没有中止，则继续发射。

点击此处查看代码图像

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

下面的例子更微妙。通道 `ch` 的缓冲区大小为 1，它交替处于空和满状态，因此一次只能有一个 `case` 执行：要么是 `i` 为偶数时的发送，要么是 `i` 为奇数时的接收。它总是打印 `0 2 4 6 8`。

点击此处查看代码图像

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

如果多个 `case` 都准备好，`select` 会随机选择一个，这确保了每个通道都有平等的被选中机会。增加前一个例子中通道的缓冲区大小会使其输出变得非确定性，因为当缓冲区既不满也不空时，`select` 语句就像抛硬币一样随机选择。

让我们让启动程序打印倒计时。下面的 `select` 语句使循环的每次迭代最多等待 1 秒以接收中止信号，但不会更久。

点击此处查看代码图像

gopl.io/ch8/countdown3

```go
func main() {
    // ...创建 abort 通道...

    fmt.Println("Commencing countdown.  Press return to abort.")
    tick := time.Tick(1 * time.Second)
    for countdown := 10; countdown > 0; countdown-- {
        fmt.Println(countdown)
        select {
        case <-tick:
            // 什么都不做。
        case <-abort:
            fmt.Println("Launch aborted!")
            return
        }
    }
    launch()
}
```

`time.Tick` 函数的行为就像它创建了一个 goroutine，在循环中调用 `time.Sleep`，每次唤醒时发送一个事件。当上述倒计时函数返回时，它停止从 `tick` 接收事件，但计时器 goroutine 依然存在，徒劳地尝试向一个没有 goroutine 接收的通道发送数据——这就是 goroutine 泄漏（§8.4.4）。

`Tick` 函数很方便，但仅适用于在应用程序的整个生命周期中都需要定时触发的场景。否则，我们应该使用这种模式：

点击此处查看代码图像

```go
ticker := time.NewTicker(1 * time.Second)

<-ticker.C // 从计时器的通道接收

ticker.Stop() // 导致计时器的 goroutine 终止
```

有时我们想尝试在通道上发送或接收，但如果通道未就绪则避免阻塞——即非阻塞通信。`select` 语句也能做到这一点。`select` 可以包含一个 `default` 分支，指定当其他通信都无法立即进行时该做什么。

下面的 `select` 语句如果能从 `abort` 通道接收到值则接收；否则什么都不做。这是一个非阻塞接收操作；反复执行它被称为轮询通道。

点击此处查看代码图像

```go
select {
case <-abort:
    fmt.Printf("Launch aborted!\n")
    return
default:
    // 什么都不做
}
```

通道的零值是 `nil`。也许令人惊讶的是，nil 通道有时很有用。因为在 nil 通道上的发送和接收操作会永远阻塞，`select` 语句中通道为 nil 的 case 永远不会被选中。这让我们可以用 `nil` 来启用或禁用对应处理超时、取消、响应其他输入事件或发送输出等功能的 case。我们将在下一节看到一个例子。

### 练习 8.8
使用 `select` 语句，为 8.3 节 中的 echo 服务器添加超时功能，使其断开 10 秒内没有任何喊话（发送数据）的客户端连接。

## 8.8 示例：并发目录遍历

在本节中，我们将构建一个程序，报告命令行指定的一个或多个目录的磁盘使用情况，类似于 Unix 的 `du` 命令。其大部分工作由下面的 `walkDir` 函数完成，该函数使用 `dirents` 辅助函数枚举目录 `dir` 的条目。

点击此处查看代码图像

gopl.io/ch8/du1

```go
// walkDir 递归遍历以 dir 为根的文件树
// 并将找到的每个文件的大小发送到 fileSizes 通道。
func walkDir(dir string, fileSizes chan<- int64) {
    for _, entry := range dirents(dir) {
        if entry.IsDir() {
            subdir := filepath.Join(dir, entry.Name())
            walkDir(subdir, fileSizes)
        } else {
            fileSizes <- entry.Size()
        }
    }
}

// dirents 返回目录 dir 的条目。
func dirents(dir string) []os.FileInfo {
    entries, err := ioutil.ReadDir(dir)
    if err != nil {
        fmt.Fprintf(os.Stderr, "du1: %v\n", err)
        return nil
    }
    return entries
}
```

`ioutil.ReadDir` 函数返回一个 `os.FileInfo` 切片——这与对单个文件调用 `os.Stat` 返回的信息相同。对于每个子目录，`walkDir` 递归调用自身；对于每个文件，`walkDir` 向 `fileSizes` 通道发送一条消息。该消息是文件的大小（以字节为单位）。

下面展示的 main 函数使用了两个 goroutine。后台 goroutine 为命令行指定的每个目录调用 `walkDir`，最后关闭 `fileSizes` 通道。主 goroutine 计算从通道接收到的文件大小之和，最后打印总计。

点击此处查看代码图像

```go
// du1 命令计算目录中文件的磁盘使用量。

package main

import (
    "flag"
    "fmt"
    "io/ioutil"
    "os"
    "path/filepath"
)

func main() {
    // 确定初始目录。
    flag.Parse()
    roots := flag.Args()
    if len(roots) == 0 {
        roots = []string{"."}
    }

    // 遍历文件树。
    fileSizes := make(chan int64)
    go func() {
        for _, root := range roots {
            walkDir(root, fileSizes)
        }
        close(fileSizes)
    }()

    // 打印结果。
    var nfiles, nbytes int64
    for size := range fileSizes {
        nfiles++
        nbytes += size
    }
    printDiskUsage(nfiles, nbytes)
}

func printDiskUsage(nfiles, nbytes int64) {
    fmt.Printf("%d files  %.1f GB\n", nfiles, float64(nbytes)/1e9)
}
```

该程序在打印结果前会暂停很长一段时间：

```
$ go build gopl.io/ch8/du1
$ ./du1 $HOME /usr /bin /etc
213201 files  62.7 GB
```

如果程序能让我们了解进度，体验会更好。然而，仅将 `printDiskUsage` 调用移入循环会导致打印成千上万行输出。

下面的 `du` 变体会定期打印总计，但仅在指定了 `-v` 标志时才打印，因为并非所有用户都想看进度消息。循环遍历 `roots` 的后台 goroutine 保持不变。主 goroutine 现在使用一个计时器每 500ms 生成一次事件，并用一个 `select` 语句等待文件大小消息（此时更新总计）或计时事件（此时打印当前总计）。如果未指定 `-v` 标志，`tick` 通道保持为 nil，`select` 中对应的 case 实际上被禁用了。

点击此处查看代码图像

gopl.io/ch8/du2

```go
var verbose = flag.Bool("v", false, "show verbose progress messages")

func main() {
    // ...启动后台 goroutine...

    // 定期打印结果。
    var tick <-chan time.Time
    if *verbose {
        tick = time.Tick(500 * time.Millisecond)
    }

    var nfiles, nbytes int64
loop:
    for {
        select {
        case size, ok := <-fileSizes:
            if !ok {
                break loop // fileSizes 已关闭
            }
            nfiles++
            nbytes += size
        case <-tick:
            printDiskUsage(nfiles, nbytes)
        }
    }
    printDiskUsage(nfiles, nbytes) // 最终总计
}
```

既然程序不再使用 `range` 循环，第一个 `select` case 必须显式检查 `fileSizes` 通道是否已关闭，使用双返回值形式的接收操作。如果通道已关闭，程序跳出循环。带标签的 `break` 语句同时跳出 `select` 和 `for` 循环；不带标签的 `break` 只会跳出 `select`，导致循环开始下一次迭代。

该程序现在会给我们提供悠闲的更新流：

```
$ go build gopl.io/ch8/du2
$ ./du2 -v $HOME /usr /bin /etc
28608 files  8.3 GB
54147 files  10.3 GB
93591 files  15.1 GB
127169 files  52.9 GB
175931 files  62.2 GB
213201 files  62.7 GB
```

然而，它完成任务仍然耗时太长。没有理由阻止对 `walkDir` 的所有调用并发执行，从而利用磁盘系统的并行性。下面是 `du` 的第三个版本，它为每次 `walkDir` 调用创建一个新的 goroutine。它使用 `sync.WaitGroup`（§8.5）来统计仍在活动的 `walkDir` 调用次数，并使用一个额外的 goroutine 在计数器降为零时关闭 `fileSizes` 通道。

点击此处查看代码图像

gopl.io/ch8/du3

```go
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

点击此处查看代码图像

```go
func walkDir(dir string, n *sync.WaitGroup, fileSizes chan<- int64) {
    defer n.Done()
    for _, entry := range dirents(dir) {
        if entry.IsDir() {
            n.Add(1)
            subdir := filepath.Join(dir, entry.Name())
```
