
| MaxPool2D || (5, 5, 48) || - || - || (2,2) |
| Dense || 256 || - || - || - |
| Dense || 84 || - || - || - |
| Dense || 10 || - || - || - |

这两个网络经过 30 个时代训练。它们在 MNIST 数据集上的测试准确率分别为 MLP 的 95.54% 和 LeNet 的 99.05%。权重和偏置已量化为 8 位。第一项研究是对这两个网络的统计分析。`bit-flip probability` 表示权重受位翻转影响的概率，范围设定在 0% 到 95% 之间，以获得 20 个不同的点。结果取自 5 次独立运行的平均值。准确率随 `bit-flip probability` 的变化曲线在 [Figure 7.9a](#chapter7.xhtml#fig7_9) 和 [Figure 7.9b](#chapter7.xhtml#fig7_9) 中分别展示。

![Figure 7.9: Accuracy and number of bit-flips vs bit-flip probability for (a) the MLP, and (b) the LeNet network.](images/fig7_9.jpg)

[Figure 7.9:](#chapter7.xhtml#b7fig7_9) 精度与位翻转数量随位翻转概率的变化（**(a)** MLP，**(b)** LeNet 网络）。

这些结果表明，即使在低 `bit-flip probability` 下，MLP 的准确率也会显著下降。然而，对于参数众多的网络，即使在低 `bit-flip probability` 时，大量参数也会发生位翻转。通过观察 [Figure 7.9a](#chapter7.xhtml#fig7_9) 和 [Figure 7.9b](#chapter7.xhtml#fig7_9)，可以清晰看到 MLP 和 LeNet 的平均准确率（右轴，红线）与平均位翻转数（左轴，蓝线）的对比，分别展示了两者的情况。相同的 `bit-flip probability` 下，位翻转数在 LeNet 中比 MLP 低一阶以上。这表明，当网络参数出现较大错误时，网络性能仍具备高度的鲁棒性，但如下节所示，这种网络仅在概率性攻击下具有韧性，而在针对性错误（攻击者可施加的错误）面前表现截然不同。

#### 7.2.2.2 Bit-Flip with Gradient Search Algorithm

**Analysis for the MNIST Dataset**: 本节讨论通过在网络参数上应用错误，以尽可能少的位翻转来降低给定网络的准确度。损失函数相对于网络参数的梯度在学习阶段同样进行分析，灵感来源于文献 \[[221](#refbib.xhtml#refbib221)\]。梯度计算返回与参数形状相同的 n 维数组列表。选取绝对值最大的梯度，并将其对应的参数设为目标参数。为了实现准确度的最大降低，对目标参数的单个位进行翻转。随后，对该参数进行屏蔽，防止其在下一次迭代中被考虑。实验结果表明，对 MLP（见 [Figure 7.10](#chapter7.xhtml#fig7_10) 中的蓝线）和 LeNet（见 [Figure 7.10](#chapter7.xhtml#fig7_10) 中的红线）进行全局参数分析时，准确度在极少数位翻转的情况下即显著下降。仅 30 次位翻转即可使两个网络的准确度完全崩溃。

![Figure 7.10: Accuracy vs. number of bit-flips for MLP@MNIST, LeNet@MNIST, and CNN@CIFAR10.](images/fig7_10.jpg)

[Figure 7.10:](#chapter7.xhtml#b7fig7_10) 精度随位翻转数量的变化（MLP@MNIST、LeNet@MNIST、CNN@CIFAR10）。

**Analysis for the CIFAR10 Dataset**: 本文还对 CIFAR10 数据集 \[[112](#refbib.xhtml#refbib112)\] 进行了类似实验，该数据集包含 60 000 幅训练图像和 10 000 幅测试 RGB 32 × 32 图像。实验使用的 CNN 架构在 [Table 7.6](#chapter7.xhtml#tbl7_6) 中给出，训练 50 个时代后达到 79% 的准确率。

[Table 7.6:](#chapter7.xhtml#b7tbl7_6) CIFAR10 实验使用的 CNN 结构。

| Layer || Output shape || Output maps || Kernel size || Strides |
| --- | --- | --- | --- | --- |
| Input || (32, 32, 3) || - || - || - |
| --- | --- | --- | --- | --- |
| Conv2D || (32, 32, 32) || 32 || (3,3) || (1,1) |
| Conv2D || (30, 30, 32) || 32 || (3,3) || (1,1) |
| MaxPool2D || (15, 15, 32) || - || - || (2,2) |
| Dropout 0.25 || (15, 15, 32) || - || - || - |
| Conv2D || (15, 15, 64) || 64 || (3,3) || (1,1) |
| Conv2D || (13, 13, 64) || 64 || (3,3) || (1,1) |
| MaxPool2D || (6, 6, 64) || - || - || (2,2) |
| Dropout 0.25 || (6, 6, 64) || - || - || - |
| Dense || 512 || - || - || - |
| Dropout 0.25 || 512 || - || - || - |
| Dense || 10 || - || - || - |

`gradient search algorithm` 被应用于网络的所有参数。结果与前几个案例相似，但 [Figure 7.10](#chapter7.xhtml#fig7_10) 中的橙色曲线显示，准确率下降更为显著。仅 4 次位翻转即可使准确率在约 10% 处趋于平稳，这一结果比在 MNIST 数据集上对 LeNet 和 MLP 的表现更为关键。

### 7.2.3 NeuroAttack Methodology

#### 7.2.3.1 Threat Model

攻击阶段假设在供应链中进行，恶意代理人可能插入硬件特洛伊（Hardware Trojan）。现代集成电路设计通常涉及多个设计公司、制造公司、第三方 IP 以及电子设计自动化工具，这些供应商各不相同，导致供应链期间保持安全极为困难 \[[3](#refbib.xhtml#refbib3)\]。攻击采用 *灰盒* 设置，即攻击者完全了解系统架构和内部参数，但不清楚训练数据集和训练超参数。

#### 7.2.3.2 Hardware Trojan Design

硬件特洛伊被设计用于在网络参数上注入故障（即位翻转），从而降低准确度并损害完整性。恶意行为通过一种精心构造的输入噪声触发。思路是激活供应链中已隐藏的较少数硬件特洛伊。基于前面的分析，硬件隐蔽特洛伊被插入到合适的位置。每个特洛伊由一个 2 路复用器组成，一个输入是原始位，另一个输入是经反相器取反后的位。复用器的选择信号仅在输入图像中加入触发信号时为高电平。因此，当输入为干净数据时，网络行为正常，对 clean dataset 具有高精度。若在输入图像中加入隐藏噪声触发器，则故障注入被激活，准确度显著下降。该过程在 [Figure 7.11](#chapter7.xhtml#fig7_11) 中说明，灰色神经元为目标神经元，橙色箭头表示已应用位翻转的突触。触发信号的选择由目标神经元的输出与阈值比较得到，阈值根据实验结果选定。触发器的目标是当在图像上加入扰动时，目标神经元的输出超过阈值，而不是在输入为干净时超过阈值。方法的第一步是选择满足所需行为的特定神经元。为了将该方法从 DNN 迁移到 SNN（ spiking neural network）领域，输入比较器的输入会累计 spikes 数量。此外，阈值需从其模拟值转换为对应的射率。计数器在每个输入处理结束后重置。

![Figure 7.11: Scheme of the Trojan attack for the MLP with the counter added present only in SNN implementation.](images/fig7_11.jpg)
