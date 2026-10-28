

![](img/86043981d34dd325adb0d4b75e402b8d_40_0.png)

**图 2.5** 将 $(0, 10)^2$ 映射到 $\mathbb{R}$ 的非凸函数 $(z_1, z_2) \mapsto \sqrt{|z_1 z_2|} \sin(z_1) \sin(z_2)$ 的示意图。左侧：函数的三维表示，颜色条表示函数值。右侧：使用相同颜色条的等高线图。

最小值。图 2.5 展示了一个输入空间为 $\mathbb{R}^2$、输出空间为 $\mathbb{R}$ 的非凸函数示例。

当损失函数是非凸且光滑时，我们可以保证*平稳性差距*有一个界，该差距由训练方案生成的模型处的梯度（欧几里得）范数来度量。具体而言，存在一个递减的（正）函数 $\phi : \mathbb{R} \rightarrow \mathbb{R}$，使得如果算法在完成 $T$ 次迭代后输出 $\hat{\boldsymbol{\theta}}$，则有

$$\mathbb{E}\left[\|\nabla \mathcal{L}\left(\hat{\boldsymbol{\theta}}\right)\|^2\right] \leq \phi(T), \tag{2.13}$$

其中期望 $\mathbb{E}[\cdot]$ 是在算法的（可能的）随机性上取的。与强凸情形类似，$\phi$ 度量了该方法平均而言能够达到平稳点的速度。在表 2.2 中，我们列出了 GD、SGD 和小批量 GD 的这种映射 $\phi$。这些方法的详细收敛性分析可以通过在 3.2.2 节给出的分析中令 $n = 1$ 得到。

**表 2.2** 式 (2.13) 中 $\phi$ 对 GD、SGD 和小批量 GD（固定批量大小 $b$）的阶数。该结果适用于一类 $\mathcal{L}$ 光滑的学习问题，并假设随机梯度的协方差迹有界

| | GD | SGD | 小批量 GD |
|---|---|---|---|
| $\phi(T)$ | $\mathcal{O}_T\left(\frac{1}{T}\right)$ | $\mathcal{O}_T\left(\sqrt{\frac{1}{T}}\right)$ | $\mathcal{O}_T\left(\sqrt{\frac{1}{bT}}\right)$ |

### 2.2.3 训练误差与梯度复杂度

我们现在已有可用于求解 ERM 问题 (2.8) 的算法，即 GD、SGD 和小批量 GD。每种方法本质上都是迭代的：我们从一个“好模型”的任意估计出发，利用训练样本上逐点损失函数的梯度来不断改进该估计。目标是使整体训练误差最小化，即根据当前损失函数的类别，使输出模型处的次优性差距或平稳性差距最小化。但同时，我们希望最小化梯度复杂度，即在训练过程中计算梯度所花费的计算量。我们主要关注梯度计算，因为在梯度下降方法的实现中，它们代表了最昂贵的计算操作。可以预期，训练误差与梯度复杂度之间存在一种权衡，这种权衡恰好由方法的收敛函数 $\phi$ 刻画，下面我们以小批量 GD 为例进行说明。

回顾算法 3，小批量 GD 的每次迭代计算 $b$ 个梯度。这意味着如果运行 $T$ 次小批量 GD 迭代，我们的梯度复杂度与 $bT$ 成正比。假设损失函数 $\mathcal{L}$ 是强凸的。在这种情况下，回顾存在一个函数 $\phi(T) \in \mathcal{O}_T(1/(bT))$，使得对于最后更新的模型 $\boldsymbol{\theta}_{T+1}$，次优性差距有如下界：

$\mathbb{E}[\mathcal{L}(\boldsymbol{\theta}_{T+1}) - \mathcal{L}^*] \leq \phi(T)$

因此，要获得小于或等于 $\epsilon$ 的训练误差，即 $\phi(T) = \epsilon$，我们需要 $T \in \mathcal{O}_{1/\epsilon}(1/(b\epsilon))$ 次迭代。因此，梯度复杂度为 $\mathcal{O}_{1/\epsilon}(1/\epsilon)$。这种梯度复杂度与训练误差之间的关系也直接适用于 SGD。对于 GD（即算法 1），每次迭代计算 $|S|$ 个梯度（$S$ 是全部训练样本），由于 $\phi(T) \in \mathcal{O}_T(e^{-T})$，梯度复杂度为 $\mathcal{O}_{1/\epsilon}(|S| \log 1/\epsilon)$。看起来，在获得相同训练误差 $\epsilon$ 的情况下，GD 的梯度复杂度小于小批量 GD 或 SGD 的梯度复杂度。然而，在实际场景中通常并非如此，因为训练样本大小（即 $|S|$）可能相当大，并在梯度复杂度中主导对训练误差的依赖关系。我们可以将上述关于训练误差与梯度复杂度之间权衡的分析扩展到非凸情形，只需将输出模型处的次优性差距替换为平稳性差距（即损失函数梯度的欧几里得范数的平方）。

## 2.3 本章注记

在本章中，我们简要概述了监督分类，以说明并形式化机器学习的主要概念。在将问题形式化之后，我们回顾了一些用于解决该任务的标准优化工具。具体来说，我们介绍了一些现代机器学习中最重要的优化方案，即基于梯度的方法。

