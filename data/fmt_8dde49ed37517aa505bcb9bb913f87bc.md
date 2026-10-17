
# 可靠的 TCP 数据流

```go
if err != nil {
    fmt.Println(err)
}

fmt.Printf("received %q (%s)\n",
    buf[:n], time.Since(now).Round(100*time.Millisecond))
}

for i, v := range []int64{0, 200, 300, 0, -1, -1, -1} {
    fmt.Printf("Run %d:\n", i+1)
    receivePing(time.Duration(v)*time.Millisecond, r)
}

cancel()
<-done // 确保在取消上下文后 pinger 退出

// 输出：
// Run 1:
// resetting timer (0s)
// received "ping" (1s)
// Run 2:
// resetting timer (200ms)
// received "ping" (200ms)
// Run 3:
// resetting timer (300ms)
// received "ping" (300ms)
// Run 4:
// resetting timer (0s)
// received "ping" (300ms)
// Run 5:
// received "ping" (300ms)
// Run 6:
// received "ping" (300ms)
// Run 7:
// received "ping" (300ms)
}
```

*Listing 3-11：测试 pinger 并重置其 ping 计时器间隔（`ping_example_test.go`）*

在这段示例中，你会创建一个缓冲通道，用于信号 pinger 的计时器重置。你在 `resetTimer` 通道上放入初始的 1 秒间隔，然后将该通道传给 `Pinger` 函数。你可以使用该时长初始化 pinger 的计时器，并决定何时向 `writer` 写入 ping 消息。

你会在循环 2 中遍历一系列毫秒时长，传递给 `receivePing` 函数。该函数会将计时器重置为给定的时长，然后等待从给定的 `reader` 中接收 ping 消息，最后打印到标准输出中接收到消息的时间。Go 会检查标准输出是否符合示例中的预期输出。

在第一次迭代 3 中，你传入时长为 0，这表示让 pinger 使用上一次的时长（本例中为 1 秒）重置计时器。如预期，`reader` 在 1 秒后收到 ping 消息。

第二次迭代 4 将计时器重置为 200 ms。当该时长到期，`reader` 会收到 ping 消息。第三次运行将计时器重置为 300 ms 5，对应的 ping 在 300 ms 处到达。

在运行 4 中，你传入时长为 0，保持 300 ms 的计时器不变。我发现使用 0 时长表示“使用上一次的计时器时长”很有用，因为不需要跟踪初始计时器时长。你可以直接将想要使用的时长作为初始值，然后通过在 `resetTimer` 通道上传入 0 时长来随时中断下一次 ping 的传输。

在未来改变计时器时长时，只需修改一行代码，而无需修改每次向 `resetTimer` 通道发送的内容。

运行 5 到 7 仅监听接收到的 ping，而不重置计时器。预期在最后三次运行中，`reader` 在 300 ms 间隔内收到 ping。

在保存 Listing 3-10 为文件名 `ping.go`，Listing 3-11 保存为文件名 `ping_example_test.go` 后，你可以通过执行以下命令运行示例：

```
$ go test ping.go ping_example_test.go
```

## 通过使用心跳来推迟截止时间

网络连接的两端都可以使用 `Pinger` 来推迟其截止时间，而之前的示例仅展示了单侧使用 `Pinger`。当任一端收到网络连接上的数据时，其 ping 计时器应重置，以避免发送不必要的 ping。Listing 3-12 是一个新文件 `ping_test.go`，展示了如何利用接收到的数据来推迟截止时间。

