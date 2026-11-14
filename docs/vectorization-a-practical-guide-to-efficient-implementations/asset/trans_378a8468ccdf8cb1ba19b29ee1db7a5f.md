

## 表 2.3 Python、NumPy、Tensorflow 和 PyTorch 中常见数学运算列表。

| 数学运算 | Python | NumPy | Tensorflow | PyTorch |
|---|---|---|---|---|
| 加法 | + | + (np.add) | + (tf.add) | + (torch.add) |
| 减法 | - | - (np.subtract) | - (tf.subtract) | - (torch.subtract) |
| 乘法 | * | * (np.multiply) | * (tf.multiply) | * (torch.multiply) |
| 除法 | / | / (np.divide)<sup>a)</sup> | / (tf.divide) | / (torch.divide) |
| 安全除法 | N/A | np.divide<sup>a)</sup> | tf.math.divide_no_nan | N/A<sup>b)</sup> |
| 整除 | // | np.floor_divide | tf.math.floordiv | torch.floor_divide |
| 倒数 | N/A | np.reciprocal | tf.math.reciprocal | torch.reciprocal |
| 安全倒数 | N/A | np.reciprocal<sup>c)</sup> | tf.math.reciprocal_no_nan | N/A<sup>d)</sup> |
| 余数 | % (math.remainder) | % (np.remainder, np.mod) | tf.math.floormod | torch.remainder |
| 幂 | ** (math.pow) | np.power | tf.math.pow | torch.pow |
| 指数 | math.exp | np.exp | tf.exp | torch.exp |
| exp(x) - 1<sup>e)</sup> | math.expm1 | np.expm1 | tf.math.expm1 | torch.expm1 |
| 以 e 为底的对数 | math.log | np.log | tf.math.log | torch.log |
| 以 2 为底的对数 | math.log2 | np.log2 | N/A<sup>f)</sup> | torch.log2 |
| 以 10 为底的对数 | math.log10 | np.log10 | N/A<sup>f)</sup> | torch.log10 |
| log(1 + x)<sup>g)</sup> | math.log1p | np.log1p | tf.math.log1p | torch.log1p |
| log(exp(x_1) + exp(x_2))<sup>h)</sup> | math.logaddexp | np.logaddexp | tf.experimental.numpy.logaddexp | torch.logaddexp |
| log(sum(exp(x)))<sup>i)</sup> | N/A | scipy.special.logsumexp | tf.math.reduce_logsumexp | torch.logsumexp |

注释：
a) NumPy 没有实现安全除法运算，但可以使用 np.divide(a, b, out=np.zeros_like(b), where=b!=0) 来达到与 tf.divide_no_nan 相同的效果。
b) PyTorch 没有实现安全除法运算，但可以使用 torch.nan_to_num 将商中的 NaN 或 inf 填充为零。NumPy 也有类似的函数 np.nan_to_num。
c) 与 np.divide 方法类似，NumPy 没有实现安全倒数运算，但可以使用 np.reciprocal(x, out=np.zeros_like(x), where=x!=0) 来达到相同的效果。
- d) 与 `divide` 方法类似，PyTorch 也没有实现安全倒数运算，但可以使用 `torch.nan_to_num` 将 `NaN`s 或 `inf`s 填充为零。
- e) `expm1(x)` 在计算表达式 \(e^x - 1\) 时比 `exp(x) - 1` 更准确，特别是在 \(x \to 0\) 时。一个著名的例子是计算年化利率，\((1+x)^{t/y} - 1\)，可以表示为 \(\exp(t/y * \log1p(x)) - 1\)，并实现为 `exp(t / y * np.log1p(x)) - 1`（见下面的示例注释）。
- f) Tensorflow 没有实现除 e 以外的其他对数底数，但可以使用例如 `math.log(x) / tf.math.log(base)` 来转换底数。
- g) `log1p(x)` 在计算表达式 \(\log(1 + x)\) 时比 `log(1 + x)` 更准确，特别是在 \(x \to 0\) 时。著名的例子包括计算年化利率，\((1+x)^{t/y} - 1\)，可以表示为 \(\exp(t/y * \log1p(x)) - 1\)，以及反双曲函数的实现。例如，\(\text{arctanh}(x) = \frac{1}{2} \log(\frac{1+x}{1-x})\) 可以实现为 \(0.5 * (\log1p(x) - \log1p(-x))\)。
- h) `logaddexp` 在 x 非常大或非常小时，对于计算表达式 \(\log(\exp(x_1) + \exp(x_2))\) 更加准确。这是 `logsumexp` 的一个特例（见下面的注释）。
- i) `logsumexp` 是上述 `logaddexp` 的更通用实现，可以对多于两个数字进行操作，计算表达式 \(\log(\sum_i \exp(x_i))\)。请注意，求和表达式是最大似然估计中 softmax 损失函数的归一化项 \(p_j = \text{softmax}(x)_j = \frac{\exp(x_j)}{\sum_i \exp(x_i)}\)，然后对数概率的形式为 \(\log(p_j) = x_j - \log(\sum_i \exp(x_i))\)。NumPy 没有该函数的原生实现，但可以在 Scipy 的 `scipy.special.logsumexp` 中找到，使用所谓的 log-sum-exp 技巧 [Wikipedia, 2023]:

