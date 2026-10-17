
Prior to later enhancements, `TCP` could only acknowledge the next byte expected. For example, in Figure 14-24, using segment numbers for simplicity, `Host A` sends segments 1 through 10 to `Host B`. If all the segments arrive except for segments 3 and 4, `Host B` replies with an acknowledgment specifying that the next segment expected is segment 3. `Host A` has no idea if any other segments arrived or not. Therefore, `Host A` re-sends segments 3 through 10. If all the re-sent segments arrive successfully, segments 5 through 10 are duplicates. This can lead to delays, congestion, and inefficiencies.

**Note**

For simplicity, segment numbers are used here instead of the byte numbers.

![](img/e71dc48d3ae3db3394e5857ab2acae75_524_0.png)

Figure 14-24 Data Retransmission

`Host` operating systems today typically employ an optional `TCP` feature called *selective acknowledgment (`SACK`)*, which is negotiated during the three-way handshake. If both hosts support `SACK`, the receiver can explicitly acknowledge which segments (bytes) were received, including any discontinuous segments. The sending host therefore needs to retransmit only the missing data. For example, in Figure 14-25, again using segment numbers for simplicity, `Host A` sends segments 1 through 10 to `Host B`. If all the segments arrive except for segments 3 and 4, `Host B` can acknowledge that it has received segments 1 and 2 (`ACK 3`) and selectively acknowledge segments 5 through 10 (`SACK 5-10`). `Host A` needs to re-send only segments 3 and 4.

![](img/e71dc48d3ae3db3394e5857ab2acae75_525_0.png)

### Figure 14-25 Selective Acknowledgment

### Note

`TCP` typically sends `ACKs` for every other packet, but other factors beyond the scope of this section may alter this behavior.

`TCP` uses timers to know how long to wait before re-sending a segment.

Video

### Video—TCP Reliability—Data Loss and Retransmission (14.6.4)

Refer to the online course to view this video. Play the video and click the link to download the PDF file. The video and PDF file examine `TCP` data loss and retransmission.

### TCP Flow Control—Window Size and Acknowledgments (14.6.5)

`TCP` provides mechanisms for flow control, which has to do with the amount of data the destination can receive and process reliably. Flow control helps maintain the reliability of `TCP` transmission by adjusting the rate of data flow between source and destination for a given session. To accomplish this, the `TCP` header includes a 16-bit field called the *window size*.

Figure 14-26 shows an example of window size and acknowledgments.

![](img/e71dc48d3ae3db3394e5857ab2acae75_526_0.png)

Figure 14-26 TCP Window Size Example

The window size determines the number of bytes that can be sent before an acknowledgment should be expected. The acknowledgment number is the number of the next expected byte.

The window size is the number of bytes that the destination device of a `TCP` session can accept and process at one time. In this example, the `PC B` initial window size for the `TCP` session is 10,000 bytes. Starting with the first byte, byte number 1, the last byte `PC A` can send without receiving an acknowledgment is byte 10,000. This is known as the *send window* of `PC A`. The window size is included in every `TCP` segment, so the destination can modify the window size at any time, depending on buffer availability.

The initial window size is agreed upon when the `TCP` session is established during the three-way handshake. The source device must limit the number of bytes sent to the destination device, based on the window size of the destination. Only after the source device receives an acknowledgment that the bytes have been received can it continue sending more data for the session. Typically, the destination does not wait for all the bytes for its window size to be received before it replies with an acknowledgment. As the bytes are received and processed, the destination sends acknowledgments to inform the source that it can continue to send additional bytes.

For example, it is typical that `PC B` would not wait until all 10,000 bytes have been received before sending an acknowledgment. This means `PC A` can adjust its send window as it receives acknowledgments from `PC B`. As shown in Figure 14-26, when `PC A` receives an acknowledgment with the acknowledgment number 2921, which is the next expected byte, the `PC A` send window increments 2920 bytes. This changes the send window from 10,000 bytes to 12,920. `PC A` can now continue to send up to another 10,000 bytes to `PC B`, as long as it does not send more than its new send window of 12,920.

A destination sending acknowledgments as it processes bytes received and the continual adjustment of the source send window is known as *sliding window*. In the previous example, the send window of `PC A` increments, or slides over, another 2921 bytes, from 10,000 to 12,920.

If the availability of the destination's buffer space decreases, the destination may reduce its window size to inform the source to reduce the number of bytes it should send without receiving an acknowledgment.

### Note

Devices today use the sliding window protocol. The receiver typically sends an acknowledgment after receiving every two segments. The number of segments received before acknowledgment occurs may vary, however. The advantage of the sliding window is that it allows the sender to continuously transmit segments, as long as the receiver is acknowledging previous segments. The details of the sliding window are beyond the scope of this book.

### TCP Flow Control—Maximum Segment Size (MSS) (14.6.6)

In Figure 14-27, the source is transmitting 1460 bytes of data within each `TCP` segment. This is typically the maximum segment size (`MSS`) that the destination device

可以接收。`MSS` 是 `TCP` 报头中 Options 字段的一部分，它指定设备在单个 `TCP` 分段中可以接收的最大数据量（以字节为单位）。`MSS` 不包括 `TCP` 报头。`MSS` 通常在三次握手期间包含。

