
时间上的实例。经过若干个这样的周期后，收敛到局部最小值的前 5 个表现最佳的快照 [4] 将作为集成的一部分进行组合，以生成单一的预测结果。

优点：在单个训练周期内，可以收集到许多模型实例。缺点：由于反复使用相同的模型，天生缺乏多样性。

**SOL-154** **CH.SOL- 6.20.**
在每次迭代/周期开始时改变随机种子，有助于引入变化，从而有助于多样化训练出的神经网络模型。

## 6.3.6 多模型集成

**SOL-155** **CH.SOL- 6.21.**
多模型集成。
既包括平均法，也包括多数投票法。

## 6.3.7 集成中的学习率调度

**SOL-156** **CH.SOL- 6.22.**
捕捉每个训练周期中表现最佳的模型，使得在只训练单个模型的成本下，能够获得多个在不同周期内收敛于不同局部最优解的模型。
该方法基于神经网络的**非凸性**以及通过特定的调度方式在训练期间调整学习率从而收敛并逃离局部最小值的能力。
而非单调递减学习率，该方法允许学习率在合理的边界值之间周期性变化。

# 参考文献

1. B. Chu 等. ‘Best Practices for Fine-Tuning Visual Classifiers to New Domains’. 收录于：Computer Vision – ECCV 2016 研讨会 . 由 G. Hua 和 H. Jégou 编辑. 查姆：Springer International Publishing，2016 年，第 435–442 页 (引用于第 184 页).
2. Y. Gal 和 Z. Ghahramani. ‘Dropout as a Bayesian approximation’. 收录于：arXiv 预印本 arXiv:1506.02157 (2015) (引用于第 190 页).
3. L. K. Hansen 和 P. Salamon. ‘Neural Network Ensembles’. 收录于：IEEE 模式分析与机器学习智能汇刊 12 (1990)，第 993–1001 页 (引用于第 189, 197 页).
4. G. Huang 等. ‘Snapshot ensembles: Train 1, get M for free. arXiv 2017’. 收录于：arXiv 预印本 arXiv:1704.00109 (引用于第 184, 190, 200 页).
5. J. Huggins, T. Campbell 和 T. Broderick. ‘Coresets for scalable Bayesian logistic regression’. 收录于：Advances in Neural Information Processing Systems . 2016，第 4080– 4088 页 (引用于第 184, 198 页).
6. C. Ju, A. Bibaut 和 M. van der Laan. ‘The relative performance of ensemble methods with deep convolutional neural networks for image classification’. 收录于：应用统计汇刊 45.15 (2018)，第 2800–2818 页 (引用于第 190 页).
7. S. Kornblith, J. Shlens 和 Q. V. Le. 更快地制作更好的 ImageNet 模型？ 2018. arXiv:1805.08974 [cs.CV] (引用于第 184 页).
8. A. Krogh 和 J. Vedelsby. ‘Neural Network Ensembles, Cross Validation, and Active Learning’. 收录于：NIPS . 1994 (引用于第 197 页).
9. S. Lee 等. ‘Stochastic multiple choice learning for training diverse deep ensembles’. 收录于：Advances in Neural Information Processing Systems . 2017，第 2119– 2127 页 (引用于第 190 页).
10. I. Loshchilov 和 F. Hutter. ‘Sgdr: Stochastic gradient descent with warm restarts’. 收录于：arXiv 预印本 arXiv:1608.03983 (2016) (引用于第 196 页).
11. P. Oshiro 等. (2012)Oshiro 和 Baranauskas. ‘How many trees in a random forest?’. 收录于：国际机器学习与数据挖掘研讨会
12. Y. Ovadia 等. ‘Can you trust your model’s uncertainty? Evaluating predictive uncertainty under dataset shift’. 收录于：*Advances in Neural Information Processing Systems*. 2019，第 13991 页 (引用于第 190 页).
13. L. N. Smith. ‘Cyclical learning rates for training neural networks’. 收录于：*2017 IEEE 计算机视觉应用冬季会议 (WACV)*. IEEE. 2017，第 464–472 页 (引用于第 184, 196 页).

# 第 7 章
深度学习：CNN 特征提取

> *上升者必下降*.
> — 艾萨克·牛顿

# 目录

