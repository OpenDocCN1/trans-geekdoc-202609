
![images](img/eq06016.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>l</m:mi><m:mi>o</m:mi><m:mi>s</m:mi><m:mi>s</m:mi><m:mo>=</m:mo><m:mo>&#45;</m:mo><m:msub><m:mi>y</m:mi><m:mi>i</m:msub></m:mi><m:mi>log</m:mi><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>h</m:mi><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>&#45;</m:mo><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>1</m:mn><m:mo>&#45;</m:mo><m:msub><m:mi>y</m:mi><m:mi>i</m:msub></m:mrow><m:mo>)</m:mo></m:mrow><m:mi>log</m:mi><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>1</m:mn><m:mo>&#45;</m:mo><m:mi>h</m:mi><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow></m:math>

该表达式及类似表达式在二元逻辑回归中常用。以下部分演示了如何在实际代码中使用逻辑函数和对数似然。

###### 将理论付诸实践

`ch6/binary_logistic.py` 中的代码使用 TensorFlow 执行二元逻辑回归。 Listing 6-3 展示了该代码。

LISTING 6-3 二元逻辑回归

```
#### Input values
N = 40
x = tf.lin_space(0., 5., N)
y = tf.constant([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.,
 1., 0., 0., 1., 0., 0., 0., 1., 0., 0.,
 1., 0., 1., 1., 1., 1., 1., 1., 1., 1.,
 1., 1., 1., 1., 1., 1., 1., 1., 1., 1.])

#### Variables
m = tf.Variable(0.)
b = tf.Variable(0.)

#### Compute model and loss
model = tf.nn.sigmoid(tf.add(tf.multiply(x, m), b))
loss = -1. * tf.reduce_sum(y * tf.log(model) + (1. - y) * (1. - tf.log(model)))

#### Create optimizer
learn_rate = 0.005
num_epochs = 350
optimizer = tf.train.GradientDescentOptimizer(learn_rate).minimize(loss)

#### Initialize variables
init = tf.global_variables_initializer()

#### Launch session
with tf.Session() as sess:
 sess.run(init)

 # Run optimizer
 for epoch in range(num_epochs):
 sess.run(optimizer)

 # Display results
 print('m =', sess.run(m))
 print('b =', sess.run(b))
```

该模块接受 Figure 6-3 中的数据点作为输入，并计算使数据点最好拟合到模型函数 ![images](img/eq06017.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>&#963;</m:mi><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>m</m:mi><m:mi>x</m:mi><m:mo>+</m:mo><m:mi>b</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow></m:math> 的 `m` 和 `b` 值。 Figure 6-5 描绘了计算得到的模型函数叠加在训练数据之上。

![FIGURE 6-5: After training, the sigmoid function approximates the experimental data.](img/9788126592555-fg0605.png)

FIGURE 6-5: 训练后，Sigmoid 函数近似实验数据。

在我系统上，计算得到的值为 m = 4 和 b = -13.5。`mx + b` 在 `x = 3.375` 时等于 0，因此当音量设置为 3.375 时达到 Sigmoid 函数的中心。

##### 多项逻辑回归：对数据进行多类别分类

许多机器学习应用需要将点分类到两个以上的类别中。这个过程称为多项式逻辑回归，它在许多方面与二元逻辑回归相似。主要区别在于它使用不同的函数来表示模型和损失。

为了介绍这个主题，我将解释如何使用 TensorFlow 来识别来自改良国家标准与技术研究所（MNIST）数据集的手写样本。每个图像都包含一个手写数字，属于十个类别之一。

###### 改良国家标准与技术研究所（MNIST）数据集

为了测试机器学习应用，国家标准与技术研究所（NIST）汇编了一组 0 到 9 之间数字的手写样本。Yann LeCun 创建了 NIST 图像的一个子集，称为改良 NIST（MNIST）数据库。

与 NIST 的样本不同，MNIST 的样本大小都相同，并且都居中到 28-x-28 图像中。每个像素以 0（白色）到 255（黑色）之间的无符号字节给出。每个图像都有一个对应的标签，用于标识手写数字（0 到 9）。

要运行多项式逻辑回归示例，您需要从 [`http://yann.lecun.com/exdb/mnist`](http://yann.lecun.com/exdb/mnist) 下载 MNIST 数据集。有四个文件可用：

* `train-images-idx1-ubyte.gz` — 训练图像

* `train-images-idx3-ubyte.gz` — 训练标签

* `t10k-labels-idx1-ubyte.gz` — 测试图像

* `t10k-images-idx3-ubyte.gz` — 测试标签

训练标签和测试标签标识了对应图像中书写的数字。例如，训练数据集中第六个标签是 8。 Figure 6-6 显示了训练数据集中第六个图像的样子。

![FIGURE 6-6: Each MNIST image contains a handwritten digit in a 28-x-28 pixel array.](img/9788126592555-fg0606.png)

FIGURE 6-6: Each MNIST image contains a handwritten digit in a 28-x-28 pixel array.

如果您解压缩一个 MNIST 文件，您会看到每个文件将其数据存储在单个数据结构中。幸运的是，您不需要了解这些结构，因为 TensorFlow 使访问 MNIST 数据变得容易。需要了解的函数是 `read_data_sets`，它由 `tensorflow.contrib.learn.datasets.mnist` 包提供：

`read_data_sets(train_dir, fake_data=False, one_hot=False, dtype=dtypes.float32, reshape=True, validation_size=5000, seed=None)`

当此函数执行时，它会在 `train_dir` 参数标识的目录中搜索四个 MNIST 归档文件。如果找不到任何文件，`read_data_sets` 将下载它们、解压缩它们并将它们存储在指定文件夹中。

要理解 `read_data_sets` 的其他参数，了解该函数的返回值非常重要，该值是 `Datasets` 类的一个实例。每个 `Datasets` 实例都有三个字段：

* `train` — 包含 MNIST 训练数据的 `Dataset`

* `validation` — 包含验证数据的 `Dataset`

* `test` — 包含用于测试的数据的 `Dataset`

很合适的是，`Datasets` 实例的每个字段都是 `Dataset` 类的一个实例。 Table 6-1 列出了该类的四个成员并提供了每个成员的描述。

TABLE 6-1 Members of the Dataset Class

| **Function** || **Description** |

| --- | --- |

| `images` || `ndarray` of images given as numpy arrays |

| --- | --- |

| `labels` || `ndarray` of category names for the images |

| `num_examples` || The number of examples in the dataset |

| `next_batch(batch_size, fake_data=False, shuffle=True)` || Returns the next batch of images |

前三个字段很直接。以下代码调用 `read_data_sets`，并为每个字段打印相应图像数组的形状：

```
import tensorflow.contrib.learn as learn

dset = learn.datasets.mnist.read_data_sets('MNIST-data')
print("Training images: ", dset.train.images.shape)
print("Validation images: ", dset.validation.images.shape)
print("Test images: ", dset.test.images.shape)
```

在我系统上，打印结果如下：

```
Training images: (55000, 784)
Validation images: (5000, 784)
Test images: (10000, 784)
```

如果您在 `read_data_sets` 中将 `one_hot` 设置为 `True`，则生成的 `Dataset` 的 `labels` 字段将包含 one-hot 向量。*one-hot 向量* 是一个一维数组，其中一个元素的值很高，其余都很低。默认情况下，高值是 1，低值是 0。如果将 `one_hot` 参数设置为 `True`，每个标签将作为一个包含十个元素的 one-hot 向量提供：数字标识位置为 1，其余位置为 0。

`Dataset` 类的 `next_batch` 方法以批量的形式提供 MNIST 数据。第一个参数设置每个批次的大小，第二个参数标识是否应生成假数据，最后一个参数指示是否应对 MNIST 数据进行洗牌。

###### 使用 softmax 函数定义模型

您可以使用 sigmoid 函数将点分类到两个类别中。 （有关更多信息，请参阅 “Defining models with the logistic function” 部分。）如果系统（例如 MNIST 分类）有超过两个类别，sigmoid 函数就不够用了。

相反，统计学家使用一种可以接受值数组并返回值数组的操作。这是 *softmax 函数*，它将 sigmoid 函数扩展到多个变量。softmax 函数的第 *j* 项表示为 ![images](img/eq06018.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>&#963;</m:mi><m:msub><m:mrow><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mi>j</m:mi></m:msub></m:mrow></m:math>，如果输入数组包含 N 个项，则可以使用以下方程计算 x[j] 的 softmax 函数：

![images](img/eq06019.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>&#963;</m:mi><m:msub><m:mrow><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mi>j</m:mi></m:msub><m:mo>=</m:mo><m:mfrac><m:mrow><m:msup><m:mi>e</m:mi><m:mrow><m:msub><m:mi>x</m:mi><m:mi>j</m:mi></m:msub></m:mrow></m:msup></m:mrow><m:mrow><m:mstyle displaystyle="true"><m:munderover><m:mo>&#8721;</m:mo><m:mrow><m:mi>i</m:mi><m:mo>=</m:mo><m:mn>0</m:mn></m:mrow><m:mrow><m:mi>N</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:munderover><m:mrow><m:msup><m:mi>e</m:mi><m:mrow><m:msub><m:mi>x</m:mi><m:mi>i</m:mi></m:msub></m:mrow></m:msup></m:mrow></m:mstyle></m:mrow></m:mfrac></m:mrow></m:math>

使用此函数时，您需要注意两点：

* 输出数组中的每个值都在 0 和 1 之间。

* 输出数组中值的总和始终等于 1。

在 TensorFlow 中，您可以通过调用 `tf.nn` 包中的 `softmax` 函数来执行 softmax 操作：

`softmax(input, dim=-1, name=None)`

默认情况下，`softmax` 函数的分母中会将输入张量的每个元素相加。但如果您设置 `dim` 参数，则只有指定维度中的值才会被包含在总和中。

一个例子将阐明此函数的工作方式。如果输入张量是 \[3.2, -2.6, 1.7, 0.0, 4.9\]，调用 `softmax` 将返回一个 5 元素张量等于 \[0.14835, 0.00045, 0.03310, 0.00605, 0.81205\]。您可以通过以下方式计算第一个 softmax 值：
