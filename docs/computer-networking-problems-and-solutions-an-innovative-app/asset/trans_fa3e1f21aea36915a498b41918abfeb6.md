

在网络工程的世界里没有绝对的真理；如果你还没有找到权衡取舍，那只是因为你还没有足够深入地思考。这同样适用于选择何时何地进行集中化，以及何时何地进行分散化。这些选择往往被呈现为非此即彼的绝对选择，但现实是，不同的问题通常需要不同的解决方案。

就控制面在现实世界中必须解决的众多不同问题而言，集中化与分布化为网络和协议设计者提供了一系列权衡。考虑到这两种提供可达性和拓扑信息的方式时，一系列可能的解决方案是显而易见的；例如：

- 将可达性和拓扑发现集中到一组分布式控制器中，*取代*分布式控制面而采用集中式控制面。这种模型并不真正假设一个“集中式”控制面，而更像是将关于网络发现的信息处理从单个交换设备中移除。信息在多个设备间的分布在创建弹性设计时仍然是关键。
- 集中控制面功能的某部分，通常是策略，并将剩余部分进行分布。`PCEP`、`I2RS`以及许多其他“覆盖”控制面都采用这种路线。
- 将控制面的所有组件都分散化，包括可达性、拓扑和策略下发。实际上，完全以这种方式分散化的大规模网络非常少；通常至少有一部分策略是集中的。

最终，控制面在现实世界中提出的问题并没有简单的答案。在复杂性理论所暗示的三方权衡（`state`、`optimization`和`surface`）与`CAP`定理（`consistency`、`accessibility`和`partitioning`）之间，设计者在构建网络和协议时可以做出广泛的选择。

明智选择。

### 进一步阅读

