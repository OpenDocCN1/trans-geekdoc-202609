
### Step 3.
定期地，发送代码会将数据包从输出队列移动到发送环。从输出队列中取出数据包的顺序将取决于 `QoS` 配置；有关 `QoS` 如何在各种情况下应用于队列的更多信息，请参阅 Chapter 8，“Quality of Service”。

### Step 4.
在数据包被移动到发送环之后的一段时间内，发送 `PHY` 芯片会从数据包缓冲区读取每一位，将其编码为适合出站物理介质类型的格式，并将数据包复制到线路上。

## 关于分组交换的最终思考

分组交换的细节可能看起来陷入琐碎。毕竟，数据包或帧在两个设备之间如何移动是否真的重要？是否真的那么关键去理解串行化和反串行化、等价成本多路径、交叉开关结构争用、发送环等？

从某种意义上说，这些细节对普通网络工程师并不重要。当网络设备正在执行其通过自身移动数据的任务时，交换机为完成该任务所遵循的实际过程都是微不足道的。“它就是能工作。”

然而，交换内部结构通常在很大程度上影响网络设计。例如，考虑端口到端口延迟。在某些高流量网络中，交换机将帧从入口端口移动到出口端口所需的时间会影响整体应用性能。在现代交换机中，端口到端口延迟以单个微秒或数百纳秒来衡量。如果一台交换机在 1 微秒内完成工作，而另一台可以在 400 纳秒内完成，这可能会影响硬件选择。

另一个考虑因素是故障排除。当网络设备似乎没有转发其接收到的所有数据包时，即入口大于出口，会发生什么？网络结构中少量数据包丢失很难追踪。了解网络设备的内部分组交换过程能极大地揭示故障可能发生的位置。

因此，不要将分组交换视为对有志于网络的人来说“过于接近线路”而无关紧要。相反，应拥抱对分组交换的了解，以获得其提供的对整体网络性能的深刻见解。

## 进一步阅读

