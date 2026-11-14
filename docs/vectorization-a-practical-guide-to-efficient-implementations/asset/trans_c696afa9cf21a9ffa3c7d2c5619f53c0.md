

```
import torch
values = torch.rand((2, 3, 4), dtype=float)
indices = torch.tensor([[3, 0]])
X = torch.zeros((5, 3, 4), dtype=float)
X = torch.index_add(X, 0, indices, values)
```

## 3.7 案例研究：批量散布数值

正如我们在 3.6 节中所见，PyTorch 实现了散布操作 `torch.scatter` 的一个版本，它是其聚合操作 `torch.gather` 的逆操作。Tensorflow 未实现 `tf.scatter`，该操作允许通过扁平索引进行散布的批量应用。然而，正如我们将在第 9 章的一个案例研究中看到，批量散布常常用于实现分组聚合逻辑。

假设我们有以下数据（另见图 3.20a），

```
import tensorflow as tf
index = tf.constant([
    [1, 3, 6, 2, 4],
    [2, 4, 8, 9, 5],
    [6, 5, 0, 1, 3],
    [3, 7, 2, 5, 4],
], dtype=tf.int64)
inputs = tf.constant([
    [2, 5, 6, 2, 8],
    [6, 1, 7, 0, 4],
    [9, 5, 4, 5, 1],
    [0, 6, 8, 3, 7],
])
```

图 3.20 使用扁平索引逐步说明批量散布过程。我们假设行是批量维度。矩阵的第一列是数值，而第二列矩阵存储对应位置的扁平索引。第三列矩阵是目标，其中括号内的数字是扁平索引。假设仅带括号索引的 tile 被填充为 0 值。(a)。初始设置；(b)。来自第一个数值的结果（row=0, col=0）；(c)。来自第二个数值的结果（row=0, col=3）；(d)。来自第二行第一个数值的结果（row=1, col=2）；(e)。所有步骤完成后的完整结果。

我们希望根据 `index` 指定的索引批量，将输入散布到新的目标矩阵中。在 PyTorch 中，这可以轻松完成，使用

```
import torch
output = torch.scatter(
    torch.zeros((4, 10), dtype=int),
    1,
    torch.tensor(index.numpy(), dtype=int),
    torch.tensor(inputs.numpy(), dtype=int),
)
# tensor([[0, 2, 2, 5, 8, 0, 6, 0, 0, 0],
#         [0, 0, 6, 0, 1, 4, 0, 0, 7, 0],
#         [4, 5, 0, 1, 0, 5, 9, 0, 0, 0],
#         [0, 0, 8, 0, 7, 3, 0, 6, 0, 0]])

```

然而，我们可以使用 Tensorflow 的 `tf.scatter_nd` 方法来实现相同的效果。更具体地说，请逐步考虑，

- 对于 `index[0, 0] = 1`，我们在相应索引处有一个值 `input[0, 0] = 2`。我们希望将此值放入新张量的位置，使得 `X[0, 1] = 2`（图 3.20b）。鉴于目标张量形状为 `(4, 10)`，多索引 `[0, 1]` 可以转换为扁平索引 1。因此，这等同于为扁平向量赋值 `X_flat[1] = 2`，然后将扁平向量重塑回 2D 矩阵。

- 对于后续图示，图 3.20c–e，我们只是遍历 `index` 的元素，从 `input` 中提取相应的值，并将其散布到 `X` 的相应位置。

请注意，最终输出矩阵包含许多零元素。包含许多零元素的矩阵称为稀疏矩阵，我们将在第 7 章中更详细地介绍。

基于上述逻辑，我们可以实现专门处理 2D 矩阵情况的以下代码。感兴趣的读者可以进一步将此实现推广到更高维张量，或者也许寻找其他方法来实现相同目标。

```
import tensorflow as tf

def scatter_batch_2d(index, inputs):
    # Determines the length of each row for the output
    row_length = tf.cast(tf.reduce_max(index), tf.int32) + 1
    row_length = tf.maximum(tf.shape(inputs)[1], row_length)
    # start and end index of each row
    # row 0: inc[0]:inc[1], row 1: inc[1]:inc[2], ...
    inc = row_length * tf.range(tf.shape(inputs)[0]+1)
    # Compute flat indices for each element
    indices = tf.cast(index, index.dtype) + tf.reshape(inc[:-1], (-1, 1))
    # Flatten to column vector
    indices = tf.reshape(indices, (-1, 1))
    # Flatten updates
    updates = tf.reshape(inputs, (-1,))
    shape = (inc[-1], )
    out = tf.scatter_nd(indices, updates, shape)
    # reshape: (batch_size, row_length)
    out = tf.reshape(out, (tf.shape(index)[0], -1))
    return out
```