Atlas, Alia, David Ward, and Thomas Nadeau. *Problem Statement for the Interface to the Routing System*. Request for Comments 7920. RFC Editor, 2016. [https://rfc-editor.org/rfc/rfc7920.txt](https://rfc-editor.org/rfc/rfc7920.txt)。

Bjorklund, Martin. *The YANG 1.1 Data Modeling Language*. Request for Comments 7950. RFC Editor, 2016. [https://rfc-editor.org/rfc/rfc7950.txt](https://rfc-editor.org/rfc/rfc7950.txt)。

Bosnich, David A. “The Principle of Subsidiarity.” *Religion & Liberty* 4, no. 4 (July 2010). [https://acton.org/pub/religion-liberty/volume-6-number-4/principle-subsidiarity](https://acton.org/pub/religion-liberty/volume-6-number-4/principle-subsidiarity)。

Clarke, Joe, Gonzalo Salgueiro, and Carlos Pignataro. *Interface to the Routing System (I2RS) Traceability: Framework and Information Model*. Request for Comments 7922. RFC Editor, 2016. [https://rfc-editor.org/rfc/rfc7922.txt](https://rfc-editor.org/rfc/rfc7922.txt)。

Doria, Avri, Ligang Dong, Weiming Wang, Hormuzd M. Khosravi, Jamal Hadi Salim, and Ram Gopal. *Forwarding and Control Element Separation (ForCES) Protocol Specification*. Request for Comments 5810. RFC Editor, 2010. [https://rfc-editor.org/rfc/rfc5810.txt](https://rfc-editor.org/rfc/rfc5810.txt)。

Hares, Susan, and Mach Chen. “Summary of I2RS Use Case Requirements.” Internet-Draft. Internet Engineering Task Force, November 2016. [https://tools.ietf.org/html/draft-ietf-i2rs-usecase-reqs-summary-03](https://tools.ietf.org/html/draft-ietf-i2rs-usecase-reqs-summary-03)。

Hares, Susan, Qin Wu, and Russ White. “Filter-Based Packet Forwarding ECA Policy.” Internet-Draft. Internet Engineering Task Force, October 2016. [https://tools.ietf.org/html/draft-ietf-i2rs-pkt-eca-data-model-02](https://tools.ietf.org/html/draft-ietf-i2rs-pkt-eca-data-model-02)。

Medved, Jan, Nitin Bahadur, Hariharan Ananthakrishnan, Xufeng Liu, Robert Varga, and Alexander Clemm. “A Data Model for Network Topologies.” Internet-Draft. Internet Engineering Task Force, March 2017. [https://tools.ietf.org/html/draft-ietf-i2rs-yang-network-topo-12](https://tools.ietf.org/html/draft-ietf-i2rs-yang-network-topo-12)。

Medved, Jan, Nitin Bahadur, and Sriganesh Kini. “Routing Information Base Info Model.” Internet-Draft. Internet Engineering Task Force, December 2016. [https://tools.ietf.org/html/draft-ietf-i2rs-rib-info-model-10](https://tools.ietf.org/html/draft-ietf-i2rs-rib-info-model-10)。

Medved, Jan, Robert Varga, Hariharan Ananthakrishnan, Nitin Bahadur, Xufeng Liu, and Alexander Clemm. “A YANG Data Model for Layer 3 Topologies.” Internet-Draft. Internet Engineering Task Force, January 2017. [https://tools.ietf.org/html/draft-ietf-i2rs-yang-l3-topology-08](https://tools.ietf.org/html/draft-ietf-i2rs-yang-l3-topology-08)。

Nadeau, Thomas, Alia Atlas, Joel M. Halpern, Susan Hares, and David Ward. *An Architecture for the Interface to the Routing System*. Request for Comments 7921. RFC Editor, 2016. [https://rfc-editor.org/rfc/rfc7921.txt](https://rfc-editor.org/rfc/rfc7921.txt)。

Prieto, Alberto Gonzalez, Eric Voit, Ambika Tripathy, Einar Nilsen-Nygaard, Balazs Lengyel, Andy Bierman, and Alexander Clemm. “Subscribing to YANG Data-store Push Updates.” Internet-Draft. Internet Engineering Task Force, October 2016. [https://tools.ietf.org/html/draft-ietf-netconf-yang-push-04](https://tools.ietf.org/html/draft-ietf-netconf-yang-push-04)。

Vissicchio, Stefano, Laurent Vanbever, and Jennifer Rexford. “Sweet Little Lies: Fake Topologies for Flexible Routing.” In *ACM HotNets*. Los Angeles, California, 2014.

Wang, Lixing, Hariharan Ananthakrishnan, Mach Chen, Sriganesh Kini, and Nitin Bahadur. “A YANG Data Model for Routing Information Base (RIB).” Internet-Draft. Internet Engineering Task Force, January 2017. [https://tools.ietf.org/html/draft-ietf-i2rs-rib-data-model-07](https://tools.ietf.org/html/draft-ietf-i2rs-rib-data-model-07)。

### 复习问题

1. 研究微软的 `SWAN` 架构。你会如何对该架构进行分类？控制面的哪些部分是集中的，哪些部分是分布式的，使用了什么接口，南向协议是什么？
2. 研究谷歌的 `FirePath` 架构。你会如何对该架构进行分类？控制面的哪些部分是集中的，哪些部分是分布式的，使用了什么接口，南向协议是什么？
3. 研究 `OpenFabric`。你会如何对该架构进行分类？控制面的哪些部分是集中的，哪些部分是分布式的，使用了什么接口，南向协议是什么？
4. 研究 `RESTful` 接口。`RESTful` 接口与非 `RESTful` 接口有什么区别？
5. 在四种可能的接口中，`forCES` 协议与哪种接口交互？
6. 研究 `OpenFlow` 混合模式。`OpenFlow` 协议的开发者为何放弃了这一想法？这种模式会如何改变 `OpenFlow` 协议的分类？
7. 使用 `BGP` 作为南向接口的运营商面临的一个问题是缺乏对网络拓扑的完整视图。`BGP-LS`（链路状态）如何解决这个问题？
8. 在撒谎中，`state`、`surface` 和 `optimization` 的权衡是什么？

[1](#ch18.xhtml#ch18fn1). Atlas, Ward, and Nadeau, *Problem Statement for the Interface to the Routing System.*

[2](#ch18.xhtml#ch18fn2). Bosnich, “The Principle of Subsidiarity.”

# 第19章
## 故障域与信息隐藏

**学习目标**

阅读完本章后，你应该理解：

![Image](graphics/bull.jpg) 控制面中隐藏信息的理由

![Image](graphics/bull.jpg) 控制面状态范围和速度的概念

![Image](graphics/bull.jpg) 反馈回路以及正反馈回路的危险

![Image](graphics/bull.jpg) 汇总拓扑与聚合可达性之间的区别

![Image](graphics/bull.jpg) 过滤可达性信息

![Image](graphics/bull.jpg) 分层控制面

