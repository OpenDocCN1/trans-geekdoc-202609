

![](img/e891acaacd4fb5b80dab2ed824618203_171_0.png)

图 5.3 阈值化前后去除背景。

且反对角线元素为 1，其余元素均为 0。我们希望将此掩码应用于形状相同的矩阵：

```python
import numpy as np
X = np.arange(25).reshape(5, 5) + 1
# array([[ 1,  2,  3,  4,  5],
#        [ 6,  7,  8,  9, 10],
#        [11, 12, 13, 14, 15],
#        [16, 17, 18, 19, 20],
#        [21, 22, 23, 24, 25]])
# Create the cross-like mask
mask = np.zeros_like(X)
np.fill_diagonal(mask, 1)
mask = mask[:, ::-1] # now the anti-diagonal is filled
np.fill_diagonal(mask, 1)
# array([[0, 0, 0, 0, 1],
#        [0, 0, 0, 1, 0],
#        [0, 0, 1, 0, 0],
#        [0, 1, 0, 1, 0],
#        [1, 0, 0, 0, 1]])
# Apply the mask with multiplication
# equivalent to np.where(mask > 0, X, 0)
X = X * mask
# array([[ 1,  0,  0,  0,  5],
#        [ 0,  7,  0,  9,  0],
#        [ 0,  0, 13,  0,  0],
#        [ 0, 17,  0, 19,  0],
#        [21,  0,  0,  0, 25]])
```

## 5.1.4 将算术运算用作布尔运算以应用和组合掩码

如第 2 章所介绍，有四种主要的布尔运算：AND、OR、NOT 和 XOR。当掩码张量表示为布尔值时，我们可以利用布尔运算符 &、|、~ 和 ^，或专用操作（如 Tensorflow 的 logical_and、logical_or、logical_not 和 logical_xor）。然而，掩码可以作为数值张量而不是布尔张量创建，因此需要进行类型转换。如果我们的掩码和数据已经是数值 dtype，则仅使用数值运算来组合和应用掩码可能更简单、更易于操作。

为了说明布尔运算如何表示为算术运算，假设我们有两个掩码 mask_a = [1, 0, 0, 1, 0] 和 mask_b = [0, 0, 0, 1, 1]。如果将它们转换为布尔掩码，则 mask_a_bool = [True, False, False, True, False] 且 mask_b_bool = [False, False, False, True, True]。

对 mask_a_bool 进行 NOT 运算得到 B = [False, True, True, False, True]，或者转换为二进制，[0, 1, 1, 0, 1]。请注意，这仅仅是 1 - mask_a。因此，1 - mask 可用于 NOT 运算。

mask_a_bool 和 mask_b_bool 之间的 AND 运算得到 B = [False, False, False, True, False]。当且仅当两个数组在对应索引处的元素都为 True（或数值上为 1）时，AND 运算才会产生 True。我们可以将两个数值掩码相乘，得到 S = [0, 0, 0, 1, 0]。请注意，这与布尔掩码 B 很好地对应，其中 0 对应 False，1 对应 True。

mask_a_bool 和 mask_b_bool 之间的 OR 运算得到 B = [True, False, False, True, True]。当两个数组在对应索引处的任一元素为 True（或数值上对应 1）时，OR 运算会产生 True。我们可以将两个数值掩码相加，得到 S = [1, 0, 0, 2, 1]。这与组合后的布尔掩码很好地对应，其中 0 对应 False，任何大于 0 的值都对应 True。为了保留组合掩码的二进制（仅 0 和 1）特性，我们可以将组合数值掩码的值裁剪为最大值 1，即 np.minimum(S, 1) = [1, 0, 0, 1, 1]。

最后，mask_a_bool 和 mask_b_bool 之间的 XOR 运算得到 B = [True, False, False, False, True]。当且仅当两个元素的值不相同时（True vs. False 或 False vs. True），XOR 运算会产生 True；否则（True vs. True 或 False vs. False）产生 False。使用 AND、OR 和 NOT 运算符，XOR 等价于 a ^ b = (a | b) & ~(a & b)。因此，更困难的方法是使用上述算术版本的 AND、OR 和 NOT 布尔运算来重构 XOR。然而，更简单的方法是使用减法和绝对值，即 np.abs(a - b) = np.abs([1, 0, 0, 0, -1]) = [1, 0, 0, 0, 1]。