- 第 5 行和第 6 行计算输出中每行的长度。这由 `index` 中的最大索引值和 `inputs` 的列数中的较大者决定。本质上，我们希望返回一个具有足够容纳所有索引的列数的输出；我们还希望返回的列数不少于输入的列数。请注意，这是为第 9 章的一个案例研究做准备。或者，我们可以指定参数 `output_shape` 以让用户控制输出的大小。

- 第 9 行计算每行的起始和结束索引作为 1D 向量。在上述示例中，我们将有 `inc = [0, 10, 20, 30, 40]`，其中 `0:10` 是第一行的切片，`10:20` 是第二行的切片，依此类推。

- 第 11 行按行索引的起始位置对特定行的扁平索引进行偏移。例如，如果索引 4 出现在原始索引矩阵的第二行，那么相应的扁平索引将是 `4 + inc[1] = 4 + 10 = 14`。

- 第 13 行将带偏移的索引作为列向量展平。

- 第 15 行到第 17 行根据索引，将值的 1D 数组散布到目标 1D 数组中。

- 第 19 行将 1D 张量重塑回所需的 2D 矩阵，形状为 `(batch_size, row_length)`。

# 参考文献

Martín Abadi, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Ian Goodfellow, Andrew Harp, Geoffrey Irving, Michael Isard, Yangqing Jia, Rafal Jozefowicz, Lukasz Kaiser, Manjunath Kudlur, Josh Levenberg, Dan Mane, Rajat Monga, Sherry Moore, Derek Murray, Chris Olah, Mike Schuster, Jonathon Shlens, Benoit Steiner, Ilya Sutskever, Kunal Talwar, Paul Tucker, Vincent Vanhoucke, Vijay Vasudevan, Fernanda Viegas, Oriol Vinyals, Pete Warden, Martin Wattenberg, Martin Wicke, Yuan Yu, and Xiaoqiang Zheng. Tf.gather. https://www.tensorflow.org/api_docs/python/tf/gather, 2023a.

Martin Abadi, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Ian Goodfellow, Andrew Harp, Geoffrey Irving, Michael Isard, Yangqing Jia, Rafal Jozefowicz, Lukasz Kaiser, Manjunath Kudlur, Josh Levenberg, Dan Mane, Rajat Monga, Sherry Moore, Derek Murray, Chris Olah, Mike Schuster, Jonathon Shlens, Benoit Steiner, Ilya Sutskever, Kunal Talwar, Paul Tucker, Vincent Vanhoucke, Vijay Vasudevan, Fernanda Viegas, Oriol Vinyals, Pete Warden, Martin Wattenberg, Martin Wicke, Yuan Yu, and Xiaoqiang Zheng. Tf.gathernd. https://www.tensorflow.org/api_docs/python/tf/gather_nd, 2023b.

Martin Abadi, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Ian Goodfellow, Andrew Harp, Geoffrey Irving, Michael Isard, Yangqing Jia, Rafal Jozefowicz, Lukasz Kaiser, Manjunath Kudlur, Josh Levenberg, Dan Mane, Rajat Monga, Sherry Moore, Derek Murray, Chris Olah, Mike Schuster, Jonathon Shlens, Benoit Steiner, Ilya Sutskever, Kunal Talwar, Paul Tucker, Vincent Vanhoucke, Vijay Vasudevan, Fernanda Viegas, Oriol Vinyals, Pete Warden, Martin Wattenberg, Martin Wicke, Yuan Yu, and Xiaoqiang Zheng. 张量简介. https://www.tensorflow.org/guide/tensor, 2023c.

Martin Abadi, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Ian Goodfellow, Andrew Harp, Geoffrey Irving, Michael Isard, Yangqing Jia, Rafal Jozefowicz, Lukasz Kaiser, Manjunath Kudlur, Josh Levenberg, Dan Mane, Rajat Monga, Sherry Moore, Derek Murray, Chris Olah, Mike Schuster, Jonathon Shlens, Benoit Steiner, Ilya Sutskever, Kunal Talwar, Paul Tucker, Vincent Vanhoucke, Vijay Vasudevan, Fernanda Viegas, Oriol Vinyals, Pete Warden, Martin Wattenberg, Martin Wicke, Yuan Yu, and Xiaoqiang Zheng. Tf.scatternd. https://www.tensorflow.org/api_docs/python/tf/scatter_nd, 2023d.

Adam Paszke, Sam Gross, Francisco Massa, Adam Lerer, James Bradbury, Gregory Chanan, Trevor Killeen, Zeming Lin, Natalia Gimelshein, Luca Antiga, Alban Desmaison, Andreas Köpf, Edward Yang, Zach DeVito, Martin Raison, Alykhan Tejani, Sasank Chilamkurthy, Benoit Steiner, Lu Fang, Junjie Bai, and Soumith

