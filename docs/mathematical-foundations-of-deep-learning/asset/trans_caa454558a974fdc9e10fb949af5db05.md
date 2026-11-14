
softmax 函数确保输出值位于范围 [0, 1] 且总和为 1，从而表示 $K$ 个类别上的概率分布。网络的最终输出是一个概率向量 $\hat{\mathbf{y}} \in \mathbb{R}^K$，其中每个元素 $\hat{y}_i$ 对应输入图像属于类别 $i$ 的预测概率。要训练 AlexNet 模型，网络最小化预测概率 $\hat{\mathbf{y}}$ 与真实标签 $\mathbf{y}$ 之间的 **交叉熵损失** 函数，其公式为：
$$L = - \sum_{i=1}^K y_i \log(\hat{y}_i)$$ (423)

其中 $y_i$ 是真实标签（如果图像属于类别 $i$，则为 1，否则为 0），$\hat{y}_i$ 是类别 $i$ 的预测概率。训练的目标是调整网络中的权重 $W$ 和偏置 $b$ 以最小化该损失。网络参数使用 **梯度下降** 进行更新。要计算梯度，使用 **反向传播** 算法。全连接层中损失相对于权重 $W$ 的梯度由以下公式给出：
$$\frac{\partial L}{\partial W} = \frac{\partial L}{\partial z} \cdot \frac{\partial z}{\partial W}$$ (424)

其中 $\frac{\partial L}{\partial z}$ 是损失相对于层输出的梯度，$\frac{\partial z}{\partial W}$ 是输出相对于权重的梯度。然后使用梯度下降更新规则利用这些梯度更新权重：
$$W \leftarrow W - \eta \cdot \frac{\partial L}{\partial W}$$ (425)

其中 $\eta$ 是学习率。该过程对网络中的每一层进行迭代重复。

训练期间通常会应用诸如 **丢弃法** 之类的正则化技术来防止过拟合。丢弃法涉及在每个训练步骤中随机将一部分激活值设置为零，这有助于防止网络过度依赖任何单一特征，并鼓励模型学习更鲁棒的特征。训练完成后，AlexNet 模型可以通过将新图像传递给网络并选择概率最高的类别来对其进行分类。卷积层、ReLU 激活、池化层、全连接层和 softmax 激活的组合使 AlexNet 成为图像分类任务的一种强大且高效的架构。

## 7.4.2 ResNet

ResNet 架构的核心在于 _残差学习_ 的概念，即网络不学习直接变换 $\mathbf{y} = f(\mathbf{x}; \mathbf{W})$，而是学习残差函数 $\mathcal{F}(\mathbf{x}; \mathbf{W})$，也就是输入与输出之间的差异。因此，网络输出 $\mathbf{y}$ 可以表示为：
$$\mathbf{y} = \mathcal{F}(\mathbf{x}; \mathbf{W}) + \mathbf{x}$$ (426)

这种表述与传统神经网络的核心区别在于，传统网络直接从输入 $\mathbf{x}$ 到输出 $\mathbf{y}$ 学习映射。引入恒等快捷连接 $\mathbf{x}$ 提供了一种强大的机制，使网络能够学习残差；如果最优残差变换是恒等函数，网络本质上可以学习 $\mathbf{y} = \mathbf{x}$，从而改善优化。这减少了训练更深层网络的挑战，因为深层通常会导致梯度消失，而梯度可以通过这些快捷连接直接传播，绕过中间层。

让我们形式化这个残差学习。设残差块的输入为 $\mathbf{x}_l$，输出为 $\mathbf{y}_l$。在传统神经网络中，第 $l$ 层从输入到输出的变换将是：

\[\mathbf{y}_l = \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)\] (427)

其中 $\mathcal{F}$ 表示由该层学习的函数，由 $\mathbf{W}_l$ 参数化。相比之下，对于 ResNet，输出是学习到的残差函数 $\mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)$ 与输入 $\mathbf{x}_l$ 本身的和，得到：

\[\mathbf{y}_l = \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l) + \mathbf{x}_l\] (428)

添加恒等快捷连接使网络在需要时可以绕过层，从而促进学习过程并解决梯度消失问题。为了形式化优化问题，我们将残差学习目标定义为关于参数 $\mathbf{W}_l$ 最小化损失函数 $\mathcal{L}$：

\[\mathcal{L} = \sum_{i=1}^N \mathcal{L}_i(\mathbf{y}_i, \mathbf{t}_i)\] (429)

其中 $N$ 是训练样本的数量，$\mathbf{t}_i$ 是目标输出，$\mathcal{L}_i$ 是第 $i$ 个样本的损失。训练过程涉及通过梯度下降调整参数 $\mathbf{W}_l$，而这反过来需要损失函数相对于网络参数的梯度。$\mathcal{L}$ 相对于 $\mathbf{W}_l$ 的梯度可以表示为：

\[\frac{\partial \mathcal{L}}{\partial \mathbf{W}_l} = \sum_{i=1}^N \frac{\partial \mathcal{L}_i}{\partial \mathbf{y}_i} \cdot \frac{\partial \mathbf{y}_i}{\partial \mathbf{W}_l}\] (430)

由于残差块将输入直接加到输出上，输出相对于权重 $\mathbf{W}_l$ 的导数由以下公式给出：

\[\frac{\partial \mathbf{y}_l}{\partial \mathbf{W}_l} = \frac{\partial \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)}{\partial \mathbf{W}_l}\] (431)

