
| 抖动 | 连续数据包之间端到端传输时间的变化。 | 如果传输时间在 80 到 120 ms 之间变化，则抖动为 40 ms。 |
| :--- | :--- | :--- |
| 丢包 | 传输过程中丢失的数据包数与传输数据包数的比例。 | 1% |

每种类型的流量都需要特定的参数簇。

**表 8.2. 语音和视频 QoS 参数**

| 流量类型 | 所需参数簇 |
| :--- | :--- |
| VoIP | 输出 = 64 kbps 延迟 <= 150 ms（待验证）抖动 <= 30 ms 丢包率 = 1% |
| 视频、视频会议、流媒体 | 输出 = 从 384 kbps 到 20MB 以上 延迟 = 200 到 400 ms 抖动 = 30-50 ms 丢包率 = 0.1-1% |

除了上述可测量和可量化的参数外，对用户感知的 QoS 评估也很有用。因此，语音通信的 QoS 可以 `MOS`（平均意见分）进行评估。MOS 值范围从 1（不可接受）到 5（优秀），通过主观测试结果获得。

### 8.2.5. QoS 的通用原则

QoS 参数取决于连接容量以及交换机节点（或路由器）内部的动态队列管理。如果网络显示过载，考虑到每种类型流量在 QoS 参数方面有不同需求，则需要为每类流量设置一个队列。实现 QoS 的网络路由器必须在足够的队列中提供数据包分类功能、管理放置在同一队列中的数据包，并进行调度以控制不同类型流量对有限链路容量的共享。

![图 8.1. QoS 建立的通用原则。图的彩色版本请参见 www.iste.co.uk/helali/systems.zip](img/fig8_1.jpg)

