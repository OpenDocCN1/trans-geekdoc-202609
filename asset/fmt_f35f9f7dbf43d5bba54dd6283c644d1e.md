
$Z_{l} \sim \mathcal{U}[ - \sqrt{3}c_{l},\sqrt{3}c_{l}],\ l = 1,\ldots,L - 1,$

(11.19b)

其中 $\mathcal{N}(0, c^{2})$ 表示均值为零、方差为 $c^{2}$ 的高斯分布，$\mathcal{U}[ - \sqrt{3}c_{l},\sqrt{3}c_{l}]$ 表示在 $[ - \sqrt{3}c_{l},\sqrt{3}c_{l}]$ 上的均匀分布。

### 11.4.2 强制平滑性

我们现在将扰动局部嵌入技术与第 11.3 节中的收敛理论联系起来。

第 11.3 节中的收敛结果在假设 11.2 下成立，该假设要求整体损失函数的平滑性。受随机平滑技术 [12, [26]](#Chp011_199-217_B978044319037700020X.xhtml#br0130) 启发，我们通过对随机神经元求期望来平滑目标函数。直观上，这遵循这样一个事实：通过与适当的分布卷积，可以增加函数的平滑性。通过添加随机神经元 $Z[l]$，$\sigma[l]$ 的地形将在关于 $Z[l]$ 的期望下被平滑。并通过数学归纳法，我们可以证明局部嵌入向量 $h[m]$ 的平滑性。那么只要损失函数 $\ell$ 关于局部嵌入向量 $h[m]$ 是平滑的，全局目标 $F$ 通过对所有随机神经元求期望就是平滑的。

我们在以下定理中正式确立这一结果。

**定理 11.5**

*对于每个嵌入函数 $h[m]$，若激活函数满足 $\sigma[l] = \sigma, \forall l$，且随机神经元的方差遵循 (11.19)，并假设 $\|w[l]\|$ 有界，则令 $\mathbf{Z} = [Z[1]^{\top}, \ldots, Z[L]^{\top}]^{\top}$，扰动损失满足假设 11.2，由下式给出*

$$F_{c} = \mathbb{E}_{\mathbf{Z}}[F(\theta[0], \boldsymbol{\theta}; \mathbf{Z})].$$

(11.20)

*从 $L_{b_{L}}^{(h)} = L_{\sigma}^{0}d/c$ 开始，局部模型 $\theta[m]$ 的平滑常数记为 $L_{\theta[m]}^{(F_{c})}$ 满足以下递推关系 ($l = 1, \ldots, L - 1$)：*

$$

\left. L_{b_{l}}^{h} = L_{b_{l + 1}}^{h} \right\|\left. w_{l + 1} \right\|\left( \left. L_{\sigma}^{0} \right)^{2} + L_{\sigma}^{0} \right\|\left. w_{L} \right\|\left. \cdots L_{\sigma}^{0} \right\|\left. w_{l + 1} \right\| L_{\overline{\sigma}}(c_{l}), L_{w_{l}}^{h} = \mathbb{E}[\|\left. u_{l - 1} \right\|] L_{b_{l}}^{h}, L_{\theta_{m}}^{F_{c}} = L_{h_{m}}^{\ell}\left( L_{h_{m}}^{0} \right)^{2} + L_{\ell}^{0}\sum\limits_{l = 1}^{L}\left( L_{w_{l}}^{h} + L_{b_{l}}^{h} \right) + L_{\theta_{m}}^{r},

$$

(11.21)

其中，$L_{\theta_{m}}^{(r)}$ 是正则化项关于 $\theta_{m}$ 的光滑常数；$L_{b_{l}}^{(h)}$ 和 $L_{w_{l}}^{(h)}$ 分别是扰动局部嵌入 $h$ 关于偏置 $b_{l}$ 和权重 $w_{l}$ 的光滑常数；而 $L_{\overline{\sigma}}(c_{l}) = 2\sqrt{d}L_{\sigma}^{0}/c_{l}$ 是第 $l$ 层神经元在均匀扰动下的光滑常数。

定理 11.5 意味着扰动损失关于局部模型 $\theta_{m}$ 是光滑的，且较大的扰动（较大的 $c_{l}$ 或 $c$）会导致较小的光滑常数。

## 11.5 数值测试

为了评估我们提出的 VAFL 方法的性能，我们在多个数据集上对联邦逻辑回归和神经网络模型进行了数值测试。我们将算法 1 中 VAFL 的完全异步版本（**async**）和算法 2 中的 $t$-同步版本（**t-sync**）与同步分块 SGD（**sync**）进行基准测试，后者要求在每次迭代中客户端之间进行同步和样本索引协调。为了模拟客户端异步性，我们使用多线程作为本地客户端，并向每个客户端添加随机延迟。

### 11.5.1 联邦逻辑回归的 VAFL

**数据分配。** 我们选择的数据集包括 CIFAR-10、帕金森病、MNIST 和 Fashion MNIST。批量大小选取为整个训练数据集的约 0.01 份额。数据在 CIFAR-10 上均匀分布在 $M = 8$ 个客户端上，帕金森病数据集上为 $M = 3$，MNIST 和 Fashion MNIST 上均为 $M = 7$。

步长对于帕金森病数据集为 $\eta = 1 \times 10^{-2}$，对于 CIFAR-10 为 $\eta = 2 \times 10^{-4}$，对于 MNIST 和 Fashion MNIST 均为 $\eta = 1 \times 10^{-4}$。

**参数。** 随机延迟遵循具有客户端特定参数的泊松分布，以反映异质性。每个工作节点 $m$ 上的延迟遵循参数为 $2m$ 并按 $1/2M$ 缩放的泊松分布，其中 $M$ 是工作节点数量，$m$ 是工作节点索引。最大工作节点延迟的期望为一秒。

添加到每个本地客户端输出的噪声对于 CIFAR-10、MNIST 和 Fashion MNIST 遵循高斯分布 $\mathcal{N}(0, 0.01)$，对于帕金森病数据集遵循 $\mathcal{N}(0, 1)$。对于每个任务，我们运行算法足够多的轮次并记录训练损失。测试准确率和时钟时间在每轮结束时记录。

我们首先在 MNIST、Fashion-MNIST、CIFAR10 和帕金森病 [[30]](#Chp011_199-217_B978044319037700020X.xhtml#br0150) 数据集上进行逻辑回归。$l_{2}$-正则化系数设为 0.001。我们为 MNIST 和 MNIST 选择 $M = 7$，为 CIFAR10 选择 $M = 8$，为 PD 数据集选择 $M = 3$。训练损失和测试准确率随墙钟时间变化的曲线见图 11.2 和 11.3。虚线水平线代表在中心化（非联邦）模型上训练的结果，虚线曲线代表方差 $c = 0.1$ 时所考虑算法的私有变体。在所有情况下，VAFL 算法学习到的联邦模型精度与需要收集所有原始数据的中心化模型相当。且在大多数情况下，async 和 $t$-sync VAFL 算法实现了 2 倍加速。

![Figure 11.2 Training loss and testing accuracy versus clock time (s) in MNIST (left two) and Fashion-MNIST (right two) datasets.](img/gr004_u3.jpg)

图 11.2 MNIST（左两图）和 Fashion-MNIST（右两图）数据集上的训练损失和测试准确率随时钟时间（秒）的变化。

![Figure 11.3 Training loss and testing accuracy versus clock time (s) in CIFAR10 (left two) and Parkinson disease (right two) datasets.](img/gr005_u3.jpg)

图 11.3 CIFAR10（左两图）和帕金森病（右两图）数据集上的训练损失和测试准确率随时钟时间（秒）的变化。

### 11.5.2 联邦深度学习的 VAFL

#### 11.5.2.1 在 ModelNet40 数据集上训练

我们训练一个基于卷积神经网络的模型，该模型由两部分组成：局部嵌入模型和服务器模型。每个局部模型是一个 7 层卷积神经网络。服务器部分是一个中心化的 3 层全连接神经网络。我们选择的数据是 ModelNet40，并将数据集中物体从 12 个角度拍摄的图像垂直分割，分配给每个本地客户端。每个客户端通过其局部卷积网络处理分配的数据，并生成一个维度为 512 的向量作为局部输出。

##### 参数

随机延迟遵循指数分布，并带有客户端特定的参数以反映异质性。对于每个工作节点 `m`，延迟遵循参数为 `m` 的指数分布。我们使用 `ReLU` 作为局部嵌入激活函数。我们在每个局部嵌入卷积层的输出上添加随机噪声。噪声遵循以下分布：`𝒰(−0.1, 0.1)`（前两层），`𝒰(−0.01, 0.01)`（除最后一层外的其他卷积层），以及 `𝒩(0, 1)`（最后一层卷积层）。服务器随后将这 12 个向量组合起来，并将它们传入三层全连接神经网络，分类为 40 个类别。每层的节点数分别为 256、100 和 40。局部更新步长 `η[m]` 为 `10^(−3)`，服务器步长 `η₀ = ηₘ/M`，其中 `M` 为工作节点数量。

我们首先使用 12 视图数据 [[40]](#Chp011_199-217_B978044319037700020X.xhtml#br0200) 训练一个基于 `MVCNN` 修改的神经网络。我们使用 `M = 4` 个客户端，每个客户端拥有每个物体的 3 个视图，并使用 7 层 `CNN` 作为局部嵌入函数，服务器使用全连接网络聚合局部嵌入向量。结果绘制在图 11.4 和 11.5 中。在这种多视图学习情况下，集中式模型与同步模型一致，因此省略。同样，异步和 `t`-sync 相较于同步具有显著的加速效果，而私有异步（`c = 1` 时）在准确性上没有太大牺牲。

![Figure 11.4 Training loss of VAFL with nonlinear local embedding on ModelNet40 dataset.](img/gr006_u2.jpg)

**图 11.4** 具有非线性局部嵌入的 VAFL 在 *ModelNet40* 数据集上的训练损失。

![Figure 11.5 Testing accuracy of VAFL with local embedding on ModelNet40 dataset.](img/gr007_u1.jpg)

**图 11.5** 具有局部嵌入的 VAFL 在 *ModelNet40* 数据集上的测试准确率。

#### 11.5.2.2 在 MIMIC-III 数据集上训练

我们进一步在 `MIMIC-III` 上测试我们的 `VAFL` 算法——这是一个包含去标识化健康数据的开放数据集 [[17]](#Chp011_199-217_B978044319037700020X.xhtml#br0085)。数据被分配给 4 个具有不同特征维度的工作节点。局部嵌入部分是一个两层 `LSTM` 模型，服务器部分是一个全连接层。第一层是双向 `LSTM`，单元数为 16。第二层是普通 `LSTM` 层，单元数也是 16。随机延迟遵循具有客户端特定参数的指数分布以反映异质性。服从高斯分布 `𝒩(0, 10^(−4))` 的随机噪声也被添加到每个局部嵌入层的输出中。我们按照 [[16]](#Chp011_199-217_B978044319037700020X.xhtml#br0080) 的方法，在 `M = 4` 个客户端中进行院内死亡率预测。每个客户端使用 `LSTM` 作为嵌入函数。在图 11.6 和 11.7 中，我们仍然可以观察到异步和 `t`-sync `VAFL` 学习到的联邦模型准确率与集中式模型相当，且所需时间相较于同步联邦学习算法更少。我们进行了一项消融研究，以展示收敛速率如何受不同客户端数量的影响。由于在垂直联邦学习场景中，客户端通常是金融机构和医疗公司，其数量通常不大，因此在图 11.8 和 11.9 中，我们报告了客户端数量 `M = 6, 8, 10` 时 `VAFL` 的训练损失和测试 AUC。从这两个图中，我们可以观察到，当客户端数量增加时，达到给定训练损失和测试 AUC 所需的实际运行时间并不会减少。这是因为在垂直联邦学习中增加客户端不会增加批量大小或降低有效方差，反而会引入额外的异步性，甚至可能阻碍学习过程。这与水平联邦学习设置中的*线性加速*不同。

![Figure 11.6 Training loss of VAFL with local LSTM embedding on MIMIC-III dataset.](img/gr008_u1.jpg)

**图 11.6** 具有局部 LSTM 嵌入的 VAFL 在 *MIMIC-III* 数据集上的训练损失。

![Figure 11.7 AUC curve of VAFL with local LSTM embedding on MIMIC-III dataset.](img/gr009.jpg)

**图 11.7** 具有局部 LSTM 嵌入的 VAFL 在 *MIMIC-III* 数据集上的 AUC 曲线。

![Figure 11.8 Training loss of VAFL with local LSTM embedding on MIMIC-III critical care dataset under different number of clients.](img/gr010.jpg)

**图 11.8** 具有局部 LSTM 嵌入的 VAFL 在不同客户端数量下的 *MIMIC-III* 重症监护数据集上的训练损失。

![Figure 11.9 AUC curve of VAFL with local LSTM embedding on MIMIC-III clinical care dataset under different number of clients.](img/gr011.jpg)

**图 11.9** 具有局部 LSTM 嵌入的 VAFL 在不同客户端数量下的 *MIMIC-III* 临床护理数据集上的 AUC 曲线。

## 参考文献

*   [[1]](#Chp011_199-217_B978044319037700020X.xhtml#cs0040_1) Martin Abadi, Andy Chu, Ian Goodfellow, H. Brendan McMahan, Ilya Mironov, Kunal Talwar, Li Zhang, Deep learning with differential privacy, *Proc. ACM SIGSAC Conf. Computer and Communications Security*. *Vienna, Austria*. October 2016:308–318.

*   [[2]](#Chp011_199-217_B978044319037700020X.xhtml#cs0020_1) Alham Fikri Aji, Kenneth Heafield, Sparse communication for distributed gradient descent, *Proc. Conf. Empirical Methods Natural Language Process.*. *Copenhagen, Denmark*. Sep. 2017:440–445.

*   [[3]](#Chp011_199-217_B978044319037700020X.xhtml#cs0020_2) Dan Alistarh, Demjan Grubic, Jerry Li, Ryota Tomioka, Milan Vojnovic, QSGD: communication-efficient SGD via gradient quantization and encoding, *Proc. Advances in Neural Info. Process. Syst.*. *Long Beach, CA*. Dec. 2017:1709–1720.

*   [[4]](#Chp011_199-217_B978044319037700020X.xhtml#cs0090_1) Arjun Nitin Bhagoji, Supriyo Chakraborty, Prateek Mittal, Seraphin Calo, Analyzing federated learning through an adversarial lens, *Proc. Intl. Conf. Machine Learn.*. *Long Beach, CA*. Jun. 2019:634–643.

*   [[5]](#Chp011_199-217_B978044319037700020X.xhtml#cs0045_1) Keith Bonawitz, Vladimir Ivanov, Ben Kreuter, Antonio Marcedone, H. Brendan McMahan, Sarvar Patel, Daniel Ramage, Aaron Segal, Karn Seth, Practical secure aggregation for privacy-preserving machine learning, *Proc. ACM Conf. on Comp. and Comm. Security*. *Dallas, TX*. Oct. 2017:1175–1191.

## 参考文献

*   [[6]](#Chp011_199-217_B978044319037700020X.xhtml#cf0140) Léon Bottou, Frank E. Curtis, Jorge Nocedal, 面向大规模机器学习的优化方法, [arXiv:1606.04838](http://www.arxiv.org/abs/1606.04838); 2016 年 6 月。