以下代码片段实现了布尔运算的算术版本。

```python
import numpy as np

def combine_mask(a, b=None, operation="not"):
    if operation == "not":
        assert b is not None, f"b is required for {operation}"
    if operation == "not": # b is ignored
        return 1 - a
    elif operation == "and":
        return a * b
    elif operation == "or":
        return np.minimum(a + b, 1)
    elif operation == "xor":
        return np.abs(a - b)
    else:
        raise(ValueError(f"Unrecognized operation {operation}."))
```

## 5.1.5 基于掩码选择元素

迄今介绍的掩码方法都会替换张量内部的值，同时保留输入张量的形状和维度。然而，在某些情况下，我们希望丢弃被掩码的元素，从而减小输入的大小。NumPy 的 np.compress（或等效的 Tensorflow 的 tf.boolean_mask 和 PyTorch 的 torch.masked_select）用于此目的。在最简单的情况下，布尔掩码与使用布尔索引选择元素相同。例如，

```python
import numpy as np

X = np.array([5, 3, 2, 6, 9])
mask = np.mod(X, 2) == 0 # even number
assert np.allclose(
    X[mask], # array([2, 6])
    np.compress(mask, X) # array([2, 6])
)
```

对于更高级的示例，假设我们有一个大小为 (N, N) 的二维方阵，希望删除所有对角线元素，使其变为

![](img/e891acaacd4fb5b80dab2ed824618203_174_0.png)

图 5.4 布尔张量掩码和压缩。

大小为 (N, N-1) 的矩形矩阵。我们可以使用以下 PyTorch 过程实现此操作（另见图 5.4）：

```python
import torch
X = torch.arange(25).reshape(5, 5) + 1
mask = torch.ones_like(X, dtype=bool)
mask.fill_diagonal_(False)
X_masked = torch.masked_select(X, mask).reshape(5, 4)
```

等效操作可以在 Tensorflow 中实现，但不能使用 NumPy 的 `np.compress`，因为 `mask` 必须是 1D 且沿输入张量 X 的某个维度进行操作。

## 5.1.6 案例研究：Top-k 掩码

假设我们有一批数组（例如二维矩阵）。对于每个数组，我们希望仅保留前三个值，而将所有其他条目设为零（见图 5.5a）。我们可以通过创建二进制掩码并将其应用于原始矩阵来实现此操作。二进制掩码应在原始矩阵值位于前三个值中的索引处设为 1，否则设为 0（见图 5.5b）。

以下代码片段使用 NumPy 实现了 top-k 掩码操作。

```python
import numpy as np
def top_k_masking(y, top_k, masked_value=0):
    """Mask the input and retain only top_k values."""
    # Get top k indices
    index = np.argsort(y) [..., -top_k:][..., ::-1]
    # Initialize the zeros mask
    mask = np.zeros_like(y)
    # scatter the indices (in-place)
    np.put_along_axis(mask, index, 1, axis=-1)
    # Adjust values such that the masked elements
    # are replaced with masked_value
    y_masked = y * mask + masked_value * (1 - mask)
    return y_masked
```

- 第 5 行获取 top-k 值的索引
- 第 7 行初始化掩码，该掩码将保留的值指示为 1，将丢弃的值指示为 0。
- 第 9 行进行原位替换，在将保留值的索引处放入 1。
- 第 12 行应用掩码。mask 是二进制的（1 和 0）。逐元素乘法 y * mask 会先将所有被掩码/丢弃的值设为零。然后，masked_value * (1 - mask) 会将被掩码的条目设为 masked_value（即，当需要掩码时，value:= 0 + masked_value = masked_value；否则，value:= value + 0 = value）。

![](img/e891acaacd4fb5b80dab2ed824618203_175_0.png)

![](img/e891acaacd4fb5b80dab2ed824618203_175_1.png)

图 5.5 掩码前 K 值。(a) 给定示例数组批次，我们希望保留每个数组中的前三个值，并将数组中的其余元素设为 0。(b) 要创建掩码，我们首先按每个数组对值进行排序并识别前三个值的索引。然后创建一个与原始矩阵形状相同的二进制掩码，并在前三个值的对应索引处将值设为 1。

```python
y = np.array([
    [1, 5, 2, 3, 8, 7],
    [2, 6, 3, 1, 9, 4]
])
```

