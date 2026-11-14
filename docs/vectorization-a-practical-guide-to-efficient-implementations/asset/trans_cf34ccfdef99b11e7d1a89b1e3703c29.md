

```python
# e.g. (1, ..., batch_size, ..., seq_size, ..., 1, ...)
shape = [1] * sequence.ndim
shape[batch_axis] = indices.shape[0]
shape[seq_axis] = indices.shape[1]
indices = indices.reshape(shape)

# reindexing
reversed_sequence = np.take_along_axis(sequence, indices, seq_axis)
return reversed_sequence
```

![](img/e891acaacd4fb5b80dab2ed824618203_376_0.png)

![](img/e891acaacd4fb5b80dab2ed824618203_376_1.png)

图 10.4 反转填充序列的实现逻辑示意图。（a）在指定序列长度内创建反向索引掩码的示意图。（b）重新排序序列的逐步过程示意图。

- 第 14–17 行获取批次中序列的长度。它使用 `assert` 进行检查，以确保批次中的每个序列都指定了一个序列长度。

- 第 20–25 行创建索引反转掩码。我们首先从正向序列索引 [0, 1, 2, ..., seq_len] 开始。然后，使用 np.where 通过广播来替换值：如果正向索引小于指定序列长度，则计算反向序列索引为 seq_lengths - 1 - indices；否则，保留当前正向索引。有关示意图，请参见图 10.4a（底部矩阵标记为“索引掩码”）。

- 第 29–32 行重塑索引掩码，以处理高维情况。批次和序列维度构成了索引掩码矩阵的两个维度。为了处理其余维度，我们依赖广播机制，使用 np.take_along_axis 对高维序列进行切片。

- 第 35 行使用 np.take_along_axis 对序列进行重新排序。有关底层迭代过程的示意图，请参见图 10.4b。

也可以通过将 NumPy 函数替换为相应的 PyTorch 函数来实现 PyTorch 版本。

```python
import torch

def torch_reverse_sequence(
    sequence: torch.Tensor,
    seq_lengths: list,
    seq_axis: int = 1,
    batch_axis: int = 0,
):
    seq_lengths = torch.asarray(seq_lengths, dtype=int)[:, None]
    assert sequence.shape[batch_axis] == len(
        seq_lengths
    ), "length of seq_lengths must be equal to sequence.shape[batch_axis]"

    # creating reversing indices via masking (batch_size, seq_len)
    indices = torch.arange(sequence.shape[seq_axis])
    # if within specified sequence length, create the reverse index
    # otherwise, retain the forward index
    indices = torch.where(
        indices < seq_lengths, seq_lengths - 1 - indices, indices
    )

    # Add additional singleton dimensions for broadcasting
    # e.g. (1, ..., batch_size, ..., seq_size, ..., 1, ...)
    shape = [1] * sequence.ndim
    shape[batch_axis] = indices.shape[0]
    shape[seq_axis] = indices.shape[1]
    indices = indices.reshape(shape)

# reindexing
reversed_sequence = torch.take_along_dim(sequence, indices, seq_axis)
return reversed_sequence
```

我们可以通过针对 Tensorflow 的实现测试几个示例来验证该实现。

```python
import numpy as np
import tensorflow as tf
# Create a 2D example
sequence = np.array([
    [3, 4, 7, 8, 0, 0, 0, 0],
    [2, 3, 5, 0, 0, 0, 0, 0],
    [8, 7, 6, 5, 4, 0, 0, 0],
])
batch_axis = 0
seq_axis = 1
seq_lengths = [4, 6, 5]
reversed_sequence_np = reverse_sequence(
    sequence, seq_lengths, seq_axis=seq_axis, batch_axis=batch_axis
)
reversed_sequence_tf = tf.reverse_sequence(
    sequence, seq_lengths, seq_axis=seq_axis, batch_axis=batch_axis
)
assert np.allclose(reversed_sequence_np, reversed_sequence_tf)
# Create a 3D example. The batch and sequence axes are not defaults.
# batch_axis = 1, seq_axis = 2
sequence = torch.asarray(
    np.array([
        [
            [3, 4, 7, 8, 0, 0, 0, 0],
            [2, 3, 5, 0, 0, 0, 0, 0],
            [8, 7, 6, 5, 4, 0, 0, 0],
        ],
        [
            [2, 4, 6, 8, 0, 0, 0, 0],
            [4, 6, 10, 0, 0, 0, 0, 0],
            [16, 14, 12, 10, 8, 0, 0, 0],
        ],
    ])
)
batch_axis = 1
seq_axis = 2
# Here padding is also not always 0 and valid sequence value is not
# always > 0
seq_lengths = [4, 6, 3]

reversed_sequence_np = reverse_sequence(
    sequence, seq_lengths, seq_axis=seq_axis, batch_axis=batch_axis
)
reversed_sequence_tf = tf.reverse_sequence(
    sequence, seq_lengths, seq_axis=seq_axis, batch_axis=batch_axis
)
assert np.allclose(reversed_sequence_np, reversed_sequence_tf)
```

