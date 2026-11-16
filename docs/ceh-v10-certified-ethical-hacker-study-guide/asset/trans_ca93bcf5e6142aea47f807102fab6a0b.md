

## 使用 tshark 打印字段

```
root@quiche:~# tshark -Tfields -e frame.number -e ip.src -e ip.dst -e ip.tos -e ip.ttl
Running as user "root" and group "root". This could be dangerous.
tshark: Lua: Error during loading:
[string "/usr/share/wireshark/init.lua"]:32: dofile has been disabled due to running Wireshark as superuser. See https://wiki.wireshark.org/CaptureSetup/CapturePrivileges for help in running Wireshark as an unprivileged user.
```

正在捕获 'eth0'

| | | | |
|---|---|---|---|
| 1 | 192.168.86.26 | 192.168.86.57 | 64 |
| 2 | | | |
| 3 | 192.168.86.57 | 192.168.86.26 | 64 |
| 4 | 192.168.86.26 | 192.168.86.57 | 64 |
| 5 | 192.168.86.22 | 224.0.0.7 | 1 |
| 6 | 192.168.86.57 | 192.168.86.26 | 64 |
| 7 | 192.168.86.57 | 192.168.86.26 | 64 |
| 8 | 192.168.86.57 | 192.168.86.26 | 64 |
| 9 | 192.168.86.26 | 192.168.86.57 | 64 |
| 10 | 192.168.86.26 | 192.168.86.57 | 64 |
| 11 | 192.168.86.26 | 192.168.86.57 | 64 |
| 12 | | | |
| 13 | | | |
| 14 | 192.168.86.57 | 192.168.86.26 | 64 |
| 15 | 192.168.86.57 | 192.168.86.26 | 64 |
| 16 | 192.168.86.57 | 192.168.86.26 | 64 |
| 17 | 192.168.86.57 | 192.168.86.26 | 64 |
| 18 | 192.168.86.57 | 192.168.86.26 | 64 |
| 19 | 192.168.86.57 | 192.168.86.26 | 64 |
| 20 | 192.168.86.57 | 192.168.86.26 | 64 |
| 21 | 192.168.86.57 | 192.168.86.26 | 64 |

可用的字段有数百个。从前面的示例中可以看出，您可以继续使用 -e 标志添加字段。其余大部分命令行标志与 tcpdump 中使用的相同。您可以设置快照长度、选择接口，还可以写出文件。这些都使用与之前从 tcpdump 中看到的相同参数。

tshark 程序随 Wireshark 包一起安装。无论您在哪个平台上安装 Wireshark，默认都会安装 tshark 和其他命令行程序。但是，Windows 上没有 tcpdump。您需要找到 windump 并安装它。这是 tcpdump 的移植版，用于在 Windows 平台上运行。

## Wireshark

Wireshark 是一个基于 GUI 的数据包捕获程序。如前所述，它附带一些命令行程序。使用 Wireshark 有很多优势。首先，它让我们能够轻松查看数据包，并在完整的捕获中移动。与 tcpdump 和 tshark 不同，我们在 Wireshark 中看到整个网络协议栈，从技术上讲，这使得我们捕获的是帧而不是数据包。Wireshark 还让我们能够轻松滚动查看所有捕获帧的列表。图 9.1 显示了捕获会话中的帧列表。与 tcpdump 类似，我们得到的是每个帧的本质摘要。

### 图 9.1 Wireshark 帧列表

![](img/421171b17a0c0dfae0aacde15d9831c1_363_0.png)

这些列是可配置的，包括帧号、从捕获开始的相对时间、地址、协议、帧长度，然后是一个信息列。我们获得的信息是每个帧的摘要。这与 tcpdump 有点类似，tcpdump 中有一个简短的摘要。Wireshark 在摘要中提供了更多详细信息。这些都是 Wireshark 从数据包和通信流中推断出的所有信息。

Wireshark 不仅提供帧列表让您查看谁在与谁通信，还提供完整的协议解码。图 9.2 中有两个协议被展开。Wireshark 知道如何解码您向其提供的几乎任何协议。图 9.2 中显示的是两种常见协议（IP 和 TCP）的简单解码。在解码中，每个字段都被拆分出来，不仅提供字段名和值，还提供含义。例如，如果您只查看包含 IP 版本和头部长度的字节，您会看到 0x45。这是字节值，但该字节在两个半字节（4 字节值）中包含两个独立的数据片段。第一个是版本，即 4。第二个是头部长度。您会看到 5，如果您不太了解 IP 协议，可能会认为长度是 5。Wireshark 知道您需要将值 5 乘以 4，因为该字段中的值实际上表示 32 位（4 字节）双字的数量。因此，Wireshark 会显示头部长度为 20。

