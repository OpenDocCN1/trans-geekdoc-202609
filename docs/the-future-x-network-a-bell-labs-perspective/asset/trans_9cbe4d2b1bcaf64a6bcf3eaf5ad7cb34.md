
虽然南北向面向 WAN 的流量在枢纽位置明显小于东西向流量，但 WAN 基础设施的基本成本结构要求这些链路在不损害这些 WAN 链路所承载的海量虚拟连接的 QoS 的前提下实现高度利用。WAN 利用率的优化一直是 Web 规模提供商在其广域 DCI 网络中使用 SDN 的主要动机。我们设想的未来网络操作系统将再次在 DCI 网络的演进中发挥关键作用，利用网络资源的集中视图，跟踪和协调流量需求，并优化网络中流和流聚合的容量使用。这些控制依赖于数据路径中的流量管理功能（例如，队列、策略、整形），以确保每个受管聚合流类和 VPN 的 QoS。在数据中心交换/WAN 边界以规模化方式实现这一点，需要比通用数据中心交换机所具备的能力和广域路径控制更强大的功能。因此，一系列新的高吞吐量、低延迟、针对 WAN 优化的交换机将出现，以补充通用数据中心交换机，用于面向 WAN 的流量接口。

利用上述所述的能力组合，新的网络“边缘云”数据中心集合将成为智能枢纽，其余网络将围绕其构建。

![](images/fig4_19.jpg)

## 可扩展、灵活且自适应的光学
互连所有这些大型数据中心枢纽以及集中式的 Web 规模数据中心，将需要光网络的数量级扩展，并带来相应的规模经济。实现满足动态需求所需的网络可编程性水平，还要求光传输具有更大程度的动态灵活性。以下关键创新将是实现这些需求在明天可调网络结构基础层中的关键。

## 超可扩展光网络
当前光纤光传输系统已利用光的振幅、相位和偏振来编码和传输数据。并且使用这些方法，光纤每单位频率的最大信息密度，或光谱效率——即所谓的“非线性香农极限”——正如 [图 19](#10-9781315365756_chapter-chap4.xhtml#fig4_19) (Winzer 2014) 所示，已达到极限。

当前采用约 100 个激光频率和约 30 Gbaud 数据调制速率的 DWDM 可在长距离传输中实现超过 10 Tb/s 的容量。实现超过该容量 10 倍以上的进一步增益将需要利用尚未耗尽的两个剩余物理维度——频率和空间。频率（波长）空间的经济高效扩展将由超宽带光放大器、收发器和波长转向组件实现，从而允许在低光纤损耗窗口中相邻于传统“C”波段的更具挑战性的较长和较短波长“L”和“S”波段中使用 DWDM 操作（[图 20](#10-9781315365756_chapter-chap4.xhtml#fig4_20) \[Winzer 2014\])。由此产生的系统容量随（光）频谱使用量的增加而直接扩展，导致容量增长潜力为三到五倍，在使用完整传输窗口的无放大跨距中可能获得更大的增益。

然而，对于每个可用波长，最大化传输速率仍然很重要，以最大化光传输系统的总吞吐量。尽管如此，我们几乎已达到实现复杂高阶调制方案所需的数字信号处理速度的极限，因此需要采用替代方法，使用多个并行载波进行低阶调制并更高效地使用频谱以实现 1 Tb/s 速率。或者，我们可以并行使用多个空间路径。这两种方法都是被称为“超通道”的形式。

存在两种主要的超通道类型，如 [图 21](#10-9781315365756_chapter-chap4.xhtml#fig4_21) 所示。

**光谱超通道** — 利用比传统 50 GHz 更小的载波频率间隔（通常为“FlexGrid” 6.25 GHz 间隔的倍数，例如 12.5 GHz），每个子载波以较低速率调制以实现目标总速率并达到预期经济性。[图 22](#10-9781315365756_chapter-chap4.xhtml#fig4_22) 显示了三个 Tb/s 示例，说明了符号速率与子载波数量之间的不同权衡点。

**空间超通道** — 是一种空间分复用（SDM）形式，其中传输通过多个并行的物理光纤进行（多模光纤内部的多个独立光路或光学模式），允许数据通过多条并行光纤路径传输以实现两点之间所需更高的总体速率。与传统的波分复用（WDM）加光谱超通道方法相比，采用这种 SDM 方法需要对光收发器、放大器和其他组件进行大规模集成以推动规模经济，如 [图 23](#10-9781315365756_chapter-chap4.xhtml#fig4_23) 所示。

## 按需自适应城域
虽然核心光网络要求整体可扩展性和相对粗略的灵活性水平，但连接边缘云和企业城域光网络必须针对不同时间流量更大规模的变化进行优化。为解决这一需求，新的弹性光网络技术将出现，结合分组技术的动态带宽灵活性与光层传输的成本效益。两种方法可能在未来被采用：
1 Using new “optical-Ethernet” switching approaches to efficiently inspect and forward flows based on (simple forwarding) information that resides between the optical and the Ethernet layers
2 Elastically varying the amount (width) of spectrum used for each optical path based on demand by using intelligent, auto-tuned “coherent optical modems” that autonomously adjust signal modulation and therefore the rate of each wavelength to achieve the highest capacity operation possible over the fiber span. Such dynamic rate-reach adaption will also be important in core DWDM optical systems, allowing capacity to be optimized as paths dynamically change due to restoration and optimization actions.

![](images/fig4_20.jpg)
![](images/fig4_21.jpg)
![](images/fig4_22.jpg)
![](images/fig4_23.jpg)

从以上内容可以明显看出，将采用各种不同的技术和技术来创建跨光域和 IP 域的可调网络结构。然而，还有另一个潜在优化维度可能会在 IP 层之上发生，如下一节所述。

## 内容路由
虽然可调网络结构可以按需为任何端点提供弹性带宽到几乎任何端点，但通过明智地将信息和内容缓存得更靠近用户，可调网络结构的效率有可能得到改善。这是当今内容分发网络（CDNs）的原理，其被设计为 IP 层之上的叠加服务，使用 DNS 和 HTTP 重定向等技术将请求定向到最佳本地缓存。
