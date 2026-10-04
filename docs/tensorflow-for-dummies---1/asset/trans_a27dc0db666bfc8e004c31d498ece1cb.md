

| `outputs_collections` || `None` || 存储归一化输出的集合 |
| `trainable` || `True` || 是否将归一化变量添加到图的 trainable 集合中 |
| `batch_weights` || `None` || 用于缩放批次均值和方差的权重 |
| `fused` || `False` || 是否使用融合归一化（更快） |
| `data_format` || `DATA_FORMAT_NHWC` || 输入数据的格式 |
| `zero_debias_moving_mean` || `False` || 用于更新移动均值的因子 |
| `scope` || `None` || 包含归一化变量的作用域 |
| `renorm` || `False` || 是否在归一化期间使用额外变量 |
| `renorm_clipping` || `None` || 提供重归一化值的字典 |
| `renorm_decay` || `0.99` || 重归一化期间更新移动均值/方差的因子 |

TensorFlow 使用 `decay` 参数来计算总体均值和方差。以下方程展示了计算的执行方式：

![images](images/eq07017.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mtable columnalign="left"><m:mtr><m:mtd><m:msub><m:mi>&#956;</m:mi><m:mi>P</m:mi></m:msub><m:mo>=</m:mo><m:msub><m:mi>&#956;</m:mi><m:mi>P</m:mi></m:msub><m:mi>d</m:mi><m:mi>e</m:mi><m:mi>c</m:mi><m:mi>a</m:mi><m:mi>y</m:mi><m:mo>+</m:mo><m:msub><m:mi>&#956;</m:mi><m:mi>B</m:mi></m:msub><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>1</m:mn><m:mo>&#45;</m:mo><m:mi>d</m:mi><m:mi>e</m:mi><m:mi>c</m:mi><m:mi>a</m:mi><m:mi>y</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mtd></m:mtr><m:mtr><m:mtd><m:msubsup><m:mi>&#963;</m:mi><m:mi>P</m:mi><m:mn>2</m:mn></m:msubsup><m:mo>=</m:mo><m:msubsup><m:mi>&#963;</m:mi><m:mi>P</m:mi><m:mn>2</m:mn></m:msubsup><m:mi>d</m:mi><m:mi>e</m:mi><m:mi>c</m:mi><m:mi>a</m:mi><m:mi>y</m:mi><m:mo>+</m:mo><m:msubsup><m:mi>&#963;</m:mi><m:mi>B</m:mi><m:mn>2</m:mn></m:msubsup><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>1</m:mn><m:mo>&#45;</m:mo><m:mi>d</m:mi><m:mi>e</m:mi><m:mi>c</m:mi><m:mi>a</m:mi><m:mi>y</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mtd></m:mtr></m:mtable></m:math>

`center` 和 `scale` 参数决定是否应移动和缩放 `inputs` 参数的值。如果 `center` 为 `True`，函数将移动输入值；如果 `scale` 为 `True`，函数将缩放输入值。

了解 `is_training` 和 `trainable` 之间的区别很重要。将 `is_training` 设置为 `True` 告诉函数归一化是在训练期间执行的，这意味着它应更新总体的均值和方差。将 `trainable` 设置为 `True` 告诉函数将其归一化变量存储在由 `TRAINABLE_VARIABLES` 键表示的图集合中。

`batch_norm` 的最后三个参数与 *重归一化* 相关。当应用程序的批次很小或相互依赖时，此过程可改善归一化。

### 正则化

在机器学习中寻找神经网络的合适结构是最困难的任务之一。如果添加的节点太少，网络将过于简单，无法准确分类数据。这称为 *欠拟合*。

如果添加的节点太多，网络将专门针对训练集进行定制，并且不适合分析通用数据。此问题称为 *过拟合*，并且是机器学习中的一个严重问题。

更新神经网络（或其他机器学习算法）以分析通用数据的过程称为 *正则化*。研究人员设计了许多正则化网络的方法，本节重点介绍其中两种：

*   **Dropout：** 随机从网络中移除节点
*   **L1/L2 正则化：** 通过增加损失来减少权重

对于这两种方法，我解释了正则化如何工作以及如何使用 TensorFlow 执行它。

#### Dropout

Dropout 过程会随机从网络中移除一个或多个节点。对于每个被移除的节点，dropout 会移除该节点的输入和输出连接及其权重。

在 TensorFlow 中，您可以通过添加 dropout 层来为神经网络配置 dropout。添加此层涉及调用 `tf.nn.dropout` 函数：

```
dropout(x, keep_prob, noise_shape=None, seed=None, name=None)
```

在此函数中，`x` 是包含前一层值的张量，`keep_prob` 是与 `x` 相同类型的标量。函数返回与 `x` 尺寸相同的张量。

`dropout` 将其每个输出值设置为 0 或 `1/keep_prob` 倍的对应输入值。更精确地说，`dropout` 以 `1-keep_prob` 的概率将输出值设置为 0，并以 `keep_prob` 的概率将输出值设置为 `1/keep_prob` 倍的输入值。

#### L1/L2 正则化

L1 和 L2 正则化通过减少网络的权重来防止过拟合。两种方法都通过一个取决于两个因素的值来增加损失：网络的权重和一个常数 λ。

L1 正则化通过 λ 乘以待更新权重的绝对值来增加损失。因此，当算法通过反向传播更新权重 w[0] 时，它会向损失添加一个等于 λ|w[0]| 的值。

L2 正则化通过 λ/2 乘以待更新权重的平方来增加损失。因此，当算法更新 w[0] 时，它会向损失添加 λ|w[0]|²/2。

在两种情况下，损失在权重增加时会增加，在权重减少时会减少。因此，正则化过程倾向于将非必要的权重减少为零，从而简化模型并（希望）避免过拟合。

要在 TensorFlow 中执行 L1/L2 正则化，您可以调用 `tf.contrib.layers.l1_regularizer` 或 `tf.contrib.layers.l2_regularizer`：

*   `l1_regularizer(lambda, scope=None)`：返回执行 L1 正则化的函数
*   `l2_regularizer(lambda, scope=None)`：返回执行 L2 正则化的函数

这些函数返回特殊的函数称为 *正则化器*。获得正则化器后，您可以通过调用 `tf.contrib.layers.apply_regularization` 来正则化一组权重：

```
apply_regularization(regularizer, weights_list=None)
```

许多 TensorFlow 函数接受正则化器作为参数。一个重要的函数是 `tf.contrib.layers.fully_connected`，我在 “[Improving the Deep Learning Process](#12_9788126592555-ch07.xhtml#c07-sec-0028)” 部分讨论了它。

## 使用作用域管理变量

使用神经网络构建应用程序时，跟踪权重是一个主要优先事项。隐藏层接受加权输入并产生加权输出。如果没有适当的<|message|>管理，很容易使一个层的权重名称与另一个层的权重名称冲突。

### 变量作用域

在深度学习应用程序中，层经常为其权重分配相同的名称。为了使变量保持分离，TensorFlow 使定义变量的 *作用域* 成为可能。应用程序可以通过调用 `tf.variable_scope` 来定义作用域：

```
tf.variable_scope(name_or_scope, default_name=None, values=None, initializer=None, regularizer=None, caching_device=None, partitioner=None, custom_getter=None, reuse=None, dtype=None, use_resource=None)
```

应用程序通常作为 `with` 语句的一部分调用此函数，如以下代码所示：

```
with tf.variable_scope("MyScope")
```

```
…
```

如果应用程序在 `with` 块内使用 `tf.get_variable` 创建变量，TensorFlow 将在变量名称前加上作用域的名称。也就是说，如果应用程序创建一个名为 `MyVar` 的新变量，则变量的完整名称将为 `MyScope/MyVar`。

[第 5 章](#09_9788126592555-ch05.xhtml) 解释了如何使用 `tf.Variable` 创建变量，但如果应用程序想在作用域内创建变量，则要调用的函数是 `tf.get_variable`：

