
WSN 的结构面临多种困难，包括拓扑结构、设计问题、可扩展性、网络寿命、能源利用等。其中，网络寿命是有效部署 WSN 的关键因素。即使其他所有问题都已得到解决，若没有显著的寿命提升，WSN 应用仍然毫无意义 (Jayarajanneditors, n.d.;, Jaiswal and Anand, 2020; Haseeb et al., 2020)。本文主要关注优化 WSN 的聚类架构以延长网络寿命。为 WSN 设计的聚类算法的主要目标是降低每个数据采集周期的网络能耗。然而，实际上发现仅通过减少单轮能耗并不能延长网络寿命 (Preeth et al., 2018; Shukla and Tripathi, 2020)。在延长 WSN 寿命时，能源平衡是至关重要的组成部分，与能源最小化并行。虽然能源平衡与能源减少看似相同，但它们实际上是网络寿命这一问题的两个完全不同的方面。因此，WSN 的最佳聚类方法必须同时保证网络能源平衡和能源减少。

## 能源

能源竞争是 WSN 的首要且通常最重要的设计问题。通信、感知和数据处理这三个功能领域——每个都需要开发——都消耗电力。传感器节点的电池寿命会对其寿命产生重大影响。由于传感器节点的能源预算有限，这一限制通常与传感器网络的方法论相关。传感器通常由电池供电，电池耗尽后需要更换或充电。

## 受限带宽

在 WSN 中，处理信息消耗的能源远大于传输数据。当前无线通信的数据速率仅限于 10 到 100 Kbits/秒。由于传感器间的消息传输受带宽限制，同步变得不可能。

## 节点价格

传感器网络由大量传感器节点组成，因此单个节点的估算对整个网络的财务指标至关重要。为了使全局指标可接受，必须考虑每个传感器节点的估算。根据传感器网络的使用方式，可能会有大量传感器随机分布在环境中（如天气观测）。如果整体传感器网络的价格合理，那么对要求慎重的消费者来说将更加经济实惠且成功。

## 部署

WSN 中节点的位置可能是一个简单的问题。要在相对有限的空间内定位和管理广泛范围的节点，需要特殊策略。在高度敏感区域，已部署了 100 到 10,000 个传感器。

## 策略限制

无线传感器设计的主要目标是创建更小、更廉价、更高效的设备。WSN 的设计受到多种竞争因素的影响。WSN 遭遇了硬件和软件受限的设计范式 (Tyagi and Kumar, 2013)。

聚类是将地理相邻的传感器节点聚集在一起的实践 (Gao et al., 2010; Gardašević et al., 2020; Surya Engineering College & Institute of Electrical and Electronics Engineers, n.d.)。集群头（CH）是管理集群的节点，可能发起聚类过程。集群成员是集群中的剩余节点。这些 CM 节点会持续感知周围环境并将数据传输到相应的 CH 节点。由于集群内的所有成员节点彼此接近，它们提供的信息也会产生冗余。在大多数应用实例中，将这些重复信息发送到基站是不必要的，并且会缩短网络的寿命。为了创建一条信息，CH 节点会汇总它们从 CMs 获得的数据。基站仅会收到这一条信息。总体而言，WSN 从聚类架构范式中受益匪浅。

**保留带宽**：当网络被分组且节点在逻辑上被分段并连接到各自的组时会发生这种情况。因此，集群可以共享相同的通信带宽而不产生任何干扰。为防止不同集群之间的干扰，每个集群都会使用自己的扩展码。

**可扩展性**：在首次部署后，新加入的节点集合会加入网络，以提高信息的准确性。新加入的节点可以通过聚类策略轻松作为新集群加入，或在部署过程中被纳入现有的组。

## X. 移动汇聚节点在 WSN 中的挑战

### 位置识别

为了传输检测到的数据，传感器节点需要移动执行器的可用性。移动汇聚节点使用广播技术向网络节点广播其位置。遗憾的是，这些方法需要大量资源定期广播汇聚节点的位置数据。网络需要每个节点进行大量的消息转发，这使得资源利用效率低下。通过使用 overhearing 方法，可以用更少的广播消息定位移动汇聚节点。移动汇聚节点创建包含最新位置数据的 Beacon 并将其发送给附近的接入点。在移动汇聚节点的通信范围内的接入点接收 Beacon 并修改其消息头，使其指向移动汇聚节点。其余网络节点在听到修改后的头信息后，会定位移动汇聚节点的新位置。此方法使用的固定点较少。传感器节点使用固定位置确定与移动汇聚节点的通信信道。节点根据固定位置确定其逻辑坐标以及通往移动汇聚节点的路径。位置识别协议的开销应得到维护和考虑，以降低广播消息的重传需求并延长网络寿命。

### 路由和移动汇聚节点轨迹

