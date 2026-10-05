

```c
/* protocol 4 */

Send_and_receive()
{
    NFTS = 0;
    FE = 0;
    from_host(buffer);
    S.info = buffer;
    S.seq = NFTS;
    S.ack = 1-FE;
    sendf(S);
    start_timer(S.seq);
    forever {
        wait(event);
        if(event == frame_arrival) {
            getf(R);
            if(R.seq == FE) {
                to_host(R.info);
                ++FE;
            }
            if(R.ack == NFTS) {
                from_host(buffer);
                ++NFTS;
            }
        }
        S.info = buffer;
        S.seq = NFTS;
        S.ack = 1-FE;
        sendf(S);
        start_timer(S.seq);
    }
}
```

# 流水传输 (Pipelining)

在许多情况下，较长的往返时间对带宽利用效率具有重要影响。

例如，考虑一个往返传播延迟为 500ms 的卫星信道。从时间 $t$ 开始直到 $t \ge 500$ ms，确认信号才返回发送者。这意味着发送者在大多数时间内处于阻塞状态，导致效率降低。

另一个例子是，如果以双向交替模式（半双工）运行链路，线路可能为了每一个帧都需要进行“切换”以接收确认信号。这种确认延迟可能会严重影响有效数据传输率。

这些问题产生可以通过允许发送者在接收确认之前传输连续的帧（例如最多 $w$ 个帧）来克服。这种技术被称为流水传输。

在卫星示例中，信道容量为 50kbps，帧长度为 1000 位。当发送者完成 26 个帧的发送时（$t \approx 520$ ms），帧 0 的确认信号将到达，允许发送者继续发送帧。在任何时刻，都有 25 个或 26 个未确认的帧处于处理状态，发送者的窗口大小至少需要为 26。

在不可靠的通信信道上对帧进行流水传输会引发严重的问题。如果长流中间的某个帧损坏或丢失了会怎样？接收者应该如何处理坏帧之后的所有正确帧？以下是处理流水传输中存在错误的两种基本自动重复请求（ARQ）方法。

一种方法是 ARQ 的普通模式——回 Go N（Go-Back-N）。如果接收者在帧 N 中检测到任何错误，它会通知发送者并丢弃任何后续帧。

发送者在检测到错误时可能正在发送帧 N+X，它将重传帧 N 以及所有后续帧。

另一种方法称为选择重复（selective repeat）。在该方法中，接收者会存储坏帧之后的所有正确帧。当发送者最终发现出现问题时，它只重传那一个坏帧，而不是所有的后继帧。

# 协议 5：流水传输，多个待处理帧 (MaxSeq)

在这一协议中，发送者可以传输多达 MaxSeq 个帧而无需等待确认。此外，与之前的协议不同，并不假设主机一直有新消息。相反，当有消息要发送时，主机会触发主机就绪事件。

该协议采用了回 Go N 技术。在下面的示例中，接收者的窗口大小等于 1，任何时刻最多可有 MaxSeq 个帧处于待处理状态。

自动重复请求是一种数据传输的错误控制方法，它利用确认和超时在不可靠信道上实现可靠的数据传输。

```c
/* protocol 5 */
send_data(frame_number)
{
  S.info = buffer[frame_number];
  S.seq = frame_number;
  S.ack = (FE+MaxSeq) % (MaxSeq+1);
  sendf(S);
  start_timer(frame_number);
}

send_receive()
{
  enable_host();
  NFTS = 0;
  Ack_expected = 0;
  Frame_expected = 0;
  nbuffered = 0;
  forever
{
    wait(event);
    switch(event)
    {
      case host_ready:
        from_host(buffer[NFTS]);
        ++nbuffered;
        send_data(NFTS);
        ++NFTS;
        break;
      case frame_arrival:
        getf(R);
        if(R.seq == Frame_expected)
        {
          to_host(R.info);
          ++Frame_expected;
        }
        if((Ack_expected <= R.ack && R.ack < NFTS)
        ||(NFTS < Ack_expected && Ack_expected <= R.ack)
        ||(R.ack < NFTS && NFTS < Ack_expected))
        {
          --nbuffered;
          stop_timer(Ack_expected);
          ++Ack_expected;
        }
        break;
      case checksum_error:
        /* ignore the bad frame */
        break;
      case timeout:
        NFTS = Ack_expected;
        i = 0;
        do
        {
          send_data(NFTS);
          ++NFTS;
        } while(i<nbuffered);
        break;
    }
    if(nbuffered < MaxSeq)
      enable_host();
    else
      disable_host();
}
```

# 协议 6

该协议采用了选择重复（selective repeat）技术。只要这些好帧落在窗口内，协议就不会因为较早的帧损坏或丢失而丢弃好帧。每个待处理帧都关联有一个计时器。当传输器收到任何错误通知时，只重传一个帧，而不是像协议 5 那重传所有待处理帧。

在该协议中，接收者的窗口大小是固定的，最大值为 (MaxSeq+1)。选择这个最大值是为了确保新窗口与旧窗口之间不会重叠。窗口重叠意味着接收者将无法区分新帧和重传帧。

接收者为其窗口内的每个序列号预留了一个缓冲区。每当帧到达时，都会检查其序列号判断是否在接收者的窗口内。如果是，且尚未接收，则无论它是否是主机预期的下一个帧，都会被接收并存储。传递给主机的帧必须是有序的。

协议 6 比协议 5 更高效，体现在：

- 协议 6 采用带有计时器的机制来防止延迟。当接收者怀疑发生错误时，会向发送者发送否定确认（NAK）。
- 这种帧格式显示了请求重传。

# 核心概念：传输模式 (CORE CONCEPT: DATA TRANSMISSION MODES)

数据从一处传输到另一个处的方式被称为传输模式。它也是数据通信模式。指示了信息的流向。有时这种模式被称为方向模式。

![f7819d0546fc14719b3ebb980271a_174_0](数据从一处传输到另一个处的方式被称为传输模式。它也是数据通信模式。指示了信息的流向。有时这种模式被称为方向模式。

数据从一处传输到其他处的方式被称为传输模式。它也是数据通信模式。指示了信息的流向。有时这种模式被称为方向模式。

# 字符模式 (Character Mode)

当操作员按键时，字符数据有两种模式：字符模式和块模式。

# 块模式 (Block Mode)

在这里，字符进入缓冲区。当操作员准备好发送时，屏幕上作为一组传输的字符被称为一个块或帧。

# XMODEM 帧格式 (XMODEM Frame Format)

XMODEM 的四个字段是 SOH 字段、头部字段、数据字段和错误检测字段。XMODEM 帧的第一个字段仅仅是一个单字节的起始头（SOH）字段。SOH 是指示头部开始的数据链路控制字符。第二个字段是一个双字节序列，即当前正在传输帧的编号。第一个头部字节被称为序列号，因为第二个头部字节只是第一个字节的 2 补码，用于验证第一个头部字节的有效性（这有时被称为冗余）。

