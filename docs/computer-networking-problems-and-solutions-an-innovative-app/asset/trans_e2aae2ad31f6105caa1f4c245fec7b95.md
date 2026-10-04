

Simpson, William A., Dr. Thomas Narten, Erik Nordmark, and Hesham Soliman. *邻居发现协议用于 IP 版本 6 (IPv6)*. Request for Comments 4861. RFC Editor, 2007. doi:10.17487/RFC4861.

Troan, Ole, and Ralph Droms. *用于动态主机配置协议版本 6 (DHCP) 的 IPv6 前缀选项*. Request for Comments 3633. RFC Editor, 2003. doi:10.17487/RFC3633.

Zeng, Shengyou, John Jason Brzozowski, Kim Kinnear, and Bernie Volz. *DHCPv6 Leasequery*. Request for Comments 5007. RFC Editor, 2007. doi:10.17487/RFC5007.

### Review Questions

1\. 考虑本章讨论的四种解决层间发现和映射问题的方法。构建一个图表描述每种方法的状态和表面交互，以及可能的优化权衡。

2\. 描述 IETF 用于维护号码注册表的过程。这看起来像是一个复杂系统还是一个简单系统？看起来它是否能有效确保标识符的唯一性？

3\. 考虑每天可能有数百万，甚至数亿次 DNS 查询。DNS 根服务器有多少个？鉴于这两个数字，你认为 DNS 系统是如何扩展以支持整个全球互联网的？

4\. 是否可以将一个全球可达的 IP 地址转换为 DNS 名称（与本章描述的方向相反进行映射）？你能想到一个这会很有用的例子吗？

5\. 更大的 DNS 系统还包含一个从 DNS 名称到有关域名所有权的人类可读信息的映射系统，称为 whois。它使用什么协议进行通信，信息存储在哪里，通过该系统可以获得哪些信息？

6\. 解释 DNS 胶水记录是什么以及它们用于什么。

7\. 从状态、优化和表面的角度来看，像 DHCP 这样的机制与像 SLAAC 这样的机制之间有什么权衡？不仅要考虑地址分配的便捷性，还要考虑每种机制可能出现的任何安全和控制问题。

8\. 为什么大多数实现默认不会启用代理 ARP？启用代理 ARP 的风险是什么？

9\. 邻居发现协议端系统到中间系统协议 End System to Intermediate System (ES-IS) 与 IPv6 ND 相比如何？

10\. 考虑 IPv6 路由器发现相对于默认网关问题的工作方式。

[1](#ch06.xhtml#ch06fn1). 该图表取自 [https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)。

[2](#ch06.xhtml#ch06fn2). Johnson and Narten, *基于 UUID 的 DHCPv6 唯一标识符 (DUID-UUID) 的定义*。

[3](#ch06.xhtml#ch06fn3). Liu et al., “DHCPv6/SLAAC 交互在地址和 DNS 配置上的问题。”

## Chapter 7
### Packet Switching

**Learning Objectives**

阅读本章后，你应该能够理解：

![Image](graphics/bull.jpg)将数据包通过网络设备切换所需的四个步骤

![Image](graphics/bull.jpg)接收和发送环在转发数据包过程中的使用方式

![Image](graphics/bull.jpg)数据包切换的基本过程，包括转发表是如何构建的

![Image](graphics/bull.jpg)路由与交换的区别以及路由的优势

![Image](graphics/bull.jpg)等价多路径的概念

![Image](graphics/bull.jpg)链路聚合的概念

![Image](graphics/bull.jpg)总线概念和交叉开关结构的概念

网络设备被插入网络以解决许多问题，包括连接不同类型的介质以及通过仅在需要的地方携带数据包来扩展网络。然而，路由器和交换机本身就是复杂的设备；工程师可以通过专门解决在数据包通过网络设备传输过程中遇到的仅一小部分问题来建立整个职业生涯。

[Figure 7-1](#ch07.xhtml#ch07fig01) 用于讨论问题空间的概述。

![Image](graphics/07fig01.jpg)

**Figure 7-1** *将数据包通过网络设备移动*

在 [Figure 7-1](#ch07.xhtml#ch07fig01) 中，有四个不同的步骤：

1\. 数据包需要从物理介质复制到设备内的内存中；这有时被称为将数据包从线路上时钟化。

2\. 数据包需要被处理，这通常意味着确定正确的出站接口并以任何必要的方式修改数据包。例如，在路由器中，底层头会被剥离并替换为新的头；在有状态数据包过滤器中，数据包可能基于内部状态被丢弃；等等。

3\. 数据包需要从入站复制到出站接口。这通常涉及跨内部结构或总线的传输。一些系统通过使用单一内存池用于入站和出站接口来跳过此步骤；这些被称为共享内存系统（你会注意到网络工程中事物的名称要么太巧妙，要么太明显）。

4\. 数据包需要复制回出站物理介质；这有时被称为将数据包时钟化到线路上。

**Note**

较小的系统，特别是那些专注于快速、一致的数据包交换的系统，通常会使用共享内存将数据包从一个接口传输到另一个接口。复制数据包到内存所需的时间通常大于接口运行的速度；共享内存系统避免了这种数据包的内存复制。

因此，下面各节讨论的问题空间在于：

**网络设备需要转发的包是如何从入站物理介质携带到出站物理介质的，以及包如何在此路径上暴露给处理？**

以下每个部分讨论此问题的解决方案的一部分。

### Physical Media to Memory

数据包通过网络设备处理的第一步是将数据包从线路复制到内存中。[Figure 7-2](#ch07.xhtml#ch07fig02) 用于说明该过程。

![Image](graphics/07fig02.jpg)

**Figure 7-2** *将数据包时钟化到内存中*

[Figure 7-2](#ch07.xhtml#ch07fig02) 中有两步：

**Step 1.** 物理介质芯片组（*PHY 芯片*）会将来自物理介质的每个时间（或逻辑）时隙，即代表单个数据位，复制到一个内存位置。该内存位置实际上映射到一个接收环中，该接收环是一组内存位置（数据包缓冲区），专门用于接收从线路上时钟化的数据包。接收环以及所有数据包缓冲区内存通常是从一种可被接收端线路卡或设备上的所有交换组件访问（共享）的单一内存中划分出来的。

**Note**

环形缓冲区是基于单个指针使用，该指针在每次将新数据包插入缓冲区时递增。例如，在 [Figure 7-2](#ch07.xhtml#ch07fig02) 中显示的环中，指针将从槽 1 开始，并在数据包被复制到环形缓冲区时递增通过各槽。如果指针到达槽 7，并且有新数据包到达，数据包将被复制到槽 1——无论槽 1 的内容是否已被处理。

在数据包交换中，最耗时且最困难的任务是从一个位置复制数据包到另一个位置；这通过使用指针尽可能避免。数据包在内存中移动，而不是移动数据包本身，指向内存位置的指针在交换路径内的进程之间传递。

