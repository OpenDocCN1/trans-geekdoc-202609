
## 15.5.3 位置编码

“原版”自注意力的性能可能较低，因为注意力是排列不变的，因此忽略了输入词的顺序。为克服这一点，我们可以将词嵌入与 **位置嵌入** 拼接，使模型知道词出现的顺序。

更详细地说，假设注意力的输入是一个矩阵 $\mathbf{X} \in \mathbb{R}^{T \times D}$，其中 $T$ 是序列的长度。为了确保注意力模型知道每个词在其输入中的位置，我们可以用一个 **位置编码** 向量对其进行增强。具体而言，我们将整数位置索引 $t \in \{1, \ldots, T\}$ 映射到矩阵 $\mathbf{P} \in \mathbb{R}^{T \times D}$。我们可以使用 $t$ 的二进制编码，这将需要 $D = \log_2 T$ 位。然而，这没有利用位置 $t$ 的向量表示 $\mathbf{p}_t$ 是稠密浮点表示这一事实。在 [Vas+17] 中，他们提出了以下替代表示：

$$\mathbf{p}_t = [\sin(\omega_1 t),\cos(\omega_1 t),\sin(\omega_2 t),\cos(\omega_2 t),\ldots,\sin(\omega_{d/2}t),\cos(\omega_{d/2}t)] \tag{15.32}$$

其中 $\omega_k = 1/C^{2k/d}$ 是第 $k$ 个条目的频率，$d$ 是基函数数，$C = 10,000$ 是某个常数。例如，如果 $d = 4$，我们有

$$\mathbf{p}_t = \left[\sin\left(\frac{t}{C^{0/4}}\right),\cos\left(\frac{t}{C^{0/4}}\right),\sin\left(\frac{t}{C^{2/4}}\right),\cos\left(\frac{t}{C^{2/4}}\right)\right] \tag{15.33}$$

这种相当晦涩的编码方案在图 15.20 中有所说明。我们看到每个位置都与一个实值向量相关联，该向量由该位置处一组不同频率的正弦和余弦函数的值导出。这种表示的优点是两方面的。首先，它可以为任意长度的输入计算，最高可达 $T \leq C$，而不像从整数到向量的学习映射。其次，相邻位置具有相似的编码，这提供了一种有用的归纳偏置。具体而言，我们有 $\mathbf{p}_{t+\phi} = f(\mathbf{p}_t)$，其中 $f$ 是一个线性变换。为此，注意

$$\begin{pmatrix}\sin(\omega_k(t+\phi))\\\cos(\omega_k(t+\phi))\end{pmatrix} = \begin{pmatrix}\sin(\omega_k t)\cos(\omega_k\phi)+\cos(\omega_k t)\sin(\omega_k\phi)\\\cos(\omega_k t)\cos(\omega_k\phi)-\sin(\omega_k t)\sin(\omega_k\phi)\end{pmatrix} \tag{15.34}$$

$$= \begin{pmatrix}\cos(\omega_k\phi)&\sin(\omega_k\phi)\\-\sin(\omega_k\phi)&\cos(\omega_k\phi)\end{pmatrix}\begin{pmatrix}\sin(\omega_k t)\\\cos(\omega_k t)\end{pmatrix} \tag{15.35}$$

一旦我们计算出位置嵌入 $\mathbf{P}$，我们需要将其与原始词嵌入 $\mathbf{X}$ 结合。如果我们使用 $d = D$ 个基函数，我们可以通过加法将 $\mathbf{P}$ 与 $\mathbf{X}$ 结合，即用 $\mathbf{X} + \mathbf{P}$ 替换 $\mathbf{X}$。

## 15.5.4 综合起来

Transformer 是一种序列到序列模型，它使用自注意力作为编码器和解码器，而不是 RNN。编码器使用一系列残差块，每个块都使用多头注意力 Sec. 15.5.2 和层归一化 Sec. 14.2.6。每个块 $\mathbf{z} = f(\mathbf{x})$ 可以定义如下：

$$\mathbf{z} = \operatorname{LayerNorm}(\varphi(\mathbf{W}\mathbf{x}' + \mathbf{x}')) \tag{15.36}$$

$$\mathbf{x}' = \operatorname{LayerNorm}(\operatorname{MultiHeadAttention}(\mathbf{x}) + \mathbf{x}) \tag{15.37}$$