```go
package ch03

import (
    "context"
    "io"
    "net"
    "testing"
    "time"
)

func TestPingerAdvanceDeadline(t *testing.T) {
    done := make(chan struct{})
    listener, err := net.Listen("tcp", "127.0.0.1:")
    if err != nil {
        t.Fatal(err)
    }

    begin := time.Now()

    go func() {
        defer func() { close(done) }()

        conn, err := listener.Accept()
        if err != nil {
            t.Log(err)
            return
        }

        ctx, cancel := context.WithCancel(context.Background())
        defer func() {
            cancel()
            conn.Close()
        }()

        resetTimer := make(chan time.Duration, 1)
        resetTimer <- time.Second
        go Pinger(ctx, conn, resetTimer)

        err = conn.SetDeadline(time.Now().Add(15 * time.Second))
        if err != nil {
            t.Error(err)
            return
        }

        buf := make([]byte, 1024)
        for {
            n, err := conn.Read(buf)
            if err != nil {
                return
            }

            t.Logf("[%s] %s",
                time.Since(begin).Truncate(time.Second), buf[:n])

            resetTimer <- 0
            err = conn.SetDeadline(time.Now().Add(5 * time.Second))
            if err != nil {
                t.Error(err)
                return
            }
        }
    }()

    conn, err := net.Dial("tcp", listener.Addr().String())
    if err != nil {
        t.Fatal(err)
    }
    defer conn.Close()

    buf := make([]byte, 1024)
    for i := 0; i < 4; i++ { // 读取最多四个 ping
        n, err := conn.Read(buf)
        if err != nil {
            t.Fatal(err)
        }
        t.Logf("[%s] %s", time.Since(begin).Truncate(time.Second), buf[:n])
    }

    _, err = conn.Write([]byte("PONG!!!")) // 应该重置 ping 计时器
    if err != nil {
        t.Fatal(err)
    }

    for i := 0; i < 4; i++ { // 读取最多四个更多的 ping
        n, err := conn.Read(buf)
        if err != nil {
            if err != io.EOF {
                t.Fatal(err)
            }
            break
        }
        t.Logf("[%s] %s", time.Since(begin).Truncate(time.Second), buf[:n])
    }

    <-done

    end := time.Since(begin).Truncate(time.Second)
    t.Logf("[%s] done", end)
    if end != 9*time.Second {
        t.Fatalf("expected EOF at 9 seconds; actual %s", end)
    }
}
```

*Listing 3-12：接收数据会推迟截止时间（`ping_test.go`）*

你会启动一个监听器，接受连接，并启动一个以 1 秒为间隔的 `Pinger`，同时将初始截止时间设置为 5 秒。从客户端的角度来看，它会在服务器达到截止时间并终止连接前收到四个 ping，然后收到 `io.EOF`。

然而，客户端可以在服务器到达截止时间之前发送数据来推迟服务器的截止时间。

如果服务器从连接上读取到数据，它可以确信网络连接仍然良好，因此可以通知 `Pinger` 重置计时器，并推迟连接的截止时间。为了在套接字被终止前抑制其终止，客户端会在服务器发送四个 ping 后发送一个明确的 `"PONG!!!"` 消息。

这应该为客户端再延长五秒，直到服务器达到其截止时间。客户端会在6读取四个更多的 ping，然后等待不可避免的结束。

你会检查到达时总共 9 秒，以确认服务器的终止是由客户端的 pong 成功触发的 ping 计时器重置所致。

这种通过数据推迟 ping 计时器的方法在实践中能显著减少因不必要的 ping 消耗的带宽。通常，如果你仅在连接上接收到数据，就不需要挑战远程网络端点。

`"ping"` 和 `"pong"` 这两个字符串是任意的。你可以根据需要使用更小的负载，例如单字节，只要双方网络连接方同意什么值代表 ping 和 pong 即可。

## 你已学到的内容

我们在本章节中涵盖了大量内容。我们从深入探讨 TCP 的握手、序列号、确认号、滑动窗口以及连接终止开始。然后，我们介绍了使用 Go 标准库建立 TCP 连接的过程。我们讨论了临时错误、超时、监听入站连接以及调用远程服务。最后，我们介绍了检测并及时修正网络完整性问题的技术。

我强烈推荐阅读 *Practical Packet Analysis*（作者 Chris Sanders，No Starch Press，2017）并安装 Wireshark。通过调试你的网络代码并在 Wireshark 中观察其对 TCP 流量的影响，是深入理解 TCP 与 Go 网络包的绝佳途径。下一章节将讲解如何通过 TCP 连接发送和接收数据。Wireshark 将帮助你更深入地理解你发送的数据，包括每个负载对滑动窗口的影响。

# SENDING TCP DATA

现在你已经掌握了如何在 Go 中正确建立并优雅地终止 TCP 连接，是时候把这些知识付诸实践，进行数据的传输。本章节介绍了使用 TCP 在网络中发送和接收数据的多种技术。

我们将讨论从网络连接中读取数据的最常用方法。你将创建一个简单的消息协议，能够在节点之间传输动态大小的负载。随后，你将探索 `net.Conn` 接口提供的网络可能性。本章节以对 `TCPConn` 对象的更深入探讨以及 Go 开发者可能遇到的隐蔽的 TCP 网络问题而结束。

## 使用 net.Conn 接口

本书中的大部分网络代码都会尽可能使用 Go 的 `net.Conn` 接口，因为它在大多数情况下都能满足我们的需求。你可以在不声明其底层类型的前提下，使用 `net.Conn` 接口编写强大的网络代码，确保代码在不同操作系统上兼容，并能编写更健壮的测试。（稍后在本章节中，你将学习如何访问 `net.Conn` 的底层类型以调用其高级方法。）`net.Conn` 方法覆盖了大多数使用场景。