![](img/e891acaacd4fb5b80dab2ed824618203_50_0.png)

其中 \(x_{\max} = \max(x_0, x_1, \dots, x_p)\)。一个 naive 实现是

```
import numpy as np
def logsumexp(x):
    x_max = np.max(x)
    return np.log(np.exp(x - x_max).sum()) + x_max
```

## 表 2.3（续）

| 数学运算 | Python | NumPy | Tensorflow | PyTorch |
|---|---|---|---|---|
| 平方根 | math.sqrt | np.sqrt | tf.sqrt | torch.sqrt |
| 平方 | N/A | np.square | tf.square | torch.square |
| 绝对值 | abs | np.abs | tf.abs | torch.abs |
| 正弦 | math.sin | np.sin | tf.sin | torch.sin |
| 余弦 | math.cos | np.cos | tf.cos | torch.cos |
| 正切 | math.tan | np.tan | tf.tan | torch.tan |
| 双曲正切 | math.tanh | np.tanh | tf.tanh | torch.tanh |
| 四舍五入 | round | np.round | tf.round | torch.round |
| 向上取整 | math.ceil | np.ceil | tf.ceil | torch.ceil |
| 向下取整 | math.floor | np.floor | tf.floor | torch.floor |
| 复数的实部 | (complex).real | np.real | tf.real | torch.real |
| 复数的虚部 | (complex).imag | np.imag | tf.imag | torch.imag |
| 复数共轭 | (complex).conjugate | np.conj(np.conjugate) | tf.math.conj | torch.conj |

j) 你可能会疑惑，为什么我们甚至需要一个特定的函数来计算一个数的平方，而不只是使用 `x ** 2`。这全部关乎性能。事实证明，计算 `x * x` 比 `pow(x, 2)` 更快。拥有一个专门的平方函数，对于实现类似 `this_is_a_variable_with_super_long_name, e.g. See this issue [Paszke et al., 2023a] in PyTorch's repository.` 的东西很方便。

k) Python 复数可以构造为 `<real> + <imag>j`，例如 `1 + 2j`（注意 `2` 和 `j` 之间没有空格）。这就是为什么我通常在编写 for 循环时不使用 `j` 作为索引，因为它可能与 Python 保留的虚数变量混淆。

> 你可能会注意到，对于 Tensorflow 操作，有些函数在 tf 模块下，有些在 tf.math 模块下。这是因为，虽然所有函数都在 tf.math 模块下实现，但一些常用函数被别名到主 tf 模块下以便于访问。你可以通过打印模块路径来验证这一点。例如，tf.math.abs 和 tf.abs 都引用操作 <function tensorflow.python.ops.math_ops.abs(x, name=None)>。

