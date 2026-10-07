

## 172 深度学习的硬件架构

至少是其中之一。如果 max_BR_width 是 BRAM 允许的最大宽度，我们可以估算 BRAM 的数量为：

```
$#BRAM = \left[ \frac{vector\_size \times DW}{max\_BR\_width} \right] \times \frac{buffer\_depth}{BR\_depth} \quad (8.4)$
```

```
$BR\_depth = \min(vector\_size \times DW, max\_BR\_width) \quad (8.5)$
```

其中 DW 是数据量化位宽，buffer\_depth 是特定缓冲区所需的深度，并向上调整到 2 的幂次。此外，vector\_size 表示每个周期并行访问的元素数量：

```
$vector\_size = \begin{cases} Tn, & \text{对于 IFM 缓冲区} \\ Tm, & \text{对于 OFM 缓冲区} \\ Tn \times Tm, & \text{对于权重缓冲区} \end{cases} \quad (8.6)$
```

为了估算寄存器和逻辑使用情况，虽然如 [13] 中的回归和插值技术，但 FPGA 逻辑被分组为包含 2-8 个寄存器和 2-6 个查找表的模块或切片，这种建模方式限制了我们，因为选择不同的设备将需要重新学习估算。相反，我们使用 OpenCL 编译器已经提供的准确预合成逻辑估算来获取逻辑估计。

### 8.6.2 统一片外和片内内存

FPICache 利用了片内、片外带宽的匹配。我们允许将不匹配的带宽影响纳入预测性能中，从而带给我们更好的运行时估算，并且不依赖于所使用的底层 FPGA 平台。

### 8.6.21 系统不匹配的影响

为了确定内存系统的访问延迟，假设加速器运行频率为 freq。如果存储/从内存读取的数据元素数量为 num\_data\_elem，DW 是以位为单位的数据位宽，则内存访问消耗的周期数公式如下：

```
$num\_cycles = mem\_latency \times freq \quad (8.7)$
```

```
$mem\_latency = \frac{data\_size}{mem\_bw} \quad (8.8)$
```

```
$data\_size = num\_data\_elem \times DW \quad (8.9)$
```

其中 mem\_bw 是内存系统的带宽。有效带宽 mem\_bw 可以通过以下方式确定。

让我们用 off\_chip\_bw 表示 DRAM 的理论带宽规格，用 on\_chip\_bw 表示后文定义的由 BRAM 缓冲区提供的总带宽。

## 与 CNN 无关的加速器设计 173

在没有宽位数据请求和用于突发传输的顺序访问的情况下，通常无法充分利用 DRAM 设备的带宽 [6]。因此，独立并行片内缓冲区端口的数量会影响片外带宽的使用。例如，IFM 缓冲区库具有 $Tn$ 个独立端口，以便每个周期提供并行像素。相应地，IFM 瓦每个周期加载 $Tn$ 个元素，尽管片外内存可能提供更多内容。

图 8.6 显示了在 800 MHz 运行的 DDR3 DRAM 下，对于具有 128 字节小突发长度的不同片内缓冲区，所达到的带宽。所用内存的最大可用性能为 25 GB/s，内存控制器提供 1024 位宽接口。正如我们所看到的，为了在 64 位宽片内缓冲区中缓存数据，每个周期必须请求 64 位，这仅实现了 1.32 GB/s，仅为可用片外内存性能的一部分。通过增加片内带宽，可以相应增加每个周期的请求宽度并更好地利用片外带宽。这足以使宽度等于接口宽度 1,024，因为更宽的请求也可以提高突发平均值。进一步的改进需要对顺序数据进行更访问。对于特征图，突发长度由缓冲区深度表示。例如，OFM 缓冲器的最大可能突发为 $Tr \times max$。片内内存的突发访问影响包含在下一节提出的运行时模型中，假设在最大片外带宽内的所有访问都不会遇到任何停顿。

### 8.6.2.2 有效带宽延迟

我们需要同时考虑最大带宽 $off\_chip\_bw$ 和请求带宽 $on\_chip\_bw$ 来研究内存延迟。因此，(8.10) 得有效带宽 $mem\_bw$，加速器可见的形式为：