`net.Conn` 最有用的两个方法是 `Read` 与 `Write`。这两个方法分别实现了 `io.Reader` 与 `io.Writer` 接口，这两个接口在 Go 标准库及其生态中随处可见。因此，你可以利用为这些接口编写的大量代码，构建极其强大的网络应用。

你使用 `net.Conn` 的 `Close` 方法来关闭网络连接。该方法在连接成功关闭时返回 `nil`，否则返回错误。`SetReadDeadline` 与 `SetWriteDeadline` 接受 `time.Time` 对象，用于设置读取和写入在网络连接上超时的绝对时间。`SetDeadline` 方法一次性设置读写超时时间。正如在“实现超时”（第 62 页，`#index_split_001.html#p84`）中讨论的那样，超时可以控制网络连接空闲的最长时间，并及时发现网络连通性问题。

## 发送和接收数据

从网络连接读取数据、向它写入数据的过程与读写文件类似，因为 `net.Conn` 实现了 `io.ReadWriteCloser` 接口，该接口用于文件的读写。本节首先介绍如何向固定大小缓冲区读取数据。接着，你将学习使用 `bufio.Scanner` 读取网络连接，直到遇到特定分隔符为止。随后，你将了解 TLV 编码方法，它允许你定义一种基本协议，动态分配用于不同负载大小的缓冲区。最后，你将看到在读取和写入网络连接时如何处理错误。

### 读取数据到固定缓冲区

Go 中的 TCP 连接实现了 `io.Reader` 接口，这使得你可以从网络连接读取数据。要从连接中读取数据，你需要提供一个缓冲区供 `Read` 方法填充。

`Read` 方法会在连接的接收缓冲区中有足够数据时，将缓冲区填充至其容量。如果接收缓冲区中的字节数少于你提供的缓冲区容量，`Read` 会填充缓冲区并立即返回，而不会等待更多数据到达。换句话说，`Read` 不保证在返回前已填充满缓冲区。Listing 4-1 展示了如何从网络连接读取数据到字节切片中。

```go
package main

import (
    "crypto/rand"
    "io"
    "net"
    "testing"
)

func TestReadIntoBuffer(t *testing.T) {
    payload := make([]byte, 1<<24) // 16 MB
    _, err := rand.Read(payload) // 生成随机负载
    if err != nil {
        t.Fatal(err)
    }

    listener, err := net.Listen("tcp", "127.0.0.1:")
    if err != nil {
        t.Fatal(err)
    }

    go func() {
        conn, err := listener.Accept()
        if err != nil {
            t.Log(err)
            return
        }
        defer conn.Close()

        _, err = conn.Write(payload)
        if err != nil {
            t.Error(err)
        }
    }()

    conn, err := net.Dial("tcp", listener.Addr().String())
    if err != nil {
        t.Fatal(err)
    }

    buf := make([]byte, 31<<19) // 512 KB
    for {
        n, err := conn.Read(buf)
        if err != nil {
            if err != io.EOF {
                t.Error(err)
            }
            break
        }
        t.Logf("read %d bytes", n) // buf[:n] 是从 conn 读取的数据
    }

    conn.Close()
}
```

*Listing 4-1：通过网络连接接收数据（`read_test.go`）*

你需要客户端提供读取的内容，因此创建一个 16MB 的随机数据负载 1——该负载大于客户端在选定缓冲区大小（512KB）中能一次读取的数据量，确保循环至少执行几次。使用更大的缓冲区或更小的负载也是可以的，单次 `Read` 即可读取整个负载。Go 会正确处理任何负载与接收缓冲区大小的组合。

### 使用分隔符的读取

前面所示的读取方法意味着你的代码必须能够理解它接收到的数据。由于 TCP 是面向字节的流式协议，客户端可能会在多个数据包中接收到字节流。与文本不同，二进制数据没有内在的标点符号来指示一个消息的起止。

例如，如果你的代码正在从服务器读取一系列电子邮件消息，你需要检查每个字节，寻找表示每条消息边界的分隔符。或者，你的客户端与服务器已约定一种协议：服务器会在发送下一段负载前发送固定数量的字节以指示接下来的负载大小。你可以利用该大小创建合适的缓冲区。稍后本章节会给出该技术的示例。

然而，如果你选择使用分隔符来标记消息的结束和下一个消息的开始，处理边界情况的代码并不简单。例如，你可能一次读取 1KB 数据，却发现其中包含两个分隔符，这意味着你已经收到了两条完整消息，但缓冲区容量不足以同时处理它们。

### 使用 bufio.Scanner 进行分隔读取

使用 `bufio.Scanner` 读取网络连接，直到遇到特定分隔符为止。后续将介绍 TLV 编码以及错误处理。
