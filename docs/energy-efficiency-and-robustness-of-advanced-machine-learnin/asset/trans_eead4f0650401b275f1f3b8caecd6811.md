
在本节中，我们分析了一组有见解的 (`V`(`t`h), `T`) 组合，并跟踪它们对 SNNs 的鲁棒性的影响，与在相同数据集上训练的 Lenet-5 CNN 进行比较。[Figure 7.21](#chapter7.xhtml#fig7_21) 比较了 SNNs 与不同结构参数的鲁棒性，相对于其对应的 CNN。该图表以更详细的方式展示了结构参数对 SNNs 安全性的影响。事实上，虽然组合 (`V`(`t`h), `T`) = (2.25, 56) 的鲁棒性低于 CNN，但组合 (`V`(`t`h), `T`) = (1, 48) 达到了高达 85% 的更高鲁棒性。另一个有趣的案例是组合 (`V`(`t`h), `T`) = (1, 32)，其清晰精度仅为 78%（如 [Figure 7.21](#chapter7.xhtml#fig7_21) 中高亮显示），但在应用强噪声预算（即 `ε` > 1）时，其精度比 CNN 高出 75%。

![Figure 7.21: Robustness of SNNs tested on MNIST with different V_{th} and T parameters under the PGD attack and compared to the Lenet-5 CNN.](images/fig7_21.jpg)

[Figure 7.21:](#chapter7.xhtml#b7fig7_21) Robustness of SNNs tested on MNIST with different `V`(`t`h) and `T` parameters under the PGD attack and compared to the Lenet-5 CNN.

### 7.3.6 Summary

在本节中，研究了 DNNs 和 SNNs 的鲁棒性，并突出了 SNNs 对抗性攻击的更高鲁棒性原因。此外，所提议的鲁棒性探索方法能够精细调整 SNNs 的结构参数以提升其鲁棒性。评估表明，这些结构参数对 SNN 鲁棒性影响显著，在将 SNNs 用于安全关键应用之前，需要进行专门的探索。这些发现使得 SNNs 成为鲁棒且高效的深度学习系统的有吸引力的解决方案。

虽然本章讨论的分析集中在离散数据的 SNN 安全性，但 SNNs 在处理基于事件的数据时表现出高效率提升，例如通过 DVS 相机捕获的事件流作为输入。针对这一点，下文 [Section 7.4](#chapter7.xhtml#sec7_4) 和 [Section 7.5](#chapter7.xhtml#sec7_5) 将讨论基于事件的 SNN 的安全相关问题。

### 7.4 R-Snn: a Methodology for Robustifying Snns Through Noise Filters for Dvs

SNNs 旨在提供能效学习能力，当部署在与事件相机（DVS）同步的神经形态芯片上时。本节研究了 SNNs 对 DVS 系统中对抗性攻击的鲁棒性，并提出 *R-SNN*，一种通过 DVS 噪声过滤来增强 SNNs 的新方法。我们在 DVS 信号上生成对抗性攻击，并利用 DVS 传感器的噪声过滤来防御这些攻击。实验结果表明，噪声过滤成功防止了 SNNs 被欺骗。我们的实验表明，SNN 在 DvsGesture \[[8](#refbib.xhtml#refbib8)\] 和 NMNIST \[[193](#refbib.xhtml#refbib193)\] 数据集上，在不同的对抗性威胁模型下，达到超过 90% 的准确率。

### 7.4.1 System Overview

与传统 DNNs 的问题类似，SNNs 的可靠性也受到对抗性攻击的威胁。尽管已有一些初步研究，但针对基于事件的 SNN 系统这一问题仍未被探索。作为起点，设计鲁棒 SNNs 的技术可以借鉴 DNNs 最近在防御机制方面的进展，包括对抗学习算法、损失/正则化函数以及图像预处理。后者方法通过专用输入过滤来抑制对抗性扰动。值得注意的是，对于由 DVS 相机输入的 SNN 系统，针对帧基传感器的攻击和预处理防御无法直接应用，因为信号属性存在差异。因此，必须采用专门针对 DVS 传感器的噪声过滤器 \[[133](#refbib.xhtml#refbib133)\]。

针对 DVS 信号过滤在安全神经形态计算中的影响，这是一个新颖且未被探索的研究课题。为此，我们提出 *R-SNN*，一种新方法，通过在 DVS 信号上应用抗攻击噪声过滤作为防御策略，以增强 SNNs 对抗性攻击的鲁棒性。由于 DVS 相机包含时间信息，对抗性扰动的生成方式与传统的图像对抗攻击不同，传统攻击仅考虑空间信息。因此，必须利用时间信息来开发稳健的防御措施。

简言之，我们的 *关键贡献* 如下：

*   我们在多种对抗者威胁模型下，分析了 DVS 噪声过滤的影响，即通过在系统不同阶段放置过滤器或假设不同对抗者知识来进行分析。

*   我们为 DVS 信号生成对抗性扰动，以攻击 SNNs。

*   *R-SNN 设计方法论*：我们提出了一种应用专用 DVS 噪声过滤的方法，以提高 SNNs 对抗性攻击的鲁棒性。

*   实验结果展示了在不同对抗者威胁模型下，SNN 对抗性攻击的高鲁棒性。

### 7.4.2 Case Study Analysis: SNN Robustness against Random Noise

为激励上述研究方向，我们进行了以下实验。我们训练了一个 4 层 Spiking CNN，包含 2 个卷积层和 2 个全连接层，用于 DvsGesture 数据集 \[[8](#refbib.xhtml#refbib8)\]，采用 SLAYER 方法 \[[248](#refbib.xhtml#refbib248)\]，在配备两块 Nvidia GeForce RTX 2080 Ti GPU 的 ML 工工作站上进行训练。对于每个事件帧，我们在测试数据集中注入均匀分布和正态分布的随机噪声，并测量分类准确率。此外，为了减轻扰动的影响，我们应用了 \[[133](#refbib.xhtml#refbib133)\] 的过滤器，并使用不同的空间-时间参数（*s* 和 *t*）。不同噪声幅度下的准确率结果如 [Figure 7.22](#chapter7.xhtml#fig7_22) 所示。如图中高亮所示，当没有噪声时，过滤器会略微降低 SNN 的准确率。但在存在噪声时，应用过滤器可提升 SNN 的鲁棒性。例如，当考虑标准分布噪声且幅度为 0.55 时，过滤器在 *s* = 1 且 *t* = 5 时使准确率提升了 64%。该过滤器在均匀分布噪声下表现更好。事实上，幅度为 0.85 和 1 的扰动被很好地过滤，SNN 保持相对较高的准确率，分别为 85% 和 74%。

![Figure 7.22: Analyzing the impact of applying normal and uniform noise to the DvsGesture dataset.](images/fig7_22.jpg)

[Figure 7.22:](#chapter7.xhtml#b7fig7_22) Analyzing the impact of applying normal and uniform noise to the DvsGesture dataset.

### 7.4.3 R-SNN Methodology

#### 7.4.3.1 Noise Filters for Dynamic Vision Sensors

*Event-based cameras* \[[128](#refbib.xhtml#refbib128)\] 是生物启发的传感器，用于直接获取场景光照变化的视觉信息。DVS 相机是异步工作的，不记录带有精确时间戳的帧。相反，传感器记录场景中的负亮度和正亮度变化。因此，每个像素编码场景的亮度变化。像素相互独立，可以记录正负光照变化。与经典帧基图像传感器相比，基于事件的传感器功耗显著更低，因为只有在场景中检测到亮度变化时才记录数据。因此，在没有光照变化的情况下，不记录任何信息，从而实现接近零功耗。因此，DVS 传感器可以高效部署到边缘设备，并直接与神经形态硬件耦合用于 SNN 应用。

