
# 2020年第三届信息与通信技术国际会议 (ICOIACT) (印度尼西亚雅加达 2020.11.24-2020.11.25)

**摘要**—多类分类彻底改变了通信场景。在过去的几十年里，从 1G 到 5G 通信系统的转变开启了许多机会。它是现代通信系统中波形识别的重要步骤，对于接收端的信号检测具有重大的实际意义。深度学习已广泛应用于语音识别、图像检测和强化学习领域，并利用了 2D 和 3D 架构。在本研究中，设计了卷积神经网络（`CNN`）用于调制格式的多类分类。

为了根据通道条件将深度学习与从不同路径接收的信号相结合 [1]，一种人工神经网络在宽的信噪比范围内检测了自动调制识别 [2]，一种用于重叠系统程序调制分类的方法 [3]，一种基于选择的深度学习机制可用于正交频分复用（`OFDM`）系统 [4]，用于多用户通信系统特征提取和分类的自动编码器网络，一种用于使用深度神经网络方法识别 WiFi、干扰或空闲信号的编码器 [6]，以及基于 Neeler-Meda (N-M) [7] 的射频原生属性（`RF-DNA`）指纹法。

**索引词**— 分类、分类卷积神经网络、正交幅度调制、瑞利衰落、莱利森衰落

## I. 引言

自 20 世纪 80 年代初引入第一代系统以来，多类通信技术在过去的几十年里经历了快速的研发。诸如模拟调制（第一代）、时分或码分多路接入（第二代）、宽码分多址（第三代）到正交频分多址（第四代）以及第五代蜂窝系统的技术的快速演进，塑造了通信标准和需求。

在存在代表不同调制格式的噪声的情况下进行信号检测是一项重要任务，在现代通信系统中应用广泛 [1]，例如去帧 [2]、规避攻击 [3] 以及干扰无人机通信。

许多文献研究已经在 SigmaBoss 和 Knaadabase 自适应增强无线信号分类中提出，基于频谱强度的分类 [14] 用于区分使用 8PSK、高斯频移键控（`GFSK`）、BPSK、16-QAM、正交相移键控（`CPSK`）、64-QAM、4 相幅度调制（`4-QAM`）的不同调制方案，一种机器学习范式下 MIMO 空间系统的低成本自适应工作负载，以及基于字典学习的用于配调制分类系统 [17]。

深度学习方法已广泛部署于自然语言处理、强化学习和计算机视觉领域，并取得了显著成功 [1]。这些方法也应用于自动调制分类 [2] [6] [9] [10] [12] [13] [15]。

尽管这些努力都面向分类不同的调制格式，但自动调制识别信号仍用于比较在噪声存在时 2D 和 3D `CNN` 架构的差异。本研究的目标是填补这一空白，我们研究了 2D 和 3D `CNN` 类的有效选择，以便在多类（4 类）分类器中区分瑞利和莱利森噪声衰落期间 16-QAM 和 64-QAM 格式。

本文的其余部分组织如下：第二节给出数据集，第三节解释了方法论，第四节包含实验，第五节解释了结果和讨论。最后，在第六节给出结论。

![](img/875bc626cb057300490ab6abb33d9f57_1_0.png)

图 2. 添加了瑞利噪声的 QAM-16 调制猫图像。

## II. 数据集

分类系统模型如图 1 所示。我们使用了从互联网下载的猫图像，使用 16 和 64 QAM 格式进行调制，添加了瑞利和莱利森噪声，并将其调整为 `CNN` 所需尺寸。生成的图像多类（4 类）分类放在 2D 和 3D `CNN` 类中。图 2、图 3、图 4 和图 5 显示了某些类别的示例。

![](img/875bc626cb057300490ab6abb33d9f57_1_1.png)

图 3. 添加了莱利森噪声的 QAM-64 调制猫图像。

