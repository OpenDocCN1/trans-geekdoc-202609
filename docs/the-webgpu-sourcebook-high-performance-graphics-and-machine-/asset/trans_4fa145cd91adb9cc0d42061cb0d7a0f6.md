

$$\\frac{\\partial p\_{i}}{\\partial y\_{j}} = p\_{i}\\left( {\\delta\_{ij} - p\_{j}} \\right)$$

将其代入损失梯度表达式中，我们得到以下结果：

$$\\begin{matrix} {\\frac{\\partial J}{\\partial y\_{j}} = - \\sum\\limits\_{i = 0}^{2}obs\_{i}\\frac{1}{p\_{i}}\\frac{\\partial p\_{i}}{\\partial y\_{j}} = - \\sum\\limits\_{i = 0}^{2}obs\_{i}\\frac{1}{p\_{i}}\\left\\lbrack {p\_{i}\\left\\lbrack {\\delta\_{ij} - p\_{j}} \\right\\rbrack} \\right\\rbrack} \\\\ {= - \\sum\\limits\_{i = 0}^{2}obs\_{i}\\left( {\\delta\_{ij} - p\_{j}} \\right)} \\\\ {= - obs\_{j}\\left( {1 - p\_{j}} \\right) + \\sum\\limits\_{i \\neq j}obs\_{i}p\_{j}} \\\\ {= - obs\_{j} + obs\_{j}p\_{j} + \\sum\\limits\_{i \\neq j}obs\_{i}p\_{j}} \\\\ {= p\_{j}\\left( {obs\_{j} + \\sum\\limits\_{i \\neq j}obs\_{i}} \\right) - obs\_{j}} \\\\ {= p\_{j} - obs\_{j}} \\\\ \\end{matrix}$$

最后一行是通过将 `obs[i]` 的和设为 1 得到。之所以可以这样做，是因为 `obs[i]` 包含鸢尾花物种的已知概率——三个值中总有一个为 1，而其余为 0。这解释了为什么计算着色器从 softmax 输出中减去正确的值。

### 计算损失梯度——第 2 部分

求交叉熵损失相对于 `y[j]`（softmax 输入）的导数是一个重要步骤，但为了获得最终的损失梯度，计算着色器需要进一步操作。目标是获得一个包含损失相对于每个权重 `w[i]` 的偏导数的向量。利用链式法则，我们可以用以下方程为此形成一个表达式：

$$\\frac{\\partial J}{\\partial w\_{i}} = \\frac{\\partial J}{\\partial y\_{j}}\\frac{\\partial y\_{j}}{\\partial w\_{i}}$$

