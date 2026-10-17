

# 1.3.2 学习方式

## 1.3.2.1 无监督学习

在无监督学习（[Figure 1.6](#bodymatter-001.xhtml#b_9783110670905-001_fig_006)）中，不需要外部训练者即可完成学习过程。输入被提供给网络，但没有所需的输出。网络必须自行决定使用哪些特征来组装输入数据。竞争学习规则是执行无监督学习的一种方式。如果一个神经网络有两层——输入层和竞争层，输入层神经元收集馈送数据，而竞争层由相互竞争的神经元组成，只有竞争的胜利者存活，其他神经元根据“胜者全拿”方法关闭。另一种无监督学习类型是 Hebbian，即相关权重调整。

![Figure 1.6: Block diagram of unsupervised learning.](graphic/converted/b_9783110670905-001_fig_006.png)

Figure 1.6: Block diagram of unsupervised learning.

## 1.3.2.2 监督学习

如果神经网络的所需输出已知并馈送到网络中，则该网络的学习方法称为监督学习。网络随后处理输入并将其生成的输出与预期输出进行比较。然后计算差分误差，使系统调节权重以控制网络。随着权重不断精细调整，此方法会重复发生。

监督学习技术（[Figure 1.7](#bodymatter-001.xhtml#b_9783110670905-001_fig_007））分为两种类型——随机（基于概率的权重调整）和误差校正。误差校正学习规则分为两种类型，如下所示。

*   `Delta rule` – 由 Widrow 和 Hoff 在 1960 年设计，也称为 Widrow 和 Hoff 学习规则或最小均方规则。`Delta rule` 使用目标激活（即目标输出值）与获得激活之间的差异来进行学习。权重值被精细调整以最小化目标和实际输出激活（即误差）之间的差异。

*   `Gradient descent rule` – `Gradient descent` 的主要特征是通过调节权重逐渐但持续地减少输出误差。如果权重的变化（`δw`）增加（减少）误差（`δE`），则相应的权重减少（增加），并可表示如下：

(1.1)$\Delta w_{ij} = - \eta \frac{\delta E_i}{\delta w_{ij}}$

距离 `η` 是神经网络中的标准参数，称为学习率。

![Figure 1.7: Block diagram of supervised learning.](graphic/converted/b_9783110670905-001_fig_007.png)

Figure 1.7: Block diagram of supervised learning.

## 1.3.2.3 强化学习

在强化学习中，网络的学习是通过与情况或环境的持续协作实现的。[Figure 1.8](#bodymatter-001.xhtml#b_9783110670905-001_fig_008) 显示了典型强化学习网络的框图，该网络围绕一个训练者构建，训练者将从环境中收集的强化信号转换为称为启发式强化信号的高级信号。

![Figure 1.8: Block diagram of reinforcement learning.](graphic/converted/b_9783110670905-001_fig_008.png)

Figure 1.8: Block diagram of reinforcement learning.

# 1.4 深度学习

深度学习（DL）是机器学习（ML）的一个类别，其中网络或模型直接从数据集学习 \[[8](#bodymatter-001.xhtml#b_9783110670905-001_ref_008)\]。“深度”一词表示网络中的层数——更深的网络包含许多层。传统神经网络仅包含两层或三层，而深度网络可以包含数百层，如 [Figure 1.9](#bodymatter-001.xhtml#b_9783110670905-001_fig_009) 所示。除了层数之外，没有具体定义可以将网络归类为“深度” \[[9](#bodymatter-001.xhtml#b_9783110670905-001_ref_009)\]。学习技术与 ML 和 ANN 相似，如前所述。DL 特别适合识别现代智能应用 \[[10](#bodymatter-001.xhtml#b_9783110670905-001_ref_010)\]，例如人脸识别、文本翻译、语音识别以及包括车道分类和交通标志识别在内的高级驾驶辅助系统。

![Figure 1.9: Block diagram of deep learning network.](graphic/converted/b_9783110670905-001_fig_009.png)

Figure 1.9: Block diagram of deep learning network.

## 1.4.1 什么使 DL 成为最先进的技术？

*   先进的工具和技术大大提高了 DL 算法的准确性。通过在相同问题和相同数据集上与 ML 进行比较，已证明 DL 大幅减少了误差百分比。

*   DL 可以处理大规模数据集，从而有目的地改进网络的训练。在当今世界，数据并不匮乏。如 [Figure 1.10](#bodymatter-001.xhtml#b_9783110670905-001_fig_010) 所示，在大量数据存在的情况下，DL 远优于 ML。

*   高性能 GPU 加快了 DL 网络的训练，处理大量数据，将训练时间从几周缩短到几小时。GPU 可在任何 DL 云平台上使用。

许多由专家开发和认可的标准模型可在云平台上使用，以便在任何 DL 网络中为任何目的重复使用。

![Figure 1.10: Performance comparison between ML and DL.](graphic/converted/b_9783110670905-001_fig_010.png)

Figure 1.10: Performance comparison between ML and DL.

## 1.4.2 激活函数

激活函数或传递函数 \[[11](#bodymatter-001.xhtml#b_9783110670905-001_ref_011), [12](#bodymatter-001.xhtml#b_9783110670905-001_ref_012)\] 将神经网络节点的输入信号转换为输出信号，该输出信号被视为网络下一层的输入。它将非线性引入网络，使网络更强大，并增加从数据中学习复杂和复杂事物的能力。因此，为任何网络选择合适的激活函数非常重要，因为它可以显著改变网络的行为。下面描述了流行的激活函数。在所有方程中，`f'(x)` 被视为 `f(x)` 的导数，其中 `x` 是输入信号。

### 1.4.2.1 Sigmoid 激活函数

Sigmoid 函数定义为

(1.2)$\begin{matrix} & {f(x) = \frac{1}{1 + e^{- x}}} \\\\ & {f^{\prime}(x) = f(x)(1 - f(x))} \\\\ \end{matrix}$

Sigmoid 函数曲线看起来像 S 形，如 [Figure 1.11](#bodymatter-001.xhtml#b_9783110670905-001_fig_011) 所示。该函数介于 0 和 1 之间。我们可以找到 Sigmoid 曲线在任意两点处的斜率；因此，它是可微的。

![Figure 1.11: Sigmoid activation function.](graphic/converted/b_9783110670905-001_fig_011.png)

Figure 1.11: Sigmoid activation function.

### 1.4.2.2 双曲正切激活函数

双曲正切函数定义为

(1.3)$\begin{matrix} & {f(x) = \tanh(x) = \frac{2}{1 + e^{- 2x}} - 1} \\\\ & {f^{\prime}(x) = 1 - f{(x)^{2}}} \\\\ \end{matrix}$

如 [Figure 1.12](#bodymatter-001.xhtml#b_9783110670905-001_fig_012) 所示，“tanh”函数也看起来像 S 形。该函数介于 -1 和 1 之间。它也是可微的。

![Figure 1.12: “tanh” activation function.](graphic/converted/b_9783110670905-001_fig_012.png)

Figure 1.12: “tanh” activation function.

### 1.4.2.3 ReLU 激活函数

目前，ReLU 是使用最广泛的激活函数。如 [Figure 1.13](#bodymatter-001.xhtml#b_9783110670905-001_fig_013) 所示，定义为

(1.4)$f(x) = 0, \text{for } x < 0; \quad x, \text{otherwise}$

(1.4)$f'(x) = 0, \text{for } x < 0; \quad 1, \text{otherwise}$

该函数介于 0 和无穷大之间。它也是可微的。

![Figure 1.13: Rectified linear unit activation function.](graphic/converted/b_9783110670905-001_fig_013.png)

