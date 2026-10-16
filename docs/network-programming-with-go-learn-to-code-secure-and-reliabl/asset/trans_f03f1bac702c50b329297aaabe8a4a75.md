
# Listing 5-6: 创建回声服务器和客户端 (*dial_test.go*)

客户端的连接可以利用 `net.Conn` 的面向流的功能（基于 UDP），但 UDP 监听器仍需使用 `net.PacketConn`。

你启动一个回声服务器实例 1，用于向客户端发送回复。然后通过将 `udp` 作为 `net.Dial` 的第一个参数传递来通过 UDP 拨号连接到回声服务器 2。与 TCP 不同，调用 `net.Dial` 后回声服务器不会收到任何流量，因为不需要握手。

# Listing 5-7: 中断客户端 (*dial_test.go*)

interloper, err := net.ListenPacket("udp", "127.0.0.1:")

if err != nil {
    t.Fatal(err)
}

Unreliable UDP Communication **113** interrupt := \[\]byte("pardon me")

n, err := interloper.WriteTo(interrupt, client.LocalAddr())

if err != nil {
    t.Fatal(err)
}

\_ = interloper.Close()

if l := len(interrupt); l != n {
    t.Fatalf("wrote %d bytes of %d", n, l)
}

# Listing 5-8: 使用 net.Conn 管理 UDP 流量 (*dial_test.go*)

正如在 Listing 5-4 中，你通过一个中继连接向客户端发送消息 1。

Listing 5-8 说明了使用 `net.Conn` 的 UDP 连接与使用 `net.PacketConn` 的 UDP 连接之间的区别，如在 Listing 5-5 中所示。

\--snip--

ping := \[\]byte("ping")

\_, err = 1client.Write(ping)

if err != nil {
    t.Fatal(err)
}

buf := make(\[\]byte, 1024)

n, err = 2client.Read(buf)

if err != nil {
    t.Fatal(err)
}

if !bytes.Equal(ping, buf\[:n\]) {
    t.Errorf("expected reply %q; actual reply %q", ping, buf\[:n\])
}

err = 3client.SetDeadline(time.Now().Add(time.Second))

if err != nil {
    t.Fatal(err)
}

\_, err = 4client.Read(buf)

if err == nil {
    t.Fatal("unexpected packet")
}

# 你学到的内容

UDP 是一种极简、基于数据报的协议，它通过放弃 TCP 的许多流控制和可靠性特性，优先考虑速度而非可靠性。

当速度和简洁性是关键且可接受数据丢失时，UDP 非常理想，例如用于实时视频流。

由于 UDP 不是面向会话的，它不存在“UDP 监听器”这一概念。

