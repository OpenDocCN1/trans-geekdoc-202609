
# 8.6 示例：并发网络爬虫

在[第 5.6 节](#part0048.html#id-anonymousfunctions)中，我们制作了一个简单的网络爬虫，按广度优先顺序探索 Web 的链接图。在本节中，我们将使其并发化，以便对 `crawl` 的独立调用能利用 Web 中可用的 I/O 并行性。`crawl` 函数保持不变，仍如 `gopl.io/ch5/findlinks3` 中所示：

[点击此处查看代码图像](#part0138_split_030.html#id240pro01_r)

gopl.io/ch8/crawl1

```
func crawl(url string) []string {
    fmt.Println(url)
    list, err := links.Extract(url)
    if err != nil {
        log.Print(err)
    }
    return list
}
```

主函数类似于 `breadthFirst`（[§5.6](#part0048.html#id-anonymousfunctions)）。与之前一样，`worklist` 记录待处理项目的队列，每个项目是一个待爬取的 URL 列表，但这次我们使用通道而非切片来表示队列。每次对 `crawl` 的调用都在各自的 goroutine 中进行，并将发现的链接发送回 `worklist`。

[点击此处查看代码图像](#part0138_split_031.html#id240pro02_r)

```
func main() {
    worklist := make(chan []string)

    // Start with the command-line arguments.
    go func() { worklist <- os.Args[1:] }()

    // Crawl the web concurrently.
    seen := make(map[string]bool)
    for list := range worklist {
        for _, link := range list {
            if !seen[link] {
                seen[link] = true
                go func(link string) {
                    worklist <- crawl(link)
                }(link)
            }
        }
    }
}
```

请注意，`crawl` goroutine 将 `link` 作为显式参数传递，以避免我们在[第 5.6.1 节](#part0048.html#id-funccaveat)首次看到的循环变量捕获问题。另请注意，将命令行参数初始发送到 `worklist` 必须在其自己的 goroutine 中运行，以避免*死锁*——一种僵局，主 goroutine 和爬虫 goroutine 都试图相互发送而双方都不接收。另一种解决方案是使用带缓冲的通道。

爬虫现在高度并发并打印大量 URL，但存在两个问题。第一个问题在运行几秒后表现为日志中的错误消息：

[点击此处查看代码图像](#part0138_split_032.html#id240pro03_r)

```
$ go build gopl.io/ch8/crawl1
$ ./crawl1 http://gopl.io/
http://gopl.io/
https://golang.org/help/

https://golang.org/doc/
https://golang.org/blog/
...
2015/07/15 18:22:12 Get ...: dial tcp: lookup blog.golang.org: no such host
2015/07/15 18:22:12 Get ...: dial tcp 23.21.222.120:443: socket:
                                                        too many open files
...
```

最初的错误消息令人惊讶地报告了一个可靠域名的 DNS 查找失败。随后的错误消息揭示了原因：程序一次性创建了太多网络连接，超过了每个进程的打开文件数限制，导致 `net.Dial` 等操作开始失败。

程序*过度*并行了。无界并行通常不是好主意，因为系统中总存在限制因素，例如计算密集型工作负载的 CPU 核心数、本地磁盘 I/O 的主轴和磁头数、流式下载的网络带宽，或 Web 服务的服务能力。解决方案是将资源的并行使用数量限制在可用并行度水平。在我们的例子中，一种简单方法是确保同时活跃的 `links.Extract` 调用不超过 *n* 个，其中 *n* 远小于文件描述符限制——比如 20。这类似于拥挤夜店的门童只在有客人离开时才允许新客人进入。

我们可以使用容量为 *n* 的带缓冲通道来建模一种称为*计数信号量*的并发原语，从而限制并行度。概念上，通道缓冲区中的每个空槽代表一个令牌，持有者有权继续执行。向通道发送值获取令牌，从通道接收值释放令牌，创建新的空槽。这确保了在没有中间接收的情况下最多只能发生 *n* 次发送。（虽然将缓冲区中的*满*槽视为令牌可能更直观，但使用空槽避免了创建后填充通道缓冲区的需要。）由于通道元素类型不重要，我们将使用大小为零的 `struct{}`。

让我们重写 `crawl` 函数，使对 `links.Extract` 的调用被获取和释放令牌的操作包围，从而确保同时最多只有 20 个对它的调用处于活跃状态。将信号量操作尽可能靠近它们所控制的 I/O 操作是一种良好的实践。

[点击此处查看代码图像](#part0138_split_033.html#id241pro01_r)

gopl.io/ch8/crawl2

```
// tokens is a counting semaphore used to
// enforce a limit of 20 concurrent requests.
var tokens = make(chan struct{}, 20)

func crawl(url string) []string {
    fmt.Println(url)
    tokens <- struct{}{} // acquire a token
    list, err := links.Extract(url)
    <-tokens // release the token

    if err != nil {
        log.Print(err)
    }
    return list
}
```

第二个问题是程序永不终止，即使已发现从初始 URL 可达的所有链接。（当然，除非你仔细选择初始 URL 或实现[练习 8.6](#part0082.html#id-crawldepthlimit) 的深度限制功能，否则不太可能注意到此问题。）为了使程序终止，我们需要在 `worklist` 为空*且*没有活跃的爬虫 goroutine 时跳出主循环。

[点击此处查看代码图像](#part0138_split_034.html#id242pro01_r)

## 练习

**练习 8.4：** 修改 `reverb2` 服务器，为每个连接使用一个 `sync.WaitGroup` 来计算活跃的 `echo` goroutine 数量。当计数降为零时，关闭 TCP 连接的写半部分，如[练习 8.3](#part0080.html#id-ex-tcp1)所述。验证你修改后的 `netcat3` 客户端（来自该练习）在标准输入关闭后，仍等待多个并发 shout 的最终回声。

**练习 8.5：** 选取一个现有的 CPU 密集型顺序程序，例如[第 3.3 节](#part0031.html#id-mandelbrot)的 Mandelbrot 程序或[第 3.2 节](#part0030.html#id-surface)的 3-D 表面计算，使用通道进行通信，并行执行其主循环。在多处理器机器上运行速度提升多少？最优 goroutine 数量是多少？

---

## 图示说明

![makeThumbnails6 中的事件序列。](images/00036.jpeg)

**图 8.5.** `makeThumbnails6` 中的事件序列。

垂直线代表 goroutine。细段表示睡眠，粗段表示活动。对角箭头表示将一个 goroutine 与另一个同步的事件。时间向下流动。请注意主 goroutine 大部分时间在 `range` 循环中睡眠，等待工作器发送值或 closer 关闭通道。

[图 8.5](#part0081.html#id-figures-waitgroup) 展示了 `makeThumbnails6` 函数中的事件序列。垂直线代表 goroutine。细段表示睡眠，粗段表示活动。对角箭头表示将一个 goroutine 与另一个同步的事件。时间向下流动。请注意主 goroutine 大部分时间在 `range` 循环中睡眠，等待工作器发送值或 closer 关闭通道。
