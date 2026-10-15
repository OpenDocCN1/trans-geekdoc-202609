
膜电位如公式 (6.4) 所示，将突触电流进行积分。每当膜电位超过电压阈值 `θ[i]` 时，神经元 `i` 会发出输出尖峰，其膜电位会被重置为 `v[r`e`s`t`]` 的值。

$$\\begin{array}{l} {{\\overset{˙}{v}}\_{i}(t) = - \\frac{1}{\\tau\_{v}}v\_{i}(t) + u\_{i}(t) - \\theta\_{i}\\sigma\_{i}(t)} \\\\ \\end{array}$$  

(6.4)

请注意，时间常数 `τ[v]` 负责模型的 *leaky* 行为 \[[40](#refbib.xhtml#refbib40)\]。

### 6.1.2 芯片架构

如 [Figure 6.1](#chapter6.xhtml#fig6_1) 所示，Loihi 芯片由 128 个神经形态核心（neurocores）组成，每个 neurocore 最多可实现 1024 个原始尖峰神经元单元（compartments），这些单元模拟出尖峰神经元的树状结构。每个神经元产生的尖峰会通过异步 NoC 以分组消息的形式发送给其突触扇出的所有 compartment，遵循一种在多个算法时间步上执行的 *mesh 操作*。该过程利用 *屏障同步机制* 确保所有神经元在下一个时间步之前已准备就绪。为实现不适合单个 128‑neurocore 芯片的更宽更深的 SNN，可将多个芯片组合在一起，且不因消息交换而产生额外延迟。芯片外部通信接口将网格扩展至 4 096 个上位核心，最高可达 16 384 个层级连接的核心。3 个嵌入式 ×86 处理器（Lakemounts）保证整个系统的正确运行，它们还可用于监测芯片性能并将信息传递给用户。

![Figure 6.1: Architectural view of the Loihi chip.](images/fig6_1.jpg)

[Figure 6.1:](#chapter6.xhtml#b6fig6_1) Loihi 芯片的结构视图。

mesh 操作包括以下子操作：

1. 每个 neurocore 独立遍历其 compartment，若 compartment 中的神经元处于放电状态，则生成尖峰消息。

2. 所有消息通过 NoC 分配到包含突触扇出的所有 neurocores。

3. 当 neurocore 完成内部将尖峰分发给神经元后，它会发送屏障同步消息，供邻居 neurocores 接收。该消息会刷新所有正在传播的尖峰，随后由同一 neurocore 生成另一条屏障消息。

4. 当所有 neurocores 收到第二条信号后，时间步加 1。

单个 neurocore 的微架构包含四个单元：

1. **Synapse** 单元负责将输入尖峰路由到合适的 compartment，并从记忆中获取相应的突触权重。

2. **Dendrite** 单元管理每个 compartment 的突触电流和膜电压，并负责检测神经元是否放电，将此信息传递给 Axon。

3. **Axon** 单元生成输出尖峰，每条消息关联到相应的后交神经元地址。

4. **Learning** 单元利用 neurocore 输出的尖峰痕迹及其他本地信息，依据学习规则更新突触权重。

### 6.1.3 支持 Loihi 开发者的工具

为实现大规模使用硬件架构并开展前沿研究，稳健的工具链至关重要。软件栈抽象了用户对低层硬件细节的关注，使其能够专注于高层次算法建模、网络架构以及学习规则的设计。

Loihi 投入科研使用后不久，*NxSDK* \[[129](#refbib.xhtml#refbib129)\] API 便被发布。通过该 API，程序员可以定义 SNN 的模型结构和参数，如衰减时间常数、突触脉冲值、突触权重、绝对延迟、放电阈值以及自定义学习规则。此外，还可在指定时间步注入外部刺激尖峰。网络状态及运行时的功耗/能耗可实时监控。在确认规格符合硬件支持后，编译器 \[[130](#refbib.xhtml#refbib130)\] 会贪婪地将网络实体（compartments、synapses、learning rules）分配至可用资源，以最小化占用的 neurocores。

为简化复杂且深度 SNN 的开发，*NxTF* \[[233](#refbib.xhtml#refbib233)\] 提供了基于 Keras 的编程接口，并经过优化的编译器，能够将深度卷积 SNN 映射至多核 Intel Loihi 架构。它同时支持直接在 spikes 上训练的 SNN，以及通过 *SNN-ToolBox* \[[234](#refbib.xhtml#refbib234)\] 将传统 DNN 转换为 SNN 的模型，处理稀疏事件数据和密集帧数据。

最近，诸如 *PyNN* \[[41](#refbib.xhtml#refbib41)\]、*Nengo* \[[12](#refbib.xhtml#refbib12), [222](#refbib.xhtml#refbib222)\]、*Brian* \[[171](#refbib.xhtml#refbib171), [258](#refbib.xhtml#refbib258)\] 等其他 SNN 模拟器也已加入对 Loihi 神经形态硬件的映射支持。

### 6.2 在 Loihi 上高效实现手势识别的 SNN

SNN 在像 Intel Loihi 这类神经形态处理器上可实现高能效，并可由事件相机提供事件流。然而，具有大量层的非尖峰 DNN 可以在图像分类和识别任务上达到相对高精度，而针对真实应用的 SNN 学习规则研究仍不成熟。SNN 的准确性结果通常通过将已训练的 DNN 转换为 SNN，或直接在尖峰域部署并训练 SNN 实现。为实现从 DNN 到 SNN 的转换，我们针对 Intel Loihi 设计了全面的分析方法，阐述了构建能够在其上实现与对应 DNN 近似精度的 SNN 的方法论。针对事件传感器，我们设计了针对 DvsGesture 数据集的预处理技术，使其能够在 DNN 域中使用。基于第一阶段分析的结果，我们在预处理后的 DvsGesture 数据集上训练 DNN，并将其转换为等价的 SNN 以便在 Intel Loihi 芯片上部署，实现实时手势识别。实验结果表明，我们的 SNN 实现 89.64% 的分类准确率，仅占用 37 个 Loihi 核心。

### 6.2.1 系统概览

在监督学习环境中，训练 SNN 的有前途方法是先使用最先进的反向传播技术训练 DNN，然后通过转换过程将训练好的参数（权重和偏置）分配给等价的 SNN 表示。该方法之所以表现出色，是因为它能够兼得两者的优势：转换后的 SNN 具备尖峰的低延迟和高能效，同时仍可利用高效训练方法实现高分类准确率。但该转换机制并不总能达到预期效果，转换时需要考虑多种因素，如原始 DNN 结构、训练过程以及控制 DNN‑to‑SNN 转换的参数。当转换后的 SNN 部署在精度受限的硬件（如 Intel Loihi）上时，这种限制更为突出，因为硬件对转换过程的自由度大幅降低。