PyTorch 将许多此类操作实现为其 torch.Tensor 类上的方法。因此，除了使用主模块中的函数外，还可以在数组/张量实例上调用相应的方法。例如，除了使用 torch.abs(x)，我们可以执行 x.abs()。这使得 PyTorch 更加面向对象。

## 2.4 归约操作

归约（或 reduce）操作是将一组值汇总为单个值的数学操作。它“缩减”张量的大小，从高维到低维，或者单个标量。表 2.4 列出了归约操作的示例。

NumPy 和 PyTorch 也将许多这些归约操作实现为其各自的 np.ndarray 和 torch.Tensor 类上的方法。因此，除了使用主模块中的函数外，还可以在数组/张量实例上调用相应的方法。例如，除了使用 np.sum(x) 或 torch.sum(x)，我们可以执行 x.sum()。TensorFlow 更偏向函数式，并没有在其 tf.Tensor 类上实现这些归约操作，可能是因为它需要通过跟踪函数调用来支持计算图的构建。

## 2.5 值比较操作

值比较操作比较张量中存储的值。表 2.5 提供了操作的简短列表。

| 归约操作 | Python | NumPy | Tensorflow | PyTorch |
| :--- | :--- | :--- | :--- | :--- |
| 求和<sup>a)</sup> | sum | np.sum | tf.reduce.sum | torch.sum |
| 均值<sup>b)</sup> | N/A | np.mean | tf.reduce.mean | torch.mean |
| 方差<sup>a)</sup> | N/A | np.var | tf.math.reduce.variance | torch.var |
| 标准差<sup>a)</sup> | N/A | np.std | tf.math.reduce.std | torch.std |
| 中位数<sup>a)</sup> | N/A | np.median | N/A<sup>b)</sup> | torch.median |
| 乘积<sup>a)</sup> | N/A | np.prod | tf.reduce.prod | torch.prod |
| 最大值<sup>a)</sup> | max | np.max | tf.reduce.max | torch.max |
| 最小值<sup>a)</sup> | min | np.min | tf.reduce.min | torch.min |
| 任意真 | any | np.any | tf.reduce.any | torch.any |
| 全真 | all | np.all | tf.reduce.all | torch.all |
| 张量范数 | N/A | np.linalg.norm | tf.norm | torch.linalg.norm |

注释：
a) 如果张量中有任何 NaN（"不是一个数字"）值，那么归约操作将始终返回 NaN。幸运的是，许多归约操作都有相应的版本，可以处理填充为 NaN 的缺失值：
- 1. 求和: np.nansum, tf.experimental.numpy.nansum, torch.nansum
- 2. 均值: np.nanmean, tf.experimental.numpy.nanmean, torch.nanmean
- 3. 方差: np.nanvar
- 4. 标准差: np.nanstd
- 5. 中位数: np.nanmedian, torch.nanmedian
- 6. 乘积: np.nanprod, tf.experimental.numpy.nanprod
- 7. 最大值: np.nanmax
- 8. 最小值: np.nanmin
b) 从技术上讲，也可以使用 Tensorflow 派生库 tensorflow_probability 或 tfp 来获取中位数，即 tfp.stats.percentile(x, 50, interpolation="midpoint")，其中 x 是浮点数数组。

| 操作 | Python | NumPy | Tensorflow | PyTorch |
| :--- | :--- | :--- | :--- | :--- |
| 两个数中的最大值 | max | np.maximum | tf.minimum | torch.maximum |
| 两个数中的最小值 | min | np.minimum | tf.maximum | torch.minimum |
| 裁剪值 | N/A | np.clip | tf.clip_by_value | torch.clip, torch.clamp |

## 2.6 逻辑操作

逻辑操作也称为布尔操作，其中计算 AND、OR、NOT 和 XOR 等操作。表 2.6 列出了这四种主要的布尔操作。

