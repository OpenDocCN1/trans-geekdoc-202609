
Hinton et al. \[[86](#refbib.xhtml#refbib86)\] 首次展示了 CapsNets 的实际可行性，这些网络以 `capsules` 作为基本块，除了能够学习图像的变形和视角条件外，还能学习图像特征。

一个更详细的解释说明如何计算姿态和概率以构建 CapsNet 的内容在 \[[236](#refbib.xhtml#refbib236)\]。一个胶囊是神经元的向量，数组中的每个元素代表实体的实例化参数，实例化概率被测量为向量的长度。为了将这种概率表示在 {0, 1} 范围内，使用了 `Squash` 函数。计算耦合系数 `c[i][j]` 的迭代过程构成了 Dynamic Routing-by-Agreement，如 [Algorithm 1](#chapter2.xhtml#comp02_1) 所示。耦合系数决定了低层胶囊 `i` 向所有高层胶囊发送其激活的程度。换句话说，`c[i][j]` 表示低层胶囊 `i` 检测到的实体属于高层胶囊 `j` 实体的先验概率。为满足这些系数的和必须为单位的性质，应用了 `Softmax` 函数（见 [Algorithm 1](#chapter2.xhtml#comp02_1) 第 8 行）。胶囊 `j` 的激活 `v[j]` 通过在预激活 `s[j]`（第 14 行）上应用 `Squash` 函数获得。最后一步是更新日志 `b[i][j]`，该步骤在下一次迭代中通过输入预测票 `û[i|j]` 与激活 `v[j]` 的标量积来计算一致性（第 18 行）。

![](images/comp02_1.jpg)

第一个 CapsNet 模型 \[[236](#refbib.xhtml#refbib236)\] 使用向量胶囊和动态路由，如 [Figure 2.7](#chapter2.xhtml#fig2_7) 所示。随后是一个带有 9×9 核大小、步长为 1 且 256 个输出通道的卷积层，接着是 PrimaryCaps 层，其中神经元被分组为 8D 向量，组织为 32 个输出通道，形成一个 9×9 步长为 2 的卷积胶囊层，使用 `Squash` 激活函数。在最后的 ClassCaps 层中，每个的 10 个胶囊专门用于识别输出类别。Dynamic Routing 分析 PrimaryCaps 层的 1152 个 8D 胶囊所编码的特征，生成 ClassCaps 层的 10 个 16D 激活。为了训练目的，构建了一个解码器网络（即三个全连接层的串联），用于获得图像重构，然后将 `reconstruction loss` 与 `margin loss`（即从输出激活的实例化概率计算得到）结合形成损失函数。尽管主要应用于相对简单的任务，如 MNIST \[[118](#refbib.xhtml#refbib118)\] 和 Fashion-MNIST \[[284](#refbib.xhtml#refbib284)\] 分类，但 Google Brain 团队开发的该架构已被学术界广泛分析和研究。因此，在下文中我们将其视为 Google CapsNet，简称 CapsNet 或 ShallowCaps，以区别于更深的 CapsNet 模型。

![Figure 2.7: Architectural model of the ShallowCaps \[236\].](images/fig2_7.jpg)

[Figure 2.7:](#chapter2.xhtml#b2fig2_7) Architectural model of the ShallowCaps \[[236](#refbib.xhtml#refbib236)\].

ShallowCaps 的一个主要局限性是它计算密集，需要大量参数才能在复杂任务上与传统 DNNs 具有可比性能。为克服这些问题，DeepCaps 架构 \[[220](#refbib.xhtml#refbib220)\] 被提出。如 [Figure 2.8](#chapter2.xhtml#fig2_8) 所示，除了增加深度外，DeepCaps 利用 3D 卷积胶囊层和 3D 动态路由，从而显著降低参数数量。此外，解码器使用池化层来捕获比全连接层更多的空间关系。

![Figure 2.8: Architectural model of the DeepCaps \[220\].](images/fig2_8.jpg)

[Figure 2.8:](#chapter2.xhtml#b2fig2_8) Architectural model of the DeepCaps \[[220](#refbib.xhtml#refbib220)\].

### 2.2.3 胶囊网络的挑战总结

正如本节详细讨论的，CapsNets 的主要挑战之一是其高复杂度，这源于涉及向量胶囊及复杂操作（如 `Squash` 和 Dynamic Routing-by-Agreement）的计算。专用硬件架构能够加速传统卷积（Conv）、全连接（FC）和池化层的执行。因此，它们要么不支持（或支持实现效率低下）涉及 CapsNets 的操作。*为解决这些挑战并弥合 CapsNets 的高学习能力与执行效率低下之间的差距，[第 3 章](#chapter3.xhtml) 介绍了提升 CapsNets 在硬件上执行能效的设计流程。该流程包括加速训练的优化以及为运行 CapsNet 推理而设计专用加速器的硬件设计优化。*

此外，不同 CapsNet 层和操作（包括计算需求和内存访问模式）的执行模式与传统 DNNs 观察到的模式显著不同，这使得高效数据流变得困难。因此，*对不同层和操作的内存访问模式及弹性进行详细监控分析，有助于设计先进的内存架构，可与 CapsNet 加速器配合使用，并通过量化和近似计算等轻量级优化进一步提升性能，这些内容将在 [第 3 章](#chapter3.xhtml) 中讨论。*

## 2.3 Spiking Neural Networks

Spiking Neural Networks (SNNs) 近年来因其高性能和低能耗而展现出巨大的成功，使其成为在嵌入式设备（如神经形态芯片）上实现的理想选择。受自然神经计算原理的启发，神经形态架构已出现为高性能、低功耗的计算平台。SNNs 是模拟人脑异步事件驱动决策过程的模型。如 [Figure 2.9](#chapter2.xhtml#fig2_9) 所示，SNNs 接收 spike 列车作为输入。这些 spikes 的发生时间、幅度和形状可以用于编码数值信息。神经元和突触执行的事件驱动计算将 spiking 信息从输入传播到输出。SNNs 可编程以实时学习和执行复杂任务，同时消耗低能量。它们被视为神经网络的第三代 \[[147](#refbib.xhtml#refbib147)\]，遵循 DNNs 的成功浪潮，用于完成复杂的机器学习任务。传统 DNN 处理连续值，而 SNNs 处理离散的 spike 列车，模拟人脑神经元的信息处理行为。除了生物学可信度之外，SNNs 的主要优势在于它们与神经形态硬件协同设计时，因其稀疏特性，有望实现能源高效的机器学习。[Figure 2.9](#chapter2.xhtml#fig2_9) 展示了 SNNs 的基本功能。输入 spikes 通过 spike 列车编码信息。网络中的神经元集成 incoming spikes，这些 spikes 会增加神经元的膜电位。当膜电位超过阈值时，就会产生输出 spikes。

![Figure 2.9: Functionality of an SNN, in which the events are encoded into spikes, and the neurons' output spikes are generated when the membrane potential exceeds the threshold voltage.](images/fig2_9.jpg)

[Figure 2.9:](#chapter2.xhtml#b2fig2_9) Functionality of an SNN, in which the events are encoded into spikes, and the neurons' output spikes are generated when the membrane potential exceeds the threshold voltage.

### 2.3.1 Spiking Neuron Models
