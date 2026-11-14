
客户端每秒显示服务器发送的时间，直到我们用 Control-C 中断客户端，在 Unix 系统上 Shell 会将其回显为 `^C`。如果系统未安装 `nc` 或 `netcat`，可使用 `telnet` 或这个使用 `net.Dial` 连接 TCP 服务器的简单 Go 版 `netcat`：

[点击查看代码图像](#part0138_split_004.html#id221pro01_01_r)

gopl.io/ch8/netcat1

```go
// Netcat1 是一个只读 TCP 客户端。
package main

import (
    "io"
    "log"
    "net"
    "os"
)

func main() {
    conn, err := net.Dial("tcp", "localhost:8000")
    if err != nil {
        log.Fatal(err)
    }
    defer conn.Close()
    mustCopy(os.Stdout, conn)
}

func mustCopy(dst io.Writer, src io.Reader) {
    if _, err := io.Copy(dst, src); err != nil {
        log.Fatal(err)
    }
}
```

该程序从连接读取数据并写入标准输出，直到遇到文件结束条件或错误。`mustCopy` 函数是本节多个示例中使用的工具函数。让我们在不同终端同时运行两个客户端，左边显示一个，右边显示另一个：

[点击查看代码图像](#part0138_split_005.html#id221pro02_r)

```
$ go build gopl.io/ch8/netcat1
$ ./netcat1
13:58:54                               $ ./netcat1
13:58:55
13:58:56
^C
                                       13:58:57
                                       13:58:58
                                       13:58:59
                                       ^C
$ killall clock1
```

`killall` 命令是一个 Unix 实用程序，用于杀死所有给定名称的进程。

第二个客户端必须等待第一个客户端完成，因为服务器是*顺序*的；它一次只处理一个客户端。只需一个小改动即可使服务器并发：在调用 `handleConn` 时添加 `go` 关键字，使每次调用在自己的 goroutine 中运行。

[点击查看代码图像](#part0138_split_006.html#id222pro01_r)

gopl.io/ch8/clock2

```go
for {
    conn, err := listener.Accept()
    if err != nil {
        log.Print(err) // 例如，连接中止
        continue
    }
    go handleConn(conn) // 并发处理连接
}
```

现在，多个客户端可以同时接收时间：

[点击查看代码图像](#part0138_split_007.html#id222pro02_r)

```
$ go build gopl.io/ch8/clock2
$ ./clock2 &
$ go build gopl.io/ch8/netcat1
$ ./netcat1
14:02:54                               $ ./netcat1
14:02:55                               14:02:55
14:02:56                               14:02:56
14:02:57                               ^C
14:02:58
14:02:59                               $ ./netcat1
14:03:00                               14:03:00
14:03:01                               14:03:01
^C                                     14:03:02
                                       ^C
$ killall clock2
```

### 练习 8.1

修改 `clock2` 以接受端口号，并编写一个程序 `clockwall`，作为多个时钟服务器的客户端同时运行，从每个服务器读取时间并在表格中显示结果，类似于某些商务办公室见到的时钟墙。如果你有地理分布的计算机，远程运行实例；否则在不同端口运行本地实例并使用假时区。

[点击查看代码图像](#part0138_split_008.html#id222pro03_r)

```
$ TZ=US/Eastern    ./clock2 -port 8010 &
$ TZ=Asia/Tokyo    ./clock2 -port 8020 &
$ TZ=Europe/London ./clock2 -port 8030 &
$ clockwall NewYork=localhost:8010 London=localhost:8020 Tokyo=localhost:8030
```

### 练习 8.2

实现一个并发文件传输协议 (FTP) 服务器。服务器应解释来自每个客户端的命令，如 `cd` 更改目录，`ls` 列出目录，`get` 发送文件内容，`close` 关闭连接。可以使用标准 `ftp` 命令作为客户端，或编写自己的客户端。

## 8.3 示例：并发 Echo 服务器

时钟服务器为每个连接使用一个 goroutine。在本节中，我们将构建一个每个连接使用多个 goroutine 的 echo 服务器。大多数 echo 服务器只是写回读取的内容，这可以用这个简单版本的 `handleConn` 完成：

[点击查看代码图像](#part0138_split_009.html#id223pro01_r)

```go
func handleConn(c net.Conn) {
    io.Copy(c, c) // 注意：忽略错误
    c.Close()
}
```

一个更有趣的 echo 服务器可能模拟真实回声的混响，响应起初很大 (`"HELLO!"`)，延迟后中等 (`"Hello!"`)，然后安静 (`"hello!"`) 最后消失，如这个版本的 `handleConn` 所示：

[点击查看代码图像](#part0138_split_010.html#id223pro02_r)

gopl.io/ch8/reverb1

```go
func echo(c net.Conn, shout string, delay time.Duration) {
    fmt.Fprintln(c, "\t", strings.ToUpper(shout))
    time.Sleep(delay)
    fmt.Fprintln(c, "\t", shout)
    time.Sleep(delay)
    fmt.Fprintln(c, "\t", strings.ToLower(shout))
}

func handleConn(c net.Conn) {
    input := bufio.NewScanner(c)
    for input.Scan() {
        echo(c, input.Text(), 1*time.Second)
    }
    // 注意：忽略 input.Err() 的潜在错误
    c.Close()
}
```

我们需要升级客户端程序，使其将终端输入发送给服务器，同时将服务器响应复制到输出，这提供了另一个使用并发的机会：

[点击查看代码图像](#part0138_split_011.html#id223pro03_r)

gopl.io/ch8/netcat2

```go
func main() {
    conn, err := net.Dial("tcp", "localhost:8000")
    if err != nil {
        log.Fatal(err)
    }
    defer conn.Close()
    go mustCopy(os.Stdout, conn)
    mustCopy(conn, os.Stdin)
}
```

主 goroutine 读取标准输入并发送给服务器，第二个 goroutine 读取并打印服务器的响应。当主 goroutine 遇到输入结束时（例如用户在终端输入 Control-D (`^D`)（或 Microsoft Windows 上的等效 Control-Z）），程序停止，即使另一个 goroutine 仍有工作要做。（一旦我们在 [8.4.1 节](#part0080.html#id-unbufferedchannels) 引入通道，将看到如何让程序等待双方都完成。）

在下面的会话中，客户端输入左对齐，服务器响应缩进。客户端对 echo 服务器喊了三次：

```
$ go build gopl.io/ch8/reverb1
$ ./reverb1 &
$ go build gopl.io/ch8/netcat2
$ ./netcat2
Hello?
    HELLO?
    Hello?
    hello?
Is there anybody there?
    IS THERE ANYBODY THERE?
Yooo-hooo!
    Is there anybody there?
    is there anybody there?
    YOOO-HOOO!
    Yooo-hooo!
    yooo-hooo!
^D
$ killall reverb1
```

注意，直到第二次喊声消失，客户端的第三次喊声才被处理，这不太真实。真实的回声应该是三次独立喊声的*合成*。为了模拟它，我们需要更多 goroutine。同样，只需添加 `go` 关键字，这次用在调用 `echo` 上：

[点击查看代码图像](#part0138_split_012.html#id224pro01_r)

gopl.io/ch8/reverb2

```go
func handleConn(c net.Conn) {
    input := bufio.NewScanner(c)
    for input.Scan() {
        go echo(c, input.Text(), 1*time.Second)
    }
    // 注意：忽略 input.Err() 的潜在错误
    c.Close()
}
```

由 `go` 启动的函数的参数在 `go` 语句本身执行时求值；因此 `input.Text()` 在主 goroutine 中求值。

现在回声是并发的并在时间上重叠：

```
$ go build gopl.io/ch8/reverb2
$ ./reverb2 &
$ ./netcat2
Is there anybody there?
    IS THERE ANYBODY THERE?

Yooo-hooo!
    Is there anybody there?
    YOOO-HOOO!
    is there anybody there?
    Yooo-hooo!
    yooo-hooo!
^D
$ killall reverb2
```