现在的目标是找到第二项，即 softmax 输入 (`y[j]`) 相对于每个权重 (`w[i]`) 的偏导数。为了了解这对于示例网络如何实现，请考虑 [图 9.16](#chapter9.xhtml#fig9_16) 中显示的图表。

![图 9.16 将 softmax 输入与权重关联。](images/fig9_16.jpg)

[图 9.16](#chapter9.xhtml#b9fig9_16) 将 softmax 输入与权重关联。

该图表说明了影响最顶层输出节点 `y[0]` 的输入、信号和权重。如前所述，每个权重表示为 `w[yz]^x`，其索引可以按以下方式解释：

* `x` 标识产生加权信号的节点的所在层
* `y` 标识产生待加权信号的节点的索引
* `z` 标识接收信号的节点的索引

假设我们想知道 `y[0]` 相对于 `w²[00]` 的偏导数。当看到以下方程时，这很容易计算：

$$\\begin{array}{l} {y\_{0} = w\_{00}^{2}h\_{0}^{2} + w\_{10}^{2}h\_{1}^{2} + w\_{20}^{2}h\_{2}^{2} + w\_{30}^{2}h\_{3}^{2} + w\_{40}^{2}} \\\\ {\\frac{\\partial y\_{0}}{\\partial w\_{00}^{2}} = h\_{0}^{2}} \\\\ \\end{array}$$

如图所示，`y[0]` 相对于 `w²[00]` 的偏导数只是乘以权重的信号（本例中为 `h²[0]`）。那么 `y[0]` 相对于 `w¹[00]` 的偏导数呢？

隐藏节点使用 `ReLU` 作为其激活函数，因此了解其导数如何获得很重要。如果 `x` 大于 0，`ReLU(x)` 返回 `x` 且其导数为 1。如果 `x` 小于或等于 0，`ReLU` 返回 0 且其导数为 0。以下方程展示了这一点，该方程推导了 `y[0]` 相对于 `w¹[00]` 的偏导数。

$$\\begin{array}{l} {y\_{0} = w\_{00}^{2}h\_{0}^{2} + w\_{10}^{2}h\_{1}^{2} + w\_{20}^{2}h\_{2}^{2} + w\_{30}^{2}h\_{3}^{2} + w\_{40}^{2}} \\\\ {\\frac{\\partial y\_{0}}{\\partial w\_{00}^{1}} = \\frac{\\partial}{\\partial w\_{00}^{1}}\\lbrack w\_{00}^{2}h\_{0}^{2} + w\_{10}^{2}h\_{1}^{2} + w\_{20}^{2}h\_{2}^{2} + w\_{30}^{2}h\_{3}^{2} + w\_{40}^{2}\\rbrack} \\\\ {\\;\\;\\;\\;\\;\\;\\;\\;\\; = \\frac{\\partial}{\\partial w\_{00}^{1}}(w\_{00}^{2}h\_{0}^{2}) = w\_{00}^{2}\\frac{\\partial}{\\partial w\_{00}^{1}}h\_{0}^{2}} \\\\ {w\_{00}^{2}\\frac{\\partial}{\\partial w\_{00}^{1}}h\_{0}^{2} = w\_{00}^{2}\\frac{\\partial}{\\partial w\_{00}^{1}}\\lbrack{Re}\\,\\text{LU}(w\_{00}^{1}h\_{0}^{1} + w\_{10}^{1}h\_{1}^{2} + w\_{20}^{1}h\_{2}^{1} + w\_{30}^{1}h\_{3}^{1} + w\_{40}^{1})\\rbrack} \\\\ {\\frac{\\partial y\_{0}}{\\partial w\_{00}^{1}} = \\left\\{ {}\_{w\_{00}^{2}h\_{0}^{1}\\, if\\, h\_{0}^{2} > 0}^{0\\,\\, if\\, h\_{0}^{2} \\leq 0}~ \\right.} \\\\ \\end{array}$$

我们可以使用类似的方法获得进一步的导数。例如，以下方程给出了 `y[0]` 相对于 `w⁰[00]` 的偏导数。

$$\\frac{\\partial y\_{0}}{\\partial w\_{00}^{0}} = \\left\\{ \\begin{matrix} {0\\;if\\;h\_{0}^{2} \\leq 0\\;or\\;h\_{0}^{1} \\leq 0} \\\\ {w\_{00}^{2}w\_{00}^{1}x\_{0}\\;if\\;h\_{0}^{2} > 0\\;and\\;h\_{0}^{1} > 0} \\\\ \\end{matrix}~ \\right.$$

对于最接近输出节点的权重，损失梯度更容易计算。因此，计算着色器通过执行一系列从第 3 层到第 1 层的循环来获得损失梯度。节点-节点权重的损失梯度存储在 workgroup 内存中的 `J` 变量中。偏置-节点权重的梯度存储在 `J_bias` 变量中。

计算损失梯度后，计算着色器使用以下代码更新网络的权重和偏置：

```
// Update weights and biases
if (id.x == 0) {

    // Iterate through weights
    for (i = 0; i < num_weights; i++) {
        sum = 0.0;
        for (j = 0; j < batch_size; j++) {
            sum += J[j * num_weights + i];
        }
        weights[i] -= eta * sum;
    }
    // Iterate through biases
    for (i = 0; i < num_bias; i++) {
        sum = 0.0;
        for (j = 0; j < batch_size; j++) {
            sum += J_bias[j * num_bias + i];
        }
        bias_weights[i] -= eta * sum;
    }
}
storageBarrier();
```

学习率 `eta` 设为 0.001，因此权重在一次迭代到下一次迭代之间不会显著变化。但经过足够多的训练迭代后，着色器将权重设置为适合正确鸢尾花分类的值。

## 测试网络

在最后一次训练迭代后，计算着色器尝试对存储在 `test_data` 缓冲区中的鸢尾花的特征进行分类。对于每个输入向量，计算着色器产生三个值：鸢尾花属于 setosa 物种的概率、属于 versicolor 物种的概率以及属于 virginica 物种的概率。

为了执行测试，着色器处理网络的每个节点。以下代码展示了如何完成此操作：

