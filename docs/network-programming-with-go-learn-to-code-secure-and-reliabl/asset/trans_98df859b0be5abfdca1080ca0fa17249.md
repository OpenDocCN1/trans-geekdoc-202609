
long. 第二，由你的 writer 返回的错误会导致 io.TeeReader 或 io.MultiWriter 也返回错误，从而中断网络数据的流动。

如果你不希望使用这些对象可能中断网络数据流，我强烈建议你实现一个始终返回 nil 错误并以可操作方式记录其底层错误的 reader。

例如，你可以修改 Monitor 的 Write 方法，使其始终返回 nil 错误：

func (m *Monitor) Write(p []byte) (int, error) {
    err := m.Output(2, string(p))
    if err != nil {
        log.Println(err) // 使用 log 包的默认 Logger
    }
    return len(p), nil
}

发送 TCP 数据 `95`

Monitor 尝试将字节切片写入其嵌套的日志记录器。如果写入失败，它会将错误写入 log 包的默认日志并返回 nil 错误给 io.TeeReader 和 io.MultiWriter（如 Listing 4-19 所示），以避免中断数据流。

***在 ICMP 过滤环境中 ping 主机***

在“Internet Control Message Protocol”（ICMP）一节（第 31 页）[^1]，你学到了 ICMP 是一种提供本地网络状况反馈的协议。

其最常见的用途是通过发送 ping 请求并收到主机的 pong 回复来判断主机是否在线。大多数操作系统都自带 ping 命令，它会向目标 IP 地址发送 ICMP echo request，一旦主机返回 ICMP echo reply，ping 会输出发送 ping 与收到 pong 之间的时间。

遗憾的是，许多互联网主机会过滤或阻止 ICMP echo reply。

如果主机过滤 pong，ping 会错误地报告远程系统不可用。一个可行的替代方案是建立 TCP 连接。如果你知道主机在特定端口上监听入站 TCP 连接，你可以利用这一点来确认主机是否可用，因为只有主机处于开启状态并完成三次握手，才能建立 TCP 连接。

Listing 4-21 展示了一个小型应用，用于报告建立 TCP 连接到特定主机和端口所需的时间。

package main

import (
    "flag"
    "fmt"
    "net"
    "os"
    "time"
)

var (
    count = flag.Int("c", 3, "number of pings: <= 0 means forever")
    interval = flag.Duration("i", time.Second, "interval between pings")
    timeout = flag.Duration("W", 5*time.Second, "time to wait for a reply")
)

func init() {
    flag.Usage = func() {
        fmt.Printf("Usage: %s [options] host:port\nOptions:\n", os.Args[0])
        flag.PrintDefaults()
    }
}

func main() {
    flag.Parse()

    if flag.NArg() != 1 {
        fmt.Print("host:port is required\n\n")
        flag.Usage()
        os.Exit(1)
    }

    target := flag.Arg(0)
    fmt.Println("PING", target)

    if *count <= 0 {
        fmt.Println("CTRL+C to stop.")
    }

    msg := 0
    for (*count <= 0) || (msg < *count) {
        msg++
        fmt.Print(msg, " ")

        start := time.Now()

        c, err := net.DialTimeout("tcp", target, *timeout)

        dur := time.Since(start)

        if err != nil {
            fmt.Printf("fail in %s: %v\n", dur, err)
            if nErr, ok := err.(net.Error); !ok || !nErr.Temporary() {
                os.Exit(1)
            }
        } else {
            _ = c.Close()
            fmt.Println(dur)
        }

        time.Sleep(*interval)
    }
}

[^1]: https://example.org/index_split_000.html#p53