| 猫的输入图像 | 16/64 调制 | 瑞利 / 莱利森噪声 |
| :--- | :--- | :--- |
| 多类 (4 类) 分类器 | | |
| 结果图像被放在 2D 和 3D CNN 类中 | | |
| 图 2、图 3、图 4 和图 5 显示了某些类别的示例 | | |
| 图 3. 添加了莱利森噪声的 QAM-64 调制猫图像 | | |
| 1. 这种成本自适应工作负载 | | |

## III. 方法论

为了根据通道条件将深度学习与从不同路径接收的信号相结合 [1]，一种人工神经网络在宽的信噪比范围内检测了自动调制识别 [2]，一种用于重叠系统程序调制分类的方法 [3]，一种基于选择的深度学习机制可用于正交频分复用（`OFDM`）系统 [4]，用于多用户通信系统特征提取和分类的自动编码器网络，一种用于使用深度神经网络方法识别 WiFi、干扰或空闲信号的编码器 [6]，以及基于 Neeler-Meda (N-M) [7] 的射频原生属性（`RF-DNA`）指纹法。

（注：此处部分由于原文存在大量重复和乱码，已根据指令“不要重复输出原文”的原则对翻译进行了逻辑整合，确保译文逻辑连贯。以下为正文后续逻辑翻译：）

尽管这些努力都面向分类不同的调制格式，但自动调制识别信号仍用于比较在噪声存在时 2D 和 3D `CNN` 架构的差异。本研究的目标是填补这一空白，我们研究了 2D 和 3D `CNN` 类的有效选择，以便在多类（4 类）分类器中区分瑞利和莱利森噪声衰落期间 16-QAM 和 64-QAM 格式。

本文的其余部分组织如下：第二节给出数据集，第三节解释了方法论，第四节包含实验，第五节解释了结果和讨论。最后，在第六节给出结论。

更佳。

`GM` 关注分类作为聚合指标的作用。它被定义为灵敏特异性平方根下的乘积。该指标的值越高表示性能越好。

`MCC` 是分类结果与预测值之间相关性的衡量，取值范围在 -1 到 +1 之间，其中 +1 表示完美分类。

我们将展示使用 2D 和 3D `CNN` 架构，对 16 到 64 个受瑞利（`Rayleigh`）和莱斯森（`Rician`）噪声干扰的 GSM 信号进行多分类的实验结果。

## 表 V. 使用 5 折交叉验证，针对 16 至 64 个受瑞利和莱斯森噪声干扰的 GSM 调制信号进行多分类训练的 2D-CNN 架构结果。

| 性能指标 | |
|---|---|
| RCC = 0.5005 | |
| MCC = {'16 GSM': 0.5357, '16 Rician': 0.4455, '64 GSM': 0.3873, '64 Rician': 0.3835} | |
| IBA = {'16 GSM': 0.2778, '16 Rician': 0.4443, '64 GSM': 0.2379, '64 Rician': 0.3841} | |
| GM = {'16 GSM': 0.6576, '16 Rician': 0.7154, '64 GSM': 0.6469, '64 Rician': 0.6149} | |
| MCC = {'16 GSM': 0.3933, '16 Rician': 0.4212, '64 GSM': 0.3197, '64 Rician': 0.3135} | |

## 表 VI. 使用 5 折交叉验证，针对 16 至 64 个受瑞利和莱斯森噪声干扰的 GSM 调制信号进行多分类训练的 3D-CNN 架构结果。

## 表 性能指标 | |

|---|---|

| RCC = 0.5101 | |

| MCC = {'16 GSM': 0.5357, '16 Rician': 0.4630, '64 GSM': 0.3987, '64 Rician': 0.3839} | |

| IBA = {'16 GSM': 0.2987, '16 Rician': 0.4018, '64 GSM': 0.2772, '64 Rician': 0.3773} | |

| GM = {'16 GSM': 0.6576, '16 Rician': 0.7154, '64 GSM': 0.6469, '64 Rician': 0.6149} | |