## 10.5 案例研究：带权重的 Gumbel-Max 采样

在训练多类分类算法时，我们使用 softmax 函数激活最终层，其输出表示为 \(\theta\)，以获取每个类的概率，

\(p_i = \text{softmax}(\theta_i) = \frac{e^{\theta_i}}{\sum_j^N e^{\theta_j}}\)

其中 \(p_i\) 表示类 \(i\) 的概率；\(N\) 是类的数量；\(\theta_i\) 是类 \(i\) 的未激活最终层输出，通常称为该类的 logit 值。通过反演 softmax 函数，我们可以从概率中计算出 logit 值，如下所示

\(\theta_i = \log \left( p_i \sum_j^N e^{\theta_j} \right) = \log(p_i) + \log(C) = \log(p_i) + C\)

其中 \(C\) 表示某些常数，后续可忽略。

在推荐系统和目标检测等某些领域中，问题通常被表述为多类或多标签分类，常见的是负类数量远多于正类。压倒性数量的负类也会降低训练效率。应对此问题的一种方法是通过随机采样选择固定数量的负类。另一方面，正标签的分布可能偏向那些更受欢迎的类。这些因素可能导致类别不平衡以及模型对更通用类别的偏差。为了缓解类别不平衡，一个可行的解决方案是通过采样减少训练数据中的负标签类别数量。采样可以偏向更通用的类别，使它们在适当时更频繁地出现为负标签。反过来，该策略会使尾部类别较少出现为负标签，从而激励模型更有效地学习预测这些不太通用的类别。为了实现这些目标，我们需要实现无放回采样策略；为了通过向量化高效地实现这些目标，我们需要依赖一次性算法而非迭代算法进行采样。因此，本节将讨论 Gumbel-Max 技巧 [Huijben et al., 2022]。

Gumbel 分布的概率密度函数（PDF）和累积分布函数（CDF）如下

\(\text{PDF}_{\text{Gumbel}}(x; \mu, \beta) = \frac{1}{\beta} e^{-\frac{x-\mu}{\beta}} e^{-\frac{x-\mu}{\beta}}\)

\(\text{CDF}_{\text{Gumbel}}(x; \mu, \beta) = e^{-e^{-\frac{x-\mu}{\beta}}}\)

通过设置 \(\mu = 0, \beta = 1\) 得到标准 Gumbel 分布，此时 PDF 和 CDF 变为

\(\text{PDF}_{\text{Gumbel}}(x; 0; 1) = e^{-x-e^{-x}}\)

\(\text{CDF}_{\text{Gumbel}}(x; 0; 1) = e^{-e^{-x}}\)

令 \(G\) 表示从标准 Gumbel 分布中获得的样本。Gumbel-Max 技巧建议，要从未激活 logits 表示为 \(\theta_i\) 的 softmax 分布中采样，我们可以首先使用以下公式获得样本在 \(N\) 个类别中的索引 \(I\)：

\(I = \text{argmax}_{i \in \{1, ..., N\}} (\theta_i + G^{(i)})\) (10.1)

括号内的项通常称为扰动 logits。由于我们可以预先确定采样方式（例如基于流行度或简单的随机均匀分布），因此可以指定每个类别的概率 \(p_i\)。因此，我们可以用 \(p_i\) 重写公式 10.1，

\(I = \text{argmax}_{i \in \{1, ..., N\}} (\theta_i + G^{(i)}) = \text{argmax}_{i \in \{1, ..., N\}} (\log(p_i) + C + G^{(i)})\) (10.2)

其中 \(C\) 是归一化常数。然而，\(C\) 不会影响扰动 logits 项的顺序，因为它只是将所有类别的值同步移动相同的量。因此，我们可以舍弃该项，并得到

\(I = \text{argmax}_{i \in \{1, ..., N\}} (\log(p_i) + G^{(i)})\) (10.3)

为了为每个类别 \(i\) 采样 \(G^{(i)}\)，我们使用逆变换采样技术。首先从均匀分布 \(y \sim U(0, 1)\) 中采样，然后使用逆累积分布函数（ICDF）来计算样本值。标准 Gumbel 分布的 ICDF 为

\(\text{CDF}_{\text{Gumbel}}^{-1}(y) = -\log(-\log y)\) (10.4)