“1.5. Basics of How Operating Systems Work.” *Operating Systems Study Guide*. Accessed April 22, 2017. [`faculty.salina.k-state.edu/tim/ossg/Introduction/OSworking.html`](http://faculty.salina.k-state.edu/tim/ossg/Introduction/OSworking.html).

Bollapragada, Vijay, Russ White, and Curtis Murphy. *Inside Cisco IOS Software Architecture*. Indianapolis, IN: Cisco Press, 2000.

*BSTJ 18: 1. January 1939: Crossbar Dial Telephone Switching System. (Scudder, F. J.; Reynolds, J. N.)*, 1939. [`archive.org/details/bstj18-1-76`](http://archive.org/details/bstj18-1-76).

“Cisco Nexus 5548P Switch Architecture.” *Cisco*. Accessed July 29, 2017. [`www.cisco.com/c/en/us/products/collateral/switches/nexus-5548p-switch/white_paper_c11-622479.html`](http://www.cisco.com/c/en/us/products/collateral/switches/nexus-5548p-switch/white_paper_c11-622479.html).

“Fast Ethernet | Integrating 100mbps into Existing 10mbps Networks.” *Savvius*. Accessed April 22, 2017. [`www.savvius.com/resources/compendium/fast_ethernet/overview`](https://www.savvius.com/resources/compendium/fast_ethernet/overview).

Heineman, George T., Gary Pollice, and Stanley Selkow. *Algorithms in a Nutshell: A Practical Guide*. 2nd edition. O’Reilly Media, 2016.

Inniss, Daryl, and Roy Rubenstein. *Silicon Photonics: Fueling the Next Information Revolution*. 1st edition. Morgan Kaufmann, 2016.

“Intel Ethernet Switch Family Hash Efficiency.” Intel, April 2009. [`www.intel.com/content/dam/www/public/us/en/documents/white-papers/ethernet-switch-hash-efficiency-paper.pdf`](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/ethernet-switch-hash-efficiency-paper.pdf).

“Interrupt.” *Wikipedia*, Accessed February 3, 2017. [`en.wikipedia.org/w/index.php?title=Interrupt&oldid=763436239`](https://en.wikipedia.org/w/index.php?title=Interrupt&oldid=763436239).

Kloth, Axel K. *Advanced Router Architectures*. Boca Raton, FL: CRC Press, 2005.

Konheim, Alan G. *Hashing in Computer Science: Fifty Years of Slicing and Dicing*. 1st edition. Wiley-Interscience, 2011.

Lekkas, Panos. *Network Processors: Architectures, Protocols and Platforms*. 1st edition. New York: McGraw-Hill Education, 2003.

Meiners, Chad R., Alex X. Liu, and Eric Torng. *Hardware Based Packet Classification for High Speed Internet Routers*. 2010 edition. New York: Springer, 2010.

Noubir, Guevara. “Signal Encoding Techniques.” Accessed April 22, 2017. [`www.ccs.neu.edu/home/noubir/Courses/CS6710/S12/slides/signals-encoding.pdf`](http://www.ccs.neu.edu/home/noubir/Courses/CS6710/S12/slides/signals-encoding.pdf).

Stringfield, Nakia, Russ White, and Stacia McKee. *Cisco Express Forwarding*. 1st edition. Indianapolis, IN: Cisco Press, 2007.

Thakur, Dinesh. “Encoding Techniques and Codec.” *Computer Notes*. Accessed April 22, 2017. [`ecomputernotes.com/computernetworkingnotes/communication-networks/encoding-techniques-and-codec`](http://ecomputernotes.com/computernetworkingnotes/communication-networks/encoding-techniques-and-codec).

“Understanding IEEE 802.3ad Link Aggregation—Technical Documentation—Support—Juniper Networks,” March 26, 2013. [`www.juniper.net/documentation/en_US/junose14.2/topics/concept/802.3ad-link-aggregation-understanding.html`](https://www.juniper.net/documentation/en_US/junose14.2/topics/concept/802.3ad-link-aggregation-understanding.html).

## Review Questions

1. What happens if one end of a link is configured as a bundle and the other end is not? Specifically, what happens if one device thinks `STP` is running and the other does not?

2. Why is flow hashing typically used as opposed to round-robin as a forwarding algorithm in `ECMP`?

3. What is the purpose of a multistage fabric? Provide an example.

4. 简要总结交叉开关结构中用于缓解竞争的技巧。

5. `iSLIP` 算法有请求、授权和接受三个步骤。请用一句话分别说明每个步骤发生了什么。

6. `iSLIP` 需要运行多少次后才不再有效于改善输入到输出的匹配？

7. 一次可以在发送环上放置多少个数据包？

8. 为什么不把发送和接收环做得足够大，以防止任何数据包因环形缓冲区中的数据包未被及时处理而被覆盖？在交换机吞吐速度、内存利用率和其他因素方面有哪些权衡？

9. 研究并描述广播风暴对网络的影响。路由如何防止广播风暴？

10. 使用 `MLAG` 构建非常大、扁平且无需路由的网络有哪些优点？有哪些缺点？

# 第 8 章

## 服务质量

### 学习目标

阅读本章后，你应该理解：

![Image](img/bull.jpg)即使网络带宽充足，为什么网络中仍需要服务质量

![Image](img/bull.jpg)流量是如何被分类的，以及为什么分类通常尽可能少地进行

![Image](img/bull.jpg)服务质量、服务类别和服务类型之间的关系

![Image](img/bull.jpg)`ToS` 标记如何在数据包中携带

![Image](img/bull.jpg)什么是 `QoS` 信任边界

![Image](img/bull.jpg)`ToS` 标记，以及在网络边界处这些标记的转换

![Image](img/bull.jpg)抖动及其对应用的影响

![Image](img/bull.jpg)队列中的公平性

在普通的日子里，高速公路足够宽，可以容纳旅行者。车道足够多。限速设定为让交通快速通过该区域。车辆数量并不过多。这条高速公路上的车辆有效移动，沿着道路行驶，无需争抢位置、猛踩刹车、穿梭于车道之间，或以其他方式应对过量交通。也就是说，在普通的日子里。

这不是一个普通的日子。在这一天，总统要来访。总统要发表演讲，许多人想听这场演讲。随着总统演讲的时间临近，这条通常有效的高速公路的交通量增加。起初，这不是问题。高速公路很少达到容量，因此交通量的增加是可以管理的。确实，道路上的车辆更多了，它们行驶得更近。但这并没有造成任何问题。

随着白天的推移，总统演讲的时间越来越近，交通量再次增加。现在，出现了问题。高速公路已无法承载试图通过它的交通量。并入高速公路的车辆发现自己被困在匝道入口的车队中。其他车辆被困在高速公路上，虽然在移动，但速度非常慢。一些车辆放弃使用高速公路，掉头回家，希望通过电视或直播观看总统演讲。

总统的车队从区域机场驶向演讲现场。他们的车辆也受到了拥堵高速公路的影响。然而，总统的车队比道路上任何其他车辆都拥有更多的一种东西——重要性。为了表明其重要性，他们打开了紧急灯。警察护送车辆、总统保护 detail、豪华轿车和威胁应对卡车都闪烁着红蓝灯。

挣扎的高速公路交通让路，总统的车辆向前冲，沿着优先车道驶向演讲现场。并非每个人都能赶上演讲，但总统不能被交通所困。无论高速公路多么超载，总统都必须通过。总统是发表演讲的人。

### 定义问题空间

网络工程师经常面临的难题是流量太多而链路太小。特别是，在几乎每条网络路径中，一条链路限制了整条路径，就像一个路口或一条道路限制了交通流量一样。Figure 8-1 进行了说明。

![Image](img/08fig01.jpg)

**Figure 8-1** *网络路径中的拥塞瓶颈*

在 Figure 8-1 中，A 与 G 通信，B 与 E 通信。如果这对设备中的每一对都使用其本地链路 \[A,C\]、\[B,C\]、\[F,G\] 和 D,E\] 接近可用带宽，假设所有链路速度相同，则 \[C,D\] 链路将被流量淹没，成为网络中的瓶颈。

当链路发生拥塞时，例如 Figure 8-1 中的 \[C,D\] 链路，则需要发送到链路的流量超过了链路的承载能力。在拥塞期间，路由器或交换机等网络设备必须确定应转发哪些流量、应丢弃哪些流量，以及数据包应按什么顺序转发。已经构建了各种优先级方案来解决这一挑战。

通过优先处理某些流量类别来管理链路拥塞，属于服务质量 `QoS` 的广泛范畴。网络工程师对 `QoS` 的认知因多种原因而存在问题。例如，许多实现，即使是最近的，也往往考虑得不够周全，尤其是在配置和维护方式上。此外，早期的方案并不总是有效，`QoS` 往往会增加网络的问题，而不是缓解它们，并且通常很难排查。

由于这些原因，以及实现优先级方案所需的配置趋向于晦涩难懂，`QoS` 通常被认为是一门黑暗艺术。要成功实施 `QoS` 策略，你必须对流量进行分类，为各种流量类别定义排队策略，并在可能出现链路拥塞的所有网络设备上一致地安装该策略。

虽然有可能陷入 `QoS` 方案和实现的众多特性和功能中，但结果始终应该是相同的。总统必须及时发表演讲。

#### 为什么不只是把链路做得足够大？

在思考 `QoS` 的价值主张后，一个明显的反应是想知道为什么网络工程师不简单地把链路做得足够大以避免拥塞。毕竟，如果链路足够大，拥塞就会消失。如果拥塞消失了，那么优先处理一种流量类型而非另一种的需求也会消失。所有流量都会被交付，所有这些因带宽不足而产生的讨厌问题都会被消除。的确，过度配置或许是最好的 `QoS`。

遗憾的是，过度配置策略并不总是可用的选择。即使是这样，最大的链路也无法克服某些流量模式。某些应用在传输数据时会使用尽可能多的可用带宽，从而为共享链路的其他应用造成拥塞点。其他应用会以微突发的方式传输，在短时间内压倒网络资源，而某些传输机制——例如传输控制协议 `TCP`——会故意偶尔拥塞一条路径以确定最佳发送速率。虽然更大的链路可以减少拥塞条件存在的时间，但在某些场景下，没有足够的带宽来满足所有需求。

大多数网络都是基于超额订阅模型构建的，其中在某些瓶颈处共享更大的聚合带宽。例如，一个繁忙数据中心中的机架顶（`ToR`）交换机可能面向主机有 48x10GbE 端口，但面向数据中心其余部分只有 4x40GbE 端口。这导致超额订阅比例为 480:160，简化后为 3:1。隐含地，面向数据中心的 160Gbps 带宽是面向主机 480Gbps 带宽的潜在瓶颈——拥塞点。然而，3:1 的超额订阅比例在数据中心交换设计中很常见。为什么？

最终的答案通常是金钱。设计一种边缘端口与可用带宽相匹配的网络通常是可行的。例如，在上述数据中心结构中，几乎肯定可以增加足够的链路容量以提供从 `ToR` 到结构中的 480Gbps，但成本可能非常高昂。网络工程师需要考虑的不仅是端口和光纤的成本，还包括额外功耗的成本，以及在添加必要设备后控制环境所需的额外制冷成本，甚至是额外的机架空间和楼面承重成本。

如果网络或结构很少拥塞，花钱提供更高的结构带宽也可能难以证明其合理性。某些拥塞事件发生的频率不足以证明昂贵的网络升级是合理的。一个城市会花费数百万甚至数十亿美元改善交通基础设施，只为缓解政客一年来一次访问时的交通吗？不会。相反，会做出其他调整来处理交通问题。

例如，公司在广域网中可能最强烈地感受到这种限制，其中链路是从服务提供商（`SPs`）租用的。`SPs` 通过为无法自行建设和运营长距离光纤电缆的组织连接不同的地理区域来赚钱。这些长途链路通常提供的带宽远低于单个校园或甚至单个建筑物内的较短、本地链路。校园或数据中心内的高速链路很容易压倒较慢的长途链路。

组织会将长途（如站点间，甚至洲际）链路按合理可能的大小进行配置，但再次需要记住的关键是金钱。`SPs` 向其他组织提供的长途链路是一项昂贵、通常重要且经常受到审查的预算项目。租用的带宽越多，成本往往越高。其结果是巨大的超额订阅，即与校园或数据中心内部可用的速度相比，`WAN` 链路在带宽上受到极大限制。

在一个存在超额订阅和由此产生的拥塞点，以及需要仔细管理的临时流量模式的世界里，`QoS` 流量优先级方案始终是必需的。

### 分类

`QoS` 优先级方案作用于不同的流量类别，但什么是流量类别，又是如何定义的？
