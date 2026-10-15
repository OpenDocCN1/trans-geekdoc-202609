
```



| MaxPool2D || (5, 5, 48) || - || - || (2,2) |
| Dense || 256 || - || - || - |
| Dense || 84 || - || - || - |
| Dense || 10 || - || - || - |

这两个网络经过 30 个时代训练。它们在 MNIST 数据集上的测试准确率分别为 MLP 的 95.54% 和 LeNet 的 99.05%。权重和偏置已量化为 8 位。第一项研究是对这两个网络的统计分析。`bit-flip probability` 表示权重受位翻转影响的概率，范围设定在 0% 到 95% 之间，以获得 20 个不同的点。结果取自 5 次独立运行的平均值。准确率随 `bit-flip probability` 的变化曲线在 Figure 7.9a 和 Figure 7.9b 中分别展示。

![Figure 7.9: Accuracy and number of bit-flips vs bit-flip probability for (a) the MLP, and (b) the LeNet network.](img/fig7_9.jpg)

Figure 7.9: 精度与位翻转数量随位翻转概率的变化（**(a)** MLP，**(b)** LeNet 网络）。

这些结果表明，即使在低 `bit-flip probability` 下，MLP 的准确率也会显著下降。然而，对于参数众多的网络，即使在低 `bit-flip probability` 时，大量参数也会发生位翻转。通过观察 Figure 7.9a 和 Figure 7.9b，可以清晰看到 MLP 和 LeNet 的平均准确率（右轴，红线）与平均位翻转数（左轴，蓝线）的对比，分别展示了两者的情况。相同的 `bit-flip probability` 下，位翻转数在 LeNet 中比 MLP 低一阶以上。这表明，当网络参数出现较大错误时，网络性能仍具备高度的鲁棒性，但如下节所示，这种网络仅在概率性攻击下具有韧性，而在针对性错误（攻击者可施加的错误）面前表现截然不同。

#### 7.2.2.2 Bit-Flip with Gradient Search Algorithm

**Analysis for the MNIST Dataset**: 本节讨论通过在网络参数上应用错误，以尽可能少的位翻转来降低给定网络的准确度。损失函数相对于网络参数的梯度在学习阶段同样进行分析，灵感来源于文献 \[221\]。梯度计算返回与参数形状相同的 n 维数组列表。选取绝对值最大的梯度，并将其对应的参数设为目标参数。为了实现准确度的最大降低，对目标参数的单个位进行翻转。随后，对该参数进行屏蔽，防止其在下一次迭代中被考虑。实验结果表明，对 MLP（见 Figure 7.10 中的蓝线）和 LeNet（见 Figure 7.10 中的红线）进行全局参数分析时，准确度在极少数位翻转的情况下即显著下降。仅 30 次位翻转即可使两个网络的准确度完全崩溃。

![Figure 7.10: Accuracy vs. number of bit-flips for MLP@MNIST, LeNet@MNIST, and CNN@CIFAR10.](img/fig7_10.jpg)

Figure 7.10: 精度随位翻转数量的变化（MLP@MNIST、LeNet@MNIST、CNN@CIFAR10）。

**Analysis for the CIFAR10 Dataset**: 本文还对 CIFAR10 数据集 \[112\] 进行了类似实验，该数据集包含 60 000 幅训练图像和 10 000 幅测试 RGB 32 × 32 图像。实验使用的 CNN 架构在 Table 7.6 中给出，训练 50 个时代后达到 79% 的准确率。

Table 7.6: CIFAR10 实验使用的 CNN 结构。

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

`gradient search algorithm` 被应用于网络的所有参数。结果与前几个案例相似，但 Figure 7.10 中的橙色曲线显示，准确率下降更为显著。仅 4 次位翻转即可使准确率在约 10% 处趋于平稳，这一结果比在 MNIST 数据集上对 LeNet 和 MLP 的表现更为关键。

### 7.2.3 NeuroAttack Methodology

#### 7.2.3.1 Threat Model

攻击阶段假设在供应链中进行，恶意代理人可能插入硬件特洛伊（Hardware Trojan）。现代集成电路设计通常涉及多个设计公司、制造公司、第三方 IP 以及电子设计自动化工具，这些供应商各不相同，导致供应链期间保持安全极为困难 \[3\]。攻击采用 *灰盒* 设置，即攻击者完全了解系统架构和内部参数，但不清楚训练数据集和训练超参数。

#### 7.2.3.2 Hardware Trojan Design

硬件特洛伊被设计用于在网络参数上注入故障（即位翻转），从而降低准确度并损害完整性。恶意行为通过一种精心构造的输入噪声触发。思路是激活供应链中已隐藏的较少数硬件特洛伊。基于前面的分析，硬件隐蔽特洛伊被插入到合适的位置。每个特洛伊由一个 2 路复用器组成，一个输入是原始位，另一个输入是经反相器取反后的位。复用器的选择信号仅在输入图像中加入触发信号时为高电平。因此，当输入为干净数据时，网络行为正常，对 clean dataset 具有高精度。若在输入图像中加入隐藏噪声触发器，则故障注入被激活，准确度显著下降。该过程在 Figure 7.11 中说明，灰色神经元为目标神经元，橙色箭头表示已应用位翻转的突触。触发信号的选择由目标神经元的输出与阈值比较得到，阈值根据实验结果选定。触发器的目标是当在图像上加入扰动时，目标神经元的输出超过阈值，而不是在输入为干净时超过阈值。方法的第一步是选择满足所需行为的特定神经元。为了将该方法从 DNN 迁移到 SNN（ spiking neural network）领域，输入比较器的输入会累计 spikes 数量。此外，阈值需从其模拟值转换为对应的射率。计数器在每个输入处理结束后重置。

![Figure 7.11: Scheme of the Trojan attack for the MLP with the counter added present only in SNN implementation.](img/fig7_11.jpg)



-   图 7.11: 带有额外开关的 MLP 的特洛伊攻击方案（仅在 SNN 实现中存在）。

#### 7.2.3.3 触发模式设计

由于神经元的模拟输出值与其对应的射速之间存在直接关系，DNN 分析所学到的知识可以转移到 SNN 实现中。此外，使用 SNN 工具箱进行 DNN 到 SNN 转换时，模拟值与射速之间的良好相关性是必要的。我们的目标是在网络中嵌入一个神经元，称为 *target neuron*（目标神经元）。换句话说，我们提出的技术的目标是：在输入图像中精心设计的面具存在时，该目标神经元会发火。设计由以下几个步骤组成：

*   **选择目标层**：目标神经元的选择高度依赖于目标层的选择。在 CNN 中，层的选择直接与触发面具的大小相关。原因是更深层的卷积层的神经元与更大的输入图像区域相连。层的阶数越高，负责触发的图像区域越大。在第一个卷积层中，梯度的位置、形状和值相对清晰，对应于神经元的 *feature map*。对于仅包含全连接层（如 MLP）的神经网络，梯度覆盖整个图像。此时，如果希望使用更小的触发图案，可以设计一个不覆盖梯度覆盖的整个区域的面具。

*   **选择目标神经元**：目标神经元被选为前一层神经元的权重绝对值之和最高的那个神经元。该模型由公式 (7.5) 给出。

    $$\\begin{array}{l} {argmax\_{t}(\\sum\\limits\_{i = 1}^{N}ABS(W\_{layer\_{i,t}}))} \\\\ \\end{array}$$  

    (7.5)

*   **选择触发面具**：生成一个 *random initial image*（随机初始图像），对网络进行推理，得到目标神经元输出值 *i**n**i**t**i**a**l**[*O**U**T**P**U**T**[*k*]]。参数 *t**a**r**g**e**t**[*O**U**T**P**U**T**[*k*]] 被设定为远大于 *i**n**i**t**i**a**l**[*O**U**T**P**U**T**[*k*]]。随后定义成本函数（公式 7.6），其中 *δ*[*i*] = *t**a**r**g**e**t**[*O**U**T**P**U**T**[*i*]] − *i**n**i**t**i**a**l**[*O**U**T**P**U**T**[*i*]]，*i* 为目标层中每个神经元的下标。

    $$\\begin{array}{l} {cost = \\frac{\\sum\\limits\_{i = 1}^{N}\\delta\_{i}^{2}}{N}} \\\\ \\end{array}$$  

    (7.6)

    令 *k* 为目标神经元的下标，上式重新表述为公式 (7.7)。

    $$\\begin{array}{l} {cost = \\frac{\\delta\_{1}^{2} + \\delta\_{2}^{2} + ... + \\delta\_{k}^{2} + ... + \\delta\_{N}^{2}}{N}} \\\\ \\end{array}$$  

    (7.7)

    对每个 *δ*[*i*]，要求 *t**a**r**g**e**t**[*O**U**T**P**U**T**[*i*]] = *i**n**i**t**i**a**l**[*O**U**T**P**U**T**[*i*]]，仅在 *δ*[*k*] 处 *t**a**r**g**e**t**[*O**U**T**P**U**T**[*k*]] ≠ *i**n**i**t**i**a**l**[*O**U**T**P**U**T**[*k*]]。为了了解哪些图像区域影响目标神经元，计算成本函数对随机输入图像像素的导数。基于此，生成面具 *M*，并通过面具与随机初始图像的点积得到 *random initial trigger*（随机初始触发器）。面具也可以选择其他形式，但必须与梯度矩阵相叠加。

*   **生成触发器**：触发器生成算法（见 Algorithm 24）受刘等人的工作启发 \[139\]。第一行设置初始化参数。 *v**a**l*[*m**i**n*] 与 *v**a**l*[*m**a**x*] 用于控制触发器的不可见性，且均需位于 (0, 1) 区间。循环持续进行，直至成本达到特定阈值或达到最大迭代次数。首先计算梯度 Δ，然后用合适的面具对梯度进行限制。相较于文献 \[139\] 的算法，额外增加了第 6 行，用于限制触发器像素的最小和最大值。

    ![](img/comp07_2.jpg)

    循环结束后，触发器的像素值经过优化，使目标神经元出现饱和。若参数 *t**a**r**g**e**t**[*O**U**T**P**U**T**[*k*]] 过高，目标神经元的输出值会降低，我们称之为 *f**i**n**a**l**[*v**a**l**u**e**[*k*]]。选择一个 *threshold*，使得当神经元输出值超过该阈值时，比较器的输出置为逻辑高，复用器随即切换。对于每个被选中的权重，对应位元会被取反。阈值通过公式 (7.8) 计算，其中 *ξ* 是依赖于网络架构和攻击方法的参数。

    $$\\begin{array}{l} {threshold = final\_{value\_{k}} - \\xi,} \\\\ \\end{array}$$  

    (7.8)

*   **触发器应用**：触发器可以以两种方式应用于图像：(1) 作为印章方式印加到图像上，或 (2) 作为图像上的噪声添加。第一种情况，触发器区域的像素值正是循环（第 2‑7 行）生成的最优值。但这种方式可能不够隐蔽。此时需仔细选择层、面具参数（位置、尺寸、*m**a**x**v**a**l*），以提高不可见性。第二种情况更具普遍性，且在隐蔽性方面表现良好，如下文 [Section 7.2.4 所示。了解像素强度分布有助于选择合适的触发器参数。

### 7.2.4 NeuroAttack 方法的评估

#### 7.2.4.1 实验设置

原始数据集和修改后的数据集均用于推理，并记录这两个数据集中目标神经元超过阈值的次数。原始数据集中可能出现一些图像本身就使目标神经元达到阈值，导致不希望的“特洛伊”激活次数增多。为了实现隐蔽攻击，触发器应使该值几乎为零。因此，即使不存在输入触发器，精度也不会显著下降。我们称 *d**i**m*[*D**A**T**A**S**E**T*] 为数据集中的图像总数，*e**x**c**e**e**d**[*O**R**I**G**I**N**A**L*]* 为原始数据集中阈值被超过的图像数量，*e**x**c**e**e**d**[*M**O**D**I**F**I**E**D*]* 为修改后数据集中阈值被超过的图像数量。因此，攻击既要实用又要隐蔽，需同时满足以下条件：

1. *e**x**c**e**e**d**[*O**R**I**G**I**N**A**L*]** <  <  *e**x**c**e**e**d**[*M**O**D**I**F**I**E**D*]  

2. *e**x**c**e**e**d**[*O**R**I**G**I**N**A**L*]** <  <  *d**i**m**[*D**A**T**A**S**E**T**]*  

3. *e**x**c**e**e**d**[*M**O**D**I**F**I**E**D*]** ≃  *d**i**m**[*D**A**T**A**S**E**T**]*  

随后将在以下章节讨论在 MNIST 和 CIFAR10 数据集上，针对 MLP、LeNet 与 CNN 网络的实验结果。

#### 7.2.4.2 在 MNIST 数据集上的结果

针对 LeNet-5 的第一个卷积层（参数见 Table 7.7 第一行），生成的触发器如 Figure 7.12d 所示。

Table 7.7: 网络结构、参数及实验结果。




| `Net` || `Layer` || `val*m` || `ξ` || `targ` || `initia` || `final` || `exc`[`ORIGINAL`] || `exc`[`MODIFIED`] |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `MNIST LeNet` || `1st Conv2D` || `0.3` || `0.1` || `100` || `0.04` || `0.21` || `0` || **`10000`** |
| `MNIST LeNet` || `2nd Conv2D` || `0.3` || `0.1` || `100` || `0.08` || `1.56` || `5` || `7585` |
| `MNIST MLP` || `1st Dense` || `0.1` || `0.1` || `100` || `0.05` || `1.21` || `15` || `9904` |
| `CIFAR10 CNN` || `1st Conv2D` || `0.3` || `0.1` || `100` || `0.02` || `0.23` || `4` || **`10000`** |

![Figure 7.12: Process of trigger generation in the first Conv layer of the LeNet. (a) Initial input trigger. (b) Gradients of the selected neuron. (c) Mask created through gradients. (d) Final trigger after loop. (e) and (f) are two images with the applied trigger.](img/fig7_12.jpg)

Figure 7.12: Process of trigger generation in the first Conv layer of the LeNet. **(a)** Initial input trigger. **(b)** Gradients of the selected neuron. **(c)** Mask created through gradients. **(d)** Final trigger after loop. **(e)** and **(f)** are two images with the applied trigger.

Figures 7.12a, b, and c show the *random initial image*, the initial gradient values, and the mask *M*, respectively. The mask is crafted to reflect the shape of the gradients. The images from both the original and modified test sets (two examples from the latter are shown in Figures 7.12e and f) are inferred. The results are reported in Table 7.7, where *e**x**c**e**e**d**[*O**R**I**G**I**N**A**L*] = 0 and *e**x**c**e**e**d**[*M**O**D**I**F**I**E**D*] = 10000.

Targeting the **second Conv layer**, the obtained results are significantly different. The trigger is more perceptible and overlapped with a significant part of the images, as can be seen in Figure 7.13. In this case, with the same experimental settings, the obtained statistics are *e**x**c**e**e**d**[*O**R**I**G**I**N**A**L*] = 5 and *e**x**c**e**e**d**[*M**O**D**I**F**I**E**D*] = 7585, as also reported in Table 7.7.

![Figure 7.13: Process of trigger generation in the second Conv layer of the LeNet. (a) Initial input trigger. (b) Gradients of the selected neuron. (c) Mask created through gradients. (d) Final trigger after loop. (e) and (f) are two images with the applied trigger.](img/fig7_13.jpg)

Figure 7.13: Process of trigger generation in the second Conv layer of the LeNet. **(a)** Initial input trigger. **(b)** Gradients of the selected neuron. **(c)** Mask created through gradients. **(d)** Final trigger after loop. **(e)** and **(f)** are two images with the applied trigger.

This demonstrates that targeting a neuron in the second Conv layer leads to a relatively worse result. In fact, we can observe that, on average, the gradients are higher than the gradients corresponding to a target neuron in the first Conv layer. We define the correlation between the target neuron and the masked area of the image *S* as in Equation (7.9), where *γ*[*i*, *j*] is the gradient corresponding to the pixel with indexes *i,j* in the trigger mask, and *M* is the size of the side trigger, in case of a square trigger.

$$\\begin{array}{l} {S = \\frac{\\sum\\limits\_{i,j}^{N}\\gamma\_{i,j}}{M^{2}}} \\\\ \\end{array}$$  

(7.9)

It can be seen that in the first convolution layer *S* = 2.21 ⋅ 10^( − 5), whereas in the second convolution layer *S* = 1.4 ⋅ 10^( − 6). This clearly shows that for a neuron in the 2^(*n**d**) layer, the variation with the input pixel is much lower. If we call *ρ* the value in Equation (7.10), we can see that it is getting lower when choosing target neurons belonging to deeper layers.

$$\\begin{array}{l} {\\rho = exceed\_{MODIFIED} - exceed\_{ORIGINAL}} \\\\ \\end{array}$$  

(7.10)

Considering the MLP network, a square mask is created and put in the bottom-right corner. Its side is varied between 5 and 17 pixels, with steps of 2 pixels. Since, in the beginning, the area of the trigger is too small, there are not enough pixels to optimize the saturation of the target neuron. The difference between *i**n**i**t**i**a**l**[*v**a**l**u**e*[*k*]] and *f**i**n**a**l**[*v**a**l**u**e*[*k*]] results in a small value. Moreover, a huge number of images from the original dataset make the target neuron exceed the threshold, leading to a small value of *ρ*. On the one hand, a larger area of the trigger increases *ρ* as can be seen in Figure 7.14 and, on the other hand, it leads to a less stealthy trigger.

![Figure 7.14: Plot of ρ with respect to the trigger size.](img/fig7_14.jpg)

Figure 7.14: Plot of *ρ* with respect to the trigger size.

In the case of the MLP network, an interesting result is obtained with a lower value of *v**a**l**[*m**a**x*] = 0.1. Even though we are targeting the first layer, the gradients are covering the complete image (Figure 7.15b) since it is an FC layer. Hence, we create a mask suited for the gradient, which spans across the whole image, as shown in Figure 7.15c. In this case, the trigger is applied as a noise in the image. Due to the low value of *v**a**l**[*m**a**x*], the trigger is imperceptible, as shown in Figures 7.15e and f. We obtained a very high *ρ*, shown in Table 7.7, and high imperceptibility at the expense of more challenging applicability.

![Figure 7.15: Process of trigger generation in the first layer of the MLP. (a) Initial input trigger. (b) Gradients of the selected neuron. (c) Mask created through gradients. (d) Final trigger after loop. (e) and (f) are two images with the applied trigger.](img/fig7_15.jpg)

Figure 7.15: Process of trigger generation in the first layer of the MLP. **(a)** Initial input trigger. **(b)** Gradients of the selected neuron. **(c)** Mask created through gradients. **(d)** Final trigger after loop. **(e)** and **(f)** are two images with the applied trigger.

#### 7.2.4.3 Results on the CIFAR10 Dataset

In this case, targeting the first layer, with parameters set as shown in Table 7.7, the trigger shown in Figure 7.16d is produced. The superposition of the trigger on the original images (two examples) is shown in Figures 7.16f and h.

![Figure 7.16: Process of trigger generation in the first layer of the CNN for the CIFAR10 dataset. (a) Initial input trigger. (b) Gradients of the selected neuron. (c) Mask created through gradients. (d) Final trigger after loop. (e) First image from the dataset. (f) First image with trigger applied. (g) Second image from the dataset. (h) Second image with trigger applied.](img/fig7_16.jpg)

Figure 7.16: Process of trigger generation in the first layer of the CNN for the CIFAR10 dataset. **(a)** Initial input trigger. **(b)** Gradients of the selected neuron. **(c)** Mask created through gradients. **(d)** Final trigger after loop. **(e)** First image from the dataset. **(f)** First image with trigger applied. **(g)** Second image from the dataset. **(h)** Second image with trigger applied.

#### 7.2.4.4 Hardware Overhead

Given the amount M of bit-flips applied, the hardware overhead is constituted as the following.

1.  M inverters, constituted by 2 transistors each.

2.  M 2-way multiplexer, constituted by 16 transistors each in a 4 NANDs implementation.



3. `在 DNN 的情况下`，一个数字比较器，其复杂度取决于神经元的扇出。

4. `在 SNN 的情况下`，一个计数器用于计数尖峰，以及一个比较器用于检查计数是否达到特定值。

多路复用器和反相器的开销可以估计为 (2 + 16) × M。从第 7.2.2 节的实验报告中可以清楚地看出，大约 30 次位翻转就足以完全破坏在 MNIST 数据集上运行的两个 DNN 的性能，而在 CIFAR10 数据集上运行的 CNN 只需 4 次位翻转。以晶体管计量的反相器和多路复用器的硬件开销分别为 (2 + 16) × 30 = 540（第一种情况）和 (2 + 16) × 4 = 72（第二种情况）。在 SNN 的情况下，会增加一个计数器，其模块至少应与神经元能达到的最大放电率相同。模块 *N* 计数所需的晶体管数量由 #[*t**r**a**n**s**i**s**t**o**r**s*] = (*N* − 2) × 6 + (*N* × 4) × 4 给出，其中第一项表示与与门的贡献，第二项表示与 T 型触发器的贡献。

### 7.2.5 Summary

拟议的 NeuroAttack 方法利用位翻转的抗性分析，设计一种隐蔽的硬件特洛伊，它会翻转 SNN 或 DNN 的最重要权重位。触发特洛伊的方式是通过精心构造的对抗性模式，在实际中几乎不可见。该攻击对 DNN 和 SNN 的可信度构成了关键威胁。它在实际中实现时硬件开销很小，同时不影响 SNN 的内部结构。然而，如下文 Section 7.3 将要展示的那样，SNN 相比 DNN 具有更高的固有鲁棒性。此外，通过调整其结构参数（如阈值电压和采样尖峰的时间窗口），该方法还可以进一步增强。

### 7.3 通过内在结构参数提升 SNN 的鲁棒性方法

最近的研究 \[114, 127\] 表明，SNN 对安全攻击具有固有的鲁棒性，即使不考虑其结构性放电参数的变异性。本节探讨通过内部结构参数来增强 SNN 的安全性。具体而言，我们研究了 SNN 对不同阈值电压阈值和时间窗口边界的对抗攻击的鲁棒性。我们在强白盒设置下，对不同噪声预算和可变放电参数下的 SNN 安全性进行了全面研究。结果表明，结构参数对 SNN 的安全性有显著影响，且可以通过调节结构参数来实现比传统非 spiking DNN 系统更高 85% 的鲁棒性，从而设计出可信的 SNN。据我们所知，这是首个研究结构参数对 SNN 对抗攻击鲁棒性的工作。

### 7.3.1 系统概览

虽然传统（即非 spiking）DNN 对抗攻击的可靠性和安全性已经得到深入研究，但 SNN 的鲁棒性分析仍 largely 未被探索。由于其生物启发性，SNN 在行为维度上比非 spiking DNN 更为丰富。因此，需要更全面的研究来理解 SNN 的内在行为，特别是在对抗攻击下。为此，我们需要研究以下关键问题：

1. **(Q1)** *结构性参数（即阈值电压和时间窗口）如何影响 SNN 在攻击下的行为？*

2. **(Q2)** *SNN 是否天然对抗攻击具有鲁棒性，无论结构参数如何？*

3. **(Q3)** *一种能够提供高精度的结构参数组合是否也能保证高鲁棒性？*

为回答这些研究问题，我们提出了以下关键贡献：

*   我们提出了一种系统的 SNN 鲁棒性分析方法。我们是首次探讨神经元的结构参数（即 spiking 阈值电压 *V*[*t**h**] 和时间窗口边界 *T*）对 SNN 在强白盒对抗攻击下的鲁棒性的影响。

*   SNN 的可学性和安全性研究表明，其固有的鲁棒性强烈依赖于这些结构参数。

*   我们通过在以往发现的“甜点”周围微调结构参数，设计出可信的 SNN。例如，在 MNIST 数据集上训练的 5 层 SNN，当应用 PGD 攻击（噪声预算 *ε* = 1.5）时，可实现相较于对应 CNN 最高 84% 的精度提升。

### 7.3.2 案例研究分析：相同架构模型下的 DNN 与 SNN 对比

为突出该问题的重要性，我们进行了一项激励性案例研究。我们在 MNIST 数据集上使用 PyTorch 框架 \[204\] 训练了一个 5 层 CNN（3 个卷积层和 2 个全连接层）\[118\]，并使用 Norse 框架 \[209\] 训练了一个结构相同、神经元数相同的 SNN。我们对两个网络分别应用白盒 PGD 攻击 \[148\]，并监控精度随噪声预算 *ε* 的变化。结果如 Figure 7.17 所示：CNN 在低噪声幅度时精度更高。但当 *ε* = 0.5 之后出现转折点时，SNN 明显比 CNN 更具抗攻击能力，精度差距超过 50%。对于 *ε* > 0.5，CNN 的精度急剧下降，而 SNN 的下降斜率较小。这一结果激励我们进一步研究 SNN 的固有鲁棒性。

![Figure 7.17: PGD adversarial attack applied to a CNN and an SNN that have the same number of layers with equal size and an equal number of neurons.](img/fig7_17.jpg)

Figure 7.17: PGD 对抗攻击应用于结构相同、尺寸相等、神经元数相同的 CNN 与 SNN。

这些实验快速展示了 SNN 相对于传统 DNN 在安全性方面的巨大潜力。但由于这些实验使用了默认的 SNN 结构参数，在没有更深入分析的情况下，这一观察无法普遍化。

### 7.3.3 威胁模型

#### 7.3.3.1 攻击者知识

在我们的实验中，我们假设攻击者在白盒攻击场景下，试图设计对抗攻击来欺骗 SNN 分类器。我们假设攻击者拥有强大的知识，完全了解受害者分类器的架构和参数（包括结构参数 *V*[*t**h**] 和 *T*）。攻击者利用这些知识构造对抗样本。

#### 7.3.3.2 攻击生成

我们使用最广为人知的 PGD 攻击 \[148\] 来评估 SNN 的鲁棒性。它是 FGSM 的最强迭代变体，对抗样本的生成遵循公式 (7.11)。

$$\\begin{array}{l} {x^{t + 1} = \\mathcal{P}\_{\\mathcal{S}\_{x}}(x^{t} + \\alpha \\cdot sign(\\nabla\_{x}\\mathcal{L}\_{\\theta}(x^{t},y)))} \\\\ \\end{array}$$  

(7.11)

其中 𝒫[𝒮[*x*]]() 是将输入投影到可行域 𝒮[*x*] 的投影算子，*α* 是每次迭代的添加噪声。PGD 攻击旨在最大化模型在给定样本上的损失，同时保持扰动幅度低于给定预算。它是一种迭代梯度攻击，被认为是高成功率的攻击。



### 7.3.4 Robustness Exploration Methodology

我们的研究探讨了在不同对抗噪声预算下 SNN 的鲁棒性，针对不同 `V[t]` 和 `T` 参数组合。Figure 7.18 给出了我们方法论的不同组成部分的概览。它由以下两个主要步骤组成。**(1)** 探索的第一步旨在排除结构参数中不利于 SNN 高效学习的组合。事实上，没有兴趣研究基线性能较低的 SNN 的鲁棒性。**(2)** 在第二步，对于所有能够使 SNN 训练高效收敛的 `V[t]` 和 `T` 设置，我们进行鲁棒性探索。

![Figure 7.18: Methodology steps for exploring the SNN robustness, varying the threshold voltage V_{th}, the time window T, and the adversarial perturbation ε.](img/fig7_18.jpg)

Figure 7.18: Methodology steps for exploring the SNN robustness, varying the threshold voltage `V[t]`, the time window `T`, and the adversarial perturbation `ε`.

Algorithm 25 详细描述了我们的鲁棒性探索方法论。第 1 行和第 2 行浏览 `n` 个阈值电压和 `m` 个时间窗口进行探索。一旦训练启动（第 3 行），我们便对给定的 `V[t]` 和 `T` 组合进行 SNN 可学性研究。如第 4 行所示，可学性通过设定一个最低基线准确率阈值来定量验证，该阈值以下我们认为 SNN 学习效率低下。该数值取决于 SNN 架构、学习方法、数据集和应用。在我们的案例研究中，我们使用准确率阈值为 70%，因为这是当前最先进的 SNN 通常能够达到的数值 \[209\]。

安全分析从第 5 行开始。它会使用不同的噪声预算生成对抗示例以欺骗 SNN。噪声预算模拟了攻击生成中允许的侵略程度；噪声预算越高，攻击越具有侵略性。首先，我们初始化成功攻击生成的计数器（第 6 行）。然后，我们遍历数据集 𝒟（第 7 行），使用 PGD 生成对抗攻击，如第 8 行所示。随后，算法验证生成的示例是否能够欺骗 SNN（第 9-10 行），即攻击是否迫使输出变为错误标签，并相应地增加对抗成功计数器。随后，我们对每个 `ε` 值评估鲁棒性，即对手未能生成能够欺骗受害者 SNN 的对抗示例的比例（第 11 行）。因此，通过跟踪准确率随 `ε` 的变化趋势，我们可以比较每个模型对抗攻击的鲁棒性。

![](img/comp07_3.jpg)

### 7.3.5 Evaluation of the SNNs' Robustness

#### 7.3.5.1 Experimental Setup

我们的实验使用 Norse \[209\]，这是一个扩展 PyTorch \[204\] 的库，提供生物启发神经元组件的原语，从而使我们能够在 spiking 域中训练和运行 SNN。对抗攻击使用 Foolbox v3.1.1 \[224\]。SNN 架构是基于 LIF 积分和差分（LIF）神经元模型的 Lenet-5，并在 MNIST 数据集上进行训练 \[118\]。实验在 Nvidia GeForce RTX 2080 Ti GPU 上进行。

#### 7.3.5.2 Learnability Study

在研究结构参数变化时的鲁棒性之前，我们需要定义探索空间。阈值电压和时间窗口参数的默认值为 `V[t]` 和 `T` = (1, 64)。因此，我们关注在围绕这些设置的邻近区域内的 SNN 可学性进行概览。Figure 7.19 展示了不同 `V[t]` 和 `T` 组合的准确率热图。水平轴和纵轴分别表示 `V[t]` 和 `T`，不同颜色表示 SNN 的准确率。注意，最高准确率的组合倾向于位于左上角，即低 `V[t]` 和高 `T`。然而，热图并非单调递增。例如，存在准确率低于 16% 的组合，却被准确率高于 89% 的组合包围。

![Figure 7.19: Heat map showing the accuracy of SNNs trained on the MNIST dataset under different combinations of V_{th} and T.](img/fig7_19.jpg)

Figure 7.19: Heat map showing the accuracy of SNNs trained on the MNIST dataset under different combinations of `V[t]` and `T`.

虽然很明显，研究不可学习的组合是没有意义的，但我们使用这张热图作为参考，来跟踪在不同噪声预算下 SNN 在攻击下的行为。

#### 7.3.5.3 Security Study

本节研究在白盒场景下，通过增加对抗噪声幅度来评估 SNN 的鲁棒性。我们首先在所有先前的 `V[t]` 和 `T` 组合下进行整体探索。Figure 7.20 展示了在 PGD 攻击下，噪声幅度为 1 和 1.5 时 SNN 精度的下降情况。

![Figure 7.20: Heat maps showing the SNN accuracy for the MNIST dataset using different combinations of (V_{i},T_{j}). (a) Security analysis for ε = 1. (b) Security analysis for ε = 1.5.](img/fig7_20.jpg)

Figure 7.20: Heat maps showing the SNN accuracy for the MNIST dataset using different combinations of `V[i]` and `T[j]`. **(a)** Security analysis for `ε` = 1. **(b)** Security analysis for `ε` = 1.5.

我们从 Figure 7.20 中提取的第一个令人着迷的洞察是：高基线可学性（即在没有对抗攻击的情况下的表现）并不能保证鲁棒性。此外，我们注意到结构参数的不同会导致 SNN 在面对对抗攻击时表现出不同的演变趋势。具体来说，两个初始精度相近的 SNN 可能在攻击下表现截然不同。例如，组合 `V[t]` 和 `T` = (0.5, 80) 与 `V[t]` 和 `T` = (0.75, 72) 都以 97% 的准确率开始。然而，在 `ε` = 1 攻击预算下，第一个组合的准确率下降至 27%，而第二个组合仅下降 6%。

Figure 7.20b 展示了在大对抗扰动（`ε` = 1.5）下的更为突出的行为，超过一半的热图区域的 SNN 准确率低于 20%。值得注意的是，`V[t]` 和 `T` = (0.75, 48) 的 SNN 在 `ε` = 1.5 时准确率降至 2%，而在 `ε` = 1 时相对较高（86%）。另一方面，`V[t]` 和 `T` = (1, 80) 的 SNN 对 PGD 攻击表现相对稳健，其准确率从 `ε` = 0 和 `ε` = 1 时的 72% 仅下降到 `ε` = 1.5 时的 66%。

#### 7.3.5.4 CNNs' vs. SNNs' Robustness Comparison




在本节中，我们分析了一组有见解的 (`V`(`t`h), `T`) 组合，并跟踪它们对 SNNs 的鲁棒性的影响，与在相同数据集上训练的 Lenet-5 CNN 进行比较。Figure 7.21 比较了 SNNs 与不同结构参数的鲁棒性，相对于其对应的 CNN。该图表以更详细的方式展示了结构参数对 SNNs 安全性的影响。事实上，虽然组合 (`V`(`t`h), `T`) = (2.25, 56) 的鲁棒性低于 CNN，但组合 (`V`(`t`h), `T`) = (1, 48) 达到了高达 85% 的更高鲁棒性。另一个有趣的案例是组合 (`V`(`t`h), `T`) = (1, 32)，其清晰精度仅为 78%（如 Figure 7.21 中高亮显示），但在应用强噪声预算（即 `ε` > 1）时，其精度比 CNN 高出 75%。

![Figure 7.21: Robustness of SNNs tested on MNIST with different V_{th} and T parameters under the PGD attack and compared to the Lenet-5 CNN.](img/fig7_21.jpg)

Figure 7.21: Robustness of SNNs tested on MNIST with different `V`(`t`h) and `T` parameters under the PGD attack and compared to the Lenet-5 CNN.

### 7.3.6 Summary

在本节中，研究了 DNNs 和 SNNs 的鲁棒性，并突出了 SNNs 对抗性攻击的更高鲁棒性原因。此外，所提议的鲁棒性探索方法能够精细调整 SNNs 的结构参数以提升其鲁棒性。评估表明，这些结构参数对 SNN 鲁棒性影响显著，在将 SNNs 用于安全关键应用之前，需要进行专门的探索。这些发现使得 SNNs 成为鲁棒且高效的深度学习系统的有吸引力的解决方案。

虽然本章讨论的分析集中在离散数据的 SNN 安全性，但 SNNs 在处理基于事件的数据时表现出高效率提升，例如通过 DVS 相机捕获的事件流作为输入。针对这一点，下文 Section 7.4 和 Section 7.5 将讨论基于事件的 SNN 的安全相关问题。

### 7.4 R-Snn: a Methodology for Robustifying Snns Through Noise Filters for Dvs

SNNs 旨在提供能效学习能力，当部署在与事件相机（DVS）同步的神经形态芯片上时。本节研究了 SNNs 对 DVS 系统中对抗性攻击的鲁棒性，并提出 *R-SNN*，一种通过 DVS 噪声过滤来增强 SNNs 的新方法。我们在 DVS 信号上生成对抗性攻击，并利用 DVS 传感器的噪声过滤来防御这些攻击。实验结果表明，噪声过滤成功防止了 SNNs 被欺骗。我们的实验表明，SNN 在 DvsGesture \[8\] 和 NMNIST \[193\] 数据集上，在不同的对抗性威胁模型下，达到超过 90% 的准确率。

### 7.4.1 System Overview

与传统 DNNs 的问题类似，SNNs 的可靠性也受到对抗性攻击的威胁。尽管已有一些初步研究，但针对基于事件的 SNN 系统这一问题仍未被探索。作为起点，设计鲁棒 SNNs 的技术可以借鉴 DNNs 最近在防御机制方面的进展，包括对抗学习算法、损失/正则化函数以及图像预处理。后者方法通过专用输入过滤来抑制对抗性扰动。值得注意的是，对于由 DVS 相机输入的 SNN 系统，针对帧基传感器的攻击和预处理防御无法直接应用，因为信号属性存在差异。因此，必须采用专门针对 DVS 传感器的噪声过滤器 \[133\]。

针对 DVS 信号过滤在安全神经形态计算中的影响，这是一个新颖且未被探索的研究课题。为此，我们提出 *R-SNN*，一种新方法，通过在 DVS 信号上应用抗攻击噪声过滤作为防御策略，以增强 SNNs 对抗性攻击的鲁棒性。由于 DVS 相机包含时间信息，对抗性扰动的生成方式与传统的图像对抗攻击不同，传统攻击仅考虑空间信息。因此，必须利用时间信息来开发稳健的防御措施。

简言之，我们的 *关键贡献* 如下：

*   我们在多种对抗者威胁模型下，分析了 DVS 噪声过滤的影响，即通过在系统不同阶段放置过滤器或假设不同对抗者知识来进行分析。

*   我们为 DVS 信号生成对抗性扰动，以攻击 SNNs。

*   *R-SNN 设计方法论*：我们提出了一种应用专用 DVS 噪声过滤的方法，以提高 SNNs 对抗性攻击的鲁棒性。

*   实验结果展示了在不同对抗者威胁模型下，SNN 对抗性攻击的高鲁棒性。

### 7.4.2 Case Study Analysis: SNN Robustness against Random Noise

为激励上述研究方向，我们进行了以下实验。我们训练了一个 4 层 Spiking CNN，包含 2 个卷积层和 2 个全连接层，用于 DvsGesture 数据集 \[8\]，采用 SLAYER 方法 \[248\]，在配备两块 Nvidia GeForce RTX 2080 Ti GPU 的 ML 工工作站上进行训练。对于每个事件帧，我们在测试数据集中注入均匀分布和正态分布的随机噪声，并测量分类准确率。此外，为了减轻扰动的影响，我们应用了 \[133\] 的过滤器，并使用不同的空间-时间参数（*s* 和 *t*）。不同噪声幅度下的准确率结果如 Figure 7.22 所示。如图中高亮所示，当没有噪声时，过滤器会略微降低 SNN 的准确率。但在存在噪声时，应用过滤器可提升 SNN 的鲁棒性。例如，当考虑标准分布噪声且幅度为 0.55 时，过滤器在 *s* = 1 且 *t* = 5 时使准确率提升了 64%。该过滤器在均匀分布噪声下表现更好。事实上，幅度为 0.85 和 1 的扰动被很好地过滤，SNN 保持相对较高的准确率，分别为 85% 和 74%。

![Figure 7.22: Analyzing the impact of applying normal and uniform noise to the DvsGesture dataset.](img/fig7_22.jpg)

Figure 7.22: Analyzing the impact of applying normal and uniform noise to the DvsGesture dataset.

### 7.4.3 R-SNN Methodology

#### 7.4.3.1 Noise Filters for Dynamic Vision Sensors

*Event-based cameras* \[128\] 是生物启发的传感器，用于直接获取场景光照变化的视觉信息。DVS 相机是异步工作的，不记录带有精确时间戳的帧。相反，传感器记录场景中的负亮度和正亮度变化。因此，每个像素编码场景的亮度变化。像素相互独立，可以记录正负光照变化。与经典帧基图像传感器相比，基于事件的传感器功耗显著更低，因为只有在场景中检测到亮度变化时才记录数据。因此，在没有光照变化的情况下，不记录任何信息，从而实现接近零功耗。因此，DVS 传感器可以高效部署到边缘设备，并直接与神经形态硬件耦合用于 SNN 应用。




DVS 传感器主要受热活动和结点漏电流引起的背景活动噪声的影响 \[191\]。当 DVS 被激活时，相邻像素的窗口同时激活，产生事件。因此，实际事件的空间-时间相关性高于噪声事件。这一经验观察被用于过滤噪声 \[133\]。计算空间-时间邻域中事件的相关性。如果相关性低于特定阈值，则事件很可能捕获噪声并被过滤掉；否则保留。该过程在 Algorithm 26 中描述，其中 `s` 和 `t` 是唯一用于确定空间-时间邻域尺寸的过滤参数。对于 `s` 和 `t` 的大值，仅有少量事件被过滤。过滤的决策依据是 `t[e]` − `M[x[e]][y[e]]` 与 `t` 的比较（Algorithm 26 的第 8‑9 行）。
![](img/comp07_4.jpg)

### 7.4.3.2 空间-时间域中的对抗攻击

目前，对抗攻击在许多深度学习（DL）应用中被部署，它们对安全关键应用构成严重威胁。成功的攻击旨在生成微小扰动，误导网络。最近，已有一些关于针对 spiking 神经网络（SNNs）的对抗攻击的初步研究 \[10, 245\]。*然而，这些先前的工作并未分析来自 DVS 摄像机的事件帧的攻击*。

对于图像的对抗攻击，扰动仅在空间域中引入。但当考虑视频对抗攻击时，视频是图像帧的序列，攻击算法也可以扰动时间域。虽然预期的扰动会通过时间交互作用传播到其他帧，但只对少量帧进行扰动会使攻击更隐蔽。事实上，当前最先进的视频攻击只在少数帧上添加扰动，这些扰动会在时间上传播，从而导致视频误分类。

### 7.4.3.3 对抗威胁模型

在我们的实验中，我们在系统设置中假设不同的威胁模型，如 Figure 7.23 所示。在三种情形中，给定的对抗攻击算法对 DVS 摄像机生成的事件帧进行扰动，以欺骗 SNN。在威胁模型 A⃝ 中，攻击者拥有输入到 SNN 的事件帧。在威胁模型 B⃝ 中，DVS 噪声过滤器并行插入系统，攻击者不知晓该过滤。基于这些假设，攻击可能较弱，因此我们还分析威胁模型 C⃝，其中攻击者知道 DVS 噪声过滤器的存在。在此情形下，过滤器被视为预处理步骤并嵌入攻击循环。

![Figure 7.23: Adversarial threat models are considered in this work. (a) The adversary introduces adversarial perturbations to the frames of events at the input of the SNN. (b) The noise filter is inserted as a defense to secure the SNNs against adversarial perturbations while the adversary is unaware of the filter. (c) The adversary is aware of the presence of the noise filter and sees it as a preprocessing step of the SNN.](img/fig7_23.jpg)

Figure 7.23: Adversarial threat models are considered in this work. **(a)** The adversary introduces adversarial perturbations to the frames of events at the input of the SNN. **(b)** The noise filter is inserted as a defense to secure the SNNs against adversarial perturbations while the adversary is unaware of the filter. **(c)** The adversary is aware of the presence of the noise filter and sees it as a preprocessing step of the SNN.

### 7.4.3.4 事件帧的对抗攻击生成

对事件帧的对抗攻击生成过程如下。受帧基视频攻击算法的启发，我们专门设计了针对 DVS 信号的攻击算法。Algorithm 27 描述了我们方法的逐步过程。它是一个迭代算法，为数据集 `D` 的每个帧序列计算扰动值（第 2‑17 行），基于 SNN 的损失函数。 masks `M` 决定在哪些子集的事件帧上添加扰动（第 3 行）。随后，在第 5‑6 行计算出带扰动的输出概率及其对应的损失。最后，扰动值根据相对于损失的输入梯度计算得出。

![](img/comp07_5.jpg)

### 7.4.3.5 我们提出的防御方法

我们针对 SNNs 的防御方法基于专用的 DVS 噪声过滤。Algorithm 28 报告了如何选择高效的空间参数 `s` 和时间参数 `t`。对于不同的威胁模型，算法会在给定参数下，用过滤器对攻击进行评估，自动搜索 `s` 与 `t` 的最佳组合。在此条件下，SNN 的准确率与之前记录的最高准确率进行比较（第 8 行）。最终输出的参数 `s^′` 与 `t^′` 是实现最高准确率的组合。

![](img/comp07_6.jpg)

## 7.4.4 R‑SNN 方法的评估

### 7.4.4.1 实验设置

在我们的实验中，我们使用了两个基于事件的数据集：DvsGesture \[8\] 和 NMNIST \[193\]。前者包含 1077 个训练样本和 264 个测试样本，涵盖 11 个类别。后者是对原始帧基 MNIST 数据集的 spiking 转换 \[118\]，包含 60 000 个训练样本和 10 000 个测试样本，由 ATIS 事件传感器在捕捉 LCD 屏幕上投射的原始 MNIST 图像时移动生成 \[211\]。对于 DvsGesture 数据集，我们采用了如 \[248\] 所述的 4 层 SNN，包括两层卷积层和两层全连接层。该网络经过 625 个时代使用 SLAYER 反向传播方法 \[248\] 训练，批量大小为 4，学习率为 0.01。对于 NMNIST 数据集，我们使用了一个包含两层全连接层的 spiking 多层感知器 \[248\]，训练 350 个时代，同样使用 SLAYER 方法，批量大小为 4，学习率为 0.01。我们使用 PyTorch 框架 \[204\] 在配备两块 Nvidia GeForce RTX 2080 Ti GPU 的 ML 工作站上实现 SNNs，同时在 PyTorch 中实现对抗攻击算法和 \[133\] 的噪声过滤。 



对于威胁模型 A⃝，攻击者直接在 SNN 的输入上引入对抗性扰动。在此情况下，如黑色条带中 Figure 7.24a 所示，DvsGesture 数据集的 SNN 未受到滤波器保护，准确率下降至 15.15%。在 NMNIST 数据集的 SNN 上也观察到类似行为，攻击将准确率降至 4%（降幅 91%，见 Figure 7.24b 中的黑色条带）。我们注意到，两个数据集中，攻击算法的第一次迭代即已达到最大的准确率下降。进一步的迭代似乎不会进一步降低准确率。

![Figure 7.24: SNN robustness under the adversarial threat model A, and the threat model B with different parameters s and t of the filter. (a) Results for the DvsGesture dataset. (b) Results for the NMNIST dataset.](img/fig7_24.jpg)

Figure 7.24: SNN robustness under the adversarial threat model A, and the threat model B with different parameters *s* and *t* of the filter. **(a)** Results for the DvsGesture dataset. **(b)** Results for the NMNIST dataset.

#### 7.4.4.3 SNN Robustness under Attack by Noise Filter-Unaware Adversary

随后，我们分析了威胁模型 B⃝ 的 SNN 稳健性，即攻击者可以在输入上引入扰动，但不清楚 DVS 滤波器的存在。对于此实验集，准确率远高于威胁模型 A⃝，证明了滤波器作为防御手段的有效性，能够保证高 SNN 稳健性。我们提出的 *R-SNN* 方法在同时变换滤波器参数 *s* 和 *t* 的情况下，其结果如 Figure 7.24 所示。对于 DvsGesture 数据集的 SNN，在 *s* 和 *t* 的广泛取值范围内，准确率变化不大，保持在约 90%；但当 *t* = 500 时，准确率下降至 48%。然而，当 *t* = 1 时，*s* 的影响更为显著：准确率从 *s* = 1 的 62.5% 上升到 *s* = 4 的 83%。在其他所有情况中，差异几乎可以忽略。相反，我们可以看到 *s* 越大，滤波器处理所有数据的速度越慢。在考虑的数值中，*t* = 10 对每个 *s* 都产生了最高的准确率，最高达到 91.67%，对应 *s* = 3 和 *s* = 4。对于 NMNIST 数据集的 SNN，行为类似。当 *t* = 1 时，准确率强烈依赖 *s*。最高的 94% 准确率出现在 (*s*, *t*) = (3, 2) 和 (*s*, *t*) = (4, 2)。注意，这仅比原始准确率（即使用干净输入时）低 1%。另一方面，当 *t* ≥ 20 时，准确率跌破 90%。

#### 7.4.4.4 SNN Robustness under Attack by Noise Filter-Aware Adversary

我们还在威胁模型 C⃝ 下评估了 *R-SNN* 方法，攻击者知道滤波器的存在。此处，滤波器被纳入 SNN，具体为预处理阶段。如预期，滤波器在此场景下同样作为防御机制有效。与威胁模型 B⃝ 的差异不明显。在 DvsGesture 数据集的实验中，最高稳健性出现在 (*s*, *t*) = (3, 10) 和 (*s*, *t*) = (4, 10)，此时 SNN 的准确率为 91.67%（见 Figure 7.25a）。对于 NMNIST 数据集，最高稳健性（即 94% 准确率）出现在 (*s*, *t*) = (3, 2) 和 (*s*, *t*) = (4, 2)（见 Figure 7.25b）。这一结果表明，此类攻击无法战胜滤波器的存在。即使攻击者知晓滤波器，基于梯度的学习算法也无法有效学习滤波器的功能。

![Figure 7.25: SNN robustness under adversarial threat model C. (a) Results for the DvsGesture dataset. (b) Results for the NMNIST dataset.](img/fig7_25.jpg)

Figure 7.25: SNN robustness under adversarial threat model C. **(a)** Results for the DvsGesture dataset. **(b)** Results for the NMNIST dataset.

#### 7.4.4.5 Case Study: Output Probability Variation

为了更细致地研究对抗攻击和滤波器的影响，我们对一条标记为 *left-hand wave* 的 DvsGesture 测试样本进行了全面的案例研究。Figure 7.26 展示了本节各个对抗威胁模型（以及清洁输入和经过滤波的事件序列）的帧以及每个类别的输出概率。对于清洁图像，SNN 正确将事件归类为类 2，即 *left-hand wave*（见 Figure 7.26a）。当使用 *s* = 2 与 *t* = 5 对输入信号进行滤波，如 Figure 7.26b 所示，事件帧明显不同于前一例，但输出概率的变化极小，SNN 仍能正确分类输入。攻击被应用后，类 0（对应 *hand clap*）的输出概率超过正确类别。尽管输出概率差异巨大，但相较于清洁事件序列，帧的修改几乎不可见（见 Figure 7.26c）。然而，在滤波器的作用下，威胁模型 B⃝ 和 C⃝ 中的 SNN 仍能正确分类输入。输出概率在 Figure 7.26d 和 Figure 7.26e 中正确类与其他类之间的差距很大，这表明我们的防御方法具有高度的稳健性。

![Figure 7.26: Detailed example of a sequence of events labeled as left-hand wave. On the left, the frames of events are shown. The histograms on the right-most column report the number of spikes emitted by the neurons of the last layer, which correspond to the output classes. (a) Clean event series. (b) Event series filtered with s = 2 and t = 5. (c) Event series under the adversarial threat model A, unfiltered. (d) Event series under the adversarial threat model B, filtered with s = 2 and t = 5. (e) Event series under the adversarial threat model C, filtered with s = 2 and t = 5.](img/fig7_26.jpg)

Figure 7.26: Detailed example of a sequence of events labeled as *left-hand wave*. On the left, the frames of events are shown. The histograms on the right-most column report the number of spikes emitted by the neurons of the last layer, which correspond to the output classes. **(a)** Clean event series. **(b)** Event series filtered with *s* = 2 and *t* = 5. **(c)** Event series under the adversarial threat model A, unfiltered. **(d)** Event series under the adversarial threat model B, filtered with *s* = 2 and *t* = 5. **(e)** Event series under the adversarial threat model C, filtered with *s* = 2 and *t* = 5.

### 7.4.5 Summary

本节研究了基于 DVS 的系统对抗攻击对 SNN 的稳健性。我们提出的 *R-SNN* 方法通过 DVS 噪声滤波来提升对抗攻击的鲁棒性。本文是首次针对 DVS 信号进行对抗攻击的研究，也是首次将此类滤波器作为防御机制应用于此类攻击。它是一个概念证明（proof‑of‑concept），后续将在 Section 7.5 中考虑更高级的噪声滤波器和专门的对抗攻击方法。

## 7.5 Dvs-Attacks: a Set of Adversarial Attacks on Event-Based Snns




Despite being energy-efficient when deployed on neuromorphic hardware and coupled with event-based DVS cameras, SNNs are vulnerable to security issues, such as adversarial attacks. Toward this, we propose `DVS-Attacks`, a set of efficient yet stealthy adversarial attack algorithms targeted to perturb the event sequences that form the input of the SNNs. Then, we demonstrate that noise filters for DVS can be employed as a defense technique against adversarial attacks. Afterward, we implement and test the attacks in the presence of two types of noise filters for DVS signals. The experimental results indicate that the filters can only partially protect the SNNs against our proposed `DVS-Attacks`. Even using the noise filter defenses, our proposed `Mask Filter-Aware Dash Attack` can reduce the SNN accuracy by more than 20% on the DvsGesture dataset and by more than 65% on the NMNIST dataset, compared to the original clean frames.

### 7.5.1 System Overview

Different security threats challenge the normal functionality of DNNs and SNNs. The DNN trustworthiness has been thoroughly investigated in recent years, highlighting that one of the most critical issues is represented by adversarial attacks. Although some initial studies have been conducted, SNNs’ trustworthiness is a relatively unexplored problem. More precisely, DVS-based systems have not yet been systematically investigated for SNN security. The generation of adversarial attacks for DVS is an open research problem. Toward this, we propose `DVS-Attacks`, a set of adversarial attack algorithms for DVS signals, and test them in systems where noise filters are employed as a defensive mechanism against them. Since the DVS cameras also contain temporal information, the generation of adversarial examples is technically different than traditional adversarial attacks on images, in which only the spatial information is considered. Hence, the temporal information must be leveraged to develop the attack and defense mechanisms.

In a nutshell, we devise the following contributions:

*   We propose `DVS-Attacks`, a set of adversarial attack methodologies injecting perturbations into DVS signals.

*   In particular, the `MF-Aware Dash Attack` is specifically crafted to be resistant against the `Mask Filter` defense by adding perturbations only to a limited set of frames.

*   The experimental results on the DvsGesture and NMNIST datasets show that the attacks fool the SNNs when no filter is employed. Moreover, the noise filters cannot fully protect against the `DVS-Attacks`, which represent a critical security threat for SNN-based neuromorphic systems.

### 7.5.2 Case Study Analysis: SNN Robustness against Random Noise

We perform the following experiments as a preliminary study to motivate our research in the above-discussed directions. We trained a 4-layer SNN with 2 Conv and 2 FC layers for the DvsGesture dataset \[8\] using the SLAYER method \[248\] in a DL-workstation having two Nvidia GeForce RTX 2080 Ti GPUs. For every frame of events, we perturb the testing dataset by adding normally-distributed random noise and measuring the classification accuracy. Moreover, to mitigate the effects of the perturbations, the `Background Activity Filter` (`BAF`) and the `Mask Filter` (`MF`) of \[133\] are applied, with various filter parameters. Figure 7.27 shows the accuracy results for different noise magnitudes. As highlighted in the figure, the filter may reduce the SNN's accuracy when no noise is applied. More than 20% accuracy drop is noticed on the `MF` with `T` = 25, and lower drops for the other filters. However, when subjected to noise, the SNN becomes more robust when the filter is applied. For instance, when considering normally distributed noise with a magnitude of 0.55, the `BAF` with `s` = 1 and `t` = 5 contributes for up to 64% accuracy improvement. On the other hand, `BAFs` with `s` ≥ 2 do not increase the accuracy significantly compared to the unfiltered SNN. Moreover, `MFs` with `T` ≥ 100 work even better than the BAFs when affected by large noise perturbations. Indeed, the perturbations with a magnitude of 1.0 are filtered out relatively well by the `MFs` with large `T`, while, for the same value of noise magnitude, both the `MFs` with `T` ≤ 50 and the `BAF` with `s` = 1 and `t` = 5 obtain an accuracy of only ≈ 33 – 34%. The key message learned from this study is that the noise filters for DVS signals can restore a large portion of SNN accuracy that would have been lost due to the perturbations. This motivates us to employ such filters as defense mechanisms against adversarial attacks.

![Figure 7.27: Analyzing the impact of applying the normally-distributed noise to the DvsGesture dataset, in the presence of BAF and MF noise filters.](img/fig7_27.jpg)

Figure 7.27: Analyzing the impact of applying the normally-distributed noise to the DvsGesture dataset, in the presence of `BAF` and `MF` noise filters.

### 7.5.3 Noise Filters for Dynamic Vision Sensors

#### 7.5.3.1 Background Activity Filter

DVS sensors are typically affected by background activity noise generated by thermal noise and junction leakage current \[191\]. When the DVS sensor is stimulated, typically a neighborhood of pixels is simultaneously generating events. Therefore, the actual events have a higher spatio-temporal correlation compared to the noise-related events. This empirical intuition is exploited for generating the `Background Activity Filter (BAF)` \[133\]. If the correlation between events in a spatio-temporal neighborhood is lower than a certain threshold, the events are filtered out since they are likely due to noise. The procedure is reported in Algorithm 29, where the parameters *S* and *T* define the dimensions of the spatio-temporal neighborhood. For large *S* and *T*, several events are filtered out. The decision of the filter is made through the comparison between *t*[*e*] − *M*\[*x*[*e*]\[*y*[*e*\] and *T* (lines 8–9 of Algorithm 29).

![](img/comp07_7.jpg)

#### 7.5.3.2 Mask Filter

Another type of scenario of spontaneous noise activity is generated on the pixels with low temporal contrast. In this case, a `Mask Filter (MF)` is required to filter out such noise \[133\]. The procedure reported in Algorithm 30 shows that, compared to the `BAF`, the `MF` has only the temporal parameter *T*. The mask is activated if a pixel's activity exceeds *T* (lines 7-8 of Algorithm 30). After the mask is set, every event generated on a coordinate where the mask is active is removed (lines 10–11 of Algorithm 30). *Both the BAF and MF have been implemented and evaluated for intrinsic and parasitic noise added to DVS sensors, while their application as a defensive mechanism against adversarial attacks is still unexplored.*

![](img/comp07_8.jpg)

### 7.5.4 Threat Model



-   我们在实验中考虑的系统由一个用于捕获环境场景的事件序列的 DVS 相机以及在神经形态设备上部署的给定 SNN 组成。如 `Figure 7.28` 所示，对抗攻击和噪声过滤器位于 SNN 的输入端，可以修改事件序列。我们使用不同组合的攻击和防御进行多次实验。如 `Section 7.5.3` 所述，噪声过滤器被用作防御机制。对于同时应用攻击和防御的组合，攻击注入的扰动在过滤操作之前进行。这样可以过滤掉攻击生成或修改的所有事件，从而在实际系统中实现强有力的防御。关于对抗攻击方法的详细讨论在下文 `Section 7.5.5` 中进行。

![Figure 7.28: Threat model considered in this work, where different types of adversarial attacks are deployed, and different types of DVS noise filters are applied as a defense.`Figure 7.28:` 本工作考虑的威胁模型，其中不同类型的对抗攻击被部署，不同类型的 DVS 噪声过滤器被用作防御。### 7.5.5.1 Sparse Attack 拟议的 `Sparse Attack` 是一个迭代算法，针对数据集 `D` 的每个帧序列，根据损失函数（`Algorithm 31` 的第 2–7 行）逐步更新扰动值。其掩码 `M` 决定在哪些子集的事件帧中应添加扰动（第 3 行）。随后，在存在扰动的情况下，计算输出概率和相应的损失，分别在第 5 和第 6 行完成。最后，根据输入相对于损失的梯度更新扰动值（第 7 行）。![](img/comp07_9.jpg)

### 7.5.5.2 Frame Attack

`Frame Attack` 是一种简单而有效的攻击方法，主要通过在样本周围添加噪声帧来实现（参见 `Algorithm 32` 的第 4–5 行）。由于同一扰动（构成帧）被添加到所有样本，因此不需要昂贵的计算。该帧在包含大图像的数据集（如 DvsGesture，128 × 128）中不易被肉眼察觉，而在 NMNIST 数据集（34 × 34）中扰动更为明显。其缺点是会在样本上增加大量事件。事实上，每个帧的事件数量会显著增加，因为攻击针对每个边界像素，导致样本尺寸和使用 SNN 与过滤器处理事件的推理延迟也随之增大。

![](img/comp07_10.jpg)

### 7.5.5.3 Corner Attack

顾名思义，`Corner Attack` 目标是图像的角落。它首先只在左上角的两个像素上进行攻击（`Algorithm 33` 的第 8–9 行）。如果攻击未能成功误导 SNN（第 11 行），算法会转移到其他角落。如果在攻击了四个角后样本仍然被正确分类，扰动大小会增大，算法从头再来。在更新阶段，当攻击在不同角落之间切换或扰动大小增加时，会对尚未被损坏的样本逐一应用攻击。随着算法推进，样本数量会减少，整体过程会加速。`Corner Attack` 的主要特点是样本受到的扰动量各不相同。例如，虽然大多数样本在几次迭代后被 SNN 错误分类，但其他样本的扰动时间更长，使得攻击更容易被发现。

![](img/comp07_11.jpg)

### 7.5.5.4 Dash Attack

`Dash Attack` 的设计灵感来源于 `Corner Attack`，两者的算法结构相似。主要区别在于 `Dash Attack` 每次只针对两个像素进行攻击。其整体结构与 `Corner Attack` 类似：从左上角开始，修改前两个像素。此外，`x` 与 `y` 坐标会更新，使其在同一时间戳内命中两个相邻像素（参见 `Algorithm 34` 的第 14–22 行）。因此，该攻击难以被察觉，且对样本的事件开销不显著。`Dash Attack` 下的所有样本均受相同数量的扰动影响。

![](img/comp07_12.jpg)

### 7.5.5.5 MF-Aware Dash Attack

上述攻击的一个关键问题（将在 `Section 7.5.6` 中讨论）是它们对 `MF` 的固有弱点。它们在整个样本时间段内同时针对同一像素的“on” 与 “off” 通道。因此，被攻击的像素产生的事件数量显著多于未受影响的像素，导致攻击修改的像素与未受影响的像素之间的事件数量差异明显。此外，这些攻击主要集中在图像边缘，而在我们使用的数据集中，主体通常位于中心，因此攻击不太可能覆盖有用信息。因此，攻击主要作用于图像边缘或角落，从而降低了在主要主体上叠加对抗噪声的风险。这些考虑解释了为什么 `MF` 能够成功恢复原始 SNN 的准确性。被攻击的像素因其事件数量巨大而容易识别，而 `MF` 过滤不会干扰有用信息，因为修改主要发生在图像边缘。

基于上述观察，我们设计了一种旨在消除 `MF` 提供的防御效果的攻击，称之为 `MF-Aware Dash Attack`。该攻击的输入参数为 `th`，该参数关联于 `MF` 的 `T` 参数（回顾 `Algorithm 30`），并限制每个像素可修改的帧数（`Algorithm 35` 的第 11 行）。因此，算法仅扰动少量像素，类似于 `Dash Attack`；但在扰动了 `th` 帧后，会继续处理后续帧（第 13–14 行）。`MF-Aware Dash Attack` 产生一种“闪电”沿线前进的视觉效果。参数 `th` 越大，闪电看起来在图像上移动得越慢。

![](img/comp07_13.jpg)

### 7.5.6 Evaluation of the DVS-Attacks

#### 7.5.6.1 Experimental Setup



我们在两个数据集上进行实验，即 DvsGesture \[8\] 和 NMNIST \[193\]。对 DvsGesture 数据集，我们使用如文献 \[248\] 所述的 4 层 SNN 作为分类器，包含两个卷积层和两个全连接层，使用 SLAYER 反向传播方法 \[248\]，批量大小为 4，学习率为 0.01。在清洁数据集上，我们测得 92.04% 的测试准确率。对 NMNIST 数据集，我们实现了一个包含两个全连接层的多层感知器作为分类器 \[248\]，使用 SLAYER 反向传播方法 \[248\]，批量大小为 4，学习率为 0.01。测试准确率为 95%。我们使用 PyTorch 框架 \[204\] 在配备两块 Nvidia GeForce RTX 2080 Ti GPU 的 DL 工作站上实现 SNN。我们还使用 PyTorch 实现对抗攻击算法和噪声滤波器。

#### 7.5.6.2 Sparse Attack 结果

*Sparse Attack* 在 DVS 帧上成功欺骗了两个基准的 SNN，因为准确率显著下降至 DvsGesture 数据集的 15.15% 和 NMNIST 数据集的 4%。观察左侧的对抗示例（Figure 7.29），不可见显著扰动，因此 *Sparse Attack* 具有隐蔽性。然而，准确率可以通过噪声滤波器轻易恢复。当应用 *BAF* 滤波器时，对于 (*s*、 *t*) 参数的广泛范围，SNN 的准确率超过 90%（如 Figure 7.29 所示）。*Sparse Attack* 可以轻松绕过 *MF*，当 *T* 较低时。相反，当 DvsGesture 数据集的 *T* ≥ 50 且 NMNIST 数据集的 *T* ≥ 25 时，实现了高鲁棒性。

![Figure 7.29: Evaluation of the Sparse Attack: frame samples and accuracy when the BAF and MF are applied, for (a) DvsGesture and (b) NMNIST.](img/fig7_29.jpg)

Figure 7.29: Evaluation of the *Sparse Attack*: frame samples and accuracy when the *BAF* and *MF* are applied, for **(a)** DvsGesture and **(b)** NMNIST.

#### 7.5.6.3 Frame Attack 结果

*Frame Attack* 的实验结果在 Figure 7.30 中报告。如预期，扰动表现为添加在场景边界的线条，这一特征在 NMNIST 数据集上更为突出，因为其分辨率为 34 × 34 像素。而在这 128 × 128 示例的 DvsGesture 数据集上，扰动不易察觉。精度在 *Frame Attack* 下分别下降至 9.85% 和 8%。然而，*BAF* 作为防御效果不佳。如 Figure 7.30 所示，不存在 (*s*、 *t*) 参数使得 *BAF* 能够几乎恢复 SNN 的准确性。与无滤波的攻击相比，准确率变化相对较小。相反，*MF* 作为防御表现出色，因为在大 *T* 值下，SNN 的准确率保持较高。

![Figure 7.30: Evaluation of the Frame Attack: frame samples and accuracy when the BAF and MF are applied, for (a) DvsGesture and (b) NMNIST.](img/fig7_30.jpg)

Figure 7.30: Evaluation of the *Frame Attack*: frame samples and accuracy when the *BAF* and *MF* are applied, for **(a)** DvsGesture and **(b)** NMNIST.

#### 7.5.6.4 Corner Attack 结果

*Corner Attack* 比 *Frame Attack* 更隐蔽。扰动仅添加到图像的角落，例如在 Figure 7.31b 的第一个示例的左上角或第二个示例的左下角可见。而且，SNN 完全被 *Corner Attack* 骗，因为无过滤时的准确率下降至 0%。虽然 *BAF* 对 DvsGesture 数据集比 NMNIST 数据集表现更好，但在 *BAF* 过滤存在的情况下，准确率仍然很低。在 DvsGesture 数据集上，仅当 *s* = 1 且 *t* = 5 时，SNN 的准确率达到最高的 15.15%（如 Figure 7.31a 所示）。与 *Frame Attack* 类似，*Corner Attack* 也可以在应用大 *T* 的 *MF* 时成功缓解。

![Figure 7.31: Evaluation of the Corner Attack: frame samples and accuracy when the BAF and MF are applied, for (a) DvsGesture and (b) NMNIST.](img/fig7_31.jpg)

Figure 7.31: Evaluation of the *Corner Attack*: frame samples and accuracy when the *BAF* and *MF* are applied, for **(a)** DvsGesture and **(b)** NMNIST.

#### 7.5.6.5 Dash Attack 结果

*Dash Attack* 与 *Corner Attack* 类似，但扰动不严格局限于角落，因此注入的扰动与 DVS 相机捕获的背景活动噪声非常相似。例如，在 NMNIST 数据集的示例中（见 Figure 7.32b），攻击注入的扰动可能被背景噪声混淆。与 *Corner Attack* 相比，虽然 *Dash Attack* 下无过滤的 SNN 准确率下降至 0%，但 *BAF* 防御在 DvsGesture 数据集上产生略高的准确率。然而，在 *BAF* 下的最高准确率为 28.41%（如 Figure 7.32a 所示，对应 *s* = 1 与 *t* = 10），这不足以认为 *BAF* 是 *Dash Attack* 的合适防御方法。再次，大 *T* 的 *MF* 保证了对 SNN 的强健防御。

![Figure 7.32: Evaluation of the Dash Attack: frame samples and accuracy when the BAF and MF are applied, for (a) DvsGesture and (b) NMNIST.](img/fig7_32.jpg)

Figure 7.32: Evaluation of the *Dash Attack*: frame samples and accuracy when the *BAF* and *MF* are applied, for **(a)** DvsGesture and **(b)** NMNIST.

#### 7.5.6.6 MF-Aware Dash Attack 结果

Figure 7.33 评估了在 *MF-Aware Dash Attack* 下的实验，针对不同的 *th* 值。虽然对抗示例的感知性与 *Corner* 和 *Dash Attack* 类似，但当应用噪声滤波器时，*MF-Aware Dash Attack* 的行为有所不同。此外，在没有过滤的情况下，SNN 在 DvsGesture 数据集上达到 7.95% 的准确率（对 *t**h** = 50）。使用 *BAF* 防御的 SNN 表现出适度的鲁棒性。当 *s* = 3 且 *t* = 1 时，在应用 *MF-Aware Dash Attack* 与 *t**h** = 50 时，DvsGesture 数据集的准确率达到 59.09%。然而，当 *t* ≥ 5 时，DvsGesture 数据集的准确率低于 31.44%，NMNIST 数据集低于 13%。与前几次攻击相比，*MF-Aware Dash Attack* 在 *MF* 存在时的表现更为出色。若 *T* ≥ *t**h**，则 DvsGesture 数据集的准确率低于 23.5%，NMNIST 数据集低于 2%。相反，当 *T* < *t**h** 时，结果与其他攻击的行为相似。例如，*MF-Aware Dash Attack* 与 *t**h** = 50 且 *T* = 25 的曲线在 DvsGesture 数据集上达到 71.21% 的准确率，这比无噪声的 SNN 准确率低 20.83%。




-   Figure 7.33: 评估 *MF-感知冲刺攻击*：当应用 *BAF* 和 *MF* 时的帧样本和准确率，用于 **(a)** DvsGesture 和 **(b)** NMNIST。图左侧报告的对抗帧样本是使用 DvsGesture 数据集的 *t**h** = 150* 和 NMNIST 数据集的 *t**h** = 20* 生成的。

#### 7.5.6.7  实验得出的关键观察

通过更详细地分析不同攻击方法的结果，我们可以得出以下关键观察：

*   所有属于 *DVS-Attacks* 集合的攻击算法在未应用过滤器的情况下能够成功欺骗 SNNs，如 SNNs 精度显著下降所显示。

*   *Sparse Attack* 是最隐蔽的攻击，而 *Corner, Dash* 和 *MF-Aware Dash Attack* 相比 *Frame Attack* 更具隐蔽性。

*   *BAF* 仅在 *Sparse Attack* 上提供良好的防御效果，其他所有攻击都能够欺骗受 *BAF* 保护的 SNNs。 *MF-Aware Dash Attack* 部分恢复了准确性，但测量到显著的准确率损失。

*   *BAF* 的不同 (*s*, *t*) 参数组合需要评估以找到最高准确率，且不同攻击算法对这些参数组合的最佳取值可能不同。

*   采用大 *T* 的 *MF* 是对几乎所有攻击的有效防御，但它对 *MF-Aware Dash Attack* 效果不佳，因为该攻击专门设计用于在 *MF* 存在时取得成功。

*   *MF-Aware Dash Attack* 的最佳表现分别在 DvsGesture 数据集上使用 *t**h** = 50*、在 NMNIST 数据集上使用 *t**h** = 10*，会使 SNNs 的准确率下降超过 20% 和 65%。

### 7.5.7 总结

提出的 DVS-Attacks 是一系列高效且隐蔽的对抗性攻击方法，用于扰动 SNNs 输入的事件序列。像 BAF 和 MF 这样的 DVS 信号噪声过滤器可以作为防御机制使用。在过滤器存在下对攻击的评估表明，过滤器能够部分恢复 SNN 精度，但专门设计用于对抗过滤器的攻击，如 MF-aware Dash Attack，仍具有高成功率。

## 7.6 Snns 的安全威胁概述

本章探讨了针对 SNNs 的多种安全威胁分析，并将其与 DNNs 进行比较。研究了包括针对离散和事件数据的对抗攻击方法以及植入后门导致位翻转的威胁。同时，利用调节 SNNs 固有结构参数的防御机制来提高其鲁棒性。针对事件域的攻击，噪声过滤器可以成功应用。然而，专门设计的攻击展示了能够绕过这些过滤器的潜力。这套全面的分析和研究为在安全关键应用中部署 SNNs 提供了先进的优化策略。结合其高鲁棒性与在神经形态计算平台上的低能耗实现，SNNs 成为强大且节能的深度学习系统的有前途解决方案。

## Chapter 8Conclusion and Outlook

DOI: [10.1201/9781003530459-8](https://doi.org/10.1201/9781003530459-8)

## 8.1 书籍概述

DNNs 已经彻底改变了各种任务的高精度预测生成方式。然而，它们计算和存储需求巨大，使得在资源受限设备上的部署面临挑战。此外，ML 社区的当前趋势表明，尽管高学习能力，高复杂度的 DL 架构仍带来更严格的约束。而且，DNNs 受到多种威胁影响，威胁其完整性，也质疑了其在安全关键应用中的实际部署。

本书通过利用先进 DL 系统的能量降低和安全增强潜力来应对这些挑战。为此，*在软件和硬件层面提出了新的技术*。采用多目标技术实现跨层优化，以提升能源效率和鲁棒性。高复杂度先进 DL 模型（如 CapsNets 和 SNNs）需要专用设计和优化以实现能源效率，同时提供独特的鲁棒性提升可能性。

其中一个关键贡献是 *CapsNets 执行优化的完整设计流程*。与传统 DNN 不同，CapsNets 包含如“压缩”和“动态路由”等更复杂的操作，这些操作在标准 DL 加速器上执行效率低。因此，需要专用设计来实现其高效执行。所提议的优化流程包括快速训练框架、计算单元硬件设计和内存组织、训练后量化与近似。在探索设计空间时，采用启发式算法利用能耗、延迟、面积和内存之间的权衡，同时监控精度。*这种端到端的设计流程和一系列优化措施使得在硬件资源有限的嵌入式设备上部署 CapsNets 成为可能*。

已进行多项安全分析，针对 CapsNets 在安全关键应用中的部署进行了比较。对 CapsNets 和 DNNs 的仿射变换和对抗攻击鲁棒性进行了研究和比较。此外，*提出了新的对抗攻击生成技术*。评估表明，在规模相似的情况下，CapsNets 通常比传统 DNN 更具鲁棒性，而在某些情况下，CapsNets 的鲁棒性甚至高于更深的 CNN 模型（如 ResNet）。

NAS（神经结构搜索）方法的出现使得在给定任务上可以以最小设计努力创建高精度 DNN。然而，高精度不一定意味着高能源效率或鲁棒性。为此，*所提议的流程将硬件效率和鲁棒性作为 NAS 算法的多目标优化目标*。因此，这种多目标 NAS 通过在专用硬件加速器上运行时，塑造 DNN 的结构和模型参数，以在精度、鲁棒性和硬件效率之间取得权衡。




SNNs 代表了先进 ML 模型的另一前沿研究方向。它们是生物学上可信的模型，与传统 DNNs 相比在实现于与 DVS 相机相连的神经形态设备时，功耗更低。然而，它们在各种应用领域的部署以及可靠性仍未得到充分探索。为此，`已设计了一套针对 Loihi 神经形态硬件芯片的 SNN 优化和实现方案`。了解目标硬件平台的规格和资源限制，使得能够在塑造低延迟、低能耗的 SNN 以适应各种应用时，调整其架构模型、训练规则以及预处理机制。此外，SNN 的脆弱性威胁已被研究。利用调节 SNN 固有结构参数的防御机制，可以提升其鲁棒性。噪声过滤在事件域中是成功的防御手段，但专门设计的攻击在特定设置下可以绕过这些过滤。鉴于其高鲁棒性与在神经形态设备上的低能耗相结合，`SNNs 代表了能源高效且具备强健性的深度学习系统的有前途的计算基础设施`。

## 8.2 拟议技术在不断演进的机器学习领域中的作用

拟议技术已被证明能够优化先进 DL 模型的能源效率和鲁棒性。然而，在机器学习这一快速演进的领域中，全球数千甚至数百万研究人员都在从事类似研究，保持与最新进展同步颇具挑战性。若缺乏应有的谨慎，前沿方法可能因新技术在性能或效率上超越它，或以更高效的方式从不同角度解决同一问题而迅速被淘汰。为减轻这些问题，并维持其在不断演进的机器学习领域中的关键角色，我们的技术具备以下特性。

*   `与其他优化技术正交`：我们的优化方法与其他优化技术正交。因此，若提出新方法，可将其纳入优化流程。例如，量化方法与剪枝等压缩技术正交，若提出新的剪枝方法，可与我们的量化方法一起使用，进一步提升能源效率。

*   `模块化`：我们的框架采用可扩展的模块化构建块，可轻松加入新算法和技术。例如，我们的多目标 NAS 框架具有模块化的层描述符，因此搜索空间可轻松扩展为新的层类型。

*   `与 DL 模型的黑盒关系`：我们的技术不依赖于被研究的 DNN、CapsNet 或 SNN 的具体架构。这一特性使得可以将我们的方法应用于文献中提出的新型 DL 模型，并适配不同应用和数据集。例如，我们提出的黑盒对抗攻击方法可部署于新提出的 DL 模型，并适配不同应用和数据集。

*   `开源`：我们的框架公开于在线仓库，其他研究人员可使用代码复现实验，并直接修改我们的方法以契合最新的研究方向。

## 8.3 未来工作

本文通过对多种实验条件的评估以及与相关最新研究的对比，凸显出缓解 DL 架构的能源和安全问题的迫切需求。下一代计算基础设施必须在资源受限的前提下支持复杂操作，并保证在各种不利条件下的高鲁棒性。本研究的宝贵贡献和成果为能源感知、成本效益的鲁棒性打开了新的研究方向，具体包括以下列表。

*   **能源效率优化**

    拟议设计表明，先进 DNN 对低精度和压缩技术的容忍度很强。但其容忍上限仍是一个开放的研究问题：我们能在不牺牲精度和鲁棒性的前提下，压缩和近似到何种程度？为此，细粒度剪枝和量化可使能源消耗更接近下限。

    另一个令人兴奋的研究方向是扩展 NAS 框架，探索硬件架构参数和内存配置的解空间。在此框架下，优化问题可同时搜索神经模型与硬件架构，以实现额外的能源节约。

    随着其他类先进 ML 模型（如 Transformer）的出现，需要专门的硬件与软件优化，以最小化其能耗。例如，可通过设计专用硬件模块来执行高级层和操作（如注意力机制），并在 NAS 操作中加入这些操作，以实现更高效的能耗优化。

    传统的计算范式将逻辑与存储分离，可能很快被新兴的在内存计算范式取代，即在特定存储单元内进行计算。该策略可显著降低内存访问次数，从而大幅提升系统的整体能源效率。

*   **面向事件驱动神经形态计算的算法与应用**

    在神经形态硬件上实现的拟议设计展示了在多种任务上实现快速性能和高能效的前景。另一方面，安全分析揭示了其弱点和鲁棒性。这些结果为在安全关键域部署基于事件的 SNN 提供了乐观前景。然而，其在各类应用中的实现仍是空白且不成熟。所有类型的控制与自主系统（如车辆、机器人、无人机）均可从在事件驱动平台上部署中获益。

    另一个有前景的研究方向是重新审视 SNN 的基本功能，设计更高效的神经元、突触以及专用的尖峰编码机制。此类研究可能催生更高效的计算与学习引擎，塑造未来我们日常生活的形态。

    此外，持续学习范式——即网络权重逐步更新以适应新输入分布——有望在保持低功耗的同时，提升 SNN 的精度和鲁棒性。

*   **鲁棒性与安全导向的优化**

    本书展示，各类攻击威胁层出不穷。对手在创造新颖、高效的攻击方法时愈发敏捷。防御技术应能够快速适应，以抵御新兴攻击。

    同时，强健防御应在不影响系统性能的前提下，防范多种脆弱性威胁。为此，鲁棒性方法可在优化目标中加入不仅对抗鲁棒性，还包括容错性、隐私保护、硬件安全以及其他根据系统需求而定的保护机制。

    另一个重要的研究方向是能源感知优化对 DL 系统鲁棒性的影响。例如，研究近似对系统鲁棒性的影响，可能导致设计专用的近似组件，从而增强系统的鲁棒性。

*   **跨层优化进一步探索**




-   [多目标 NAS 方法](https://wiki.example.org/feynmans_learning_method)基于进化算法，另一种确定架构参数的有前途的研究方向是可微分 NAS。

-   隐私保护深度学习的前景正在转向不泄露敏感内容的加密与解密机制。为此，为加密深度学习系统设计专用加速器是迫切需要的，因为其计算复杂度被禁止。加密属性也可以纳入 NAS 框架，以保障深度学习系统的安全。

## Bibliography

*   [\[1\]](#chapter2.xhtml#b2refbib1) Martn Abadi, Paul Barham, Jianmin Chen, Zhifeng Chen, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Geoffrey Irving, Michael Isard, Manjunath Kudlur, Josh Levenberg, Rajat Monga, Sherry Moore, Derek Gordon Murray, Benoit Steiner, Paul A. Tucker, Vijay Vasudevan, Pete Warden, Martin Wicke, Yuan Yu, and Xiaoqiang Zheng. Tensorflow: A system for large-scale machine learning. In Kimberly Keeton and Timothy Roscoe, editors, 12th USENIX Symposium on Operating Systems Design and Implementation, OSDI 2016, *Savannah, GA, USA*, *November 2-4, 2016*, pages 265–283. USENIX Association, 2016.

*   [\[2\]](#chapter1.xhtml#b1refbib2) Martn Abadi, Andy Chu, Ian J. Goodfellow, H. Brendan McMahan, Ilya Mironov, Kunal Talwar, and Li Zhang. Deep learning with differential privacy. In Edgar R. Weippl, Stefan Katzenbeisser, Christopher Kruegel, Andrew C. Myers, and Shai Halevi, editors, *Proceedings of the 2016 ACM SIGSAC Conference on Computer and Communications Security, Vienna*, *Austria, October 24-28, 2016*, pages 308–318. ACM, 2016.

*   [\[3\]](#chapter7.xhtml#b7refbib3) Imran Hafeez Abbassi, Faiq Khalid, Semeen Rehman, Awais Mehmood Kamboh, Axel Jantsch, Siddharth Garg, and Muhammad Shafique. Trojanzero: Switching activity-aware design of undetectable hardware trojans with zero power and area footprint. In Jürgen Teich and Franco Fummi, editors, *Design, Automation & Test in Europe Conference & Exhibition, DATE 2019, Florence, Italy, March 25-29, 2019*, pages 914–919. IEEE, 2019.

*   [\[4\]](#chapter2.xhtml#b2refbib4) Paniti Achararit, Muhammad Abdullah Hanif, Rachmad Vidya Wicaksana Putra, Muhammad Shafique, and Yuko Hara-Azumi. APNAS: accuracy-and-performance-aware neural architecture search for neural hardware accelerators. IEEE Access, 8: 165319–165334, 2020.

*   [\[5\]](#chapter2.xhtml#b2refbib5) Michel Agoyan, Jean-Max Dutertre, Amir-Pasha Mirbaha, David Naccache, Anne-Lise Ribotta, and Assia Tria. How to flip a bit? In *16th IEEE International On-Line Testing Symposium (IOLTS 2010), 5-7 July, 2010, Corfu, Greece*, pages 235–239. IEEE Computer Society, 2010.

*   [\[6\]](#chapter2.xhtml#b2refbib6) Hassan Ali, Faiq Khalid, Hammad Tariq, Muhammad Abdullah Hanif, Rehan Ahmed, and Semeen Rehman. Sscnets: Robustifying dnns using secure selective convolutional filters. IEEE Des. Test, 37(2):58–65, 2020.

*   [\[7\]](#chapter3.xhtml#b3refbib7) H. Amin, K.M. Curtis, and B.R. Hayes-Gill. Piecewise linear approximation applied to nonlinear function of a neural network. *IEE Proceedings - Circuits, Devices and Systems*, 144(6):313–317, 1997.

*   [\[8\]](#chapter2.xhtml#b2refbib8) Arnon Amir, Brian Taba, David J. Berg, Timothy Melano, Jeffrey L. McKinstry, Carmelo di Nolfo, Tapan K. Nayak, Alexander Andreopoulos, Guillaume Garreau, Marcela Mendoza, Jeff Kusnitz, Michael DeBole, Steven K. Esser, Tobi Delbrück, Myron Flickner, and Dharmendra S. Modha. A low power, fully event-based gesture recognition system. In *2017 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2017, Honolulu, HI, USA, July 21-26, 2017*, pages 7388–7397. IEEE Computer Society, 2017.

*   [\[9\]](#chapter3.xhtml#b3refbib9) Kevin Bache, Dennis DeCoste, and Padhraic Smyth. Hot swapping for online adaptation of optimization hyperparameters. In Yoshua Bengio and Yann LeCun, editors, *3rd International Conference on Learning Representations, ICLR 2015, San Diego, CA, USA, May 7-9, 2015, Workshop Track Proceedings*, 2015.

*   [\[10\]](#chapter2.xhtml#b2refbib10) Alireza Bagheri, Osvaldo Simeone, and Bipin Rajendran. Adversarial training for probabilistic spiking neural networks. In *19th IEEE International Workshop on Signal Processing Advances in Wireless Communications, SPAWC 2018, Kalamata, Greece, June 25-28, 2018*, pages 1–5. IEEE, 2018.

*   [\[11\]](#chapter2.xhtml#b2refbib11) R.C. Baumann. Radiation-induced soft errors in advanced semiconductor technologies. IEEE Transactions on Device and Materials Reliability, 5(3):305–316, 2005.

*   [\[12\]](#chapter6.xhtml#b6refbib12) Trevor Bekolay, James Bergstra, Eric Hunsberger, Travis DeWolf, Terrence C. Stewart, Daniel Rasmussen, Feng-Xuan Choo, Aaron Voelker, and Chris Eliasmith. Nengo: a python tool for building large-scale functional brain models. Frontiers Neuroinformatics, 7: 48, 2013.

*   [\[13\]](#chapter2.xhtml#b2refbib13) Yoshua Bengio. Learning deep architectures for AI. Foundations and Trends in Machine Learning, 2(1):1–127, 2009.

*   [\[14\]](#chapter3.xhtml#b3refbib14) Yoshua Bengio. Practical recommendations for gradient-based training of deep architectures. In Grégoire Montavon, Genevieve B. Orr, and Klaus-Robert Müller, editors, Neural Networks: Tricks of the Trade - Second Edition, volume 7700 of *Lecture Notes in Computer Science*, pages 437–478. Springer, 2012.

*   [\[15\]](#chapter7.xhtml#b7refbib15) Yoshua Bengio, Pascal Lamblin, Dan Popovici, and Hugo Larochelle. Greedy layer-wise training of deep networks. In Bernhard Schölkopf, John C. Platt, and Thomas Hofmann, editors, *Advances in Neural Information Processing Systems 19, Proceedings of the Twentieth Annual Conference on Neural Information Processing Systems, Vancouver, British Columbia, Canada, December 4-7, 2006*, pages 153–160. MIT Press, 2006.

*   [\[16\]](#chapter2.xhtml#b2refbib16) Ben Varkey Benjamin, Peiran Gao, Emmett McQuinn, Swadesh Choudhary, Anand Chandrasekaran, Jean-Marie Bussat, Rodrigo Alvarez-Icaza, John V. Arthur, Paul Merolla, and Kwabena Boahen. Neurogrid: A mixed-analog-digital multichip system for large-scale neural simulations. Proc. IEEE, 102(5):699–716, 2014.

*   [\[17\]](#chapter6.xhtml#b6refbib17) Alan C. Bovik, Marianna Clark, and Wilson S. Geisler. Multichannel texture analysis using localized spatial filters. IEEE Trans. Pattern Anal. Mach. Intell., 12(1):55–73, 1990.

*   [\[18\]](#chapter2.xhtml#b2refbib18) Christian Brandli, Raphael Berner, Minhao Yang, Shih-Chii Liu, and Tobi Delbrück. A 240 180 130 db 3 *µ*s latency global shutter spatiotemporal vision sensor. IEEE J. Solid State Circuits, 49(10):2333–2341, 2014.

*   [\[19\]](#chapter2.xhtml#b2refbib19) Jakub Breier, Xiaolu Hou, Dirmanto Jap, Lei Ma, Shivam Bhasin, and Yang Liu. Practical fault attack on deep neural networks. In David Lie, Mohammad Mannan, Michael Backes, and XiaoFeng Wang, editors, *Proceedings of the 2018 ACM SIGSAC Conference on Computer and Communications Security, CCS 2018, Toronto, ON, Canada, October 15-19, 2018*, pages 2204–2206. ACM, 2018.

*   [\[20\]](#chapter2.xhtml#b2refbib20) Wieland Brendel, Jonas Rauber, and Matthias Bethge. Decision-based adversarial attacks: Reliable attacks against black-box machine learning models. In the *6th International Conference on Learning Representations, ICLR 2018, Vancouver, BC, Canada, April 30—May 3, 2018, Conference Track Proceedings*. [OpenReview.net](https://OpenReview.net), 2018.

*   [\[21\]](#chapter2.xhtml#b2refbib21) Julian Büchel, Gregor Lenz, Yalun Hu, Sadique Sheik, and Martino Sorbaro. Adversarial attacks on spiking convolutional networks for event-based vision. *CoRR*, abs/2110.02929, 2021.




-   [\[22\]](#chapter1.xhtml#b1refbib22) Maurizio Capra, Beatrice Bussolino, Alberto Marchisio, Guido Masera, Maurizio Martina, and Muhammad Shafique. Hardware and software optimizations for accelerating deep neural networks: Survey of current trends, challenges, and the road ahead. IEEE Access, 8: 225134–225180, 2020.

-   [\[23\]](#chapter2.xhtml#b2refbib23) Maurizio Capra, Beatrice Bussolino, Alberto Marchisio, Muhammad Shafique, Guido Masera, and Maurizio Martina. An updated survey of efficient hardware architectures for accelerating deep convolutional neural networks. Future Internet, 12(7):113, 2020.

-   [\[24\]](#chapter2.xhtml#b2refbib24) Nicholas Carlini and David A. Wagner. Towards evaluating the robustness of neural networks. In *2017 IEEE Symposium on Security and Privacy, SP 2017, San Jose, CA, USA, May 22-26, 2017*, pages 39–57. IEEE Computer Society, 2017.

-   [\[25\]](#chapter3.xhtml#b3refbib25) M. Emre Celebi, Fatih Celiker, and Hassan A. Kingravi. On euclidean norm approximations. Pattern Recognit., 44(2):278–283, 2011.

-   [\[26\]](#chapter2.xhtml#b2refbib26) Chia-Yu Chen, Jungwook Choi, Kailash Gopalakrishnan, Viji Srinivasan, and Swagath Venkataramani. Exploiting approximate computing for deep learning acceleration. In Jan Madsen and Ayse K. Coskun, editors, *2018 Design, Automation & Test in Europe Conference & Exhibition, DATE 2018, Dresden, Germany, March 19-23, 2018*, pages 821–826. IEEE, 2018.

-   [\[27\]](#chapter6.xhtml#b6refbib27) Liang-Chieh Chen, George Papandreou, Florian Schroff, and Hartwig Adam. Rethinking atrous convolution for semantic image segmentation. *CoRR*, abs/1706.05587, 2017.

-   [\[28\]](#chapter2.xhtml#b2refbib28) Shoushun Chen and Menghan Guo. Live demonstration: Celex-v: A 1m pixel multi-mode event-based sensor. In the *IEEE Conference on Computer Vision and Pattern Recognition Workshops, CVPR Workshops 2019, Long Beach, CA, USA, June 16-20, 2019*, pages 1682–1683. Computer Vision Foundation/IEEE, 2019.

-   [\[29\]](#chapter1.xhtml#b1refbib29) Yu-Hsin Chen, Joel S. Emer, and Vivienne Sze. Eyeriss: A spatial architecture for energy-efficient dataflow for convolutional neural networks. In *43rd ACM/IEEE Annual International Symposium on Computer Architecture, ISCA 2016, Seoul, South Korea, June 18-22, 2016*, pages 367–379. IEEE Computer Society, 2016.

-   [\[30\]](#chapter2.xhtml#b2refbib30) Yu-Hsin Chen, Joel S. Emer, and Vivienne Sze. Using dataflow to optimize energy efficiency of deep neural network accelerators. IEEE Micro, 37(3):12–21, 2017.

-   [\[31\]](#chapter1.xhtml#b1refbib31) Yu-Hsin Chen, Tien-Ju Yang, Joel S. Emer, and Vivienne Sze. Eyeriss v2: A flexible accelerator for emerging deep neural networks on mobile devices. IEEE J. Emerg. Sel. Topics Circuits Syst., 9(2):292–308, 2019.

-   [\[32\]](#chapter1.xhtml#b1refbib32) Zitao Chen, Guanpeng Li, and Karthik Pattabiraman. Ranger: Boosting error resilience of deep neural networks through range restriction. *CoRR*, abs/2003.13874, 2020.

-   [\[33\]](#chapter2.xhtml#b2refbib33) Wensheng Cheng, Hao Luo, Wen Yang, Lei Yu, Shoushun Chen, and Wei Li. DET: A high-resolution DVS dataset for lane extraction. In *IEEE Conference on Computer Vision and Pattern Recognition Workshops, CVPR Workshops 2019, Long Beach, CA, USA, June 16-20, 2019*, pages 1666–1675. Computer Vision Foundation/IEEE, 2019.

-   [\[34\]](#chapter2.xhtml#b2refbib34) Sharan Chetlur, Cliff Woolley, Philippe Vandermersch, Jonathan Cohen, John Tran, Bryan Catanzaro, and Evan Shelhamer. cudnn: Efficient primitives for deep learning. *CoRR*, abs/1410.0759, 2014.

-   [\[35\]](#chapter6.xhtml#b6refbib35) Shriyash Chougule, Nora Kozonek, Asad Ismail, Ganesh Adam, Vikram Narayan, and Matthias Schulze. Reliable multilane detection and classification by utilizing CNN as a regression network. In Laura Leal-Taixé and Stefan Roth, editors, *Computer Vision - ECCV 2018 Workshops - Munich, Germany, September 8-14, 2018, Proceedings, Part V,* volume 11133 of *Lecture Notes in Computer Science*, pages 740–752. Springer, 2018.

-   [\[36\]](#chapter2.xhtml#b2refbib36) Joseph Clements and Yingjie Lao. Hardware trojan design on neural networks. In *IEEE International Symposium on Circuits and Systems, ISCAS 2019, Sapporo, Japan, May 26-29, 2019*, pages 1–5. IEEE, 2019.

-   [\[37\]](#chapter2.xhtml#b2refbib37) Jeremy M. Cohen, Elan Rosenfeld, and J. Zico Kolter. Certified adversarial robustness via randomized smoothing. In Kamalika Chaudhuri and Ruslan Salakhutdinov, editors, *Proceedings of the 36th International Conference on Machine Learning, ICML 2019, 9-15 June 2019, Long Beach, California, USA*, volume 97 of *Proceedings of Machine Learning Research*, pages 1310–1320. PMLR, 2019.

-   [\[38\]](#chapter2.xhtml#b2refbib38) Alessio Colucci, Andreas Steininger, and Muhammad Shafique. enpheeph: A fault injection framework for spiking and compressed deep neural networks. *CoRR*, abs/2208.00328, 2022.

-   [\[39\]](#chapter6.xhtml#b6refbib39) Jonathan Cook and Vikram Ramadas. When to consult precision-recall curves. The Stata Journal, 20(1):131–148, 2020.

-   [\[40\]](#chapter1.xhtml#b1refbib40) Mike Davies, Narayan Srinivasa, Tsung-Han Lin, Gautham N. Chinya, Yongqiang Cao, Sri Harsha Choday, Georgios D. Dimou, Prasad Joshi, Nabil Imam, Shweta Jain, Yuyun Liao, Chit-Kwan Lin, Andrew Lines, Ruokun Liu, Deepak Mathaikutty, Steven McCoy, Arnab Paul, Jonathan Tse, Guruguhanathan Venkataramanan, Yi-Hsin Weng, Andreas Wild, Yoonseok Yang, and Hong Wang. Loihi: A neuromorphic manycore processor with on-chip learning. IEEE Micro, 38(1):82–99, 2018.

-   [\[41\]](#chapter2.xhtml#b2refbib41) Andrew P. Davison, Daniel Brüderle, Jochen M. Eppler, Jens Kremkow, Eilif B. Müller, Dejan Pecevski, Laurent U. Perrinet, and Pierre Yger. Pynn: a common interface for neuronal network simulators. Frontiers Neuroinformatics, 2: 11, 2008.

-   [\[42\]](#chapter3.xhtml#b3refbib42) Kalyanmoy Deb, Samir Agrawal, Amrit Pratap, and T. Meyarivan. A fast and elitist multiobjective genetic algorithm: NSGA-II. IEEE Trans. Evol. Comput., 6(2):182–197, 2002.

-   [\[43\]](#chapter2.xhtml#b2refbib43) Jia Deng, Wei Dong, Richard Socher, Li-Jia Li, Kai Li, and Li Fei-Fei. Imagenet: A large-scale hierarchical image database. In *2009 IEEE Computer Society Conference on Computer Vision and Pattern Recognition (CVPR 2009), 20-25 June 2009, Miami, Florida, USA*, pages 248–255. IEEE Computer Society, 2009.

-   [\[44\]](#chapter3.xhtml#b3refbib44) Aditya Devarakonda, Maxim Naumov, and Michael Garland. Adabatch: Adaptive batch sizes for training deep neural networks. *CoRR*, abs/1712.02029, 2017.

-   [\[45\]](#chapter6.xhtml#b6refbib45) Peter U. Diehl, Daniel Neil, Jonathan Binas, Matthew Cook, Shih-Chii Liu, and Michael Pfeiffer. Fast-classifying, high-accuracy spiking deep networks through weight and threshold balancing. In *2015 International Joint Conference on Neural Networks, IJCNN 2015, Killarney, Ireland, July 12-17, 2015*, pages 1–8. IEEE, 2015.

-   [\[46\]](#chapter2.xhtml#b2refbib46) Zidong Du, Robert Fasthuber, Tianshi Chen, Paolo Ienne, Ling Li, Tao Luo, Xiaobing Feng, Yunji Chen, and Olivier Temam. Shidiannao: shifting vision processing closer to the sensor. In Deborah T. Marr and David H. Albonesi, editors, *Proceedings of the 42nd Annual International Symposium on Computer Architecture, Portland, OR, USA, June 13-17, 2015*, pages 92–104. ACM, 2015.

-   [\[47\]](#chapter1.xhtml#b1refbib47) Rida El-Allami, Alberto Marchisio, Muhammad Shafique, and Ihsen Alouani. Securing deep spiking neural networks against adversarial attacks through inherent structural parameters. In *Design, Automation & Test in Europe Conference & Exhibition, DATE 2021, Grenoble, France, February 1-5, 2021*, pages 774–779. IEEE, 2021.



-   [\[48\]](#chapter2.xhtml#b2refbib48) Kevin Eykholt, Ivan Evtimov, Earlence Fernandes, Bo Li, Amir Rahmati, Chaowei Xiao, Atul Prakash, Tadayoshi Kohno, and Dawn Song. Robust physical-world attacks on deep learning visual classification. In `2018 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2018, Salt Lake City, UT, USA, June 18-22, 2018`, pages 1625–1634. Computer Vision Foundation/IEEE Computer Society, 2018.

-   [\[49\]](#chapter1.xhtml#b1refbib49) Reza Fani and Morteza Saheb Zamani. Runtime hardware trojan detection by reconfigurable monitoring circuits. The Journal of Supercomputing, 2022.

-   [\[50\]](#chapter2.xhtml#b2refbib50) Thomas Finateu, Atsumi Niwa, Daniel Matolin, Koya Tsuchimoto, Andrea Mascheroni, Etienne Reynaud, Pooria Mostafalu, Frederick T. Brady, Ludovic Chotard, Florian LeGoff, Hirotsugu Takahashi, Hayato Wakabayashi, Yusuke Oike, and Christoph Posch. 5.10 A 1280720 back-illuminated stacked temporal contrast event-based vision sensor with 4.86µm pixels, 1.066geps readout, programmable event-rate controller and compressive data-formatting pipeline. In `2020 IEEE International Solid- State Circuits Conference, ISSCC 2020, San Francisco, CA, USA, February 16-20, 2020`, pages 112–114. IEEE, 2020.

-   [\[51\]](#chapter1.xhtml#b1refbib51) Jonathan Frankle and Michael Carbin. The lottery ticket hypothesis: Finding sparse, trainable neural networks. In `7th International Conference on Learning Representations, ICLR 2019, New Orleans, LA, USA, May 6-9, 2019`. [OpenReview.net](https://OpenReview.net), 2019.

-   [\[52\]](#chapter2.xhtml#b2refbib52) Scott Freeman and Healy Hamilton. `Biological Science`, 2005.

-   [\[53\]](#chapter2.xhtml#b2refbib53) Charlotte Frenkel, Martin Lefebvre, Jean-Didier Legat, and David Bol. A 0.086-mm² 12.7-pj/sop 64k-synapse 256-neuron online-learning digital spiking neuromorphic processor in 28-nm CMOS. IEEE Trans. Biomed. Circuits Syst., 13(1):145–158, 2019.

-   [\[54\]](#chapter2.xhtml#b2refbib54) Nicholas Frosst, Sara Sabour, and Geoffrey E. Hinton. DARCCC: detecting adversaries by reconstruction from class conditional capsules. `CoRR`, abs/1811.06969, 2018.

-   [\[55\]](#chapter2.xhtml#b2refbib55) Steve B. Furber, Francesco Galluppi, Steve Temple, and Luis A. Plana. The spinnaker project. Proc. IEEE, 102(5):652–665, 2014.

-   [\[56\]](#chapter2.xhtml#b2refbib56) Stefano Fusi, Mario Annunziato, Davide Badoni, Andrea Salamon, and Daniel J. Amit. Spike-driven synaptic plasticity: Theory, simulation, VLSI implementation. Neural Comput., 12(10):2227–2258, 2000.

-   [\[57\]](#chapter2.xhtml#b2refbib57) Guillermo Gallego, Tobi Delbrück, Garrick Orchard, Chiara Bartolozzi, Brian Taba, Andrea Censi, Stefan Leutenegger, Andrew J. Davison, Jörg Conradt, Kostas Daniilidis, and Davide Scaramuzza. Event-based vision: A survey. IEEE Trans. Pattern Anal. Mach. Intell., 44(1):154–180, 2022.

-   [\[58\]](#chapter2.xhtml#b2refbib58) Karan Ganju, Qi Wang, Wei Yang, Carl A. Gunter, and Nikita Borisov. Property inference attacks on fully connected neural networks using permutation invariant representations. In David Lie, Mohammad Mannan, Michael Backes, and XiaoFeng Wang, editors, `Proceedings of the 2018 ACM SIGSAC Conference on Computer and Communications Security, CCS 2018, Toronto, ON, Canada, October 15-19, 2018`, pages 619–633. ACM, 2018.

-   [\[59\]](#chapter3.xhtml#b3refbib59) Yue Gao, Weiqiang Liu, and Fabrizio Lombardi. Design and implementation of an approximate softmax layer for deep neural networks. In `IEEE International Symposium on Circuits and Systems, ISCAS 2020, Sevilla, Spain, October 10-21, 2020`, pages 1–5. IEEE, 2020.

-   [\[60\]](#chapter2.xhtml#b2refbib60) Craig Gentry. Fully homomorphic encryption using ideal lattices. In Michael Mitzenmacher, editor, `Proceedings of the 41st Annual ACM Symposium on Theory of Computing, STOC 2009, Bethesda, MD, USA, May 31 - June 2, 2009`, pages 169–178. ACM, 2009.

-   [\[61\]](#chapter2.xhtml#b2refbib61) Wulfram Gerstner and Werner M. Kistler. Spiking Neuron Models: Single Neurons, Populations, Plasticity. Cambridge University Press, 2002.

-   [\[62\]](#chapter1.xhtml#b1refbib62) Ran Gilad-Bachrach, Nathan Dowlin, Kim Laine, Kristin E. Lauter, Michael Naehrig, and John Wernsing. Cryptonets: Applying neural networks to encrypted data with high throughput and accuracy. In Maria-Florina Balcan and Kilian Q. Weinberger, editors, `Proceedings of the 33nd International Conference on Machine Learning, ICML 2016, New York City, NY, USA, June 19-24, 2016`, volume 48 of `JMLR Workshop and Conference Proceedings`, pages 201–210. [JMLR.org](https://JMLR.org), 2016.

-   [\[63\]](#chapter3.xhtml#b3refbib63) G. A. Gillani, Muhammad Abdullah Hanif, M. Krone, Sabih H. Gerez, Muhammad Shafique, and André B. J. Kokkeler. Squash: Approximate square-accumulate with self-healing. IEEE Access, 6: 49112–49128, 2018.

-   [\[64\]](#chapter3.xhtml#b3refbib64) Tobias Glasmachers. A fast incremental BSP tree archive for non-dominated points. In Heike Trautmann, Günter Rudolph, Kathrin Klamroth, Oliver Schütze, Margaret M. Wiecek, Yaochu Jin, and Christian Grimme, editors, `Evolutionary Multi-Criterion Optimization - 9th International Conference, EMO 2017, Münster, Germany, March 19-22, 2017, Proceedings`, volume 10173 of `Lecture Notes in Computer Science`, pages 252–266. Springer, 2017.

-   [\[65\]](#chapter4.xhtml#b4refbib65) Ian J. Goodfellow, Nicolas Papernot, and Patrick D. McDaniel. cleverhans v0.1: an adversarial machine learning library. `CoRR`, abs/1610.00768, 2016.

-   [\[66\]](#chapter2.xhtml#b2refbib66) Ian J. Goodfellow, Jean Pouget-Abadie, Mehdi Mirza, Bing Xu, David Warde-Farley, Sherjil Ozair, Aaron C. Courville, and Yoshua Bengio. Generative adversarial networks. `CoRR`, abs/1406.2661, 2014.

-   [\[67\]](#chapter1.xhtml#b1refbib67) Ian J. Goodfellow, Jonathon Shlens, and Christian Szegedy. Explaining and harnessing adversarial examples. In Yoshua Bengio and Yann LeCun, editors, `3rd International Conference on Learning Representations, ICLR 2015, San Diego, CA, USA, May 7-9, 2015, Conference Track Proceedings`, 2015.

-   [\[68\]](#chapter2.xhtml#b2refbib68) Jindong Gu and Volker Tresp. Improving the robustness of capsule networks to image affine transformations. In `2020 IEEE/CVF Conference on Computer Vision and Pattern Recognition, CVPR 2020, Seattle, WA, USA, June 13-19, 2020`, pages 7283–7291. Computer Vision Foundation/IEEE, 2020.

-   [\[69\]](#chapter2.xhtml#b2refbib69) Jindong Gu, Volker Tresp, and Han Hu. Capsule network is not more robust than convolutional network. In `IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2021, virtual, June 19-25, 2021`, pages 14309–14317. Computer Vision Foundation/IEEE, 2021.

-   [\[70\]](#chapter2.xhtml#b2refbib70) Jindong Gu, Baoyuan Wu, and Volker Tresp. Effective and efficient vote attack on capsule networks. In `9th International Conference on Learning Representations, ICLR 2021, Virtual Event, Austria, May 3-7, 2021`. [OpenReview.net](https://OpenReview.net), 2021.

-   [\[71\]](#chapter2.xhtml#b2refbib71) Tianyu Gu, Kang Liu, Brendan Dolan-Gavitt, and Siddharth Garg. Badnets: Evaluating backdooring attacks on deep neural networks. IEEE Access, 7: 47230–47244, 2019.

-   [\[72\]](#chapter2.xhtml#b2refbib72) Amira Guesmi, Ihsen Alouani, Khaled N. Khasawneh, Mouna Baklouti, Tarek Frikha, Mohamed Abid, and Nael B. Abu-Ghazaleh. Defensive approximation: securing cnns using approximate computing. In Tim Sherwood, Emery D. Berger, and Christos Kozyrakis, editors, `ASPLOS ‘21: 26th ACM International Conference on Architectural Support for Programming Languages and Operating Systems, Virtual Event, USA, April 19-23, 2021`, pages 990–1003. ACM, 2021.



*   [\[73\]](#chapter2.xhtml#b2refbib73) Josef Gugglberger, David Peer, and Antonio Jose Rodr​guez-Sánchez. Training deep capsule networks with residual connections. In Igor Farkas, Paolo Masulli, Sebastian Otte, and Stefan Wermter, editors, *Artificial Neural Networks and Machine Learning - ICANN 2021 - 30th International Conference on Artificial Neural Networks, Bratislava, Slovakia, September 14-17, 2021, Proceedings, Part I*, volume 12891 of *Lecture Notes in Computer Science*, pages 541–552. Springer, 2021.

*   [\[74\]](#chapter2.xhtml#b2refbib74) Wenzhe Guo, Mohammed E. Fouda, Ahmed M. Eltawil, and Khaled Nabil Salama. Neural coding in spiking neural networks: A comparative study for robust neuromorphic systems. Frontiers in Neuroscience, 15, 2021.

*   [\[75\]](#chapter2.xhtml#b2refbib75) Suyog Gupta, Ankur Agrawal, Kailash Gopalakrishnan, and Pritish Narayanan. Deep learning with limited numerical precision. In Francis R. Bach and David M. Blei, editors, *Proceedings of the 32nd International Conference on Machine Learning, ICML 2015, Lille, France, 6-11 July 2015*, volume 37 of *JMLR Workshop and Conference Proceedings*, pages 1737–1746. [JMLR.org](https://JMLR.org), 2015.

*   [\[76\]](#chapter2.xhtml#b2refbib76) Rehan Hameed, Wajahat Qadeer, Megan Wachs, Omid Azizi, Alex Solomatnikov, Benjamin C. Lee, Stephen Richardson, Christos Kozyrakis, and Mark Horowitz. Understanding sources of inefficiency in general-purpose chips. In André Seznec, Uri C. Weiser, and Ronny Ronen, editors, *37th International Symposium on Computer Architecture (ISCA 2010), June 19-23, 2010, Saint-Malo, France*, pages 37–47. ACM, 2010.

*   [\[77\]](#chapter1.xhtml#b1refbib77) Song Han, Xingyu Liu, Huizi Mao, Jing Pu, Ardavan Pedram, Mark A. Horowitz, and William J. Dally. EIE: efficient inference engine on compressed deep neural network. In *43rd ACM/IEEE Annual International Symposium on Computer Architecture, ISCA 2016, Seoul, South Korea, June 18-22, 2016*, pages 243–254. IEEE Computer Society, 2016.

*   [\[78\]](#chapter2.xhtml#b2refbib78) Song Han, Huizi Mao, and William J. Dally. Deep compression: Compressing deep neural network with pruning, trained quantization and huffman coding. In Yoshua Bengio and Yann LeCun, editors, *4th International Conference on Learning Representations, ICLR 2016, San Juan, Puerto Rico, May 2-4, 2016, Conference Track Proceedings*, 2016.

*   [\[79\]](#chapter1.xhtml#b1refbib79) Song Han, Jeff Pool, John Tran, and William J. Dally. Learning both weights and connections for efficient neural network. In Corinna Cortes, Neil D. Lawrence, Daniel D. Lee, Masashi Sugiyama, and Roman Garnett, editors, *Advances in Neural Information Processing Systems 28: Annual Conference on Neural Information Processing Systems 2015, December 7-12, 2015, Montreal, Quebec, Canada*, pages 1135–1143, 2015.

*   [\[80\]](#chapter2.xhtml#b2refbib80) Muhammad Abdullah Hanif, Rehan Hafiz, and Muhammad Shafique. Error resilience analysis for systematically employing approximate computing in convolutional neural networks. In Jan Madsen and Ayse K. Coskun, editors, *2018 Design, Automation & Test in Europe Conference & Exhibition, DATE 2018, Dresden, Germany, March 19-23, 2018*, pages 913–916. IEEE, 2018.

*   [\[81\]](#chapter2.xhtml#b2refbib81) Muhammad Abdullah Hanif, Giuseppe Maria Sarda, Alberto Marchisio, Guido Masera, Maurizio Martina, and Muhammad Shafique. Conlocnn: Exploiting correlation and non-uniform quantization for energy-efficient low-precision deep convolutional neural networks. In *2022 International Joint Conference on Neural Networks, IJCNN 2022*. IEEE, 2022.

*   [\[82\]](#chapter2.xhtml#b2refbib82) Muhammad Abdullah Hanif and Muhammad Shafique. Salvagednn: salvaging deep neural network accelerators with permanent faults through saliency-driven fault-aware mapping. Philosophical Transactions of the Royal Society A, 378(2164), 2020.

*   [\[83\]](#chapter2.xhtml#b2refbib83) Muhammad Abdullah Hanif and Muhammad Shafique. Dnn-life: An energy-efficient aging mitigation framework for improving the lifetime of on-chip weight memories in deep neural network hardware architectures. In *Design, Automation & Test in Europe Conference & Exhibition, DATE 2021, Grenoble, France, February 1-5, 2021*, pages 729–734. IEEE, 2021.

*   [\[84\]](#chapter2.xhtml#b2refbib84) Kaiming He, Xiangyu Zhang, Shaoqing Ren, and Jian Sun. Deep residual learning for image recognition. In *2016 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2016, Las Vegas, NV, USA, June 27-30, 2016*, pages 770–778. IEEE Computer Society, 2016.

*   [\[85\]](#chapter7.xhtml#b7refbib85) G. E. Hinton and R. R. Salakhutdinov. Reducing the dimensionality of data with neural networks. Science, 313(5786):504–507, 2006.

*   [\[86\]](#chapter2.xhtml#b2refbib86) Geoffrey E. Hinton, Alex Krizhevsky, and Sida D. Wang. Transforming auto-encoders. In Timo Honkela, Wlodzislaw Duch, Mark A. Girolami, and Samuel Kaski, editors, *Artificial Neural Networks and Machine Learning - ICANN 2011 - 21st International Conference on Artificial Neural Networks, Espoo, Finland, June 14-17, 2011, Proceedings, Part I*, volume 6791 of *Lecture Notes in Computer Science*, pages 44–51. Springer, 2011.

*   [\[87\]](#chapter7.xhtml#b7refbib87) Geoffrey E. Hinton, Simon Osindero, and Yee Whye Teh. A fast learning algorithm for deep belief nets. Neural Comput., 18(7):1527–1554, 2006.

*   [\[88\]](#chapter6.xhtml#b6refbib88) Yaoshiang Ho and Samuel Wookey. The real-world-weight cross-entropy loss function: Modeling the costs of mislabeling. IEEE Access, 8: 4806–4813, 2020.

*   [\[89\]](#chapter1.xhtml#b1refbib89) Le Ha Hoang, Muhammad Abdullah Hanif, and Muhammad Shafique. Ft-clipact: Resilience analysis of deep neural networks and improving their fault tolerance using clipped activation. In *2020 Design, Automation & Test in Europe Conference & Exhibition, DATE 2020, Grenoble, France, March 9-13, 2020*, pages 1241–1246. IEEE, 2020.

*   [\[90\]](#chapter2.xhtml#b2refbib90) A. L. Hodgkin and A. F. Huxley. A quantitative description of membrane current and its application to conduction and excitation in nerve. The Journal of Physiology, 117(4):500–544, 1952.

*   [\[91\]](#chapter7.xhtml#b7refbib91) Lasse Holmström and Petri Koistinen. Using additive noise in back-propagation training. IEEE Trans. Neural Networks, 3(1):24–38, 1992.

*   [\[92\]](#chapter3.xhtml#b3refbib92) Sebastian Houben, Johannes Stallkamp, Jan Salmen, Marc Schlipsing, and Christian Igel. Detection of traffic signs in real-world images: The german traffic sign detection benchmark. In *The 2013 International Joint Conference on Neural Networks, IJCNN 2013, Dallas, TX, USA, August 4-9, 2013*, pages 1–8. IEEE, 2013.

*   [\[93\]](#chapter2.xhtml#b2refbib93) Andrew G. Howard, Menglong Zhu, Bo Chen, Dmitry Kalenichenko, Weijun Wang, Tobias Weyand, Marco Andreetto, and Hartwig Adam. Mobilenets: Efficient convolutional neural networks for mobile vision applications. *CoRR*, abs/1704.04861, 2017.

*   [\[94\]](#chapter2.xhtml#b2refbib94) Sergey Ioffe and Christian Szegedy. Batch normalization: Accelerating deep network training by reducing internal covariate shift. In Francis Bach and David Blei, editors, *Proceedings of the 32nd International Conference on Machine Learning, volume 37 of Proceedings of Machine Learning Research*, pages 448–456, Lille, France, 07–09 Jul 2015. PMLR.

*   [\[95\]](#chapter2.xhtml#b2refbib95) Eugene M. Izhikevich. Simple model of spiking neurons. IEEE Trans. Neural Networks, 14(6):1569–1572, 2003.



-   [\[96\]](#chapter1.xhtml#b1refbib96) Benoit Jacob, Skirmantas Kligys, Bo Chen, Menglong Zhu, Matthew Tang, Andrew G. Howard, Hartwig Adam, and Dmitry Kalenichenko. Quantization and training of neural networks for efficient integer-arithmetic-only inference. In `2018 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2018`, pages 2704–2713. Computer Vision Foundation/IEEE Computer Society, 2018.

-   [\[97\]](#chapter6.xhtml#b6refbib97) Shruti Jadon. A survey of loss functions for semantic segmentation. In `IEEE Conference on Computational Intelligence in Bioinformatics and Computational Biology, CIBCB 2020`, pages 1–7. IEEE, 2020.

-   [\[98\]](#chapter2.xhtml#b2refbib98) Weiwen Jiang, Lei Yang, Sakyasingha Dasgupta, Jingtong Hu, and Yiyu Shi. Standing on the shoulders of giants: Hardware and neural architecture co-search with hot start. `IEEE Trans. Comput. Aided Des. Integr. Circuits Syst.`, 39(11):4154–4165, 2020.

-   [\[99\]](#chapter2.xhtml#b2refbib99) Jianhao Jiao, Huaiyang Huang, Liang Li, Zhijian He, Yilong Zhu, and Ming Liu. Comparing representations in tracking for event camera-based SLAM. In `IEEE Conference on Computer Vision and Pattern Recognition Workshops, CVPR Workshops 2021`, pages 1369–1376. Computer Vision Foundation/IEEE, 2021.

-   [\[100\]](#chapter1.xhtml#b1refbib100) Norman P. Jouppi, Cliff Young, Nishant Patil, David A. Patterson, Gaurav Agrawal, Raminder Bajwa, Sarah Bates, Suresh Bhatia, Nan Boden, Al Borchers, Rick Boyle, Pierre-luc Cantin, Clifford Chao, Chris Clark, Jeremy Coriell, Mike Daley, Matt Dau, Jeffrey Dean, Ben Gelb, Tara Vazir Ghaemmaghami, Rajendra Gottipati, William Gulland, Robert Hagmann, C. Richard Ho, Doug Hogberg, John Hu, Robert Hundt, Dan Hurt, Julian Ibarz, Aaron Jaffey, Alek Jaworski, Alexander Kaplan, Harshit Khaitan, Daniel Killebrew, Andy Koch, Naveen Kumar, Steve Lacy, James Laudon, James Law, Diemthu Le, Chris Leary, Zhuyuan Liu, Kyle Lucke, Alan Lundin, Gordon MacKean, Adriana Maggiore, Maire Mahony, Kieran Miller, Rahul Nagarajan, Ravi Narayanaswami, Ray Ni, Kathy Nix, Thomas Norrie, Mark Omernick, Narayana Penukonda, Andy Phelps, Jonathan Ross, Matt Ross, Amir Salek, Emad Samadiani, Chris Severn, Gregory Sizikov, Matthew Snelham, Jed Souter, Dan Steinberg, Andy Swing, Mercedes Tan, Gregory Thorson, Bo Tian, Horia Toma, Erick Tuttle, Vijay Vasudevan, Richard Walter, Walter Wang, Eric Wilcox, and Doe Hyun Yoon. In-datacenter performance analysis of a tensor processing unit. In `Proceedings of the 44th Annual International Symposium on Computer Architecture, ISCA 2017`, pages 1–12. ACM, 2017.

-   [\[101\]](#chapter2.xhtml#b2refbib101) Chiraag Juvekar, Vinod Vaikuntanathan, and Anantha P. Chandrakasan. GAZELLE: A low latency framework for secure neural network inference. In William Enck and Adrienne Porter Felt, editors, `27th USENIX Security Symposium, USENIX Security 2018`, pages 1651–1669. USENIX Association, 2018.

-   [\[102\]](#chapter6.xhtml#b6refbib102) Jacques Kaiser, Alexander Friedrich, Juan Camilo Vasquez Tieck, Daniel Reichard, Arne Roennau, Emre Neftci, and Rüdiger Dillmann. Embodied event-driven random backpropagation. `CoRR`, abs/1904.04805, 2019.

-   [\[103\]](#chapter2.xhtml#b2refbib103) Kunhyuk Kang, Saakshi Gangwal, Sang Phill Park, and Kaushik Roy. NBTI induced performance degradation in logic and memory circuits: how effectively can we approach a reliability solution? In Chong-Min Kyung, Kiyoung Choi, and Soonhoi Ha, editors, `Proceedings of the 13th Asia South Pacific Design Automation Conference, ASP-DAC 2008`, pages 726–731. IEEE, 2008.

-   [\[104\]](#chapter2.xhtml#b2refbib104) Faiq Khalid, Hassan Ali, Muhammad Abdullah Hanif, Semeen Rehman, Rehan Ahmed, and Muhammad Shafique. Fadec: A fast decision-based attack for adversarial machine learning. In `2020 International Joint Conference on Neural Networks, IJCNN 2020`, pages 1–8. IEEE, 2020.

-   [\[105\]](#chapter2.xhtml#b2refbib105) Faiq Khalid, Hassan Ali, Hammad Tariq, Muhammad Abdullah Hanif, Semeen Rehman, Rehan Ahmed, and Muhammad Shafique. Qusecnets: Quantization-based defense mechanism for securing deep neural network against adversarial attacks. In Dimitris Gizopoulos, Dan Alexandrescu, Panagiota Papavramidou, and Michail Maniatakos, editors, `25th IEEE International Symposium on On-Line Testing and Robust System Design, IOLTS 2019`, pages 182–187. IEEE, 2019.

-   [\[106\]](#chapter6.xhtml#b6refbib106) Jihun Kim and Minho Lee. Robust lane detection based on convolutional neural network and random sample consensus. In Chu Kiong Loo, Keem Siah Yap, Kok Wai Wong, Andrew Teoh Beng Jin, and Kaizhu Huang, editors, `Neural Information Processing - 21st International Conference, ICONIP 2014`, volume 8834 of `Lecture Notes in Computer Science`, pages 454–461. Springer, 2014.

-   [\[107\]](#chapter2.xhtml#b2refbib107) Yoongu Kim, Ross Daly, Jeremie S. Kim, Chris Fallin, Ji-Hye Lee, Donghyuk Lee, Chris Wilkerson, Konrad Lai, and Onur Mutlu. Flipping bits in memory without accessing them: An experimental study of DRAM disturbance errors. In `ACM/IEEE 41st International Symposium on Computer Architecture, ISCA 2014`, pages 361–372. IEEE Computer Society, 2014.

-   [\[108\]](#chapter2.xhtml#b2refbib108) Youngeun Kim, Hyoungseob Park, Abhishek Moitra, Abhiroop Bhattacharjee, Yeshwanth Venkatesha, and Priyadarshini Panda. Rate coding or direct coding: Which one is better for accurate, robust, and energy-efficient spiking neural networks? In `IEEE International Conference on Acoustics, Speech and Signal Processing, ICASSP 2022`, pages 71–75. IEEE, 2022.

-   [\[109\]](#chapter2.xhtml#b2refbib109) Youngeun Kim, Yeshwanth Venkatesha, and Priyadarshini Panda. Privatesnn: Privacy-preserving spiking neural networks. In `Thirty-Sixth AAAI Conference on Artificial Intelligence, AAAI 2022`, pages 1192–1200. AAAI Press, 2022.

-   [\[110\]](#chapter2.xhtml#b2refbib110) Diederik P. Kingma and Jimmy Ba. Adam: A method for stochastic optimization. In Yoshua Bengio and Yann LeCun, editors, `3rd International Conference on Learning Representations, ICLR 2015`, 2015.

-   [\[111\]](#chapter2.xhtml#b2refbib111) Sarada Krithivasan, Sanchari Sen, Nitin Rathi, Kaushik Roy, and Anand Raghunathan. Efficiency attacks on spiking neural networks. In Rob Oshana, editor, `DAC ‘22: 59th ACM/IEEE Design Automation Conference`, pages 373–378. ACM, 2022.

-   [\[112\]](#chapter3.xhtml#b3refbib112) Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton. Cifar-10 (canadian institute for advanced research). 2009.

-   [\[113\]](#chapter2.xhtml#b2refbib113) Alex Krizhevsky, Ilya Sutskever, and Geoffrey E. Hinton. Imagenet classification with deep convolutional neural networks. In Peter L. Bartlett, Fernando C. N. Pereira, Christopher J. C. Burges, Léon Bottou, and Kilian Q. Weinberger, editors, `Advances in Neural Information Processing Systems 25: 26th Annual Conference on Neural Information Processing Systems 2012`, pages 1106–1114, 2012.



-   [\[114\]](#chapter2.xhtml#b2refbib114) Souvik Kundu, Massoud Pedram, and Peter A. Beerel. HIRE-SNN: harnessing the inherent robustness of energy-efficient deep spiking neural networks by training with crafted input noise. In `2021 IEEE/CVF International Conference on Computer Vision, ICCV 2021`, `Montreal, QC, Canada`, October 10-17, 2021, pages 5189–5198. IEEE, 2021.

-   [\[115\]](#chapter2.xhtml#b2refbib115) Alexey Kurakin, Ian J. Goodfellow, and Samy Bengio. Adversarial examples in the physical world. In `5th International Conference on Learning Representations, ICLR 2017`, `Toulon, France`, April 24-26, 2017, `Workshop Track Proceedings`. [OpenReview.net](https://OpenReview.net), 2017.

-   [\[116\]](#chapter1.xhtml#b1refbib116) Hyoukjun Kwon, Ananda Samajdar, and Tushar Krishna. MAERI: enabling flexible dataflow mapping over DNN accelerators via reconfigurable interconnects. In Xipeng Shen, James Tuck, Ricardo Bianchini, and Vivek Sarkar, editors, `Proceedings of the Twenty-Third International Conference on Architectural Support for Programming Languages and Operating Systems, ASPLOS 2018`, `Williamsburg, VA, USA`, March 24-28, 2018, pages 461–475. ACM, 2018.

-   [\[117\]](#chapter6.xhtml#b6refbib117) Xavier Lagorce, Garrick Orchard, Francesco Galluppi, Bertram E. Shi, and Ryad Benosman. HOTS: A hierarchy of event-based time-surfaces for pattern recognition. `IEEE Trans. Pattern Anal. Mach. Intell.`, 39(7):1346–1359, 2017.

-   [\[118\]](#chapter6.xhtml#b6refbib118) Yann Lecun, Leon Bottou, Y. Bengio, and Patrick Haffner. Gradient-based learning applied to document recognition. `Proceedings of the IEEE`, 86: 2278 –2324, 12 1998.

-   [\[119\]](#chapter6.xhtml#b6refbib119) Seokju Lee, Junsik Kim, Jae Shin Yoon, Seunghak Shin, Oleksandr Bailo, Namil Kim, Tae-Hee Lee, Hyun Seok Hong, Seung-Hoon Han, and In So Kweon. Vpgnet: Vanishing point guided network for lane and road marking detection and recognition. In `IEEE International Conference on Computer Vision, ICCV 2017`, `Venice, Italy`, October 22-29, 2017, pages 1965–1973. IEEE Computer Society, 2017.

-   [\[120\]](#chapter2.xhtml#b2refbib120) Wooju Lee and Hyun Myung. Adversarial attack for asynchronous event-based data. In `Thirty-Sixth AAAI Conference on Artificial Intelligence, AAAI 2022`, `Thirty-Fourth Conference on Innovative Applications of Artificial Intelligence, IAAI 2022`, `The Twelveth Symposium on Educational Advances in Artificial Intelligence, EAAI 2022 Virtual Event`, February 22 - March 1, 2022, pages 1237–1244. AAAI Press, 2022.

-   [\[121\]](#chapter3.xhtml#b3refbib121) Gilbert N. Lewis, Nancy J. Boynton, and F. Warren Burton. Expected complexity of fast search with uniformly distributed data. `Information Processing Letters`, 13(1):4–7, 1981.

-   [\[122\]](#chapter2.xhtml#b2refbib122) Haitong Li, Mudit Bhargava, Paul N. Whatmough, and H.-S. Philip Wong. On-chip memory technology design space explorations for mobile deep neural network accelerators. In `Proceedings of the 56th Annual Design Automation Conference 2019, DAC 2019`, `Las Vegas, NV, USA`, June 02-06, 2019, page 131. ACM, 2019.

-   [\[123\]](#chapter2.xhtml#b2refbib123) Jingtao Li, Adnan Siraj Rakin, Yan Xiong, Liangliang Chang, Zhezhi He, Deliang Fan, and Chaitali Chakrabarti. Defending bit-flip attack through DNN weight reconstruction. In `57th ACM/IEEE Design Automation Conference, DAC 2020`, `San Francisco, CA, USA`, July 20-24, 2020, pages 1–6. IEEE, 2020.

-   [\[124\]](#chapter3.xhtml#b3refbib124) Sheng Li, Ke Chen, Jung Ho Ahn, Jay B. Brockman, and Norman P. Jouppi. CACTI-P: architecture-level modeling for sram-based structures with advanced leakage reduction techniques. In Joel R. Phillips, Alan J. Hu, and Helmut Graeb, editors, `2011 IEEE/ACM International Conference on Computer-Aided Design, ICCAD 2011`, `San Jose, California, USA`, November 7-10, 2011, pages 694–701. IEEE Computer Society, 2011.

-   [\[125\]](#chapter1.xhtml#b1refbib125) Bin Liang, Hongcheng Li, Miaoqiang Su, Xirong Li, Wenchang Shi, and Xiaofeng Wang. Detecting adversarial image examples in deep neural networks with adaptive noise reduction. `IEEE Transactions on Dependable and Secure Computing`, 18(1):72–85, 2021.

-   [\[126\]](#chapter2.xhtml#b2refbib126) Ling Liang, Xing Hu, Lei Deng, Yujie Wu, Guoqi Li, Yufei Ding, Peng Li, and Yuan Xie. Exploring adversarial attack in spiking neural networks with spike-compatible gradient. `CoRR`, abs/2001.01587, 2020.

-   [\[127\]](#chapter2.xhtml#b2refbib127) Ling Liang, Kaidi Xu, Xing Hu, Lei Deng, and Yuan Xie. Toward robust spiking neural network against adversarial perturbation. `CoRR`, abs/2205.01625, 2022.

-   [\[128\]](#chapter2.xhtml#b2refbib128) Patrick Lichtsteiner, Christoph Posch, and Tobi Delbrück. A 128128 120 db 15 *µ*s latency asynchronous temporal contrast vision sensor. `IEEE Journal of Solid-State Circuits`, 43(2):566–576, 2008.

-   [\[129\]](#chapter6.xhtml#b6refbib129) Chit-Kwan Lin, Andreas Wild, Gautham N. Chinya, Yongqiang Cao, Mike Davies, Daniel M. Lavery, and Hong Wang. Programming spiking neural networks on intel's loihi. `Computer`, 51(3):52–61, 2018.

-   [\[130\]](#chapter6.xhtml#b6refbib130) Chit-Kwan Lin, Andreas Wild, Gautham N. Chinya, Tsung-Han Lin, Mike Davies, and Hong Wang. Mapping spiking neural networks onto a manycore neuromorphic architecture. In Jeffrey S. Foster and Dan Grossman, editors, `Proceedings of the 39th ACM SIGPLAN Conference on Programming Language Design and Implementation, PLDI 2018`, `Philadelphia, PA, USA`, June 18-22, 2018, pages 78–89. ACM, 2018.

-   [\[131\]](#chapter6.xhtml#b6refbib131) Guosheng Lin, Anton Milan, Chunhua Shen, and Ian D. Reid. Refinenet: Multi-path refinement networks for high-resolution semantic segmentation. In `2017 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2017`, `Honolulu, HI, USA`, July 21-26, 2017, pages 5168–5177. IEEE Computer Society, 2017.

-   [\[132\]](#chapter1.xhtml#b1refbib132) Ji Lin, Chuang Gan, and Song Han. Defensive quantization: When efficiency meets robustness. In `7th International Conference on Learning Representations, ICLR 2019`, `New Orleans, LA, USA`, May 6-9, 2019. [OpenReview.net](https://OpenReview.net), 2019.

-   [\[133\]](#chapter2.xhtml#b2refbib133) Alejandro Linares-Barranco, Fernando Perez-Peña, Diederik Paul Moeys, Francisco Gomez-Rodriguez, Gabriel Jiménez-Moreno, Shih-Chii Liu, and Tobi Delbrück. Low latency event-based filtering and feature extraction for dynamic vision sensors in real-time FPGA applications. `IEEE Access`, 7: 134926–134942, 2019.

-   [\[134\]](#chapter2.xhtml#b2refbib134) Chen Liu, Guillaume Bellec, Bernhard Vogginger, David Kappel, Johannes Partzsch, Felix Neumärker, Sebastian Höppner, Wolfgang Maass, Steve B. Furber, Robert Legenstein, and Christian G. Mayr. Memory-efficient deep learning on a spinnaker 2 prototype. `Frontiers in Neuroscience`, 12, 2018.

-   [\[135\]](#chapter2.xhtml#b2refbib135) Jian Liu, Mika Juuti, Yao Lu, and N. Asokan. Oblivious neural network predictions via minionn transformations. In Bhavani M. Thuraisingham, David Evans, Tal Malkin, and Dongyan Xu, editors, `Proceedings of the 2017 ACM SIGSAC Conference on Computer and Communications Security, CCS 2017`, `Dallas, TX, USA`, October 30–November 03, 2017, pages 619–631. ACM, 2017.

-   [\[136\]](#chapter2.xhtml#b2refbib136) Kang Liu, Brendan Dolan-Gavitt, and Siddharth Garg. Fine-pruning: Defending against backdooring attacks on deep neural networks. In Michael Bailey, Thorsten Holz, Manolis Stamatogiannakis, and Sotiris Ioannidis, editors, `Research in Attacks, Intrusions, and Defenses - 21st International Symposium, RAID 2018`, `Heraklion, Crete, Greece`, September 10-12, 2018, Proceedings, volume 11050 of `Lecture Notes in Computer Science`, pages 273–294. Springer, 2018.

-   [\[137\]](#chapter2.xhtml#b2refbib137) Ximeng Liu, Robert H. Deng, Pengfei Wu, and Yang Yang. Lightning-fast and privacy-preserving outsourced computation in the cloud. `Cybersecurity`, 3(1):17, 2020.



*   [\[138\]](#chapter2.xhtml#b2refbib138) Yannan Liu, Lingxiao Wei, Bo Luo, and Qiang Xu. 故障注入攻击深度神经网络。在 Sri Parameswaran 编辑的 `2017 IEEE/ACM 计算机辅助设计国际会议 (ICCAD 2017)`，美国加利福尼亚州 Irvine，2017 年 11 月 13-16，页 131-138。IEEE，2017。

*   [\[139\]](#chapter7.xhtml#b7refbib139) Yingqi Liu, Shiqing Ma, Yousra Aafer, Wen-Chuan Lee, Juan Zhai, Weihang Wang, and Xiangyu Zhang. 特洛伊攻击神经网络。在 `25th 年度网络与分布式系统安全研讨会 (NDSS 2018)`，美国加利福尼亚州 San Diego，2018 年 2 月 18-21，The Internet Society，2018。

*   [\[140\]](#chapter6.xhtml#b6refbib140) Jonathan Long, Evan Shelhamer, and Trevor Darrell. 完全卷积网络用于语义分割。在 `IEEE 计算机视觉与模式识别会议 (CVPR 2015)`，美国波士顿，2015 年 6 月 7-12，页 3431-3440。IEEE 计算机学会，2015。

*   [\[141\]](#chapter3.xhtml#b3refbib141) Ilya Loshchilov and Frank Hutter. SGDR：带有温重启的随机梯度下降。在 `5th 国际会议 (ICLR 2017)`，法国托隆，2017 年 4 月 24-26，会议论文集。[OpenReview.net](https://OpenReview.net)，2017。

*   [\[142\]](#chapter6.xhtml#b6refbib142) Ilya Loshchilov and Frank Hutter. 解耦权重衰减正则化。在 `7th 国际会议 (ICLR 2019)`，美国新奥尔良，2019 年 5 月 6-9，[OpenReview.net](https://OpenReview.net)，2019。

*   [\[143\]](#chapter6.xhtml#b6refbib143) Sheng Lu, Zhaojie Luo, Feng Gao, Mingjie Liu, KyungHi Chang, and Chang Hao Piao. 一种基于语义分割和光流估计的快速且稳健的车道检测方法。`Sensors`，21(2):400，2021。

*   [\[144\]](#chapter1.xhtml#b1refbib144) Wenyan Lu, Guihai Yan, Jiajun Li, Shijun Gong, Yinhe Han, and Xiaowei Li. Flexflow：一种灵活的卷积神经网络数据流加速器架构。在 `2017 IEEE 高性能计算机架构国际研讨会 (HPCA 2017)`，美国奥斯汀，2017 年 2 月 4-8，页 553-564。IEEE 计算机学会，2017。

*   [\[145\]](#chapter4.xhtml#b4refbib145) Bo Luo, Yannan Liu, Lingxiao Wei, and Qiang Xu. 面向不可见且稳健的对抗性示例攻击神经网络。在 Sheila A. McIlraith 和 Kilian Q. Weinberger 编辑的 `第三十二届 AAAI 人工智能大会 (AAAI-18)`，第 30 届人工智能创新应用研讨会 (IAAI-18) 和第 8 届 AAAI 教育先进研讨会 (EAAI-18)，美国路易斯安那州新奥尔良，2018 年 2 月 2-7，页 1652-1659。AAAI Press，2018。

*   [\[146\]](#chapter2.xhtml#b2refbib146) Robert E. Lyons and Wouter Vanderkulk. 使用三模冗余提高计算机可靠性。`IBM Journal of Research and Development`，6(2):200-209，1962。

*   [\[147\]](#chapter1.xhtml#b1refbib147) Wolfgang Maass. 神经网络模型的第三代：网络中的脉冲神经元。`Neural Networks`，10(9):1659-1671，1997。

*   [\[148\]](#chapter1.xhtml#b1refbib148) Aleksander Madry, Aleksandar Makelov, Ludwig Schmidt, Dimitris Tsipras, and Adrian Vladu. 面向对抗攻击的深度学习模型。在 `6th 国际会议 (ICLR 2018)`，加拿大温哥华，2018 年 4 月 30-5 月 3，会议论文集。[OpenReview.net](https://OpenReview.net)，2018。

*   [\[149\]](#chapter1.xhtml#b1refbib149) Alberto Marchisio, Beatrice Bussolino, Alessio Colucci, Muhammad Abdullah Hanif, Maurizio Martina, Guido Masera, and Muhammad Shafique. Fastrcaps：一个用于快速且准确训练胶囊网络的集成框架。在 `2020 年国际神经网络联合会议 (IJCNN 2020)`，英国格拉斯哥，2020 年 7 月 19-24，页 1-8。IEEE，2020。

*   [\[150\]](#chapter1.xhtml#b1refbib150) Alberto Marchisio, Beatrice Bussolino, Alessio Colucci, Maurizio Martina, Guido Masera, and Muhammad Shafique. Q-capsnets：专用于量化胶囊网络的框架。在 `57th ACM/IEEE 设计自动化会议 (DAC 2020)`，美国旧金山，2020 年 7 月 20-24，页 1-6。IEEE，2020。

*   [\[151\]](#chapter1.xhtml#b1refbib151) Alberto Marchisio, Beatrice Bussolino, Edoardo Salvati, Maurizio Martina, Guido Masera, and Muhammad Shafique. 通过近似软 max 和挤压操作，使胶囊网络能够在边缘实现。在 Hai Helen Li, Charles Augustine, Ayse Kivilcim Coskun, and Swaroop Ghosh 编辑的 `ISLPED ‘22: ACM/IEEE 低功耗电子设计国际研讨会`，美国波士顿，2022 年 8 月 1-3，页 27:1-6。ACM，2022。

*   [\[152\]](#chapter1.xhtml#b1refbib152) Alberto Marchisio, Giovanni Caramia, Maurizio Martina, and Muhammad Shafique. fakeweather：用于模拟自主系统摄像头镜头上的天气条件的深度神经网络对抗攻击。在 `国际神经网络联合会议 (IJCNN 2022)`，意大利帕多瓦，2022 年 7 月 18-23，页 1-9。IEEE，2022。

*   [\[153\]](#chapter1.xhtml#b1refbib153) Alberto Marchisio, Antonio De Marco, Alessio Colucci, Maurizio Martina, and Muhammad Shafique. RobCaps：评估胶囊网络对仿射变换和对抗攻击的鲁棒性。在 `国际神经网络联合会议 (IJCNN)`，2023。

*   [\[154\]](#chapter1.xhtml#b1refbib154) Alberto Marchisio, Muhammad Abdullah Hanif, Maurizio Martina, and Muhammad Shafique. Prunet：一种无类别的深度神经网络剪枝方法。在 `2018 年国际神经网络联合会议 (IJCNN 2018)`，巴西里约热内卢，2018 年 7 月 8-13，页 1-8。IEEE，2018。

*   [\[155\]](#chapter1.xhtml#b1refbib155) Alberto Marchisio, Muhammad Abdullah Hanif, and Muhammad Shafique. Capsacc：一种用于胶囊网络的高效硬件加速器，采用数据复用。在 Jürgen Teich 和 Franco Fummi 编辑的 `设计、自动化与测试在欧洲会议与展览 (DATE 2019)`，意大利佛罗伦萨，2019 年 3 月 25-29，页 964-967。IEEE，2019。

*   [\[156\]](#chapter1.xhtml#b1refbib156) Alberto Marchisio, Andrea Massa, Vojtech Mrazek, Beatrice Bussolino, Maurizio Martina, and Muhammad Shafique. Nascaps：一个用于优化卷积胶囊网络的准确性和硬件效率的神经结构搜索框架。在 `IEEE/ACM 计算机辅助设计国际会议 (ICCAD 2020)`，美国旧金山，2020 年 11 月 2-5，页 114:1-114:9。IEEE，2020。

*   [\[157\]](#chapter1.xhtml#b1refbib157) Alberto Marchisio, Vojtech Mrazek, Muhammad Abdullah Hanif, and Muhammad Shafique. Red-cane：系统性方法，用于分析和设计在近似下胶囊网络的弹性。在 `2020 年设计、自动化与测试在欧洲会议与展览 (DATE 2020)`，法国格勒诺布尔，2020 年 3 月 9-13，页 1205-1210。IEEE，2020。

*   [\[158\]](#chapter1.xhtml#b1refbib158) Alberto Marchisio, Vojtech Mrazek, Muhammad Abdullah Hanif, and Muhammad Shafique. Descnet：为胶囊网络硬件开发高效的 scratchpad 存储器。`IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems`，40(9):1768-1781，2021。

*   [\[159\]](#chapter1.xhtml#b1refbib159) Alberto Marchisio, Vojtech Mrazek, Muhammad Abdullah Hanif, and Muhammad Shafique. FEECA：低延迟且节能的胶囊网络加速器的设计空间探索。`IEEE Transactions on Very Large Scale Integration Systems`，29(4):716-729，2021。

*   [\[160\]](#chapter1.xhtml#b1refbib160) Alberto Marchisio, Vojtech Mrazek, Andrea Massa, Beatrice Bussolino, Maurizio Martina, and Muhammad Shafique. HARNAS：联合优化硬件效率和对抗鲁棒性的卷积与胶囊网络神经结构搜索。ICML 工作坊动态神经网络 (DyNN*)*，2022。



*   [\[161\]](#chapter1.xhtml#b1refbib161) Alberto Marchisio, Vojtech Mrazek, Andrea Massa, Beatrice Bussolino, Maurizio Martina, and Muhammad Shafique. Rohnas: A neural architecture search framework with conjoint optimization for adversarial robustness and hardware efficiency of convolutional and capsule networks. IEEE Access, 10: 109043–109055, 2022.

*   [\[162\]](#chapter1.xhtml#b1refbib162) Alberto Marchisio, Giorgio Nanfa, Faiq Khalid, Muhammad Abdullah Hanif, Maurizio Martina, and Muhammad Shafique. CapsAttacks: Robust and Imperceptible Adversarial Attacks on Capsule Networks. ICML Workshop on Uncertainty & Robustness in Deep Learning, UDL 2019, Long Beach, CA, USA, July 9-15, 2019.

*   [\[163\]](#chapter1.xhtml#b1refbib163) Alberto Marchisio, Giorgio Nanfa, Faiq Khalid, Muhammad Abdullah Hanif, Maurizio Martina, and Muhammad Shafique. Is spiking secure? A comparative study on the security vulnerabilities of spiking and deep neural networks. In 2020 International Joint Conference on Neural Networks, IJCNN 2020, Glasgow, United Kingdom, July 19-24, 2020, pages 1–8. IEEE, 2020.

*   [\[164\]](#chapter1.xhtml#b1refbib164) Alberto Marchisio, Giorgio Nanfa, Faiq Khalid, Muhammad Abdullah Hanif, Maurizio Martina, and Muhammad Shafique. SeVuC: A Study on the Security Vulnerabilities of Capsule Networks against Adversarial Attacks. Microprocessors and Microsystems (MICPRO), 2023.

*   [\[165\]](#chapter1.xhtml#b1refbib165) Alberto Marchisio, Giacomo Pira, Maurizio Martina, Guido Masera, and Muhammad Shafique. Dvs-attacks: Adversarial attacks on dynamic vision sensors for spiking neural networks. In International Joint Conference on Neural Networks, IJCNN 2021, Shenzhen, China, July 18-22, 2021, pages 1–9. IEEE, 2021.

*   [\[166\]](#chapter1.xhtml#b1refbib166) Alberto Marchisio, Giacomo Pira, Maurizio Martina, Guido Masera, and Muhammad Shafique. R-SNN: an analysis and design methodology for robustifying spiking neural networks against adversarial attacks through noise filters for dynamic vision sensors. In IEEE/RSJ International Conference on Intelligent Robots and Systems, IROS 2021, Prague, Czech Republic, September 27 - Oct. 1, 2021, pages 6315–6321. IEEE, 2021.

*   [\[167\]](#chapter2.xhtml#b2refbib167) Stefano Markidis, Steven Wei Der Chien, Erwin Laure, Ivy Bo Peng, and Jeffrey S. Vetter. NVIDIA tensor core programmability, performance & precision. In 2018 IEEE International Parallel and Distributed Processing Symposium Workshops, IPDPS Workshops 2018, Vancouver, BC, Canada, May 21-25, 2018, pages 522–531. IEEE Computer Society, 2018.

*   [\[168\]](#chapter1.xhtml#b1refbib168) Riccardo Massa, Alberto Marchisio, Maurizio Martina, and Muhammad Shafique. An efficient spiking neural network for recognizing gestures with a DVS camera on the loihi neuromorphic processor. In 2020 International Joint Conference on Neural Networks, IJCNN 2020, Glasgow, United Kingdom, July 19-24, 2020, pages 1–9. IEEE, 2020.

*   [\[169\]](#chapter2.xhtml#b2refbib169) Warren S. McCulloch and Walter H. Pitts. A logical calculus of the ideas immanent in nervous activity. In Margaret A. Boden, editor, The Philosophy of Artificial Intelligence, Oxford readings in philosophy, pages 22–39. Oxford University Press, 1990.

*   [\[170\]](#chapter1.xhtml#b1refbib170) Paul A. Merolla, John V. Arthur, Rodrigo Alvarez-Icaza, Andrew S. Cassidy, Jun Sawada, Filipp Akopyan, Bryan L. Jackson, Nabil Imam, Chen Guo, Yutaka Nakamura, Bernard Brezzo, Ivan Vo, Steven K. Esser, Rathinakumar Appuswamy, Brian Taba, Arnon Amir, Myron D. Flickner, William P. Risk, Rajit Manohar, and Dharmendra S. Modha. A million spiking-neuron integrated circuit with a scalable communication network and interface. Science, 345(6197):668–673, 2014.

*   [\[171\]](#chapter6.xhtml#b6refbib171) Carlo Michaelis, Andrew B. Lehr, Winfried Oed, and Christian Tetzlaff. Brian2loihi: An emulator for the neuromorphic chip loihi using the spiking neural network simulator brian. CoRR, abs/2109.12308, 2021.

*   [\[172\]](#chapter2.xhtml#b2refbib172) Felix Michels, Tobias Uelwer, Eric Upschulte, and Stefan Harmeling. On the vulnerability of capsule networks to adversarial attacks. CoRR, abs/1906.03612, 2019.

*   [\[173\]](#chapter1.xhtml#b1refbib173) Payman Mohassel and Yupeng Zhang. Secureml: A system for scalable privacy-preserving machine learning. In 2017 IEEE Symposium on Security and Privacy, SP 2017, San Jose, CA, USA, May 22-26, 2017, pages 19–38. IEEE Computer Society, 2017.

*   [\[174\]](#chapter7.xhtml#b7refbib174) Martin Fodslette Møller. A scaled conjugate gradient algorithm for fast supervised learning. Neural Networks, 6(4):525–533, 1993.

*   [\[175\]](#chapter2.xhtml#b2refbib175) Happy Nkanta Monday, Jianping Li, Grace Ugochi Nneji, Saifun Nahar, Md Altab Hossin, and Jehoiada Jackson. Covid-19 pneumonia classification based on neurowavelet capsule network. Healthcare, 10(3), 2022.

*   [\[176\]](#chapter2.xhtml#b2refbib176) Seyed-Mohsen Moosavi-Dezfooli, Alhussein Fawzi, Omar Fawzi, and Pascal Frossard. Universal adversarial perturbations. In 2017 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2017, Honolulu, HI, USA, July 21-26, 2017, pages 86–94. IEEE Computer Society, 2017.

*   [\[177\]](#chapter2.xhtml#b2refbib177) Seyed-Mohsen Moosavi-Dezfooli, Alhussein Fawzi, and Pascal Frossard. Deepfool: A simple and accurate method to fool deep neural networks. In 2016 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2016, Las Vegas, NV, USA, June 27-30, 2016, pages 2574–2582. IEEE Computer Society, 2016.

*   [\[178\]](#chapter2.xhtml#b2refbib178) Saber Moradi, Qiao Ning, Fabio Stefanini, and Giacomo Indiveri. A scalable multicore architecture with heterogeneous memory structures for dynamic neuromorphic asynchronous processors (dynaps). IEEE Transactions on Biomedical Circuits and Systems, 12(1):106–122, 2018.

*   [\[179\]](#chapter2.xhtml#b2refbib179) Vojtech Mrazek, Radek Hrbacek, Zdenek Vascek, and Lukás Sekanina. Evoapproxsb: Library of approximate adders and multipliers for circuit design and benchmarking of approximation methods. In David Atienza and Giorgio Di Natale, editors, Design, Automation & Test in Europe Conference & Exhibition, DATE 2017, Lausanne, Switzerland, March 27-31, 2017, pages 258–261. IEEE, 2017.

*   [\[180\]](#chapter2.xhtml#b2refbib180) Vojtech Mrazek, Zdenek Vascek, Lukás Sekanina, Muhammad Abdullah Hanif, and Muhammad Shafique. ALWANN: automatic layer-wise approximation of deep neural network accelerators without retraining. In David Z. Pan, editor, Proceedings of the International Conference on Computer-Aided Design, ICCAD 2019, Westminster, CO, USA, November 4-7, 2019, pages 1–8. ACM, 2019.

*   [\[181\]](#chapter6.xhtml#b6refbib181) Farzeen Munir, Shoaib Azam, Moongu Jeon, Byung-Geun Lee, and Witold Pedrycz. Ldnet: End-to-end lane marking detection approach using a dynamic vision sensor. IEEE Transactions on Intelligent Transportation Systems, 23(7):9318–9334, 2022.

*   [\[182\]](#chapter2.xhtml#b2refbib182) Karthikeyan Nagarajan, Junde Li, Sina Sayyah Ensan, Mohammad Nasim Imtiaz Khan, Sachhidh Kannan, and Swaroop Ghosh. Analysis of power-oriented fault injection attacks on spiking neural networks. In Cristiana Bolchini, Ingrid Verbauwhede, and Ioana Vatajelu, editors, Design, Automation & Test in Europe Conference & Exhibition, DATE 2022, Antwerp, Belgium, March 14-23, 2022, pages 861–866. IEEE, 2022.

*   [\[183\]](#chapter3.xhtml#b3refbib183) Vinod Nair and Geoffrey E. Hinton. Rectified linear units improve restricted boltzmann machines. In Johannes Fürnkranz and Thorsten Joachims, editors, Proceedings of the 27th International Conference on Machine Learning (ICML-10), June 21-24, 2010, Haifa, Israel, pages 807–814. Omnipress, 2010.



-   [184] Karthik Nandakumar, Nalini K. Ratha, Sharath Pankanti, and Shai Halevi. 面向加密数据的深度神经网络训练。在`IEEE 计算机视觉与模式识别会议工作坊, CVPR Workshops 2019, Long Beach, CA, USA, 6 月 16-20, 2019`, 页 40-48。`计算机视觉基金会/IEEE`, 2019.

-   [185] Emre O. Neftci, Hesham Mostafa, and Friedemann Zenke. 替代梯度学习在尖峰神经网络中：将梯度基优化的力量带给尖峰神经网络。`IEEE 信号处理杂志`, 36(6):51-63, 2019.

-   [186] Yuval Netzer, Tao Wang, Adam Coates, Alessandro Bissacco, Bo Wu, and Andrew Y. Ng. 自然图像中的数字识别与无监督特征学习。在`NIPS 深度学习与无监督特征学习工作坊`, 2011.

-   [187] Davy Neven, Bert De Brabandere, Stamatios Georgoulis, Marc Proesmans, and Luc Van Gool. 面向端到端车道检测：实例分割方法。在`2018 IEEE 智能车辆研讨会, IV 2018, Changshu, Suzhou, China, 6 月 26-30, 2018`, 页 286-291。`IEEE`, 2018.

-   [188] Andrew Y. Ng. 特征选择、L1 与 L2 正则化以及旋转不变性。在`第二十一届国际机器学习会议, ICML ‘04`, 页 78, New York, NY, USA, 2004。`计算机协会`。

-   [189] Farzad Nikfam, Alberto Marchisio, Maurizio Martina, and Muhammad Shafique. Accelat: 一个用于加速深度神经网络对抗训练的准确度梯度加速框架。`IEEE Access`, 10: 108997-109007, 2022.

-   [190] Osamu Nomura, Yusuke Sakemi, Takeo Hosomi, and Takashi Morie. 基于时间到第一次尖峰编码的尖峰神经网络对抗攻击的鲁棒性。`IEEE 电路与系统 II: Express Briefs`, 页 1-1, 2022.

-   [191] Yuji Nozaki and Tobi Delbruck. 动态视觉传感器的温度和寄生光电流效应。`IEEE 电子设备杂志`, 64(8):3239-3245, 2017.

-   [192] Peter O'Connor, Daniel Neil, Shih-Chii Liu, Tobi Delbruck, and Michael Pfeiffer. 实时分类和传感器融合与尖峰深度信念网络。`Frontiers in Neuroscience`, 7: 178, 2013.

-   [193] Garrick Orchard, Ajinkya Jayawant, Gregory Cohen, and Nitish V. Thakor. 使用眼动将静态图像数据集转换为尖峰神经形态数据集。`CoRR`, abs/1507.07629, 2015.

-   [194] Elbruz Ozen and Alex Orailoglu. 实证检查：提高关键安全深度神经网络应用的可靠性。在`第 28 届 IEEE 亚洲测试研讨会, ATS 2019, Kolkata, India, 12 月 10-13, 2019`, 页 7-12。`IEEE`, 2019.

-   [195] Elbruz Ozen and Alex Orailoglu. 通过中位特征选择增强 DNN 加速器的位错误抗性。`IEEE 设计自动化系统与集成电路系统`, 39(11):3250-3262, 2020.

-   [196] Pascal Paillier. 基于复合程度余数类的公钥加密系统。在 Jacques Stern, 编辑, `Advances in Cryptology - EUROCRYPT ‘99, 国际密码学理论与应用国际会议, Prague, Czech Republic, 5 月 2-6, 1999, 程序`, 卷 1592 of `计算机科学讲义`, 页 223-238。`Springer`, 1999.

-   [197] Xingang Pan, Jianping Shi, Ping Luo, Xiaogang Wang, and Xiaoou Tang. 空间即深度：用于交通场景理解的空间 CNN。在 Sheila A. McIlraith 和 Kilian Q. Weinberger, 编辑, `第三十二届 AAAI 人工智能大会 (AAAI-18), 第三十创新人工智能应用 (IAAI-18) 和第八届 AAAI 教育先进研讨会 (EAAI-18), New Orleans, Louisiana, USA, 2 月 2-7, 2018`, 页 7276-7283。`AAAI Press`, 2018.

-   [198] Xingang Pan, Jianping Shi, Ping Luo, Xiaogang Wang, and Xiaoou Tang. 空间即深度：用于交通场景理解的空间 CNN。在 Sheila A. McIlraith 和 Kilian Q. Weinberger, 编辑, `第三十二届 AAAI 人工智能大会 (AAAI-18), 第三十创新人工智能应用 (IAAI-18) 和第八届 AAAI 教育先进研讨会 (EAAI-18), New Orleans, Louisiana, USA, 2 月 2-7, 2018`, 页 7276-7283。`AAAI Press`, 2018.

-   [199] Zihan Pan, Jibin Wu, Malu Zhang, Haizhou Li, and Yansong Chua. 神经群体编码用于有效的时间分类。在`国际神经网络会议, IJCNN 2019 Budapest, Hungary, 7 月 14-19, 2019`, 页 1-8。`IEEE`, 2019.

-   [200] Preeti Ranjan Panda, Nikil D. Dutt, and Alexandru Nicolau. 板上与板下存储：嵌入式处理器系统中的数据分区问题。`ACM 设计自动化系统与集成电路系统`, 5(3):682-704, 2000.

-   [201] Pramesh Pandey, Prabal Basu, Koushik Chakraborty, and Sanghamitra Roy. Greentpu: 一个用于提高近阈值张量处理单元时序误差抗性的预测设计范式。`IEEE 非常大规模集成系统杂志`, 28(7):1557-1566, 2020.

-   [202] Nicolas Papernot, Shuang Song, Ilya Mironov, Ananth Raghunathan, Kunal Talwar, and Úlfar Erlingsson. 可扩展私有学习与 PATE。在`第 6 届学习表示会议, ICLR 2018, Vancouver, BC, Canada, 4 月 30 日-May 3, 2018, 会议论文集`. `[OpenReview.net](https://OpenReview.net)`, 2018.

-   [203] Angshuman Parashar, Minsoo Rhu, Anurag Mukkara, Antonio Puglielli, Rangharajan Venkatesan, Bruck Khailany, Joel S. Emer, Stephen W. Keckler, and William J. Dally. SCNN: 一个用于压缩稀疏卷积神经网络的加速器。在`第 44 届国际计算机体系结构研讨会, ISCA 2017`, 页 27-40。`ACM`, 2017.

-   [204] Adam Paszke, Sam Gross, Francisco Massa, Adam Lerer, James Bradbury, Gregory Chanan, Trevor Killeen, Zeming Lin, Natalia Gimelshein, Luca Antiga, Alban Desmaison, Andreas Köpf, Edward Z. Yang, Zachary DeVito, Martin Raison, Alykhan Tejani, Sasank Chilamkurthy, Benoit Steiner, Lu Fang, Junjie Bai, and Soumith Chintala. PyTorch: 一个声明式、高性能的深度学习库。在 Hanna M. Wallach, Hugo Larochelle, Alina Beygelzimer, Florence d'Alché-Buc, Emily B. Fox, and Roman Garnett, 编辑, `Neural Information Processing Systems 32: Annual Conference on Neural Information Processing Systems 2019, NeurIPS 2019, December 8-14, 2019, Vancouver, BC, Canada`, 页 8024-8035, 2019.

-   [205] Bijaya Paudel, Aashish Itani, and Spyros Tragoudas. 面向黑盒对抗攻击的 SNN 的鲁棒性。在 M. Arif Wani, Ishwar K. Sethi, Weisong Shi, Guangzhi Qu, Daniela Stan Raicu, and Ruoming Jin, 编辑, `20th IEEE International Conference on Machine Learning and Applications, ICMLA 2021, Pasadena, CA, USA, December 13-16, 2021`, 页 799-806。`IEEE`, 2021.

-   [206] Andrea Paudice, Luis Muñoz-González, András György, and Emil C. Lupu. 通过异常检测检测中毒攻击的对抗训练示例。`CoRR`, abs/1802.03041, 2018.



-   [\[207\]](#chapter2.xhtml#b2refbib207) Hélène Paugam-Moisy and Sander M. Bohté. Computing with spiking neuron networks. In Grzegorz Rozenberg, Thomas Bäck, and Joost N. Kok, editors, Handbook of Natural Computing, pages 335–376. Springer, 2012.

-   [\[208\]](#chapter5.xhtml#b5refbib208) Karl Pearson. Note on regression and inheritance in the case of two parents. *Proceedings of the Royal Society of London*, 58: 240–242, 1895.

-   [\[209\]](#chapter7.xhtml#b7refbib209) Christian Pehle and Jens Egholm Pedersen. Norse - A deep learning library for spiking neural networks, January 2021. Documentation: [`norse.ai/docs/`](https://norse.ai/docs/).

-   [\[210\]](#chapter2.xhtml#b2refbib210) Filip Ponulak and Andrzej J. Kasinski. Introduction to spiking neural networks: Information processing, learning and applications. Acta neurobiologiae experimentalis, 71 4: 409–33, 2011.

-   [\[211\]](#chapter2.xhtml#b2refbib211) Christoph Posch, Daniel Matolin, and Rainer Wohlgenannt. A QVGA 143 db dynamic range frame-free PWM image sensor with lossless pixel-level video compression and time-domain CDS. IEEE J. Solid State Circuits, 46(1):259–275, 2011.

-   [\[212\]](#chapter2.xhtml#b2refbib212) V. Prasanth, Virendra Singh, and Rubin A. Parekhji. Reduced overhead soft error mitigation using error control coding techniques. In *17th IEEE International On-Line Testing Symposium (IOLTS 2011), 13-15 July, 2011, Athens, Greece*, pages 163–168. IEEE Computer Society, 2011.

-   [\[213\]](#chapter2.xhtml#b2refbib213) Rachmad Vidya Wicaksana Putra, Muhammad Abdullah Hanif, and Muhammad Shafique. Drmap: A generic DRAM data mapping policy for energy-efficient processing of convolutional neural networks. In *57th ACM/IEEE Design Automation Conference, DAC 2020, San Francisco, CA, USA, July 20-24, 2020*, pages 1–6. IEEE, 2020.

-   [\[214\]](#chapter2.xhtml#b2refbib214) Rachmad Vidya Wicaksana Putra, Muhammad Abdullah Hanif, and Muhammad Shafique. Respawn: Energy-efficient fault-tolerance for spiking neural networks considering unreliable memories. In *IEEE/ACM International Conference On Computer Aided Design, ICCAD 2021, Munich, Germany, November 1-4, 2021*, pages 1–9. IEEE, 2021.

-   [\[215\]](#chapter2.xhtml#b2refbib215) Rachmad Vidya Wicaksana Putra, Muhammad Abdullah Hanif, and Muhammad Shafique. Softsnn: Low-cost fault tolerance for spiking neural network accelerators under soft errors. *CoRR*, abs/2203.05523, 2022.

-   [\[216\]](#chapter2.xhtml#b2refbib216) Yao Qin, Nicholas Frosst, Colin Raffel, Garrison W. Cottrell, and Geoffrey E. Hinton. Deflecting adversarial attacks. *CoRR*, abs/2002.07405, 2020.

-   [\[217\]](#chapter2.xhtml#b2refbib217) Yao Qin, Nicholas Frosst, Sara Sabour, Colin Raffel, Garrison W. Cottrell, and Geoffrey E. Hinton. Detecting and diagnosing adversarial images with class-conditional capsule reconstructions. In *8th International Conference on Learning Representations, ICLR 2020, Addis Ababa, Ethiopia, April 26-30, 2020*. [OpenReview.net](https://OpenReview.net), 2020.

-   [\[218\]](#chapter3.xhtml#b3refbib218) Maithra Raghu, Ben Poole, Jon M. Kleinberg, Surya Ganguli, and Jascha Sohl-Dickstein. On the expressive power of deep neural networks. In Doina Precup and Yee Whye Teh, editors, *Proceedings of the 34th International Conference on Machine Learning, ICML 2017, Sydney, NSW, Australia, 6-11 August 2017*, volume 70 of *Proceedings of Machine Learning Research*, pages 2847–2854. PMLR, 2017.

-   [\[219\]](#chapter2.xhtml#b2refbib219) Bharathwaj Raghunathan, Yatish Turakhia, Siddharth Garg, and Diana Marculescu. Cherry-picking: exploiting process variations in dark-silicon homogeneous chip multi-processors. In Enrico Macii, editor, *Design, Automation and Test in Europe, DATE 13, Grenoble, France, March 18-22, 2013*, pages 39–44. EDA Consortium San Jose, CA, USA/ACM DL, 2013.

-   [\[220\]](#chapter1.xhtml#b1refbib220) Jathushan Rajasegaran, Vinoj Jayasundara, Sandaru Jayasekara, Hirunima Jayasekara, Suranga Seneviratne, and Ranga Rodrigo. Deepcaps: Going deeper with capsule networks. In *IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2019, Long Beach, CA, USA, June 16-20, 2019*, pages 10725–10733. Computer Vision Foundation/IEEE, 2019.

-   [\[221\]](#chapter2.xhtml#b2refbib221) Adnan Siraj Rakin, Zhezhi He, and Deliang Fan. Bit-flip attack: Crushing neural network with progressive bit search. In *2019 IEEE/CVF International Conference on Computer Vision, ICCV 2019, Seoul, Korea (South), October 27 - November 2, 2019*, pages 1211–1220. IEEE, 2019.

-   [\[222\]](#chapter6.xhtml#b6refbib222) Daniel Rasmussen. Nengodl: Combining deep learning and neuromorphic modelling methods. *CoRR*, abs/1805.11144, 2018.

-   [\[223\]](#chapter2.xhtml#b2refbib223) Nitin Rathi, Gopalakrishnan Srinivasan, Priyadarshini Panda, and Kaushik Roy. Enabling deep spiking neural networks with hybrid conversion and spike timing dependent backpropagation. In *8th International Conference on Learning Representations, ICLR 2020, Addis Ababa, Ethiopia, April 26-30, 2020*. [OpenReview.net](https://OpenReview.net), 2020.

-   [\[224\]](#chapter7.xhtml#b7refbib224) Jonas Rauber, Wieland Brendel, and Matthias Bethge. Foolbox v0.8.0: A python toolbox to benchmark the robustness of machine learning models. *CoRR*, abs/1707.04131, 2017.

-   [\[225\]](#chapter6.xhtml#b6refbib225) Raimundo Real and J. Vargas. The probabilistic basis of jaccard's index of similarity. Systematic Biology - SYST BIOL, 45: 380–385, 09 1996.

-   [\[226\]](#chapter2.xhtml#b2refbib226) Joseph Redmon and Ali Farhadi. YOLO9000: better, faster, stronger. In *2017 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2017, Honolulu, HI, USA, July 21-26, 2017*, pages 6517–6525. IEEE Computer Society, 2017.

-   [\[227\]](#chapter2.xhtml#b2refbib227) Alpha Renner, Forrest Sheldon, Anatoly Zlotnik, Louis Tao, and Andrew T. Sornborger. The backpropagation algorithm implemented on spiking neuromorphic hardware. *CoRR*, abs/2106.07030, 2021.

-   [\[228\]](#chapter3.xhtml#b3refbib228) Frank Rhodes. On the metrics of chaudhuri, murthy and chaudhuri. Pattern Recognition, 28(5):745–752, 1995.

-   [\[229\]](#chapter7.xhtml#b7refbib229) Enrique Romero, Ferran Mazzanti, Jordi Delgado, and David Buchaca Prats. Weighted contrastive divergence. Neural Networks, 114: 147–156, 2019.

-   [\[230\]](#chapter2.xhtml#b2refbib230) Frank Rosenblatt. The perceptron: a probabilistic model for information storage and organization in the brain. Psychological review, 65 6: 386–408, 1958.

-   [\[231\]](#chapter2.xhtml#b2refbib231) Bita Darvish Rouhani, M. Sadegh Riazi, and Farinaz Koushanfar. Deepsecure: scalable provably-secure deep learning. In *Proceedings of the 55th Annual Design Automation Conference, DAC 2018, San Francisco, CA, USA, June 24-29, 2018*, pages 2: 1–2:6. ACM, 2018.

-   [\[232\]](#chapter6.xhtml#b6refbib233) Bodo Rückauer, Nicolas Känzig, Shih-Chii Liu, Tobi Delbrück, and Yulia Sandamirskaya. Closing the accuracy gap in an event-based visual recognition task. *CoRR*, abs/1906.08859, 2019.

-   [\[233\]](#chapter6.xhtml#b6refbib233) Bodo Rueckauer, Connor Bybee, Ralf Goettsche, Yashwardhan Singh, Joyesh Mishra, and Andreas Wild. Nxtf: An API and compiler for deep spiking neural networks on intel loihi. *CoRR*, abs/2101.04261, 2021.

-   [\[234\]](#chapter2.xhtml#b2refbib234) Bodo Rueckauer, Iulia-Alexandra Lungu, Yuhuang Hu, Michael Pfeiffer, and Shih-Chii Liu. Conversion of continuous-valued deep networks to efficient event-driven networks for image classification. Frontiers in Neuroscience, 11, 2017.



-   [235] 伯哈德·鲁夫和迈克尔·舒密特。在神经元尖峰网络中使用时间编码的赫伯学习。在 José Mira、Roberto Moreno-Daz 和 Joan Cabestany 编辑的《生物与人工计算：从神经科学到技术国际工作会议论文集》中，卷 1240，Lecture Notes in Computer Science，第 380–389 页。Springer，1997。

-   [236] Sara Sabour、Nicholas Frosst 和 Geoffrey E. Hinton。动态胶囊之间的路由。在 Isabelle Guyon、Ulrike von Luxburg、Samy Bengio、Hanna M. Wallach、Rob Fergus、S. V. N. Vishwanathan 和 Roman Garnett 编辑的《神经信息处理系统进展：2017 年国际神经信息处理系统会议（NeurIPS 2017），2017 年 12 月 4–9 日，美国长滩，加利福尼亚州》中，第 3856–3866 页，2017。

-   [237] Sebastian Schmitt、Johann Klähn、Guillaume Bellec、Andreas Grübl、Maurice Güttler、Andreas Hartel、Stephan Hartmann、Dan Husmann de Oliveira、Kai Husmann、Sebastian Jeltsch、Vitali Karasenko、Mitja Kleider、Christoph Koke、Alexander Kononov、Christian Mauch、Eric Müller、Paul Müller、Johannes Partzsch、Mihai A. Petrovici、Stefan Schiefer、Stefan Scholze、Vasilis N. Thanasoulis、Bernhard Vogginger、Robert Legenstein、Wolfgang Maass、Christian Mayr、René Schüffny、Johannes Schemmel 和 Karlheinz Meier。在环路中的突触硬件：在大脑尺度系统上训练深度尖峰网络。在 2017 年国际神经网络联合会议（IJCNN 2017），2017 年 5 月 14–19 日，美国安克雷奇，IEEE，第 2227–2234 页，2017。

-   [238] Christoph Schorn、Thomas Elsken、Sebastian Vogel、Armin Runge、Andre Guntoro 和 Gerd Ascheid。自动设计容错且高效的深度神经网络硬件。Neural Comput. Appl.，32(24)：18327–18345，2020。

-   [239] Lukás Sekanina。神经结构搜索与硬件加速器协同搜索：综述。IEEE Access，9：151337–151362，2021。

-   [240] Ali Shafahi、W. Ronny Huang、Mahyar Najibi、Octavian Suciu、Christoph Studer、Tudor Dumitras 和 Tom Goldstein。中毒青蛙！针对神经网络的目标清晰中毒攻击。在 Samy Bengio、Hanna M. Wallach、Hugo Larochelle、Kristen Grauman、Nicolò Cesa-Bianchi 和 Roman Garnett 编辑的《神经信息处理系统进展：2018 年国际神经信息处理系统会议（NeurIPS 2018），2018 年 12 月 3–8 日，加拿大蒙特利尔》中，第 6106–6116 页，2018。

-   [241] Muhammad Shafique、Alberto Marchisio、Rachmad Vidya Wicaksana Putra 和 Muhammad Abdullah Hanif。面向能源效率和安全边缘人工智能的跨层框架：ICCAD 特别会议论文。在 IEEE/ACM 国际计算机辅助设计会议（ICCAD 2021），2021 年 11 月 1–4 日，德国慕尼黑，第 1–9 页。IEEE，2021。

-   [242] Muhammad Shafique、Mahum Naseer、Theocharis Theocharides、Christos Kyrkou、Onur Mutlu、Lois Orosa 和 Jungwook Choi。健壮机器学习系统：挑战、当前趋势、视角以及未来之路。IEEE Des. Test，37(2)：30–57，2020。

-   [243] Mahmood Sharif、Sruti Bhagavatula、Lujo Bauer 和 Michael K. Reiter。为犯罪配饰：对最先进的人脸识别系统的真实和隐蔽攻击。在 Edgar R. Weippl、Stefan Katzenbeisser、Christopher Kruegel、Andrew C. Myers 和 Shai Halevi 编辑的《2016 年 ACM SIGSAC 计算机与通信安全会议论文集》（维也纳，奥地利，2016 年 10 月 24–28 日），第 1528–1540 页。ACM，2016。

-   [244] Hardik Sharma、Jongse Park、Naveen Suda、Liangzhen Lai、Benson Chau、Vikas Chandra 和 Hadi Esmaeilzadeh。Bit fusion：位元级可组合架构，用于加速深度神经网络。在 Murali Annavaram、Timothy Mark Pinkston 和 Babak Falsafi 编辑的《第 45 届 ACM/IEEE 年度计算机架构国际会议（ISCA 2018）》，2018 年 6 月 1–6 日，美国洛杉矶，第 764–775 页。IEEE 计算机学会，2018。

-   [245] Saima Sharmin、Priyadarshini Panda、Syed Shakib Sarwar、Chankyu Lee、Wachirawit Ponghiran 和 Kaushik Roy。对尖峰神经网络对抗鲁棒性的全面分析。在 International Joint Conference on Neural Networks, IJCNN 2019，2019 年 7 月 14–19 日，匈牙利布达佩斯，第 1–8 页。IEEE，2019。

-   [246] Saima Sharmin、Nitin Rathi、Priyadarshini Panda 和 Kaushik Roy。深度尖峰神经网络的固有对抗鲁棒性：离散输入编码和非线性激活的影响。在 Computer Vision - ECCV 2020 - 第 16 届欧洲会议，2020 年 8 月 23–28 日，英国格拉斯哥，卷 12374，Lecture Notes in Computer Science，第 399–414 页。Springer，2020。

-   [247] Reza Shokri、Marco Stronati、Congzheng Song 和 Vitaly Shmatikov。对机器学习模型的成员推断攻击。在 2017 年 IEEE 安全与隐私研讨会（SP 2017），2017 年 5 月 22–26 日，美国圣何塞，第 3–18 页。IEEE 计算机学会，2017。

-   [248] Sumit Bam Shrestha 和 Garrick Orchard。SLAYER：时间中的尖峰层错误重新分配。在 Samy Bengio、Hanna M. Wallach、Hugo Larochelle、Kristen Grauman、Nicolò Cesa-Bianchi 和 Roman Garnett 编辑的《神经信息处理系统进展：2018 年国际神经信息处理系统会议（NeurIPS 2018）》，2018 年 12 月 3–8 日，加拿大蒙特利尔，第 1419–1428 页，2018。

-   [249] Ayesha Siddique 和 Khaza Anuarul Hoque。近似是否对深度神经网络的对抗攻击具有普遍防御作用？在 Cristiana Bolchini、Ingrid Verbauwhede 和 Ioana Vatajelu 编辑的《2022 年设计、自动化与测试在欧洲会议与展览（DATE 2022）》，2022 年 3 月 14–23 日，比利时安特卫普，第 364–369 页。IEEE，2022。

-   [250] Arnold J. F. Siegert。首次通过时间概率问题。Phys. Rev.，81：617–623，1951。

-   [251] Karen Simonyan 和 Andrew Zisserman。用于大规模图像识别的非常深层卷积网络。在 Yoshua Bengio 和 Yann LeCun 编辑的《第 3 届表示学习国际会议（ICLR 2015）》，2015 年 5 月 7–9 日，美国旧金山，会议论文集，2015。

-   [252] Amos Sironi、Manuele Brambilla、Nicolas Bourdis、Xavier Lagorce 和 Ryad Benosman。HATS：时间表的直方图用于稳健的事件基对象分类。在 2018 年 IEEE 计算机视觉与模式识别会议（CVPR 2018），2018 年 6 月 18–22 日，美国盐湖城，第 1731–1740 页。Computer Vision Foundation/IEEE 计算机视觉协会，2018。

-   [253] Leslie N. Smith 和 Nicholay Topin。超快训练：使用大学习率快速训练残差网络。CoRR，abs/1708.07120，2017。

-   [254] Theofilos Spyrou、Sarah A. El-Sayed、Engin Afacan、Luis A. Camuñas-Mesa、Bernabé Linares-Barranco 和 Haralampos-G. Stratigopoulos。尖峰神经网络的神经元容错性。在 Design, Automation & Test in Europe Conference & Exhibition, DATE 2021，2021 年 2 月 1–5 日，法国格勒诺布尔，第 743–748 页。IEEE，2021。



-   [\[255\]](#chapter2.xhtml#b2refbib255) Gopalakrishnan Srinivasan, Priyadarshini Panda, and Kaushik Roy. Stdp-based unsupervised feature learning using convolution-over-time in spiking neural networks for energy-efficient neuromorphic computing. ACM Journal on Emerging Technologies in Computing Systems, 14(4):44:1–44:12, 2018.

-   [\[256\]](#chapter2.xhtml#b2refbib256) Nitish Srivastava, Geoffrey Hinton, Alex Krizhevsky, Ilya Sutskever, and Ruslan Salakhutdinov. Dropout: A simple way to prevent neural networks from overfitting. Journal of Machine Learning Research, 15(56):1929–1958, 2014.

-   [\[257\]](#chapter2.xhtml#b2refbib257) Kenneth Stewart, Garrick Orchard, Sumit Bam Shrestha, and Emre Neftci. Online few-shot gesture learning on a neuromorphic processor. IEEE Journal on Emerging and Selected Topics in Circuits and Systems, 10(4):512–521, 2020.

-   [\[258\]](#chapter6.xhtml#b6refbib258) Marcel Stimberg, Romain Brette, and Dan FM Goodman. Brian 2, an intuitive and efficient neural simulator. eLife, 8: e47314, aug 2019.

-   [\[259\]](#chapter2.xhtml#b2refbib259) Jan Stuijt, Manolis Sifalakis, Amirreza Yousefzadeh, and Federico Corradi. µbrain: An event-driven and fully synthesizable architecture for spiking neural networks. Frontiers in Neuroscience, 15, 2021.

-   [\[260\]](#chapter2.xhtml#b2refbib260) Jiawei Su, Danilo Vasconcellos Vargas, and Kouichi Sakurai. One pixel attack for fooling deep neural networks. IEEE Transactions on Evolutionary Computation, 23(5):828–841, 2019.

-   [\[261\]](#chapter2.xhtml#b2refbib261) Yunjae Suh, Seungnam Choi, Masamichi Ito, Jeongseok Kim, Youngho Lee, Jongseok Seo, Heejae Jung, Dong-Hee Yeo, Seol Namgung, Jongwoo Bong, Sehoon Yoo, Seung-Hun Shin, Doowon Kwon, Pilkyu Kang, Seokho Kim, Hoonjoo Na, Kihyun Hwang, Chang-Woo Shin, Jun-Seok Kim, Paul K. J. Park, Joonseok Kim, Hyunsurk Ryu, and Yongin Park. A 1280960 dynamic vision sensor with a 4.95-µm pixel pitch and motion artifact minimization. In *IEEE International Symposium on Circuits and Systems, ISCAS 2020, Sevilla, Spain, October 10-21, 2020*, pages 1–5. IEEE, 2020.

-   [\[262\]](#chapter2.xhtml#b2refbib262) Vivienne Sze, Yu-Hsin Chen, Tien-Ju Yang, and Joel S. Emer. Efficient processing of deep neural networks: A tutorial and survey. Proceedings of the IEEE, 105(12):2295–2329, 2017.

-   [\[263\]](#chapter2.xhtml#b2refbib263) Mingxing Tan, Bo Chen, Ruoming Pang, Vijay Vasudevan, Mark Sandler, Andrew Howard, and Quoc V. Le. Mnasnet: Platform-aware neural architecture search for mobile. In *IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2019, Long Beach, CA, USA, June 16-20, 2019*, pages 2820–2828. Computer Vision Foundation/IEEE, 2019.

-   [\[264\]](#chapter6.xhtml#b6refbib264) Jigang Tang, Songbin Li, and Peng Liu. A review of lane detection methods based on deep learning. Pattern Recognition, 111: 107623, 2021.

-   [\[265\]](#chapter2.xhtml#b2refbib265) Simen Thys, Wiebe Van Ranst, and Toon Goedemé. Fooling automated surveillance cameras: Adversarial patches to attack person detection. In *IEEE Conference on Computer Vision and Pattern Recognition Workshops, CVPR Workshops 2019, Long Beach, CA, USA, June 16-20, 2019*, pages 49–55. Computer Vision Foundation/IEEE, 2019.

-   [\[266\]](#chapter4.xhtml#b4refbib266) Tijmen Tieleman. The affnist dataset. [cs.toronto.edu](http://cs.toronto.edu), 2013.

-   [\[267\]](#chapter2.xhtml#b2refbib267) Florian Tramèr, Fan Zhang, Ari Juels, Michael K. Reiter, and Thomas Ristenpart. Stealing machine learning models via prediction apis. In Thorsten Holz and Stefan Savage, editors, *25th USENIX Security Symposium, USENIX Security 16, Austin, TX, USA, August 10-12, 2016*, pages 601–618. USENIX Association, 2016.

-   [\[268\]](#chapter2.xhtml#b2refbib268) Frederick Tung and Greg Mori. CLIP-Q: deep network compression learning by in-parallel pruning-quantization. In *2018 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2018, Salt Lake City, UT, USA, June 18-22, 2018*, pages 7873–7882. Computer Vision Foundation/IEEE Computer Society, 2018.

-   [\[269\]](#chapter2.xhtml#b2refbib269) Ramakrishna Vadlamani, Jia Zhao, Wayne P. Burleson, and Russell Tessier. Multicore soft error rate stabilization using adaptive dual modular redundancy. In Giovanni De Micheli, Bashir M. Al-Hashimi, Wolfgang Müller, and Enrico Macii, editors, *Design, Automation and Test in Europe, DATE 2010, Dresden, Germany, March 8-12, 2010*, pages 27–32. IEEE Computer Society, 2010.

-   [\[270\]](#chapter1.xhtml#b1refbib270) Valerio Venceslai, Alberto Marchisio, Ihsen Alouani, Maurizio Martina, and Muhammad Shafique. Neuroattack: Undermining spiking neural networks security through externally triggered bit-flips. In *2020 International Joint Conference on Neural Networks, IJCNN 2020, Glasgow, United Kingdom, July 19-24, 2020*, pages 1–8. IEEE, 2020.

-   [\[271\]](#chapter1.xhtml#b1refbib271) Alberto Viale, Alberto Marchisio, Maurizio Martina, Guido Masera, and Muhammad Shafique. Carsnn: An efficient spiking neural network for event-based autonomous cars on the loihi neuromorphic research processor. In *International Joint Conference on Neural Networks, IJCNN 2021, Shenzhen, China, July 18-22, 2021*, pages 1–10. IEEE, 2021.

-   [\[272\]](#chapter1.xhtml#b1refbib272) Alberto Viale, Alberto Marchisio, Maurizio Martina, Guido Masera, and Muhammad Shafique. Lanesnns: Spiking neural networks for lane detection on the loihi neuromorphic processor. In *IEEE/RSJ International Conference on Intelligent Robots and Systems, IROS 2022, Kyoto, Japan, October 23-27, 2022*, pages 79–86. IEEE, 2022.

-   [\[273\]](#chapter2.xhtml#b2refbib273) Sameer Wagh, Divya Gupta, and Nishanth Chandran. Securenn: 3-party secure computation for neural network training. Proc. Priv. Enhancing Technol., 2019(3):26–49, 2019.

-   [\[274\]](#chapter2.xhtml#b2refbib274) Binghui Wang and Neil Zhenqiang Gong. Stealing hyperparameters in machine learning. In *2018 IEEE Symposium on Security and Privacy, SP 2018, Proceedings, 21-23 May 2018, San Francisco, California, USA*, pages 36–52. IEEE Computer Society, 2018.

-   [\[275\]](#chapter1.xhtml#b1refbib275) Kuan Wang, Zhijian Liu, Yujun Lin, Ji Lin, and Song Han. HAQ: hardware-aware automated quantization with mixed precision. In *IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2019, Long Beach, CA, USA, June 16-20, 2019*, pages 8612–8620. Computer Vision Foundation/IEEE, 2019.

-   [\[276\]](#chapter4.xhtml#b4refbib276) Limin Wang, Sheng Guo, Weilin Huang, and Yu Qiao. Places205-vggnet models for scene recognition. *CoRR*, abs/1508.01667, 2015.

-   [\[277\]](#chapter3.xhtml#b3refbib277) Meiqi Wang, Siyuan Lu, Danyang Zhu, Jun Lin, and Zhongfeng Wang. A high-speed and low-complexity architecture for softmax function in deep learning. In *2018 IEEE Asia Pacific Conference on Circuits and Systems, APCCAS 2018, Chengdu, China, October 26-30, 2018*, pages 223–226. IEEE, 2018.

-   [\[278\]](#chapter2.xhtml#b2refbib278) Zhenzhong Wang, Lilin Guo, and Malek Adjouadi. A biological plausible generalized leaky integrate-and-fire neuron model. In *36th Annual International Conference of the IEEE Engineering in Medicine and Biology Society, EMBC 2014, Chicago, IL, USA, August 26-30, 2014*, pages 6810–6813. IEEE, 2014.

-   [\[279\]](#chapter4.xhtml#b4refbib279) Devin Willmott et al. You only query once: Effective black box adversarial attacks with minimal repeated queries. *arXiv*, 2021.

-   [\[280\]](#chapter2.xhtml#b2refbib280) Bichen Wu, Xiaoliang Dai, Peizhao Zhang, Yanghan Wang, Fei Sun, Yiming Wu, Yuandong Tian, Peter Vajda, Yangqing Jia, and Kurt Keutzer. Fbnet: Hardware-aware efficient convnet design via differentiable neural architecture search. In *IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2019, Long Beach, CA, USA, June 16-20, 2019*, pages 10734–10742. Computer Vision Foundation/IEEE, 2019.



-   [μ]Brain，29

A

*   AccelAT framework，39

*   Accelerator 

    *   construction，70

    *   DNN，15，17，54，76–77，98

    *   efficient hardware，54–64

    *   energy-efficient CapsNet，64–76

    *   hardware，8，10，54，67，90，112，172–173，184–185，293

    *   parameters of，67–68

    *   pareto-optimal CapsNet，64

*   Accumulator，56，57，*58*，60–61，80–81，86–89，97，99，125–126

*   Accuracy_model，107

*   Activation functions，12，35，42，56，110

*   Activation unit，57，*58*，59，61

*   Adaptive batch size (AdaBatch)，44，46–48，50，52

*   Address event representation (AER) protocol，30

*   Adversarial attacks，36–41，131–140，141–143，152–166，262–263，265–269，271–272，*282* 

    *   Carlini Wagner (CW) attack，138–139

    *   evaluation of robustness on，134–135

    *   functionality，example of，*36*

    *   generation，145

    *   robustness against，137–140

    *   and R-SNN，271–273

    *   types of methods，*37*

*   Adversarial defenses，39

*   Adversarial examples，generation of，144

*   Adversarial goal，36，*37*

*   Adversarial perturbation，3，8，38–39，168，185–191，*264*，269，*272* 

    *   selection，188

    *   value，187

*   Adversarial security threats，36–37，131–166 

    *   CapsAttack，142–152

    *   for CapsNets，131–166

    *   for DNNs，131–166

    *   fakeWeather attack，152–166

    *   overview，131，*132*

    *   RobCaps，132–142

*   Adversarial success rate (ASR)，139，161–162，*162*



-   对抗训练, 39–40, 131, 133, 135, 139–140, 142, 166

-   Affine-CIFAR10, 133–137, 140

-   Affine-GTSRB, 133–136

-   仿射变换, 131–137, 140–141, 142, 166, 292  

    *   鲁棒性评估, 134

    *   结果, 136–137

    *   鲁棒性对, 135–137, **141**

-   聚合图案, 156–157

-   老化, 3, 32, 35

-   AlexNet, 14, 20, *20*, 237

-   算法  

    *   位翻转与梯度搜索, 253–254

    *   穷举, 70, *71*, 72–73

    *   动态路由量化, 106

    *   假雪掩码生成, 160

    *   梯度下降优化, 227

    *   启发式搜索, 72–73

    *   层级量化, 105

    *   马尔可夫链蒙特卡洛, 241

    *   多目标 NSGA-II, 172–177

    *   非占优遗传算法 (NSGA-II)), 64

    *   优化, 13, 191, 227

    *   鲁棒性探索, 265

    *   R-SNN 防御方法论, 274

    *   搜索, 65–66

    *   监督学习, 241

    *   触发生成循环, 257

-   算法容错 (ABFT)), 34

-   对抗过拟合, 230–231, **231**

-   面向应用的记忆功率管理, 78, 86–87, 99

-   应用特定优化技术, 6

-   近似  

    *   组件, 19, 57, 110–118, 295

    *   计算, 7, 39, 110, 120, 121, 130

    *   软 max 设计, 122–125  

        *   评估, 127–130

        *   概述, 120–121

        *   软 max-b2, 124–125

        *   软 max-lnu, 123–124

        *   软 max-taylor, 122–123

    *   挤压设计, 125–127  

        *   评估, 127–130

        *   概述, 120–121

        *   挤压-经验, 126, *127*

        *   挤压-规范, 125, *126*

        *   挤压-2 的幂, 126–127

-   近似 DNNs, 19

-   近似误差, 19, 43, 110, 111, 120, 236

-   架构  

    *   硬件, 14

    *   网络, 228–230

    *   神经形态, 2, 10, 24, 28–29, 193

    *   优化目标, 2–3

    *   参数化建模, 171–172

    *   空间, 14–17, *15*

    *   时间, 14–15, *15*

-   区域  

    *   减少字长的分析, 100–101

    *   vs. 延迟, 69, 70, *71*

-   算术逻辑单元 (ALUs)), 15

-   异步基于时间的图像传感器 (ATIS)), 212

-   攻击)  

    *   后门, 38, 39, 291

    *   位翻转, 34, 251

    *   黑盒, 36, 40, 153

    *   边界, 40

    *   Carlini Wagner (CW)), 40, 138–139

    *   角, 283, 288

    *   dash, 283–284, 288–289

    *   基于决策的, 38

    *   deepfool, 40

    *   规避, 37, 38

    *   FaDec, 38

    *   假雨, 160–161

    *   假雨, 156–158

    *   假雪, 158–160, *159*

    *   帧, 282–283, 287–288

    *   灰色框, 36

    *   MF-aware dash, 284–286, 289–290

    *   模型提取, 33

    *   模型倒置, 33

    *   一像素, 38, 155

    *   物理世界, 39

    *   中毒, 38, 39

    *   实际故障, 34

    *   行黑客, 34

    *   稀疏, 282

    *   通用, 40

    *   投票, 40

    *   白盒, 36, 40, 133–134

-   攻击者知识, 36, *37*

-   攻击生成, 264

-   攻击方法讨论, 144

-   注意力窗口策略, 212




*   delimited points for, `213`

*   SNN model for first, `215`

*   SNN model for second, `215`

*   Autonomous Driving (AD), `41`, `211`

*   Average normalized Euclidean distance (ANED), `71`, `73`

*   Axon, `10`, `195`, `197`

B

*   Backdoor attacks, `38`, `39`, `291`; *see also* `Attack(s)`

*   Background activity filter (BAF), `279`–`280`

*   Batch normalization, `12`, `14`, `134`

*   Bias temperature instability (BTI), `35`

*   Binary cross-entropy (BCE), `227`–`228`

*   Biological brain, `28`

*   Bit-flip attack, `34`, `251`; *see also* `Attack(s)`

*   Bit-widths, `2`, `57`

*   Black-box attacks, `36`, `40`, `153`; *see also* `Attack(s)`

*   Black-box relations with DL model, `294`

*   Boundary attack, `40`; *see also* `Attack(s)`

*   BrainScaleS, `29`

*   Brute-force algorithm, `70`, *71*, `72`–`73`

*   Brute-force *vs.* heuristic search, `65`–`66`

C

*   CACTI-P tool, `70`, `84`, `90`, `91`

*   CapsAcc architecture design, `54`–`64` 

    *   accumulator, `57`

    *   activation unit, `57`–`58`

    *   analyses of CapsNets complexity, `54`–`56`

    *   analyses of execution time, `54`–`56`

    *   architecture design, `56`–`59`

    *   control unit, `58`–`59`

    *   different components of, `63`

    *   evaluation of, `62`–`63`

    *   memory hierarchy, `59`

    *   overview, `54`, `56`

    *   parameters of, `63`

    *   processing element array, `57`

*   CapsAttacks, `142`–`152` 

    *   adversarial examples, `143`–`146`

    *   evaluation of, `146`–`152`

    *   imperceptibility, `143`–`144`

    *   overview, `142`–`143`

    *   robustness, `143`–`144`

*   CapsNet inference, resource analysis of, `80`–`85` 

    *   energy breakdown analysis, `83`–`85`

    *   memory analyses 

        *   for DeepCaps, `83`

        *   for google's capsnet, `80`–`83`

    *   performance analyses 

        *   for DeepCaps, `83`

        *   for google's capsnet, `80`–`83`

*   CapsNet layers, parametric modeling of, `171`–`172`

*   Capsule(s), defined, `20`–`21`

*   Capsule layers, `8`, `23`, `44`, `134`, `168`–`172`, `180`, `184`, `190`

*   Capsule networks (CapsNets), `19`–`24`, `42`–`130` 

    *   adversarial security threats for, `131`–`166`

    *   analysis of different operations in, `112`–`113`

    *   applications, `21`–`23`

    *   approximate 

        *   computing, `121`

        *   squash, `120`–`130`

    *   attack vulnerability comparison between CNNs and, `151`–`152`

    *   CapsAcc and, `54`–`64`

    *   challenges for, `23`–`24`

    *   *vs.* CNNs, `139`

    *   decoder, `49`–`50`

    *   DESCNet, `76`–`99`

    *   DNNs *vs.*, `20`–`21`, *21*

    *   FasTrCaps, `44`–`54`

    *   FEECA, `64`–`76`

    *   hardware, `6`–`7`, `76`–`99`, `110`, `112`

    *   hardware optimizations for, `42`–`130`

    *   inferences 

        *   off-chip accesses for, *82*

        *   operations, `55`

    *   models, `21`–`23`

    *   output probabilities for, *165*

    *   overview, `42`–`43`

    *   Q-CapsNets, `99`–`110`

    *   ReD-CaNe, `110`–`120`

    *   selected memory configurations for, `92`

    *   softmax designs, `120`–`130`

    *   software optimizations for, `42`–`130`

    *   trainable parameters of, `54`–`55`

    *   vulnerability studies for, `40`

*   Carlini Wagner (CW) attack, `40`, `138`–`139`

*   CarSNN, `211`–`224` 

    *   accuracy results for, `220`

    *   evaluation of, `219`–`223`

    *   general design decisions, `212`–`213`

    *   implemented on Loihi chip, `220`–`222`

    *   methodology, `213`–`219`

    *   model design, `213`–`215`

    *   overview, `211`–`212`

    *   parameters for feeding input data, `217`–`219`

    *   problem analysis, `212`–`213`

*   Cars *vs.* background, `212`–`213`, `223`

*   Catholic University of Louvain, `29`

*   CeleX V sensor, `31`

*   Chain rule, `13`

*   Chaudhuri, Kamalika, `125`

*   Chip




-   `architecture`, 196–197

-   `BrainScaleS`, 29

-   `DYNAP-SE`, 29

-   `fabrication`, 32, 34

-   `Loihi`, 9, 194, 195, 196, 198, 203, 212–214, 219–220, 222, **222**, **223**, 235

-   `NeuroGrid`, 29

-   `neuromorphic`, 24, 28, 211–214, 219–220, 222, 224, 236, 269

-   `ODIN`, 29

-   `SpiNNaker`, 28

-   `TrueNorth`, 28

-   `*μ*Brain`, 29

-   `CIFAR10` datasets, 107, **109**, 111, 136 

    *   `adversarial perturbation values for`, *189*

    *   `affined-transformed version of`, 133

    *   `detailed analysis for`, 117

    *   `methodology applied to`, 149–151

    *   `Q-CapsNets results of DeepCaps for`, *109*

    *   `quantized deepcaps for`, 108–109

-   `ClassCaps` layer, 22, 50, 53–55, 61, 71, 83, 134–136, 140; *see also* `Layer(s)`

-   `Clements, Joseph`, 34

-   `CMOS technology`, 28–29, 54, 62, 76, 78, 84, 96, 101, 112, 177

-   `CNN LaneSNN`, 230

-   `Compartment voltage threshold`, 234

-   `Complexity reduction`, 47, 49

-   `Compression`, 2, 4, 18, 134, 293, 294

-   `Computer architecture`, 28

-   `Control unit`, 58–59, *59*

-   `Conv1 layers`, 71

-   `ConvCaps2D layers`, 83

-   `Conventional computing`, 28, 193, 295

-   `Conversion process`, 202–203 

    *   `conversion`, 202

    *   `mapping`, 203

    *   `parsing`, 202

    *   `partition`, 203

-   `Convolutional (Conv) layers`, 2, 11–12; *see also* `Layer(s)`

-   `Convolutional neural networks (CNNs)`, 44 

    *   *vs.* `CapsNets`, 139

    *   `layer choice in`, 256

    *   `structure, in experiments on CIFAR10`, **254**

-   `Corner attack`, 283, 288; *see also* `Attack(s)`

-   `Cost-effective optimizations`, 5–6

-   `Coupling coefficients`, 21, 55, 61, 141

-   `Cross-layer methodology`, 8

-   `Cross-layer optimizations`, 4, 10, 292, 296

-   `Crossover between two genotypes`, *176*

-   `Crossover operations`, 176

-   `CryptoNets`, 33

-   `CuDNN`, 15

-   `CUrrent BAsed Leaky-Integrateand- Fire (CUBA-LIF) neuron`, 195

-   `Dash attack`, 283–284, 288–289; *see also* `Attack(s)`

-   `Data augmentation`, 39, 107, 134–135, 153, 166, 226, 227

-   `Dataflow design`, 59–61 

    *   `of ClassCaps layer`, 61

    *   `of Conv1 Layer`, 59

    *   `of dynamic routing`, 61

    *   `of PrimaryCaps layer`, 60

-   `Data register`, 57

-   `Data reuse`, 15, 17, 57, 61, 77

-   `Dataset pre-processing`, 226

-   `Dataset structure`, 209

-   `DAVIS pixel`, *30*

-   `Decision-based attacks`, 38

-   `Decoupled weight decay strategy`, 233

-   `Deep belief networks (DBNs)`, 241

-   `DeepCaps` 

    *   `architectural model of`, *23*

    *   `architecture`, 23, 108, 135, 140, 146, 172, 180, 181

    *   *vs.* `CNN`, 136–137

    *   `methodology applied to`, 149–151

    *   *vs.* `ResNet20`, 136–137

    *   `selected memory configurations for`, **94**

    *   *vs.* `ShallowCaps`, 136, 137, 139

-   `Deepfool attack`, 40

-   `Deep learning (DL) systems`, 1, 10–41, 169, 268 

    *   `capsule networks`, 19–24

    *   `deep neural networks (DNNs)`, 10–19

    *   `flow`, 36–37, *37*

    *   `overview`, 10

    *   `spiking neural networks (SNNs)`, 24–32

    *   `vulnerabilities of`, 32–41 

        *   `adversarial security threats`, 36–39

        *   `fault injection`, 34

        *   `hardware trojans`, 34

        *   `privacy threats`, 32–34

        *   `reliability threats`, 34–35

        *   `vulnerability studies for CapsNets`, 40



# vulnerability studies for SNNs
Deep neural networks (DNNs) 1, 10–19–15, 17, 54, 76–77, 98–131–166–19–10–14–18–12–11–13, 131, 161, 163–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–2–3–[2](#chapter1.xhtml#<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> [content]...