

Graceful Restart (GR) 和 ISSU 依赖于设备在控制平面重启期间能够在硬件中转发流量；硬件必须能够保存转发表，并在控制平面将新的路由信息输入转发表之前转发数据包。在没有控制平面的情况下转发存在一定的风险，因为在控制平面重启期间网络拓扑可能会发生变化，导致在控制平面重新收敛之前出现环路。这是由于拓扑不同步的数据库而导致微环路发生的又一个实例。

每种解决方案都有其优点和缺点——每种方案在某些情况下适用，而在其他情况下不适用——但工程师应了解这些工具及其在构建弹性网络问题上的应用。

### 双平面和多平面核心

虽然很少使用，但双平面和多平面核心有时会被部署以确保最高级别的可用性。 [Figure 23-6](#ch23.xhtml#ch23fig06) 说明了这两种类型的核心。

![Image](graphics/23fig06.jpg)

**Figure 23-6** *Dual and Multiplanar Cores*

在 [Figure 23-6](#ch23.xhtml#ch23fig06) 中，每个核心都用不同类型的虚线表示，以便更容易看到两个核心。在这两种核心类型中，*一切*都是不同的：

• 使用来自两个不同厂商的设备，或至少使用两条不同的硬件线路，使用两种不同的协议实现，以防止单个错误或一种故障影响整个网络。

• 使用两种不同的内部网关协议，例如开放最短路径优先 OSPF 和中间系统到中间系统 IS-IS，各自用于一个核心，以便单个协议的问题不会影响整个网络。

• 与两个不同的提供商签订合同，为每个核心提供站点之间的链路。

通过创建两个完全独立的核心，可以避免与单一文化或允许问题在整个网络中传播的错误相关的问题。

这两种核心类型的主要区别在于分流链路，在 [Figure 23-6](#ch23.xhtml#ch23fig06) 右侧的多平面核心图示中以破折号点表示，例如 C 和 D 之间的曲线链路。这些分流链路被设置为非常高的度量值，因此只有在没有其他路径可用时才会被用于转发流量。外部网关协议，例如边界网关协议 BGP，用于将整个网络连接在一起；每个站点边缘路由器，例如 A，都将拥有到网络中任何给定目的地的两条路由。其中一条是通过一个核心通过 BGP 学习到的，第二条是通过第二个核心通过 BGP 学习到的。

### 模块化和弹性

MTTR 可以分解为两个部分：

• 网络恢复所有可达目标之间转发流量的时间

• 将网络恢复到原始设计和操作状态所需的时间

第一个定义与机器级信息过载有关；控制平面中的信息越少，网络收敛速度越快。第二个与操作员信息过载有关；配置越一致，理解网络应该是什么样子的越容易，操作员找到和定位任何网络问题的速度就越快。MTTR 与模块化之间的关系如 [Figure 23-7](#ch23.xhtml#ch23fig07) 所示。

![Image](graphics/23fig07.jpg)

**Figure 23-7** *Modularization Tradeoff with MTTR*

从单一的扁平故障域转向更模块化的设计，找到和修复网络中的问题所需的时间会迅速减少，从而降低 MTTR。然而，有一点额外的模块化开始增加 MTTR，即将网络划分为更小的域会导致网络变得更复杂。为了理解这种现象，请考虑这样一种网络，其中每个网络设备，例如路由器或交换机，都成为其自身的故障域（想象一个完全使用静态路由且没有动态路由协议配置的网络）。很容易看出这种情况下与单一大型扁平故障域的情况没有区别。如何找到 MTTR 曲线上的正确点？答案总是“视情况而定”，但制定一些通用规则很重要。

*首先*，任何给定故障域的正确大小永远不会是整个网络（除非网络真的非常小）。几乎任何规模的网络都可以，也应该被划分为一个以上的故障域。

*其次*，给定故障域的正确大小总是会取决于控制平面协议的进步、处理能力的提升和其他因素。在网络世界中，关于 OSPF 区域的最佳大小存在长期的激烈争论。单个路由器能处理多少条 LSA？SPF 在给定大小的数据库上运行有多快？经过多年的优化 OSPF 运行方式的工作，以及平均路由器处理能力的提升，这一争论通常已被事件所克服。

随着技术的改进，单个故障域的最佳大小会随时间增加。随着网络规模的扩大，单个网络中最佳故障域数量往往保持不变。这两种趋势往往相互抵消，因此大多数网络在其生命周期中故障域的数量大致相同，即使它们随着业务不断增长的需求而增长和扩展。

那么多大算太大？从基本规则开始：围绕策略要求构建模块并将复杂性与复杂性分离。在围绕这两件事划定界限并根据业务单元、地理位置和其他因素添加自然边界之后，你就有了确定故障域边界应放置位置的坚实起点。

从这一点出发，考虑哪些服务需要比其他服务更隔离，仅仅是为了提高其生存能力，并查看网络的性能指标，以确定是否存在过大故障域。

### 关于弹性的最终思考

虽然冗余是工程师构建网络弹性时的“首选工具”，但冗余的管理负面方面与正面方面一样多。弹性需要的不仅仅是冗余链路和设备；它必须包括许多其他技术，涉及整个网络栈，从物理链路，通过控制平面，到应用程序本身。

弹性，如同安全一样，必须构建到网络中，而不是在最后才附加上去。

### 进一步阅读

Papadimitriou, Dimitri. “Inference of Shared Risk Link Groups.” Internet-Draft. Internet Engineering Task Force, November 2001. [https://datatracker.ietf.org/doc/html/draft-many-inference-srlg-02](https://datatracker.ietf.org/doc/html/draft-many-inference-srlg-02).

Pillay-Esnault, Padma, and John Moy. *Graceful OSPF Restart*. Request for Comments 3623. RFC Editor, 2003. [https://rfc-editor.org/rfc/rfc3623.txt](https://rfc-editor.org/rfc/rfc3623.txt).

Rekhter, Yakov, and Rahul Aggarwal. *Graceful Restart Mechanism for BGP with MPLS*. Request for Comments 4781. RFC Editor, 2007. [https://rfc-editor.org/rfc/rfc4781.txt](https://rfc-editor.org/rfc/rfc4781.txt).

Rekhter, Yakov, John Scudder, Srihari S. Ramachandra, Enke Chen, and Rex Fernando. *Graceful Restart Mechanism for BGP*. Request for Comments 4724. RFC Editor, 2007. [https://rfc-editor.org/rfc/rfc4724.txt](https://rfc-editor.org/rfc/rfc4724.txt).

Torrell, Wendy, and Victor Avelar. “Mean Time Between Failure: Explanation and