移动汇聚节点的轨迹对于感知数据的路由至关重要。与大规模 WSN 相比，移动汇聚节点可能会遍历网络中的每个节点以收集感知数据。利用少于网络总节点数的特殊节点，基于随机游走的策略将移动汇聚节点的路径与传感器节点解耦。移动汇聚节点可以自由漫游，并从指定数量的节点（作为子汇聚节点或接入点）收集数据。通过使用位置识别方法，传感器节点定位移动汇聚节点。为了提高 WSN 的使用寿命，轨迹和路径选择至关重要。移动汇聚节点的轨迹必须保证在网络中保持可用性，同时将路由开销降到最低。

### 传输调度

当移动汇聚节点进入节点的通信范围时，WSN 中的节点会立即将检测到的数据传输到移动汇聚节点。WSN 是资源受限的网络，旨在在将数据分发到移动汇聚节点的同时降低能耗。在移动汇聚节点到达最近的通信范围点之前，节点将无法按照传输调度方案发送数据。

当多个节点在其通信范围内同时识别移动汇聚节点时，densely 分布的 WSN 中的数据传输会变得困难。数据调度技术解决了在 densely 分布 WSN 中移动汇聚节点如何选择传输信道的问题，如在 Figure 14.5 所示。移动汇聚节点根据需要传输的数据量和节点剩余电量分配信道。要在 WSN 中有效分配数据，需要在数据聚合的效率与节点访问移动汇聚节点的能力之间取得合理的平衡，这十分困难。移动汇聚节点必须保持在传感器节点的通信范围内，直到所有节点完成传输。基站必须快速响应 WSN 应用，以管理感兴趣区域。移动汇聚节点凭借传输调度和路由算法以受控速度沿轨迹移动，迫使传感器节点传输其观测到的数据。为了延长网络寿命，应选择行程距离最小且覆盖网络最大的轨迹。所提模型在移动汇聚节点的速度和行程距离方面提升了性能。

```
![Figure 14.5 Framework for mobile sinks In WSN](img/fig14_5_C.jpg)
```

Figure 14.5 Framework for mobile sinks In WSN

### 安全

由于汇聚节点是移动的，WSN 面临各种攻击的威胁。传统的安全技术对于部署移动汇聚节点的 WSN 仍然不足 (Abella et al., 2019)。移动汇聚节点可能被入侵，从而获取整个网络的访问权限。如果部署多个移动汇聚节点，劫持其中一个将使攻击者获得网络的大量部分。密钥管理方法会生成两套密钥池：一套用于连接传感器节点和接入点，另一套用于连接移动汇聚节点和接入点。汇聚节点的移动性增加了安全复杂度。Figure 14.5 展示了接入点被劫持以及攻击者将复制的移动汇聚节点引入网络的情形。研究人员需要高度关注 WSN 安全。

### 网络维护

在部署前必须设定移动汇聚节点的特权级别，以便基站能够管理网络。Figure 14.6 展示了移动汇聚节点如何用于节点撤销以及在重大安全威胁期间向整个网络广播私有控制消息。

```
![Multiple nodes request for transmission channel at the same time](img/fig14_6_C.jpg)
```

Figure 14.6 Multiple nodes request for transmission channel at the same time

移动汇聚节点在 WSN 中的需求正在快速增长。移动汇聚节点的引入为网络带来了新的挑战。实现移动汇聚节点的困难已被指出。WSN 仍然在使用当前技术时会出现资源耗尽的问题 (Figures 14.7 和 14.8)。

```
![WSN with compromised access point and replicated mobile sink](img/fig14_7_C.jpg)
```

Figure 14.7 WSN with compromised access point and replicated mobile sink

```
![Mobile sink revoke compromised node and broadcast control messages to the network](img/fig14_8_C.jpg)
```

Figure 14.8 Mobile sink revoke compromised node and broadcast control messages to the network

- 图 14.8 移动基站撤销受损节点并向网络广播控制消息

## XI. 一般基本特征

### A. 传感器网络架构

传感器使用以下方法将数据发送到基站：

* 在扁平自组网架构中，传感器协同工作将数据发送到访问点，也称为基站（AP 或 BS），传输过程中会使用多跳传输。
* 在层级网络中，传感器被分组为簇，簇头负责收集和聚合传感器的数据并报告给访问点。层级网络采用单跳传输到基站以及簇间多跳传输。
* 在带移动访问的传感器网络中，移动基站在传感器场域中直接与传感器通信，传感器到基站的传输为单跳。

### B. 无线传感器节点

节点是传感器节点的另一种称呼。市场上提供种类繁多的传感器。以下是当前使用的部分传感器节点：

**加州大学洛杉矶分校（UCLA）无线集成传感器（WINS）** UCLA 开发了一些低功耗无线集成微传感器，用作传感器节点。使用 1 mW 发射器，可在 10 米距离内以 100 Kbps 的速度提供无线通信。

