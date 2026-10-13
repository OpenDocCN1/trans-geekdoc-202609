
$$
\left. P(\mathbf{y}_{1},\mathbf{y}_{2},\ldots,\mathbf{y}_{N^{\prime} + 1} \middle| \mathbf{y}_{0},\mathcal{X}_{0:N + 1}) = \prod\limits_{n = 0}^{N^{\prime}}\prod\limits_{i = 1}^{l}{\widehat{y}}_{ni}^{y_{n + 1,i}}. \right.
$$

![Equation](images/B9780443292385000251/si323.png)

回顾等式右侧第二个乘积中的各项，除了一项之外，其余所有项均等于 1（$y[n + 1, i] = 0, i \neq \text{id}$），该例外项出现在 $i$ 等于目标 id 时，其值等于 $\hat{y}[n i]$（$y[n + 1, i] = 1, i = \text{id}$）。我们对上述等式取负对数，对语料库 $\mathcal{D}$ 中所有 $\mathcal{Y}, \mathcal{X}$ 训练对求和，此时目标变为*最小化*代价函数，

![Equation](images/B9780443292385000251/fx011.jpg) (19.45)

其中 $\boldsymbol{\theta}$ 是包含 Transformer 网络中所有相关参数的向量。为了关于 $\boldsymbol{\theta}$ 最小化 $J(\boldsymbol{\theta})$，采用了反向传播算法的原理。此时，请将公式 [(19.45)](#Chp019_997-1102_B9780443292385000251.xhtml#deq101) 与公式 [(18.41)](#Chp018_885-995_B978044329238500024X.xhtml) 中定义的交叉熵代价进行比较。

### 19.3.11 解码器：掩码自注意力

单个解码器块的结构如 [图 19.13](#Chp019_997-1102_B9780443292385000251.xhtml#f0070) 所示。我们将重点关注下部（输入）块。在训练期间（推理情况见第 [19.3.13](#Chp019_997-1102_B9780443292385000251.xhtml#s0140) 节），输入包含目标输出序列嵌入。其余各块具有完全相同的结构，唯一的区别在于各自的输入是下方块的输出向量。在本小节中，重点在于块中的第一层，即所谓的*掩码自注意力*在此执行。

![Figure 19.13 Each block of the decoder consists of six layers. The outputs of each layer become the inputs to the layer above. One of the layers, i.e., the Encoder-decoder attention layer, receives as additional inputs the outputs of the encoder part. The outputs of each block are provided as inputs to the block above. The normalization layers are implemented as residual networks, as it was the case with the encoder.](images/B9780443292385000251/gr013.jpg)

**图 19.13** 解码器的每个块由六层组成。每层的输出成为上一层的输入。其中一层，即编码器-解码器注意力层，额外接收编码器部分的输出作为输入。每个块的输出被提供给上方的块作为输入。归一化层以残差网络的形式实现，这与编码器的情况相同。
