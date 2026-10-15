
DVS 传感器主要受热活动和结点漏电流引起的背景活动噪声的影响 \[[191](#refbib.xhtml#refbib191)\]。当 DVS 被激活时，相邻像素的窗口同时激活，产生事件。因此，实际事件的空间-时间相关性高于噪声事件。这一经验观察被用于过滤噪声 \[[133](#refbib.xhtml#refbib133)\]。计算空间-时间邻域中事件的相关性。如果相关性低于特定阈值，则事件很可能捕获噪声并被过滤掉；否则保留。该过程在 [Algorithm 26](#chapter7.xhtml#comp07_4) 中描述，其中 `s` 和 `t` 是唯一用于确定空间-时间邻域尺寸的过滤参数。对于 `s` 和 `t` 的大值，仅有少量事件被过滤。过滤的决策依据是 `t[e]` − `M[x[e]][y[e]]` 与 `t` 的比较（[Algorithm 26](#chapter7.xhtml#comp07_4) 的第 8‑9 行）。
![](images/comp07_4.jpg)

### 7.4.3.2 空间-时间域中的对抗攻击

目前，对抗攻击在许多深度学习（DL）应用中被部署，它们对安全关键应用构成严重威胁。成功的攻击旨在生成微小扰动，误导网络。最近，已有一些关于针对 spiking 神经网络（SNNs）的对抗攻击的初步研究 \[[10](#refbib.xhtml#refbib10), [245](#refbib.xhtml#refbib245)\]。*然而，这些先前的工作并未分析来自 DVS 摄像机的事件帧的攻击*。

对于图像的对抗攻击，扰动仅在空间域中引入。但当考虑视频对抗攻击时，视频是图像帧的序列，攻击算法也可以扰动时间域。虽然预期的扰动会通过时间交互作用传播到其他帧，但只对少量帧进行扰动会使攻击更隐蔽。事实上，当前最先进的视频攻击只在少数帧上添加扰动，这些扰动会在时间上传播，从而导致视频误分类。

### 7.4.3.3 对抗威胁模型

在我们的实验中，我们在系统设置中假设不同的威胁模型，如 [Figure 7.23](#chapter7.xhtml#fig7_23) 所示。在三种情形中，给定的对抗攻击算法对 DVS 摄像机生成的事件帧进行扰动，以欺骗 SNN。在威胁模型 A⃝ 中，攻击者拥有输入到 SNN 的事件帧。在威胁模型 B⃝ 中，DVS 噪声过滤器并行插入系统，攻击者不知晓该过滤。基于这些假设，攻击可能较弱，因此我们还分析威胁模型 C⃝，其中攻击者知道 DVS 噪声过滤器的存在。在此情形下，过滤器被视为预处理步骤并嵌入攻击循环。

![Figure 7.23: Adversarial threat models are considered in this work. (a) The adversary introduces adversarial perturbations to the frames of events at the input of the SNN. (b) The noise filter is inserted as a defense to secure the SNNs against adversarial perturbations while the adversary is unaware of the filter. (c) The adversary is aware of the presence of the noise filter and sees it as a preprocessing step of the SNN.](images/fig7_23.jpg)

[Figure 7.23:](#chapter7.xhtml#b7fig7_23) Adversarial threat models are considered in this work. **(a)** The adversary introduces adversarial perturbations to the frames of events at the input of the SNN. **(b)** The noise filter is inserted as a defense to secure the SNNs against adversarial perturbations while the adversary is unaware of the filter. **(c)** The adversary is aware of the presence of the noise filter and sees it as a preprocessing step of the SNN.

### 7.4.3.4 事件帧的对抗攻击生成

对事件帧的对抗攻击生成过程如下。受帧基视频攻击算法的启发，我们专门设计了针对 DVS 信号的攻击算法。[Algorithm 27](#chapter7.xhtml#comp07_5) 描述了我们方法的逐步过程。它是一个迭代算法，为数据集 `D` 的每个帧序列计算扰动值（第 2‑17 行），基于 SNN 的损失函数。 masks `M` 决定在哪些子集的事件帧上添加扰动（第 3 行）。随后，在第 5‑6 行计算出带扰动的输出概率及其对应的损失。最后，扰动值根据相对于损失的输入梯度计算得出。

![](images/comp07_5.jpg)

### 7.4.3.5 我们提出的防御方法

我们针对 SNNs 的防御方法基于专用的 DVS 噪声过滤。[Algorithm 28](#chapter7.xhtml#comp07_6) 报告了如何选择高效的空间参数 `s` 和时间参数 `t`。对于不同的威胁模型，算法会在给定参数下，用过滤器对攻击进行评估，自动搜索 `s` 与 `t` 的最佳组合。在此条件下，SNN 的准确率与之前记录的最高准确率进行比较（第 8 行）。最终输出的参数 `s^′` 与 `t^′` 是实现最高准确率的组合。

![](images/comp07_6.jpg)

## 7.4.4 R‑SNN 方法的评估

### 7.4.4.1 实验设置

在我们的实验中，我们使用了两个基于事件的数据集：DvsGesture \[[8](#refbib.xhtml#refbib8)\] 和 NMNIST \[[193](#refbib.xhtml#refbib193)\]。前者包含 1077 个训练样本和 264 个测试样本，涵盖 11 个类别。后者是对原始帧基 MNIST 数据集的 spiking 转换 \[[118](#refbib.xhtml#refbib118)\]，包含 60 000 个训练样本和 10 000 个测试样本，由 ATIS 事件传感器在捕捉 LCD 屏幕上投射的原始 MNIST 图像时移动生成 \[[211](#refbib.xhtml#refbib211)\]。对于 DvsGesture 数据集，我们采用了如 \[[248](#refbib.xhtml#refbib248)\] 所述的 4 层 SNN，包括两层卷积层和两层全连接层。该网络经过 625 个时代使用 SLAYER 反向传播方法 \[[248](#refbib.xhtml#refbib248)\] 训练，批量大小为 4，学习率为 0.01。对于 NMNIST 数据集，我们使用了一个包含两层全连接层的 spiking 多层感知器 \[[248](#refbib.xhtml#refbib248)\]，训练 350 个时代，同样使用 SLAYER 方法，批量大小为 4，学习率为 0.01。我们使用 PyTorch 框架 \[[204](#refbib.xhtml#refbib204)\] 在配备两块 Nvidia GeForce RTX 2080 Ti GPU 的 ML 工作站上实现 SNNs，同时在 PyTorch 中实现对抗攻击算法和 \[[133](#refbib.xhtml#refbib133)\] 的噪声过滤。 