本章的主要目的是介绍由监督学习引出的一般优化问题，而非对该领域进行详尽无遗的阐述。特别地，我们没有讨论泛化、结构风险最小化、一致性和损失函数校准等主题。关于监督学习的更多细节，我们建议读者参阅机器学习入门教材，如 [3, 9, 11, 15]。这些书对该领域给出了更全面的概述。特别是，它们提供了关于泛化和结构风险最小化概念的充分信息，使读者能够正确理解 ERM（或其正则化版本）为什么（以及在何时）能在未见数据上产生令人满意的模型。关于这一点，感兴趣的读者可参阅 [11, 第 4 章] 和 [3, 第 4 章]。关于损失函数校准与一致性的更专门介绍，感兴趣的读者可参阅 [4, 16, 17]。

关于高级优化算法及梯度下降方法的更多细节，我们建议读者参阅 [5–7, 12, 13]。关于一阶梯度下降方法相对于 $T$ 的收敛速率下界，可在 [2, 13] 中找到。尽管我们在本章给出的随机（和小批量）梯度下降方法的上界一般而言是紧的，但在额外假设损失函数对数据点是光滑的情况下，可以使用基于动量的方差缩减在非凸情形中进一步改进这些上界，如 [8] 所示。我们将在第 5 章的鲁棒机器学习背景下介绍基于动量的优化的更多有趣性质。关于随机（和小批量）梯度下降在非凸情形下收敛性的更多细节（包括更紧的分析），感兴趣的读者可参阅论文 [10]。

## 参考文献

- Abadi M, Agarwal A, Barham P, Brevdo E, Chen Z, Citro C, Corrado GS, Davis A, Dean J, Devin M, Ghemawat S, Goodfellow I, Harp A, Irving G, Isard M, Jia Y, Jozefowicz R, Kaiser L, Kudlur M, Levenberg J, Mané D, Monga R, Moore S, Murray D, Olah C, Schuster M, Shlens J, Steiner B, Sutskever I, Talwar K, Tucker P, Vanhoucke V, Vasudevan V, Viégas F, Vinyals O, Warden P, Wattenberg M, Wicke M, Yu Y, Zheng X (2015) TensorFlow：异构系统上的大规模机器学习。软件可从 Tensorflow.org 获取
- Arjevani Y, Carmon Y, Duchi JC, Foster DJ, Srebro N, Woodworth B (2023) 非凸随机优化的下界. Math Program 199(1–2):165–214
- Bach F (2023) 基于第一性原理的学习理论. MIT Press (Draft), Cambridge
- Bartlett PL, Jordan MI, McAuliffe JD (2006) 凸性、分类与风险界. J Amer Stat Assoc 101(473):138–156
- Bottou L (1999) 在线学习与随机逼近. In: 神经网络中的在线学习. Saad D（编）. 牛顿研究所出版物. 剑桥大学出版社，剑桥，第 9–42 页
- Bottou L, Curtis FE, Nocedal J (2018) 大规模机器学习的优化方法. SIAM Rev 60(2):223–311
- Boyd S, Vandenberghe L (2004) 凸优化. 剑桥大学出版社，剑桥
- Cutkosky A, Orabona F (2019) 非凸 SGD 中基于动量的方差缩减. In: 神经信息处理系统进展，第 32 卷. Curran Associates, Red Hook, 第 15236–15245 页
- Hastie T, Tibshirani R, Friedman J (2001) 统计学习基础. Springer 统计学系列. Springer 纽约，纽约
- Khaled A, Richtárik P (2023) 非凸世界中 SGD 的更好理论. Trans Mach Learn Res. Survey Certification. ISSN: 2835-8856. https://openreview.net/forum?id=AU4qHN2VkS
- Mohri M, Rostamizadeh A, Talwalkar A (2018) 机器学习基础. MIT 出版社，剑桥
- Moulines E, Bach F (2011) 机器学习中随机逼近算法的非渐近分析. In: 神经信息处理系统进展. Shawe-Taylor J, Zemel R, Bartlett P, Pereira F, Weinberger K，第 24 卷. Curran Associates, Red Hook
- Nesterov Y (2018) 凸优化讲义，第 137 卷. Springer，柏林
- Paszke A, Gross S, Massa F, Lerer A, Bradbury J, Chanan G, Killeen T, Lin Z, Gimelshein N, Antiga L, Desmaison A, Kopf A, Yang E, DeVito Z, Raison M, Tejani A, Chilamkurthy S, Steiner B, Fang L, Bai J, Chintala S (2019) PyTorch：一种命令式风格的高性能深度学习库. In: 神经信息处理系统进展，第 32 卷. Curran Associates, Red Hook, 第 8024–8035 页
- Shalev-Shwartz S, Ben-David S (2014) 理解机器学习：从理论到算法. 剑桥大学出版社，剑桥
- Steinwart I (2007) 如何比较不同损失函数及其风险. Construct Approx 26(2):225–287
- Zhang T (2004) 基于凸风险最小化的分类方法的统计行为与一致性. Ann Statist 32(1):56–85