## MSS = 最大分段大小

![](img/e71dc48d3ae3db3394e5857ab2acae75_528_0.png)

## 图 14-27 最大分段大小

使用 `IPv4` 时常见的 `MSS` 为 1460 字节。主机通过从以太网最大传输单元（`MTU`）中减去 `IP` 和 `TCP` 报头来确定其 `MSS` 字段的值。在以太网接口上，默认 `MTU` 为 1500 字节。减去 `IPv4` 报头 20 字节和 `TCP` 报头 20 字节后，默认 `MSS` 大小为 1460 字节，如图 14-28 所示。

![](img/e71dc48d3ae3db3394e5857ab2acae75_528_1.png)

## 图 14-28 1460 字节 MSS

### TCP 流量控制—拥塞避免 (14.6.7)

网络拥塞会导致数据包被超载的路由器丢弃。当包含 `TCP` 分段的数据包未到达其目的地时，它们将未被确认。通过确定 `TCP` 分段被发送但未被确认的速率，源可以假设网络拥塞的某个水平。

每当发生拥塞时，源会重传丢失的 `TCP` 分段。如果重传未得到适当控制，`TCP` 分段的额外重传可能会使拥塞变得更糟。不仅网络中引入了包含 `TCP` 分段的新数据包，而且丢失的被重传 `TCP` 分段的反馈效应也会增加拥塞。为了避免和控制拥塞，`TCP` 采用了多种拥塞处理机制、计时器和算法。

如果源确定 `TCP` 分段未被确认或未及时被确认，则它可以减少在收到确认之前发送的字节数。例如，在图 14-29 中，`PC A` 感知到存在拥塞，因此减少了在收到 `PC B` 的确认之前发送的字节数。

> 我没有收到来自 `PC B` 的预期确认，因此我将减少在收到确认之前发送的字节数。

![](img/e71dc48d3ae3db3394e5857ab2acae75_529_0.png)

图 14-29 TCP 拥塞控制

请注意，减少未确认字节数的是源，而不是由目标确定的窗口大小。

### 注

拥塞处理机制、计时器和算法的解释超出了本书的范围。

交互式图形

## 检查你的理解—可靠性与流量控制 (14.6.8)

请参考在线课程完成此活动。

## UDP 通信 (14.7)

有时与 `TCP` 相关的可靠性并非必需，或者提供这种可靠性的开销不适合该应用。这时就会使用 `UDP`。

### UDP 低开销与可靠性 (14.7.1)

如本章前面所述，`UDP` 非常适合 `VoIP` 等需要快速的通信。本节详细解释了为什么 `UDP` 非常适合某些类型的传输。如图 14-30 所示，`UDP` 不建立连接。`UDP` 提供低开销的数据传输，因为它具有小的數據报报头且没有网络管理流量。

![](img/e71dc48d3ae3db3394e5857ab2acae75_530_0.png)

图 14-30 发送方与接收方之间的无连接传输

### UDP 数据报重组 (14.7.2)

与 `TCP` 分段一样，发送到同一目的地的 `UDP` 数据报通常会走不同的路径并乱序到达。`UDP` 不像 `TCP` 那样跟踪序列号。`UDP` 没有办法将数据报重新排序为其传输顺序，如图 14-31 所示。

因此，`UDP` 只是按接收到的顺序重新组装数据并将其转发给应用程序。如果数据的顺序对应用程序很重要，则应用程序必须识别正确的顺序并确定应如何处理数据。

![](img/e71dc48d3ae3db3394e5857ab2acae75_531_0.png)

图 14-31 UDP：无连接且不可靠

### UDP 服务器进程和请求 (14.7.3)

与基于 `TCP` 的应用程序一样，基于 `UDP` 的服务器应用程序被分配众所周知或已注册的端口号，如图 14-32 所示。当这些应用程序或进程在服务器上运行时，它们接受与分配的端口号匹配的数据。当 `UDP` 收到发往这些端口之一的数据报时，它会根据端口号将应用数据转发给适当的应用程序。

**注**

图 14-32 中显示的远程身份验证拨入用户服务（`RADIUS`）服务器提供身份验证、授权和计费服务来管理用户访问。`RADIUS` 的操作超出了本书的范围。

### UDP 客户端进程 (14.7.4)

与 `TCP` 一样，在 `UDP` 中，客户端/服务器通信由请求服务器进程数据的客户端应用程序发起。`UDP` 客户端进程从端口号范围内动态选择一个端口号，并将其用作会话的源端口。目标端口通常是分配给服务器进程的众所周知或已注册的端口号。

![](img/e71dc48d3ae3db3394e5857ab2acae75_532_0.png)

## 图 14-32 UDP 服务器监听请求

客户端选择源端口和目标端口后，交易中所有数据报的报头中都使用相同的两个端口。对于从服务器返回到客户端的数据，数据报报头中的源端口号和目标端口号是反转的。

图 14-33 说明了两个主机请求 `DNS` 和 `RADIUS` 身份验证服务器服务的示例。在图中，客户端 1 正在发送 `DNS` 请求，而客户端 2 正在请求同一服务器的 `RADIUS` 身份验证服务。