**UC 伯克利引用：** Crossbow 的 Mica 系列包含 Mica、Mica2、Mica2Dot 和 MicaZ。MicaZ 配备 16 MHz CPU、4 KB RAM、2 KB 闪存，支持 IEEE 802.15.4 标准和 ZigBee 协议，数据速率最高可达 250 Kbps。

**MIT 的 AMPS：** 这是一个低端独立守护节点，也可作为中端传感器网络的完整节点，或作为更高端传感器系统的辅助元件。该机构将这些节点用于多种目的。

**Tiny 节点：** 具备 512 KB 外部闪存、8 KB RAM 用于程序和数据，以及 TinyOS 操作系统。此外还有 BTNode、Imote、Iris Mote、TelosB、Wasp Mote 等。

## XII. 结论

无线传感器网络（WSN）是实现多种应用（包括轻量数据流传输和简单事件/现象监测系统）的关键技术。无线传感器网络的能源效率在开发和运行时是一个关键问题。本次努力的目标是提高信息处理和路由过程的能源效率。这项工作的主要目标是提供对 WSN 的完整综述。

## 参考文献

* Abella, C. S., Bonina, S., Cucuccio, A., D'Angelo, S., Giustolisi, G., Grasso, A. D., Imbruglia, A., Mauro, G. S., Nastasi, G. A. M., Palumbo, G., Pennisi, S., Sorbello, G., and Scuderi, A. (2019). Autonomous energyefficient wireless sensor network platform for home/office automation. IEEE Sens. J., 19(9), 3501–3512. [`doi.org/10.1109/JSEN.2019.2892604`](https://doi.org/10.1109/JSEN.2019.2892604)
* Ahmad, Arshad, Ayaz Ullah, Chong Feng, Muzammil Khan, Shahzad Ashraf, Muhammad Adnan, Shah Nazir, and Habib Ullah Khan. (2020). Towards an improved energy efficient and end-to-end secure protocol for iot healthcare applications. Security and Communication Networks. vol. 2020: 1–10. [`doi.org/10.1155/2020/8867792`](https://doi.org/10.1155/2020/8867792)
* Ahmed, G., Zhao, X., Fareed, M. M. S., Asif, M. R., and Raza, S. A. (2019). Data redundancy-control energy-efficient multi-hop framework for wireless sensor networks. Wire. Person. Comm., 108(4), 2559–2583. [`doi.org/10.1007/s11277-01906538-0`](https://doi.org/10.1007/s11277-01906538-0)
* Ahmed, M., Salleh, M., and Channa, M. I. (2018). Routing protocols based on protocol operations for underwater wireless sensor network: A survey. Egyptian Informat. J., 19(1), 57–62. [`doi.org/10.1016/j.eij.2017.07.002`](https://doi.org/10.1016/j.eij.2017.07.002)
* Al Qundus, J., Dabbour, K., Gupta, S., Meissonier, R., and Paschke, A. (2022). Wireless sensor network for AI-based flood disaster detection. Ann. Oper. Res, 319(1), 697–719. [`doi.org/10.1007/s10479020-03754-x`](https://doi.org/10.1007/s10479020-03754-x)
* Alghamdi, T. A. (2020). Energy efficient protocol in wireless sensor network: Optimized cluster head selection model. Telecomm. Sys., 74(3), 331–345. [`doi.org/10.1007/s11235-020-00659-9`](https://doi.org/10.1007/s11235-020-00659-9)
* Ali, Ahmad, Yu Ming, Sagnik Chakraborty, and Saima Iram. (2017). A comprehensive survey on real-time applications of WSN. Future internet. 9(4): 77 pp.122. [`doi.org/10.3390/fi9040077`](https://doi.org/10.3390/fi9040077)
* Al-Turjman, F. (2019). Cognitive-node architecture and a deployment strategy for the future WSNs. Mobile Netw. Appl., 24(5), 1663–1681. [`doi.org/10.1007/s11036-017-0891-0`](https://doi.org/10.1007/s11036-017-0891-0)
* Behera, T. M., Mohapatra, S. K., Samal, U. C., Khan, M. S., Daneshmand, M., and Gandomi, A. H. (2020). I-SEP: An improved routing protocol for heterogeneous WSN for IoT-based environmental monitoring. IEEE Internet of Things J., 7(1), 710–717. [`doi.org/10.1109/JIOT.2019.2940988`](https://doi.org/10.1109/JIOT.2019.2940988)
* Benayache, A., Bilami, A., Barkat, S., Lorenz, P., and Taleb, H. (2019). MsM: A microservice middleware for smart WSN-based IoT application. J. Netw. Comp. Appl., 144, 138–154. [`doi.org/10.1016/j.jnca.2019.06.015`](https://doi.org/10.1016/j.jnca.2019.06.015)
* Chaitra, M., and B. Sivakumar. (2017). Disaster debris detection and management system using wsn & iot.. International Journal of Advanced Networking and Applications. 9(1): 3306–3310.
