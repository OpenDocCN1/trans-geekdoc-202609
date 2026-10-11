

整数模型的动机是为了节省时钟周期方面的资源。我们现在可以证明，如果底层架构较弱，即浮点运算较慢，则这种减少的影响更大。[图 9.4](#9783110785937_093138.xhtml#b_9783110785944-009_fig_004) 中的两个条形图展示了整数 MRF 在两种不同 CPU 架构上的运行时对比。一种是 Sandy Bridge，它也是所有其他实验的平台；另一种是采用 ARM11 架构的树莓派设备。正如预期的那样，整数模型在树莓派设备上的加速效果实际上比在另一种架构上更明显，即树莓派获得了 2.56× 的加速比，而 Sandy Bridge 为 2.34×。就标准差而言，ARM11 架构比 Sandy Bridge 更稳定，这可能是后者架构具有更复杂的乱序指令执行所致。

![Fig. 9.3 Top: negative log-likelihood and MAP accuracy of MRF as a function of *K*. Bottom: the left plot shows how the width of the parameter space behaves as a function of the number of vertices (in log-scale) for different state space sizes, whereas −*s* is the smallest and *m* the largest element of the corresponding estimated parameter vector. The relative norm of the gradient for various values of *K* is shown on the right.](graphic/b_9783110785944-009_fig_003.png)

图 9.3 上图：MRF 的负对数似然和 MAP 准确率作为 `K` 的函数。下图：左图展示了参数空间宽度如何作为顶点数量的函数（对数刻度）对于不同状态空间大小而变化，其中 `−s` 是对应估计参数向量中最小的元素，`m` 是最大的元素。不同 `K` 值下的梯度相对范数显示在右侧。

### 9.1.4.5 使用随机整数梯度下降训练整数 CRF

在最后的评估中，研究了判别模型的随机随机梯度训练。构建了一个整数线性链 CRF，并通过随机梯度下降算法进行训练。对于整数 CRF，参数更新是通过缩放整数梯度计算的（参见[第 9.1.3 节](#9783110785937_093138.xhtml#b_9783110785944-009_s_001_s_003)末尾）。两种算法都对训练数据进行 20 次遍历，每次遍历以随机顺序循环遍历训练实例。这重复了 50 次，以计算随机训练过程预期质量的估计值。浮点 CRF 的参数更新是用步长 `η = 10^(−1)` 计算的。质量与运行时的比率呈现在[图 9.4](#9783110785937_093138.xhtml#b_9783110785944-009_fig_004)中，其中负对数似然在所有训练实例上取平均，准确率是针对块标签计算的。[表 9.2](#9783110785937_093138.xhtml#b_9783110785944-009_tab_002) 展示了块类型的精确率、召回率和 F[1]\-score，其中参数 `θ = 0` 的模型的总体 F[1]\-score 约为 26%。正如所期望的，整数近似的性能是合理的。除一种块类型 (INTJ) 外，精确率、召回率和 F[1]\-score 的标准差相对较小，约为 2%。使用整数 CRF 时精确率高出三倍；使用整数 CRF 时召回率和 F[1]\-score 高出一倍，优于实数 CRF。仅对于动词短语 (VP)，IntCRF 明显比 RealCRF 差。对于许多实际应用而言，这是可以接受的代价，因为 IntCRF 的速度大约是 RealCRF 的两倍。

![Fig. 9.4 Top: Runtime comparison of integer and floating-point MRF on two architectures for a varying number of states. Left: Raspberry PI@700 MHz (ARM11). Right: Intel Core i7-2600K@ 3.4 GHz (Sandy Bridge). Bottom: progress of stochastic gradient training in terms of training error and test accuracy of the CRFs over running seconds.](graphic/b_9783110785944-009_fig_004.png)

图 9.4 上图：整数和浮点 MRF 在两种架构上针对不同状态数量的运行时对比。左侧：Raspberry PI@700 MHz (ARM11)。右侧：Intel Core i7-2600K@ 3.4 GHz (Sandy Bridge)。下图：随机梯度训练在运行秒数下的训练误差和 CRF 测试准确率方面的进展。

### 9.1.5 结论

在本文中，介绍了整数无向图模型，以及仅依赖整数运算的概率推断和参数估计算法。从预测质量和运行时两方面评估了生成模型和判别模型。我们了解到，最优整数模型参数通常取幅度较小的值，与 64 位双精度数相比，降低了存储需求。这使我们能够从高维生成模型中采样，并使用结构化判别分类器，即使在没有浮点运算单元或浮点运算单元较慢的计算设备上，或在需要节省能量的情况下也是如此。

**表 9.2** 在 CoNLL-2000 数据集上，RealCRF 和 IntCRF 的精确率、召回率和 F[1]\-score 差异在 50 次重复中的平均值。数值单位为百分比，即 −0.29 意味着整数 CRF 在相应指标上平均比其浮点对应物好 0.29%。

| | **ADJP** | **ADVP** | **CONJP** | **INTJ** | **LST** | **NP** | **PP** | **PRT** | **SBAR** | **VP** | **Overall** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Prec | −0.29 | −0.46 | 4.81 | −15.56 | 0 | 1.11 | 0.33 | 3.78 | 1.15 | 6.09 | 0.73 |
| Rec | 1.61 | 2.69 | −3.55 | 0 | 0 | 0.34 | 0.13 | 1.82 | 1.78 | 6.31 | 0.48 |
| F[1] | 0.74 | 1.17 | 1.60 | −4.03 | 0 | 0.73 | 0.23 | 2.85 | 1.50 | 6.20 | 0.61 |

## 9.2 功耗分析与上行链路发射功率

*Robert Falkenberg*

**摘要：** 由于灵活和移动的应用可能性，无线通信系统在工业和私人环境中的渗透率在不断提高。可穿戴设备、智能手机，或用于标记、跟踪和传感的工业系统，只是此类系统庞大种类中的几个例子。然而，使这些系统摆脱电网供电也意味着可用能量是一种有限资源，必须节约并审慎管理。

通信系统的能耗估计与其他组件有显著不同，因为它强烈依赖于外部影响。这些影响包括无线信道质量、信道接入方案，以及其他参与者对共享传输介质的利用，这些参与者通常不是实际系统的一部分。数据传输可能持续更长时间、需要更高的发射功率，或因冲突而失败，从而不得不重传。其后果是收发器的活跃时间变长，而在高效省电模式下的驻留时间变短。因此，在设计阶段需要现实的仿真模型，这些模型要同时考虑通信接口的特性和外部环境。

下文将讨论针对不同通信技术建模功耗的方法。这包括短距离设备 (SRD) 频段内的分散式窄带通信，以及通过上下文感知功耗模型 (CoPoMo) 对长期演进 (LTE)、LTE-Advanced (LTE-A) 和窄带物联网 (NB-IoT) 等蜂窝技术进行的全面建模。

