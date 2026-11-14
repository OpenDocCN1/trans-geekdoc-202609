

![](img/e891acaacd4fb5b80dab2ed824618203_407_0.png)

图 11.4 原始Transformer论文中的正弦位置编码。

- i 是嵌入维度上的索引，i \in (0, 1, 2, ..., d_{model} // 2)，
- d_{model} 是嵌入大小。

这通常被称为正弦位置编码，因为它利用由序列和嵌入维度上的位置参数化的正弦波。以下代码块展示了如何使用 PyTorch 实现原始论文中的正弦位置编码：

```python
import torch

def sinusoidal_positional_encoding_vaswani(emb_size, seq_len):
    position = torch.arange(seq_len)
    timescales = torch.pow(
        1 / 10000,
        2 * (torch.arange(emb_size) // 2) / emb_size,
    )
    angles = position.unsqueeze(1) * timescales.unsqueeze(0)
    out = torch.zeros((seq_len, emb_size))
    # Interleaving sin and cos along embedding dimension
    out[:, 0::2] = torch.sin(angles[:, 0::2])
    out[:, 1::2] = torch.cos(angles[:, 1::2])
    return out
```

- 第 4–9 行实现了方程 11.3 中正弦和余弦函数内部的项。它通过嵌入维度矩阵创建一个序列（例如时间）。
- 第 10 行创建输出占位符，并用零初始化。
- 第 12–13 行分别将偶数位置赋予正弦值，奇数位置赋予余弦值。

我们可以根据嵌入大小 256 和序列长度 500 绘制位置编码，如图 11.4 所示。

![](img/e891acaacd4fb5b80dab2ed824618203_408_0.png)

图 11.5 正弦位置编码的 Tensor2Tensor 变体。

Google 的 tensor2tensor [Vaswani et al., 2018] 深度学习库 [Vaswani et al., 2023] 在 TransformerXL 架构中引入了正弦位置编码的另一种公式。（这也是 Google 关于 Transformer 教程 [Abadi et al., 2023] 中的实现。）它不再沿深度维度交错正弦和余弦项，而是直接将两部分拼接在一起。以下是这种正弦位置编码变体的实现，编码映射如图 11.5 所示。

```python
import torch

def sinusoidal_positional_encoding_tensor2tensor(emb_size, seq_len):
    position = torch.arange(seq_len)
    timescales = torch.pow(
        1 / 10000,
        2 * (torch.arange(emb_size) // 2) / emb_size,
    )
    angles = position.unsqueeze(1) * timescales.unsqueeze(0)
    out = torch.zeros((seq_len, emb_size))
    # Stacking the two partitions
    out = torch.cat([
        torch.sin(angles[:, 0::2]),
        torch.cos(angles[:, 1::2])
    ], axis=1)
    return out
```

## 11.4.2 作为分类嵌入的位置

正弦位置信息是硬编码的。不过，也可以学习表示位置信息。学习表示位置信息的一种方法是将位置视为分类特征。然后，通过反向传播，网络学会高效地编码位置信息。使用学习分类位置嵌入的著名架构包括 BERT [Devlin et al., May 2019] 和 RoBERTa [Liu et al., 2019]。让我们实现一个简单的层，将位置嵌入添加到输入中。

```python
import torch
from torch import nn

class PositionalEmbedding(nn.Module):
    def __init__(self, seq_len, emb_size):
        super().__init__()
        self.embed = nn.Embedding(seq_len, emb_size)

    def forward(self, x):
        # x: (batch_size, seq_len, emb_size)
        pos = torch.arange(x.shape[1], dtype=torch.int32)
        # embedding lookup (batch_size, seq_len, emb_size)
        pos_emb = self.embed(pos)
        # add
        x = x + pos_emb
        return x
```

- __init__（第 5–7 行）：初始化位置嵌入模块并创建嵌入查找表。
- forward（第 9–17 行）：
  - 第 11 行为当前序列输入创建位置向量。
  - 第 13 行查找相应的嵌入向量。
  - 第 15 行将位置嵌入向量添加到输入中。

## 11.4.3 相对位置编码（RPE）

正弦位置编码有时也被称为绝对位置编码。因此，作为对应物，开发了相对位置编码（RPE），仅用于在注意力机制中编码序列对之间的相对距离。回顾自注意力在原始 Transformer 论文 [Vaswani et al., 2017] 中定义为

![](img/e891acaacd4fb5b80dab2ed824618203_409_0.png)

其中

- \(d_k\) 是键的嵌入大小。

Q、K 和 V 是查询、键和值向量，通过将输入传入密集投影层获得，例如 Q = W_q X_q，其中 X_q 是查询的嵌入向量。在自注意力场景中，X_q、X_k 和 X_v 相同，因此我们将其表示为 X。

在绝对正弦位置编码的情况下，通常在嵌入输出 X 上添加位置编码，然后使用密集层投影再计算注意力分数。在数学上，我们可以将其表述为 Q = (X + PE)W_q 和 K = (X + PE)W_k。那么，

```
QK^T = (X + PE)W_q \cdot ((X + PE)W_k)^T
```

然而，RPE 将此项表述为 [Luo et al., 2022]

```
QK^T = (XW_q) \cdot (XW_k)^T + B
```

其中 B 是一个方阵。也就是说，RPE 将位置编码信息添加到注意力分数图上，而不是直接添加到输入 token 表示上，在此过程中计算每对 token 之间的相对距离。B 的著名公式包括：

- 原始 RPE 论文 [Shaw et al., 2018]：b_ij = X_i W_q r_{i-j}^T，其中 r_{i-j} 是序列中位置 i 和 j 之间的可学习参数。
- Transformer-XL [Dai et al., 2019]：b_ij = X_i W_q (r_{i-j} \tilde{W}_k)^T + u(X_j W_k)^T + v(r_{i-j} \tilde{W}_k)^T，其中 u、v 和 \tilde{W}_k 是可学习向量，而 r_{i-j} 是正弦位置编码。
- T5（文本到文本传输 Transformer）[Raffel et al., 2020]：b_ij 是一个独立的可学习参数。

图 11.6 说明了 T5 模型的情况。计算键和查询位置之间的成对距离。然后，使用相对距离的嵌入来构建形状为 (q_len, k_len, emb_size) 的位置嵌入张量，然后将其添加到注意力分数 [Wolf et al., 2020; HuggingFace, 2023]。请注意，T5 模型采用一种策略，将大相对距离映射到对数尺度的桶号，因此这些大相对距离可能对应相同的嵌入向量。

## 11.4.4 旋转位置编码（RoPE）

RoFormer 论文 [Su et al., 2020] 引入了旋转位置编码（RoPE），这也是一种相对注意力形式。它不是将位置编码添加到输入中，而是通过旋转序列的嵌入向量的理念

图 11.6 T5 模型中的相对位置嵌入。

![](img/e891acaacd4fb5b80dab2ed824618203_411_0.png)

由位置参数化的角度旋转。具体来说，给定旋转矩阵 \( R \)，旋转位置编码通过乘法 \( RX \) 融入输入 \( X \) 中。在此，\( R\) 具有如下形式：

```
R_{\Theta, d}^{(p)} = \begin{bmatrix} \cos(p\theta_1) & -\sin(p\theta_1) & 0 & 0 & \dots & 0 & 0 \\ \sin(p\theta_1) & \cos(p\theta_1) & 0 & 0 & \dots & 0 & 0 \\ 0 & 0 & \cos(p\theta_2) & -\sin(p\theta_2) & \dots & 0 & 0 \\ 0 & 0 & \sin(p\theta_2) & \cos(p\theta_2) & \dots & 0 & 0 \\ \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \\ 0 & 0 & 0 & 0 & \dots & \cos(p\theta_{d/2}) & -\sin(p\theta_{d/2}) \\ 0 & 0 & 0 & 0 & \dots & \sin(p\theta_{d/2}) & \cos(p\theta_{d/2}) \end{bmatrix}
```

其中，

- \( R_{\Theta, d}^{(p)} \) 是位置 \( p \) 的旋转矩阵的第 \( p \) 个切片。
- 每个切片是一个 \( d \times d \) 矩阵，其中 \( d \) 是嵌入大小（即 \( d_{model} \)）。
- \( \Theta \) 是一个数组，每个元素为 \( \theta_i = 10,000^{-2(i-1)/d} \)，其中 \( i \in [1, 2, 3, \dots, d/2] \)。

请注意，每个块都是形式为

```
\begin{bmatrix} \cos(\theta) & -\sin(\theta) \\ \sin(\theta) & \cos(\theta) \end{bmatrix}
```

这意味着，我们正在沿嵌入向量旋转每对值，旋转角度由 \( p\theta_i \) 计算得出。以下代码块是旋转矩阵 \( R \) 的一个实现：

