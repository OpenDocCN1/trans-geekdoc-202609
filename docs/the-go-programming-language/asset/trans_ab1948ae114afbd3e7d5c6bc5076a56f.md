
`sizes` 通道将每个文件的大小传回主 goroutine，主 goroutine 使用 `range` 循环接收它们并计算总和。请注意我们是如何创建一个 closer goroutine 的，它会在关闭 `sizes` 通道之前等待 worker 完成。这两个操作——等待和关闭——必须与对 `sizes` 的循环并发执行。考虑一下替代方案：如果等待操作被放在循环之前的主 goroutine 中，它将永远不会结束；如果放在循环之后，它将永远无法到达，因为没有任何东西关闭通道，循环将永远不会终止。

![makeThumbnails6 中的事件序列。](graphics/waitgroup.png)

**图 8.5.** `makeThumbnails6` 中的事件序列。

[图 8.5](#ebook_split_080.html#id-figures-waitgroup) 展示了 `makeThumbnails6` 函数中的事件序列。垂直线代表 goroutine。细线段表示休眠，粗线段表示活动。对角线箭头表示将一个 goroutine 与另一个 goroutine 同步的事件。时间向下流动。请注意主 goroutine 如何将大部分时间花在 `range` 循环的休眠中，等待 worker 发送值或 closer 关闭通道。

**练习 8.4：** 修改 `reverb2` 服务器，使其为每个连接使用一个 `sync.WaitGroup` 来计数活跃的 `echo` goroutine 数量。当计数降为零时，关闭 TCP 连接的写入端，正如 [练习 8.3](#ebook_split_079.html#id-ex-tcp1) 所述。验证你修改后的 `netcat3` 客户端（来自该练习）会等待多个并发 shout 的最终回显，即使在标准输入已关闭之后。

**练习 8.5：** 选取一个现有的 CPU 密集型顺序程序，例如 [3.3 节](#ebook_split_030.html#id-mandelbrot) 的 Mandelbrot 程序或 [3.2 节](#ebook_split_029.html#id-surface) 的 3D 曲面计算程序，并使用通道进行通信将其主循环并行执行。它在多处理器机器上运行得快多少？最优的 goroutine 数量是多少？

## 8.6 示例：并发 Web 爬虫

在 [5.6 节](#ebook_split_047.html#id-anonymousfunctions) 中，我们制作了一个简单的 Web 爬虫，它以广度优先的顺序探索 Web 的链接图。在本节中，我们将使其并发化，以便对 `crawl` 的独立调用可以利用 Web 中可用的 I/O 并行性。`crawl` 函数与 `gopl.io/ch5/findlinks3` 中的完全相同：

[点击此处查看代码图像](#ch08_images.html#id240pro01_r)

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

main 函数类似于 `breadthFirst`（[§5.6](#ebook_split_047.html#id-anonymousfunctions)）。和以前一样，worklist 记录需要处理的项目队列，每个项目是一个待爬取的 URL 列表，但这一次，我们不使用切片来表示队列，而是使用通道。每次对 `crawl` 的调用都在其自己的 goroutine 中进行，并将发现的链接发送回 worklist。

[点击此处查看代码图像](#ch08_images.html#id240pro02_r)

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

请注意，crawl goroutine 将 `link` 作为显式参数传递，以避免我们在 [5.6.1 节](#ebook_split_047.html#id-funccaveat) 中首次看到的循环变量捕获问题。还请注意，将命令行参数初始发送到 worklist 必须在其自己的 goroutine 中运行，以避免*死锁*——一种僵局，在这种僵局中，主 goroutine 和一个 crawler goroutine 都试图相互发送，而双方都不接收。另一种解决方案是使用带缓冲的通道。

爬虫现在高度并发并打印出大量 URL，但它有两个问题。第一个问题在运行几秒钟后表现为日志中的错误消息：

[点击此处查看代码图像](#ch08_images.html#id240pro03_r)

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

最初的错误消息令人惊讶地报告了一个可靠域名的 DNS 查找失败。随后的错误消息揭示了原因：程序一次性创建了如此多的网络连接，以至于超过了每个进程打开文件数量的限制，导致 DNS 查找和 `net.Dial` 调用等操作开始失败。

该程序*过度*并行了。无界并行通常不是一个好主意，因为系统中总存在限制因素，例如计算密集型工作负载的 CPU 核心数、本地磁盘 I/O 操作的磁盘数和磁头数、流式下载的网络带宽，或 Web 服务的服务能力。解决方案是将资源的并行使用数量限制在可用并行度水平以内。在我们的例子中，一种简单的方法是确保对 `links.Extract` 的活跃调用不超过 *n* 个，其中 *n* 远小于文件描述符限制——比如 20。这类似于拥挤夜总会的门卫只有在有客人离开时才允许新客人进入。

我们可以使用容量为 *n* 的带缓冲通道来建模一种称为*计数信号量*的并发原语，从而限制并行度。概念上，通道缓冲区中的每个 *n* 个空槽位代表一个令牌，持有者有权继续执行。向通道发送值可获取一个令牌，从通道接收值可释放一个令牌，从而创建一个新的空槽位。这确保了在没有中间接收操作的情况下，最多只能发生 *n* 次发送。（虽然将通道缓冲区中的*已填充*槽位视为令牌可能更直观，但使用空槽位避免了创建通道后填充缓冲区的需要。）由于通道元素类型并不重要，我们将使用大小为零的 `struct{}`。

让我们重写 `crawl` 函数，使对 `links.Extract` 的调用被获取和释放令牌的操作包围，从而确保一次最多只有 20 个对它的调用处于活跃状态。将信号量操作尽可能靠近它们所控制的 I/O 操作是一种良好的实践。

[点击此处查看代码图像](#ch08_images.html#id241pro01_r)

gopl.io/ch8/crawl2

```
// tokens 是一个计数信号量，用于
// 强制执行最多 20 个并发请求的限制。
var tokens = make(chan struct{}, 20)

func crawl(url string) []string {
    fmt.Println(url)
    tokens <- struct{}{} // 获取一个令牌
    list, err := links.Extract(url)
    <-tokens // 释放令牌

    if err != nil {
        log.Print(err)
    }
    return list
}
```

第二个问题是程序永远不会终止，即使它已经发现了从初始 URL 可达的所有链接。（当然，除非你仔细选择初始 URL 或实现 [练习 8.6](#ebook_split_081.html#id-crawldepthlimit) 的深度限制功能，否则你不太可能注意到这个问题。）为了使程序终止，我们需要在 worklist 为空*且*没有活跃的 crawl goroutine 时跳出主循环。

[点击此处查看代码图像](#ch08_images.html#id242pro01_r)