```
mem_bw = min(off_chip_bw, on_chip_bw) (8.10)
on_chip_bw = vector_size × DW × freq (8.11)
```

其中 vector\_size 是如 (8.6) 所示每个周期访问的数据元素数量。为了实现无停顿运行，我们希望 $on\_chip\_bw$ 尽可能接近 $off\_chip\_bw$。

![](img/e6e752b99eb1621488c89445a57e2a86_198_0.png)

图 8.6 数据请求宽度对所实现 off\_chip\_bw 的影响。DRAM 接口宽度为 1,024 位，突发访问长度为 128

## 174 深度学习的硬件架构

较低的 on\_chip\_bw 意味着 off\_chip\_bw 正在使用，并且内存性能有提升的空间。另一方面，较高的 on\_chip\_bw 意味着性能受内存限制，并受限于 off\_chip\_bw。随着架构扩展，on\_chip\_bw 随后超过 off\_chip\_bw 并成为瓶颈。FICC 架构考虑这种不匹配的 off\_chip\_bw 和 on\_chip\_bw，尝试调整设计。我们将 (8.7)-(8.10) 表达为单一表达式：

```
num\_cycles = num\_data\_elem \times\min(off\_chip\_bw, on\_chip\_bw) \times freq (12)
```

其中我们将 avg\_cycles\_per\_elem 表示为根据 on\_chip\_bw 计算的 $ACPE\_i$、$ACPE\_o$ 和 $ACPE\_w$ 分别对应 IFM、OFM 和权重。

### 8.6.3 分析运行时

我们将运行时周期、total\_cycles 分类为以下阶段：

- ifm\_pl\_cycles：预取 IFM 的周期
- wt\_ld\_cycles：权重的总周期
- conv\_cycles：卷积的总周期
- mem\_ld\_cycles：加载/存储 IFM 的总周期
- ofm\_ps\_cycles：存储最后的 OFM 的周期

阶段 1、2、4 和 5 是需要最小化的开销。本节其余用于这些变量。在计算之前，加载了 IFM。由于 IFM 维度由 Tr 决定（此处所示），它们是：

```
ifm\_pl\_cycles = N_{itr} \times N\_C \times Tn \times ACPE\_i (13)
```

权重加载到芯片缓冲区并从全局内存取回。这种重叠对于 IFM 是显著的：

```
wt\_ld\_cycles = M\_C \times M\_R \times N_{itr} \times Tm \times ACPE\_w (14)
```

```
bias\_cycles = M_{itr} \times Tm \times ACPE\_o (15)
```

## 与 CNN 无关的加速器设计 175

如果 8.5 的 on\_chip\_bw 周期没有产生任何停顿，则卷积的总周期可以为：

```
conv\_cycles = M\_C \times M\_R \times N_{itr} \times M_{iter} + R_{itr} \times M_{iter} (16)
```

其中第二项被循环循环。可以在卷积周期内部隐藏 IFM 加载和 OFM 存储。但为了准确估算，我们移除最后的 OFM 存储内存流量：

```
mem\_ld\_cycles = ifm\_ld\_cycles + ofm\_st\_cycles (17)
```

这些的详细信息如下。由于卷积器的步长可能小于 IFM 维度，IFM 行倾向于轻微重叠。对于 CNN 深层中较小的 IFM，如果 Tr 足够大，IFM 尺寸不需要分块。这在 Tr 上引入了另一个权衡。由于 IFM 流量很复杂，我们改为计算每个 IFM 行所需的 IFM 元素：

```
rows1 = \begin{cases} 0, & \text{如果 } R_{itr} = 1 \\ K\_R + S \times (M\_R - (R_{itr} - 1)) \times Tr) \times (R_{itr} - 2), & \text{否则} \end{cases} (18)
```

```
rows2 = K\_R + S \times (M\_R - (R_{itr} - 1)) \times Tr (19)
```

```
ifm\_ld\_cycles = N_{itr} \times N\_C \times (rows1 + rows2) \times Tn \times ACPE (20)
```

```
ofm\_ld\_cycles = M\_C \times M\_R \times M_{itr} \times (N_{itr} - 1) \times Tm \times ACPE (21)
```