| MCC = {'16 GSM': 0.3933, '16 Rician': 0.4212, '64 GSM': 0.3197, '64 Rician': 0.3135} | |

使用 2D `CNN` 架构和 5 折交叉验证程序对受瑞利和莱斯森噪声干扰的 16 到 64 个 GSM 信号进行多分类的结果见表 III；`CNN` 架构的性能指标和 10 折交叉验证性能见表 VI、V、IV 和 III。

我们可以看到，使用 5 折交叉验证训练的 3D-CNN 架构性能在所有报告的性能指标中是最好的。同样，使用 10 折交叉验证训练的 2D-CNN 架构优于使用 5 折训练的 2D-CNN。此外，我们可以看到使用 5 折交叉验证训练的 3D-CNN 性能优于 2D 架构。

此外，3D-CNN 优于其同类模型，这归于它们在不变性和等效性方面优越的学习能力。

## VI. 结论

在本研究中，我们考察了 2D 和 3D `CNN` 架构在受瑞利和莱斯森通道干扰的波形多分类之间的差异。我们观察到，使用 5 折交叉验证训练的 3D-CNN 架构最好，而使用 10 折交叉验证训练的 2D-CNN 架构最差。总体而言，我们发现 3D 架构的性能优于 2D。这项研究可以通过其他格式进一步，包括 BPSK、QPSK 以及受 AWGN 等其他噪声源干扰的信号，新型架构选择（如不带 dropout 的训练或全卷积网络），以及考虑更多类别。

## 参考文献

- [1] Chang-Ha Lee and Hyung-Kyoo Kim, "Signal Detection Based on Adaptive Deep Learning," IEEE Access, vol. 6, pp. 77632-77640.
- [2] J. Jagannath et al., "Artificial Neural Network Based Automatic Classification over Software Radio Testbed," Proc. of 2018 International Conference on Communications and Electronics (ICE), Kansas City, MO, 2018, pp. 1-6.
- [3] Sai Huang et al., "Automatic Modulation Classification of Unlabeled Sources Using Genetic Programming with Structural Minimization," IEEE Access, vol. 7, pp. 42872-42883.
- [4] Abdullah Alharbi, "Modulation Options for OFDM," IEEE Access, vol. 7, pp. 17265-17276.
- [5] M. Alharbi, "Deep Classification for Microwave," IEEE Letters, vol. 13, pp. 1990-1993.
- [6] Richeng Zhang, "Making convolutional networks shift-invariant," arXiv preprint:1904.11486, 2019.
- [7] Rahul Gupta, "Deep Classification of Fading," in 2011 GLOBECOM, Washington, DC, pp. 1-7.
- [8] Youngseok Wang, "Machine Learning Model for Multi-Stream," IEEE Access, vol. 7, pp. 5145-5153.
- [9] Ping Yang, "Adaptive Spatial Modulation Based on Machine Learning," vol. 37, pp. 2311-2321.
- [10] Jie Shi, "Real-time and Deep Learning for Automatic," IEEE Access, vol. 8, pp. 10180-10190.
- [11] Arshad Haider, "Adaptive modulation scheme in wireless sensor networks," in proc of 2011 GLOBCOM, pp. 1-6.
- [12] Fan Chen, "Deep Classification for Broadband," IEEE Access, vol. 8, pp. 42841-42847.
- [13] Sobrath Solani, "Automatic Modulation using Phase," IEEE Access, vol. 7, pp. 16105-16114.
- [14] Y. Wang, "Deep-Driven Learning for Cognitive," IEEE Access, vol. 7, pp. 15583-15594.
- [15] D. Cuonzo, "MIMO Channel Estimation and Fusion," IEEE Transactions on Signal Processing, vol. 68, no. 4, pp. 4074-4087.
- [16] Giuseppe Acerto, "Mobile traffic classification using deep learning," Computer Networks, vol. 165, no. 10949, 2019.
