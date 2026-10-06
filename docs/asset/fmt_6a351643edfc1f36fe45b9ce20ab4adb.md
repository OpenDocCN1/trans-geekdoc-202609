
![images](img/eq07014.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>y</m:mi><m:mrow><m:mo>(</m:mo><m:mrow><m:msub><m:mi>x</m:mi><m:mi>i</m:mi></m:msub></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>=</m:mo><m:msub><m:mi>f</m:mi><m:mn>2</m:mn></m:msub><m:mrow><m:mo>(</m:mo><m:mrow><m:msubsup><m:mi>w</m:mi><m:mrow><m:mn>00</m:mn></m:mrow><m:mn>1</m:mn></m:msubsup><m:msub><m:mi>f</m:mi><m:mn>0</m:mn></m:msub><m:mrow><m:mo>(</m:mo><m:mrow><m:msubsup><m:mi>w</m:mi><m:mrow><m:mn>00</m:mn></m:mrow><m:mn>0</m:mn></m:msubsup><m:msub><m:mi>x</m:mi><m:mn>0</m:mn></m:msub><m:mo>+</m:mo><m:msubsup><m:mi>w</m:mi><m:mrow><m:mn>10</m:mn></m:mrow><m:mn>0</m:mn></m:msubsup><m:msub><m:mi>x</m:mi><m:mn>1</m:mn></m:msub><m:mo>+</m:mo><m:msubsup><m:mi>w</m:mi><m:mrow><m:mn>20</m:mn></m:mrow><m:mn>0</m:mn></m:msubsup><m:msub><m:mi>x</m:mi><m:mn>2</m:mn></m:msub><m:mo>+</m:mo><m:msubsup><m:mi>w</m:mi><m:mrow><m:mn>30</m:mn></m:mrow><m:mn>0</m:mn></m:msubsup><m:msub><m:mi>x</m:mi><m:mn>3</m:mn></m:msub></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>+</m:mo><m:msubsup><m:mi>w</m:mi><m:mrow><m:mn>10</m:mn></m:mrow><m:mn>1</m:mn></m:msubsup><m:msub><m:mi>f</m:mi><m:mn>1</m:mn></m:msub><m:mrow><m:mo>(</m:mo><m:mrow><m:msubsup><m:mi>w</m:mi><m:mrow><m:mn>41</m:mn></m:mrow><m:mn>0</m:mn></m:msubsup><m:msub><m:mi>x</m:mi><m:mn>4</m:mn></m:msub><m:mo>+</m:mo><m:msubsup><m:mi>w</m:mi><m:mrow><m:mn>51</m:mn></m:mrow><m:mn>0</m:mn></m:msubsup><m:msub><m:mi>x</m:mi><m:mn>5</m:mn></m:msub><m:mo>+</m:mo><m:msubsup><m:mi>w</m:mi><m:mrow><m:mn>61</m:mn></m:mrow><m:mn>0</m:mn></m:msubsup><m:msub><m:mi>x</m:mi><m:mn>6</m:mn></m:msub></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow></m:math>

训练的目标是找到使 `y(x[i])` 尽可能接近观测数据的权重。换句话说，目标是最小化 `y(x[i])` 与观测数据之间的差异。如 第 5 章 和 第 6 章 中所讨论的，这种差异称为损失，而计算损失的一种流行方法是均方误差（MSE）。

如果你将 `y(x[i])` 设为一条简单的直线或多项式，你可以轻松计算损失并将其操作传递给优化器，例如 `GradientDescentOptimizer`。第 5 章 涵盖了不同的优化算法及其对应的 TensorFlow 类。

神经网络的模型更为复杂，因此损失并不那么容易计算。但在 1974 年，Paul Werbos 是第一个使用一种称为 *反向传播* 的方法优化神经网络权重的人。此后研究人员提出了其他训练神经网络的算法，但由于其简单性和速度，反向传播仍然是最流行的方法。

本质上，反向传播将 第 5 章 中的优化算法扩展到适用于神经网络。总体过程涉及六个步骤：

1. **初始化网络的权重。**

2. **对于输入集 `x[i]`，计算 `y(x[i])`。**

   该计算称为 *前向传播*。

3. **对于输入集 `x[i]`，确定损失。**

4. **对于每个权重，计算损失相对于该权重的偏导数。**

5. **使用步骤 4 中计算的偏导数更新网络中的每个权重。**

6. **返回步骤 2 并继续，直到损失的偏导数接近零。**

要了解反向传播如何计算偏导数，了解微积分的链式法则很有帮助。如果 `p(x) = f(g(x))`，则可以按以下方式表达 `p(x)` 的导数：

![images](img/eq07015.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>p</m:mi><m:mo>&#39;</m:mo><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow><m:mo>=</m:mo><m:mi>f</m:mi><m:mo>&#39;</m:mo><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>g</m:mi><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>)</m:mo></m:mrow><m:mi>g</m:mi><m:mo>&#39;</m:mo><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow></m:math>

反向传播将链式法则扩展到偏导数和涉及函数求和的导数。通过这种方式，该算法确定网络中每个权重相对于损失的偏导数。

值得庆幸的是，你无需担心偏导数或链式法则，因为 TensorFlow 会自动执行反向传播。但你需要创建反向传播将用于更新网络权重的优化器。

### 实现深度学习

在你对节点、权重以及神经网络的整体结构有了扎实理解之后，你就可以看到实际应用如何在代码中组合这些元素。`ch7/deep_learning.py` 模块演示了如何使用 TensorFlow 实现深度学习。

与 `the ch6/multi_regression.py` 模块类似，`ch7/deep_learning.py` 从 MNIST 数据集加载并对图像进行分类。但它没有使用逻辑回归，而是创建了一个由全连接层组成的神经网络。Listing 7-1 展示了代码。

#### LISTING 7-1 使用深度学习对图像进行分类

```
#### Read MNIST data
dataset = learn.datasets.mnist.read_data_sets('MNIST-data', one_hot=True)

#### Placeholders for MNIST images
img_holder = tf.placeholder(tf.float32, [None, 784])
lbl_holder = tf.placeholder(tf.float32, [None, 10])

#### Layer settings
hid_nodes = 200
out_nodes = 10

#### Define weights
w0 = tf.Variable(tf.random_normal([784, hid_nodes]))
w1 = tf.Variable(tf.random_normal([hid_nodes, hid_nodes]))
w2 = tf.Variable(tf.random_normal([hid_nodes, hid_nodes]))
w3 = tf.Variable(tf.random_normal([hid_nodes, out_nodes]))

#### Define biases
b0 = tf.Variable(tf.random_normal([hid_nodes]))
b1 = tf.Variable(tf.random_normal([hid_nodes]))
b2 = tf.Variable(tf.random_normal([hid_nodes]))
b3 = tf.Variable(tf.random_normal([out_nodes]))

#### Create layers
layer_1 = tf.add(tf.matmul(img_holder, w0), b0)
layer_1 = tf.nn.relu(layer_1)
layer_2 = tf.add(tf.matmul(layer_1, w1), b1)
layer_2 = tf.nn.relu(layer_2)
layer_3 = tf.add(tf.matmul(layer_2, w2), b2)
layer_3 = tf.nn.relu(layer_3)
out_layer = tf.matmul(layer_3, w3) + b3

#### Compute loss
loss = tf.reduce_mean(
 tf.nn.softmax_cross_entropy_with_logits(
 logits=out_layer, labels=lbl_holder))

#### Create optimizer
learning_rate = 0.01
num_epochs = 15
batch_size = 100
num_batches = int(dataset.train.num_examples/batch_size)
optimizer = tf.train.AdamOptimizer(learning_rate).minimize(loss)

#### Initialize variables
init = tf.global_variables_initializer()

#### Launch session
with tf.Session() as sess:
 sess.run(init)

 # Loop over epochs
 for epoch in range(num_epochs):

 # Loop over batches
 for batch in range(num_batches):
 img_batch, lbl_batch = dataset.train.next_batch(batch_size)
 sess.run(optimizer, feed_dict={img_holder: img_batch,
 lbl_holder: lbl_batch})

 # Determine success rate
 prediction = tf.equal(tf.argmax(out_layer, 1), tf.argmax(lbl_holder, 1))
 success = tf.reduce_mean(tf.cast(prediction, tf.float32))
 print('Success rate: ', sess.run(success,
 feed_dict={img_holder: dataset.test.images,
 lbl_holder: dataset.test.labels}))
```

该应用程序通过调用 `tf.Variable` 创建权重（`w`[`i`]) 和偏置（`b`[`i`])。然后它将输入值乘以权重并加上偏置。三个隐藏层中的每一个都通过调用 `tf.nn.relu` 对其输出进行校正。

最终层（`out_layer`）执行类似的乘法和加法，但它没有调用 `tf.nn.relu`，而是将输出传递给 `tf.nn.softmax_cross_entropy_with_logits`。该模块使用此输出为 MNIST 图像选择十个输出类别之一。

### 调优神经网络

前一节中的神经网络对于演示来说是合适的，但不适合专业应用。为了提高应用程序的准确性和处理速度，专业开发人员使用统称为 *调优* 的特殊例程。我喜欢称它们为四个“zations”：

* **输入标准化：** 预处理输入数据，使其在统计上与训练数据相似

* **权重初始化：** 获取初始权重的合适值

* **批归一化：** 在激活函数之前处理数据以降低饱和的可能性

* **正则化：** 降低过拟合的可能性

大多数开发人员都同意神经网络需要一定程度的调优，但很少有人同意最佳流程。与其选边站，我更专注于解释如何在 TensorFlow 应用程序中执行操作。

#### 输入标准化

机器学习应用程序应该能够分析从未见过的数据。但即使传入的数据完全是新的，它也应与应用程序的训练数据具有相同的均值和标准差。这种一致性可确保应用程序不会因数据集而感到困惑。

因此，开发人员经常转换输入数据以使均值等于 0，标准差等于 1。此操作称为 *标准化*，TensorFlow 的 `tf.nn` 包提供了两个有助于标准化的函数：`moments` 和 `batch_normalization`。

`moments` 返回一个包含张量轴中元素的均值和方差的元组。其签名如下：

`moments(x, axes, shift=None, name=None, keep_dims=False)`

要设置均值和方差，请将 `x` 分配给要分析的张量，将 `axes` 分配给标识张量轴的整数数组。如果将 `keep_dims` 设置为 `True`，返回的均值和方差将与输入张量具有相同的维度。

`batch_normalization` 接受张量的均值和方差并标准化张量的元素。其签名如下：

`batch_normalization(x, mean, variance, offset, scale, variance_epsilon, name=None)`

`offset` 参数向张量中的每个值添加一个常数，`scale` 将每个值乘以一个常数。`variance_epsilon` 标识要添加到分母的值，以确保 TensorFlow 不会除以零。应用程序经常将 `offset` 设置为 0.0，`scale` 设置为 1.0，`variance_epsilon` 设置为 0.0001。

例如，以下代码调用 `moments` 获取张量的均值和方差。然后它调用 `batch_normalization` 获取具有标准化数据的新的张量：

```
input_data = tf.constant([1., 3., 5., 7., 9.])
stat_mean, stat_var = tf.nn.moments(input_data, 0)
standard_data = tf.nn.batch_normalization(input_data, stat_mean, stat_var, 0., 1., 0.0001, name=None)
```

这将 `standard_data` 设置为 \[-1.4142, -0.7071, 0.0, 0.7071, 1.4142\]。该张量的均值为 0，标准差为 1。

#### 权重初始化

当我开始编写神经网络代码时，我没有考虑初始化权重——我只是将它们设置为小的随机值。研究人员已详细分析了这一主题，以下研究论文介绍了他们的研究成果：

* 1998 年：“Efficient BackProp” 由 Yann Lecun、Leon Bottou、Genevieve Orr 和 Klaus-Robert Muller 撰写

* 2010 年：“Understanding the Difficulty of Training Deep Feedforward Neural Networks” 由 Xavier Glorot 和 Yoshua Bengio 撰写

* 2015 年：“Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification” 由 Kaiming He、Xiangyu Zhang、Shaoqing Ren 和 Jian Sun 撰写

这些论文各自提出了不同的神经网络权重初始化方法。TensorFlow 通过提供 `tf.contrib.keras.initializers` 包中的函数来支持这些方法。每个函数都以相应方法的首席研究员命名，而 表 7-2 列出了其中五个可用的函数。

##### TABLE 7-2 权重初始化函数

| **函数** || **描述** |

| --- | --- |

| `lecun_uniform(seed=None)` || 返回介于 -sqrt(3/insize) 和 sqrt(3/insize) 之间的均匀分布值 |

| --- | --- |

| `glorot_uniform(seed=None)` || 返回介于 -sqrt(6/(insize+outsize)) 和 sqrt(6/(insize+outsize)) 之间的均匀分布值 |

| `glorot_normal(seed=None)` || 返回标准差为 sqrt(2/(insize+outsize)) 的正态分布值 |

| `he_uniform(seed=None)` || 返回介于 -sqrt(6/insize) 和 sqrt(6/insize) 之间的均匀分布值 |

| `he_normal(seed=None)` || 返回标准差为 sqrt(2/insize) 的正态分布值 |