这应用于嵌入后并与位置编码拼接的原始输入序列。此过程在图 15.21 的左侧有所说明。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_518_0.png)

表 15.1 Transformer 与其他神经序列生成模型的比较。T 是序列长度，D 是输入特征的维度，K 是卷积的核大小，R 是局部自注意力的邻域大小。对于短序列，我们通常有 T ≪ D。基于 [Vas+17] 的表 1。

| 层类型 | 复杂度 | 顺序操作 | 最大路径长度 |
|------------|------------|-----------------|------------------|
| 自注意力 | O(T^2D) | O(1) | O(1) |
| 自注意力（受限） | O(RTD) | O(1) | O(T/R) |
| 循环 | O(TD^2) | O(T) | O(T) |
| 卷积 | O(KTD^2) | O(1) | O(log_K T) |

解码器具有 somewhat 更复杂的结构。它通过另一个多头注意力块访问编码器。但它也访问之前生成的输出：这些输出被移位，然后与位置嵌入结合，然后馈入掩蔽 因果 多头注意力模型。最后在每个位置并行计算标记的输出分布。参见图 15.21 的右侧以了解说明，并参见 [Rus18] 以获取该模型的详细教程。

## 15.5.5 比较 Transformer、CNN 和 RNN

Transformer 模型相对于 RNN Sec. 15.2 和卷积马尔可夫模型 Sec. 15.3 有两个主要优势。第一个优势是计算方面的：Transformer 中的编码可以并行计算，而 RNN 需要顺序编码。此外，在训练期间，解码也可以并行进行，因为教师强制将所有输出钳定到其正确值，而无需采样。

第二个优势是统计方面的：在 Transformer 中，远距离位置可以直接影响彼此的输出，因为两个标记之间的最大路径长度为 1。相比之下，RNN 需要 T 步才能将长度为 T 的序列中的信息从第一个位置传播到最后一个位置。而在核大小为 K 的卷积模型中，我们需要 T/K 层的堆栈或 log_K(T) 个扩张层以确保所有配对可以通信。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_519_0.png)

主要缺点是 Transformer 在训练和推理时都需要 O(T₁T₂D) 时间，其中 T₁ 是输入长度，T₂ 是输出长度，因为每个输出标记都可以关注所有输入标记。我们在 Sec. 15.6 中讨论各种更快的替代方案

## 15.6 高效 Transformer

常规 Transformer 需要 O(N²) 的时间和空间复杂度，这使得它们难以应用于长序列。在过去几年中，研究人员提出了几种更高效的 Transformer 变体以绕过这一困难。本节简要回顾了其中一些方法 参见图 15.22 了解总结。对于更多细节，参见例如 [Tay+20a; Tay+20b]。

## 15.6.1 固定的不可学习局部注意力模式

注意力机制最简单的修改是将注意力约束为固定的不可学习局部窗口，换句话说限制每个标记仅关注预先选定的其他标记集合。例如，如果每个序列被切分为 K 个块，每个块长度为 N/K，并且仅在块内进行注意力，则时间和空间复杂度从 O(N²) 降低到 O(N²/K)。

> 3. 本节与 Krzysztof Choromanski 合著。

> 未经 Kevin P. Murphy 和 MIT Press 许可请勿分发。

K ≫ 1，这构成了总体计算的实质性改进。这种方法特别应用于 [Qiu+19a; Par+18]。注意力模式不一定采用块的形式。其他方法涉及步幅/扩张窗口 或混合模式，其中多个固定注意力模式组合在一起 [Chi+19b; BPC20]。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_520_0.png)

图 15.22：展示不同高效 Transformer 架构分类的 Venn 图。从 [Tay+20a]。经 Yi Tay 友好许可使用。

## 15.6.2 可学习的稀疏注意力模式

上述方法的自然扩展是允许上述紧凑模式可学习。注意力仍然限制在某个划分的某个划分中所有标记集合的标记对之间，但现在这些划分是训练的。在此类方法中我们可以区分两个主要方法：基于哈希和聚类。在哈希场景中，所有标记都被哈希，因此不同的划分对应于不同的哈希桶。例如 Reformer 架构 [KKL20] 就是这种情况，其中应用了局部敏感哈希 LSH。这导致注意力模块的时间复杂度为 O(NM² log(M))，其中 M 表示标记嵌入的维度。

哈希方法要求查询集合与键集合相同。此外，