- 引言
- 问题
  - 作为固定特征提取器的 CNN
  - 微调 CNN
  - 神经风格迁移，NST
- 解决方案
  - 作为固定特征提取器的 CNN
  - 微调 CNN
  - 神经风格迁移

## 7.1 引言

![](img/574135cb1d7125b50cf484d943cdd676_214_0.png)

从一个（或多个）预训练 CNN 的层中提取 n 维特征向量（FV）或嵌入，被称为特征提取（FE）。通常，FE 的工作原理是首先移除 CNN 的最后一个全连接（FC）层，然后将 CNN 剩余的层视为固定的 FE。如图 (7.1) 和图 (7.2) 所示，将此方法应用于 ResNet34 架构时，生成的 FV 由 512 个浮点值组成。同样，对 ResNet152 架构应用相同逻辑时，生成的 FV 具有 2048 个浮点元素。

![](img/574135cb1d7125b50cf484d943cdd676_215_0.png)

```python
import torchvision.models as models
...
res_model = models.resnet34(pretrained=True)
```

图 7.2：预训练 ResNet34 CNN 的 PyTorch 声明（简化版）。

FE 背后的前提是，最初在 ImageNet 大规模视觉识别竞赛 [2] 上训练的 CNN，可以适应并用于完全不同的（目标）领域（例如分类任务），而**无需对 CNN 层进行任何额外训练**。CNN 之所以具备这种能力，在于它能够很好地泛化到其最初训练数据集之外的范围，因此针对新目标数据集的 FE 不涉及训练，只需要推理。

## 7.2 问题

### 7.2.1 作为固定特征提取器的 CNN

在尝试本章的问题之前，强烈建议阅读以下论文 [1, 3, 2]。在许多深度学习求职面试中，你会被出示一篇从未见过的论文，随后被问到关于它的问题；因此阅读这些参考文献是模拟这一现实任务的极佳练习。

**PRB-157** **CH.PRB- 7.1.**
*判断对错：* 虽然 AlexNet [↓] 使用了 $11 \times 11$ 大小的滤波器，但 VGG [§] 架构提出的主要新颖性在于使用空间范围小得多、尺寸为 $3 \times 3$ 的滤波器。

**PRB-158** **CH.PRB- 7.2.**
*判断对错：* 与 AlexNet 或 VGG 等 CNN 架构不同，ResNet 没有任何隐藏 FC 层。

**PRB-159** **CH.PRB- 7.3.**
*假设 VGG-Net 具有 138,357,544 个浮点参数，在永久性存储中持久化一个训练好的 VGG-Net 实例所需的物理大小是多少兆字节（MB）？*

**PRB-160** **CH.PRB- 7.4.**
*判断对错：* 大多数利用 FE 研究图像表示的尝试，仅专注于复用从接近 CNN 输出的层（更具体地说是全连接层）获得的激活值。

**PRB-161** **CH.PRB- 7.5.**
*判断对错：* 在深度学习背景下，当目标问题没有足够的标记数据来成功训练出泛化能力强的 CNN 时，FE 特别有用。

**PRB-162** **CH.PRB- 7.6.**
*为什么在 ImageNet 数据集 [Σ] 上训练的 CNN 是源问题的良好候选者？*

**PRB-163** **(2)** **CH.PRB- 7.7.**

补全有关 VGG19 CNN 架构的缺失部分：

1. VGG19 CNN 由 [...] 层组成。
2. 它由 [...] 卷积层和 3 个 [...] 层组成。
3. 输入图像的大小是 [...]。
4. 输入通道的数量是 [...]。
5. 每张图像的均值 RGB 值都被 [减去 / 加上]。
6. 每个卷积层都有一个 [小/大] 的 [...] 大小的核。
7. 填充和步长的像素数量是 [...]。
8. 有 5 个 [...] 层，其核大小为 [...]，步长为 [...] 像素。
9. 非线性使用 [整流线性单元 (ReLU [≤])/Sigmoid]。
10. [...] FC 层是线性分类器的一部分。
11. 前两个 FC 层由 [...] 特征组成。
12. 最后一个 FC 层仅具有 [...] 特征。
13. 最后一个 FC 层由一个 [...] 激活层终止。
14. FC 层之间 [使用 / 不使用] Dropout。