**图 8.1. QoS 建立的通用原则。图的彩色版本请参见 [www.iste.co.uk/helali/systems.zip](http://www.iste.co.uk/helali/systems.zip)**

#### 8.2.5.1. 分类

分类是 QoS 实现的第一阶段。其原理是分析数据包以确定相应的流，从而确定适当的服务级别。分类功能由流分类器或包分类器根据特定的分类规则执行。这些规则可能引用报头或标记、端口、源和目的地址等。这一阶段至关重要，因为它实现了数据包的差异化。

数据包标记机制允许路由器区分不同的数据流类别，因此跨越设备不需要每次都对接收到的数据包进行重新分类。

#### 8.2.5.2. 队列管理

队列主要用于管理网络基础设施中的拥塞。为每个标记或类别创建一个相应的队列。

管理这些队列涉及管理器的机制，缓冲区在交换机或路由器级别是有限资源。其目标是通过决定在拥塞时拒绝哪些数据包来控制队列中数据包的数量。这意味着这是一项丢包控制函数。有多种相应的技术，包括尾包丢弃和随机早期检测（`RED`），后者在队列达到预定义阈值之前随机丢弃数据包。Cisco 开发了 `RED` 的改进变体——加权随机早期检测（`WRED`），它根据流量类别定义了多个阈值。

#### 8.2.5.3. 调度

调度涉及确定路由器输出端的数据包处理顺序。这种决策最初基于公平原则，但可能有利于某些流而损害其他流（实时应用、某些协议、特定的机器源等）。此功能对每个流的延迟和输出参数有显著影响。这样，调度器控制了服务类对有限网络资源（即带宽）的访问。可以使用多种调度技术或算法，包括但不限于：

- 严格优先级：在移动到 `n-1` 队列之前，完全处理优先级 `n` 队列；
- 轮询优先级：路由器从最高优先级队列开始，处理每个队列中的一个数据包；
- 加权优先级或加权公平队列（`WFQ`）：每个输出队列接收特定的权重。然后根据分配的权重在不同流之间共享可用带宽。

#### 8.2.5.4. 流量监管/整形

这些是用于整形和调节流量的机制，从而控制每个流量段的输出或带宽，以减少流量的突发性。

流量整形是在输入端或网络内部的操作，确保流量保持在限制范围内。它有助于避免峰值并提供准恒定流。过量流量被放在缓冲区中，并在可能时释放。

网络输入端的流量监管以不同的方式处理超过限制的流量；它通常会消除或（重新）标记这些数据包，而不会向网络引入延迟。

在 IT 基础设施中实施 QoS 需要一个准备阶段，包括：

- 识别基础设施中的流量类型及其需求；
- 确定每种流量对公司最佳活动的重要性；
- 流量进行分类；
- 定义应用于每类别的策略（最小保证带宽、最大带宽、固定优先级级别）；
- 定义采用管理拥塞的 QoS 机制（监管、整形）。

### 8.2.6. QoS 机制

QoS 是管理多媒体应用以及 IP 协议作为下一代收敛网络基础统一协议成功的关键因素。为此，提出了各种解决方案或机制，以区分网络流并对其进行适当处理。

这些机制基于两种主要方法：

- 要么让应用流适应网络容量；
- 或者通过按类别管理流组来让网络适应应用流。

#### 8.2.6.1. 在传输层

在此层级，实现了 `RTP` 和 `RTCP` 协议以管理 VoIP 和流媒体等实时应用。它们代表了第一种方法的具体化。换句话说，它们使得应用程序的流能够适应网络可用带宽：

- 在 `RTP`（实时传输协议）数据包传输数据。`RTP` 允许对数据包进行编号，从而能够检测丢包、媒体同步并识别消息内容以便在丢失时进行可能的恢复。`RTP` 传输用户数据；
- 会话质量控制（输出、丢包、抖动、延迟）由 `RTCP`（实时控制协议）数据包管理。接收端使用该协议向发送端发送包含主要服务质量参数的报告。这些信息使源能够适应状况。通过这种方式，`RTCP` 传输监控包，使网络节点能够更好地控制实时应用。

#### 8.2.6.2. 在网络层

这涉及通过管理单个流或分类流组来使网络适应应用流的特征。IETF 发布了针对此的尽力而为模型以及两种网络层 QoS 管理模型。

##### IntServ

IntServ 独立处理每个流。为了做到这一点，它使用一种名为 `RSVP`（资源保留协议）的特定信号协议。

# RSVP (资源预留协议)

RSVP 用于预留资源。它被对特定流有明确 `QoS` 要求的主机以及位于这些流路径上的路由器使用。交叉路由器的内存资源由源通过信令消息进行预留。在接收端请求后可以修改 `QoS`。`QoS` 并不集成在每个数据包中，而是与网络设备进行协商；这就是我们所说的端到端 `QoS`。`RSVP` 是一种信令或控制协议，不传输用户数据。

![图 8.2. RSVP 的基本原理。彩色版本请访问 www.iste.co.uk/helali/systems.zip](img/fig8_2.jpg)

**图 8.2.** *`RSVP` 的基本原理。彩色版本请参阅 [`www.iste.co.uk/helali/systems.zip`](http://www.iste.co.uk/helali/systems.zip)*

这种 `IntServ` 模型确保了细粒的粒度，并将每个流与其他流隔离离开。然而，它相对复杂且昂贵。它还存在扩展性问题（难以扩展到大规模场景）。它可以部署在局域网（`LANs`）上，但在服务提供商的规模上很难使用。

##### DiffServ (区分服务)

`DiffServ` 基于根据数据包的类别进行区分。`QoS` 由类进行管理并代表多个流的聚合。因此，通过源端的数据包标记定义具有不同服务质量的多个类。一旦数据包被交换机或路由器分类并标记，就会对其应用一种称为逐跳行为（`PHB`）的处理。`PHB` 识别从源到目的整个路径上每个跳点对数据包的处理方式。目前使用三种类型的 `PHB`：

- 默认 `PHB`，对应于尽力为（best effort）模型；
- `EF`（加速转发），确保每个配置了 `DiffServ` 的节点都保证延迟、抖动和数据包丢失的最小值。这种保证对于语音和视频等实时应用是必须的；
- `AF`（确保转发）提供的质量水平低于 `EF`，适用于非实时应用。

标记包括修改进入 `IPv4` 数据包的头部，以填入 `TOS`（服务类型）字段，该字段后会被图 8.3）。

![图 8.3. IPv4 头部和 TOS/DSCP 字段。彩色版本请访问 www.iste.co.uk/helali/systems.zip](img/fig8_3.jpg)

**图 8.3.** `IPv4` 头部和 `TOS`/`DSCP` 字段。彩色版本请参阅 [`www.iste.co.uk/helali/systems.zip`](http://www.iste.co.uk/helali/systems.zip)*

![图 8.4. IPv6 头部和流量类别字段。彩色版本请访问 www.iste.co.uk/helali/systems.zip](img/fig8_4.jpg)

**图 8.4.** `IPv6` 头部和流量类别字段。彩色版本请参阅 [`www.iste.co.uk/helali/systems.zip`](http://www.iste.co.uk/helali/systems.zip)*

`TOS` 字段（IP 优先级）显示如下。

![图 8.5. TOS（服务类型）字段的结构](img/fig8_5.jpg)

**图 8.5.** *`TOS`（服务类型）字段的结构*

`DSCP` 字段采用 6 位编码，与仅采用 3 位的 `TOS` 字段相比，它可以增加优先级级别的数量。

![图 8.6. DSCP（区分服务代码点）字段结构](img/fig8_6.jpg)

**图 8.6.** `DSCP`（区分服务代码点）字段结构

`DiffServ` 模型基于 `DSCP` 字段提供了更高的粒度，通过添加 3 位 `DS2`、`DS1` 和 `DS0` 对其进行精细化。前三位 `DS2`、`DS1` 和 `DS0` 定义了概率。前三位 `DS2`、`DS1` 和 `DS0` 预留用于网络控制。前三位 `DS2`、`DS1` 和 `DS0` 用于语音。前三位 `DS2`、`DS1` 和 `DS0` 用于交互式视频。前三位 `DS2`、`DS1` 和 `DS0` 用于流媒体。前三位 `DS2`、`DS1` 和 `DS0` 用于极力而。前三位 `DS2`、`DS1` 和 `DS0` 用于后台努力。这些位代表尽力为。

![图 8.4. IPv6 头部和流量类别字段。彩色版本请访问 www.iste.co.uk/helali/systems.zip](img/fig8_4.jpg)

**图 8.4.** `IPv6` 头部和流量类别字段。彩色版本请参阅 [`www.iste.co.uk/helali/systems.zip`](http://www.iste.co.uk/helali/systems.zip)*

#### 8.2.6.3 数据链路层

`802.1p` 标准使用以太网帧中的三位来分配优先级。这种 `802.1p` 机制可以对流量进行分类。在网络拥塞的情况下，高优先级帧会在低优先级帧之前传输。

![图 8.5. TOS（服务类型）字段的结构](img/fig8_5.jpg)

**图 8.5.** *`TOS`（服务类型）字段的结构*

### 8.2.6.4 应用

#### 应用 1：路由器的 QoS 配置

默认情况下，没有 QoS 机制的路由器根据先来优先（FIFO）原则以相同的方式处理所有包，但这可能会破坏某些类型关键流量的操作。

在这里，我们将使用 `MQC`（模块化质量命令行接口）方法，它具有许多优点：

- 在所有 Cisco 平台上实现了 QoS 实现的标准化，同时隐藏了底层硬件架构。通过这种方式，客户可以升级到新一代 Cisco 硬件并复制现有的 MQC 配置；
- 得益于模块化配置，可以区分分类修改和策略修改，并通过单个命令禁用 QoS 策略。一种 QoS 策略也可以应用到多个接口上。

这种方法通过三个阶段过程具体：

1. 定义流类或类映射（class-map）。此阶段定义了一组网络流量（或 MQC 术语中的类映射），使用了多种分类标准：协议、访问控制列表（`ACL`）。IP 地址、IP 优先级、`DSCP`、`IEEE 802.1p` 等。必须指定类名，以及用于设置分类标准的系列匹配命令。

命令 `router(config)#class-map match-all classname` 要求数据包必须满足所有标准才能属于该类。

命令 `router(config)#class-map match-any classname` 表示数据包只需满足设定的标准中的至少一个即可属于该类。

一旦创建了服务类，我们就开始指定具体的准则。表 8.4 提供了了一些示例。

**表 8.4.** *分类准则示例*

| **准则** | **解释** |
| --- | --- |
| `router(config-cmap)#match input-interface interface name` | 数据包必须来自设置的输入接口才能属于相应的类 |
| `router(config-cmap)#match access-group ACL number` | 相应的 ACL 决定了数据包是否属于该类 |
| `router(config-cmap)#match protocol protocol name` | 协议决定了数据包是否属于该类 |

2) 定义 QoS 策略或 `policy-map`，为每个流类分配优先级级别。策略的定义可以用于标记，也可用于带宽共享。这一阶段代表了根据公司需求对 QoS 设置的有效实施。具体而言，`class-map` 将用于应用标记、队列、抑制、调节和整形等 QoS 功能。

3) 根据需要，将开发的策略应用于相应的接口（入站或出站）。

本示例采用的架构方案见图 8.8。

![图 8.8. 我们的示例拓扑](img/fig8_8.jpg)

**图 8.8.** *我们的示例拓扑*

#### 阶段 1：创建 class-map 或流类

定义的第一个 class-map 涉及 VoIP 流量：

```
Router1(config)#class-map VOICE
Router1(config-cmap)#match protocol rtp audio
Router1(config) #exit
```

定义的第二个 class-map 用于 Web 流量：

```
Router1(config)#class-map match-any WEB
Router1(config-cmap)#match protocol http
Router1(config-cmap)#match protocol https
Router1(config) #exit
```

定义的第三个 class-map 涉及 FTP 流量：

```
Router1(config)#class-map match-any TRANSFER
Router1(config-cmap)#match protocol ftp
Router1(config-cmap)#match protocol tftp
Router1(config) #exit
```

最终结果汇总如下：

```
Router1#show class-map
Class Map match-any class-default (id 0)
Match any
Class Map match-any TRANSFER (id 1)
Match protocol ftp
Match protocol tftp
Class Map match-all VOICE (id 2)
Match protocol rtp
Class Map match-any WEB (id 3)
Match protocol http
Match protocol https
```

#### 阶段 2：创建 policy-map

使用以下命令创建一个名为 `QOSPOLICY` 的 `policy-map`：

```
Router1(config)#policy-map QOSPOLICY
Router1(config-pmap)#class TRANSFER
Router1(config-pmap-c)#bandwidth percent 10
Router1(config-pmap-c)#random-detect dscp-based
```

现在已经创建了一个名为 `QOSPOLICY` 的 `policy-map`。接下来，我们开始处理 `TRANSFER` `class-map`。通过 `bandwidth` 命令，我们为其分配至少 10% 的可用带宽。命令 `random-detect dscp-based` 是一种路由器队列管理特定的主动 WRED（加权随机早期检测）技术，用于设置根据 DSCP 值抑制数据包的决策参数。

接下来，进入 `policy-map-class` 配置模式处理 `VOICE` 流量类并分配优先级：

```
Router1(config-pmap)#class VOICE
Router1(config-pmap-c)#priority 256
```

该流量类现在将具有 256 kbps 的最大带宽且不会更多，其数据包将在其他数据包之前发送。

最后，我们配置 `WEB` 流量类：

```
Router1(config-pmap)#class WEB
Router1(config-pmap-c)#bandwidth percent 60
Router1(config-pmap-c)#random-detect dscp-based
```

通过这种方式，Web 流量从 60% 的带宽，并使用了基于 DSCP 的检测。

#### 阶段 3：应用 policy-map

我们在 `gi0/0` 接口上应用 `policy-map`：

```
Router1(config)#interface gi0/0
Router1(config-if)#service-policy output QPOLICY
```

#### QoS 策略或 policy-map 的定义

策略的定义可以用于标记，也可用于带宽共享。这一阶段代表了根据公司需求对 QoS 设置的有效实施。具体而言，`class-map` 将用于应用标记、队列、抑制、调节和整形等 QoS 功能。

```
Switch(config-if)#mlsqos cos 3 override
```

然后该端口将所有帧（无论是否标记）的 `COS` 值定义为 3。因此，之前配置的信任值将被忽略。