现在，让我们探讨一下残差连接的添加如何直接影响反向传播过程。在传统前馈网络中，每一层的反向传播梯度仅取决于前一层的输出。然而，在残差网络中，梯度流得到了增强，因为恒等映射 $\mathbf{x}_l$ 直接传递给后续层。这确保了随着网络加深，梯度不会丢失，这一现象在非常深层的网络中至关重要。第 $l$ 层相对于损失 $\mathcal{L}$ 的梯度为：

\[\frac{\partial \mathcal{L}}{\partial \mathbf{x}_l} = \frac{\partial \mathcal{L}}{\partial \mathbf{y}_l} \cdot \frac{\partial \mathbf{y}_l}{\partial \mathbf{x}_l}\] (432)

由于 $\mathbf{y}_l = \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l) + \mathbf{x}_l$，$\mathbf{y}_l$ 相对于 $\mathbf{x}_l$ 的导数为：

\[\frac{\partial \mathbf{y}_l}{\partial \mathbf{x}_l} = \mathbf{I} + \frac{\partial \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)}{\partial \mathbf{x}_l}\] (433)

其中 $\mathbf{I}$ 是单位矩阵。这确保了梯度 $\frac{\partial \mathcal{L}}{\partial \mathbf{x}_l}$ 可以更容易地通过网络传播，因为它现在被单位矩阵项增强。因此，这一项有助于在反向传播过程中保持梯度的幅度，解决了深层网络中通常出现的梯度消失问题。此外，为了确保残差块输入和输出的维度匹配，特别是当通道数量发生变化时，ResNet 引入了 _投影快捷连接_。当 $\mathbf{x}_l$ 和 $\mathbf{y}_l$ 的维度不一致时使用这些连接，通常通过 $1 \times 1$ 卷积实现。投影快捷连接将残差块的输出修改为：

\[\mathbf{y}_l = \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l) + \mathbf{W}_x \cdot \mathbf{x}_l\] (434)

其中 $\mathbf{W}_x$ 是卷积滤波器，$\mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)$ 是残差变换。引入 $1 \times 1$ 卷积确保输入 $\mathbf{x}_l$ 映射到适当的维度，同时仍然受益于残差学习框架。可以通过堆叠多个残差块来扩展 ResNet 架构。对于具有 $L$ 层的网络，通过整个网络后的输出可以递归地写成：

$\mathbf{y}^{(L)} = \mathbf{x} + \mathcal{F}(\mathbf{y}^{(L-1)}; \mathbf{W}_L)$ (435)

其中 $\mathbf{y}^{(L-1)}$ 是经过 $L - 1$ 层后的输出。该公式的递归特性确保网络输出逐层构建，每一层都相对于传递给它的输入贡献一个变换。从数学上讲，深层残差网络中损失函数相对于参数的梯度可以递归地表示，每一层的梯度都涉及来自恒等快捷连接的贡献。这通过在反向传播过程中保持梯度的稳定和一致流动，促进了非常深层网络的训练。

因此，*残差神经网络 (ResNet)* 通过引入残差学习，显著提高了深度神经网络的可训练性，使网络能够专注于学习输入与输出之间的差异，而不是整个变换。这种方法结合恒等快捷连接和用于维度匹配的投影快捷连接，确保梯度能够有效地通过网络流动，即使在非常深层的架构中也是如此。由此产生的 ResNet 架构已被证明能够实现数百层网络的训练，在从图像分类到语义分割的广泛任务中取得了出色的性能，同时缓解了梯度消失等问题。通过其递归结构和严谨的数学表述，ResNet 已成为现代深度学习中的基础架构。

## 7.4.3 VGG

**视觉几何组 (VGG) 卷积神经网络 (CNN)** 由 Simonyan 和 Zisserman 于 2014 年提出，详细探讨了深度对深度神经网络性能的影响，特别是在图像分类等计算机视觉任务中。VGG 架构基于以下假设：当使用小而一致的卷积核构建时，更深层的网络更能捕捉数据中的层次化模式，特别是在视觉识别领域。与其他 CNN 架构相比，VGG 优先使用堆叠在不断增加深度中的小型 $3 \times 3$ 卷积滤波器（步幅为 1），而不是依赖较大的滤波器（例如 $5 \times 5$ 或 $7 \times 7$），从而在不牺牲表示能力的情况下提供计算优势。这种设计选择本质上鼓励稀疏的局部感受野，确保在扩展到更深层时具有更丰富的学习能力。

设 $I \in \mathbb{R}^{H \times W \times C}$ 表示高度为 $H$、宽度为 $W$、通道数为 $C$ 的输入图像，其中通道对应不同的颜色表示（例如，对于 $C = 3$ 则为 RGB）。对于特定层 $k$ 上应用的卷积操作，输出特征图 $O^{(k)}$ 可以通过将输入 $I$ 与一组对应第 $k$ 层的卷积核 $K^{(k)}$ 进行卷积来计算。每个空间位置 $i, j$ 的卷积可以描述为：

$O_{i,j}^{(k)} = \sum_{u=1}^{k_h} \sum_{v=1}^{k_w} \sum_{c'=1}^{C_{in}} K_{u,v,c',c}^{(k)} I_{i+u,j+v,c'} + b_c^{(k)}$ (436)

其中 $O_{i,j}^{(k)}$ 是第 $k$ 个滤波器的特征图在位置 $(i, j)$ 处的输出值，$K_{u,v,c',c}^{(k)}$ 是第 $k$ 层中从 $c'$ 到 $c$ 的滤波器的 $u, v$ 第空间元素，$b_c^{(k)}$ 表示偏置项