### 图 9.2 协议详细信息

```
Internet Protocol Version 4, Src: 192.168.86.26, Dst: 52.109.88.39
    0100 .... = Version: 4
    .... 0101 = Header Length: 20 bytes (5)
    Differentiated Services Field: 0x00 (DSCP: CS0, ECN: Not-ECT)
    Total Length: 159
    Identification: 0x0000 (0)
    Flags: 0x0000 (Don't fragment)
    Time to live: 64
    Protocol: TCP (6)
    Header checksum: 0x9702 [validation disabled]
    [Header checksum status: Unverified]
    Source: 192.168.86.26
    Destination: 52.109.88.39
Transmission Control Protocol, Src Port: 53394, Dst Port: 443, Seq: 218, Ack: 5672, Len: 107
    Source Port: 53394
    Destination Port: 443
    [Stream index: 28]
    [TCP Segment Len: 107]
    Sequence number: 218    (relative sequence number)
    [Next sequence number: 325    (relative sequence number)]
    Acknowledgment number: 5672    (relative ack number)
    ... .... = ACK
    Flags: 0x018 (PSH, ACK)
    Window size value: 2848
    [Calculated window size: 131072]
    [Window size scaling factor: 64]
    Checksum: 0xF513 [unverified]
```

这使得理解您所看到的内容容易得多。Wireshark 还了解许多其他协议。它甚至可以在一定程度上帮助您理解加密通信。如果您查看帧列表，可以看到用于设置 TLS 会话加密的不同帧。在 Wireshark 窗口中间的解码窗格中打开协议，您可以看到具体内容，如图 9.3 所示。您可以看到正在使用的 TLS 版本以及正在发送的具体消息。您根据头部信息知道这一点，因为整个消息尚未被加密。

### 图 9.3 TLS 信息

```
Frame 1253: 69 bytes on wire (480 bits), 69 bytes captured (480 bits) on interface 8
Ethernet II, Src: Apple_Be:c3:49 (f0:18:98:bc:c4:69), Dst: Tp-LinkT_7d:f4:8a (18:d6:c7:7d:f4:8a)
Internet Protocol Version 4, Src: 192.168.86.26, Dst: 13.107.136.9
Transmission Control Protocol, Src Port: 53406, Dst Port: 443, Seq: 292, Ack: 5690, Len: 6
Secure Sockets Layer
    TLSv1.2 Record Layer: Change Cipher Spec Protocol: Change Cipher Spec
        Content Type: Change Cipher Spec (20)
        Version: TLS 1.2 (0x0303)
        Length: 1
        Change Cipher Spec Message
```

在进行数据包捕获时，加密始终是一个问题。加密的目的在于只有发送方和接收方可以阅读消息。会话密钥（例如用于 TLS 加密 Web 消息的密钥）是在会话期间派生的。这是通过使用证书来完成的，证书包含公钥和私钥。在对称密钥派生过程中，这些密钥用于共享信息。要解密任何信息，您需要会话密钥，这意味着您需要拥有证书信息，以便能够处于对话中间，从而获取密钥。

> 您经常会看到 SSL/TLS 被用于加密。SSL（安全套接层）已被弃用，信誉良好的网站不再使用它。许多浏览器甚至不允许基于 SSL 的连接。因此，您现在看到的全是 TLS，这意味着继续提及 SSL 已经没有多大意义。

Wireshark 确实具有使用 RSA（Rivest、Shamir、Adleman，即创建该算法的人的名字）密钥来解密已加密 TLS 消息的能力。图 9.4 显示了首选项视图，您可以在其中添加 RSA 密钥。这可能允许您解密 TLS 消息。您还可以看到一个输入预共享密钥的位置。在某些情况下，您可能会看到使用预共享密钥的加密，这基本上意味着双方已经知道的一个密码。密钥已事先在双方之间共享（预共享）。

### 图 9.4 RSA 密钥首选项

![](img/421171b17a0c0dfae0aacde15d9831c1_365_0.png)

迄今为止您看到的所有内容都可以使用，无论您是在 Wireshark 中打开已保存并打开的文件，还是实时进行了捕获。Wireshark 可以打开由 tcpdump 或 tshark 写入的任何文件。当然，它也可以保存自己的捕获。要从 Wireshark 创建捕获，有多种途径

