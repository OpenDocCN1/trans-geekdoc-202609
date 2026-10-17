
Pascanu, R., Molchanov, S., Groy, R. L., Bengio, Y., & Courville, A. (2015). Malware classification with recurrent networks. In 2015 IEEE International Conference on Acoustics, Signal Processing (ICASSP) (pp. 1916–1920). 10.1109/ICASSP.2015.8

Paszke, A., Gross, S., Chintala, S., & Bradbury, J. (2019). PyTorch: An intuitive way to deep learning.

Perone, C., Salavia, A., & Fergus, P. (2018). Droid-sec: Deep learning in android malware detection. Zenodo. 10.5281/zenodo.149535

Ravenelli, M., Colotte, T., & Marines, M. (2019). PyTorch-kaldi. In 2019 IEEE International Conference on Acoustics, Signal Processing (ICASSP) (pp. 6465–6469). 10.1109/ICASSP.2019.86837

Rumelhart, D. E., Hinton, G. E., & Williams, R. J. (1988). Learning representations by back-propagating errors. Cognitive Modeling, 5(3), 1.

Sutskever, I., Vinyals, O., & Le, Q. V. (2014). Sequence to sequence learning with neural networks. In Advances in neural processing systems (pp. 3104–3112).

de Leeumpt, S. C., Teuwen, J., & Manningies, R. (2018). MemCNN: a Framework for Developing Memory Efficient Deep Neural Networks.

Yuan, Z., Lu, Y., Wang, Z., & Xue, Y. (2014, August). Droid-sec: Deep learning in android malware detection. Computer Communication Review, 44(4), 371–372. doi:10.1145/2740070.2631434

Zeiler, M. D., & Fergus, R. (2014, September). Visualizing and understanding convolutional networks. In European conference on computer vision (pp. 818-833).

Shoham, Y. (2018). The AI Index Annual Report. AI Index Steering Committee, Human-Centered AI, Stanford University. Available at http://cdn.aiindex.org/2018/AI%20Index%20Annual%20Report.pdf

Yes you should understand backprop. (n.d.). Karpathy. 2019年检索于 https://medium.com/@karpathy/yes-you-should-understand-backprop-e2f06eab49b

# 第 4 章

# 使用 TensorFlow 进行深度学习

Shahina Anwar

印度石油与能源研究大学 (UPES) 计算机科学学院系统系

Deepa Joshi

印度石油与能源研究大学 (UPES) 计算机科学学院系统系

## 摘要

本章旨在让用户熟悉 TensorFlow 的关键点以及关于深度学习的一些基本概念。特别是，用户将学会如何在 TensorFlow 中进行基础计算，以及如何使用 TensorFlow 实现深度学习。本章旨在为复杂的 Google TensorFlow 框架提供一份易于理解的直观手册。此外还将讨论 TensorFlow 的安装和设置的基本步骤。从一个简单的“Hello World”示例开始，将使用 MNIST 数据集讨论识别手写数字的深度学习实际实现。只有通过大量的实践示例，才能真正理解深度学习。因此，作者们包含了深度学习的实际实现，以激励读者深入研究这些示例，并尝试用自己的想法使用 TensorFlow 尝试不同的操作，因为仅仅在理论上理解算法是远远不够的。

### 深度学习

深度学习是人工智能（AI）中机器学习的一个子集，如图 1 所示，它具有能够在监督、无监督或半监督模式下学习的网络。它也被称为深层结构化学习和层次学习（Jason）。深度学习的核心组件是神经网络。大多数深度学习模型都基于人工神经网络。卷积神经网络由单个输入层、单个隐藏层和一个输出层组成。深度学习网络与这些卷积神经网络不同，如图 2 所示，它们包含更多的隐藏层。它们具有更大的深度，这就是深层网络的原因。这类网络擅于从未标记和无结构数据中探索隐藏结构。

DOI: 10.4018/978-1-7998-3095-5.ch004

# 使用 TensorFlow 进行深度学习

图 1. 人工智能、机器学习与深度学习之间的关系

![](img/c5cbbc72cd5e7b9be32079eac36d685c_116_0.png)

图 2. a) 传统神经网络，b) 深度神经网络

![](img/c5cbbc72cd5e7b9be32079eac36d685c_116_1.png)

## TENSORFLOW

本章题为“使用 TensorFlow 进行深度学习”，重点介绍了 TensorFlow。它是 Google 开发的用于实现深度学习的最优秀软件库之一。该框架用于使用带有节点和边的数据流图进行数值计算。TensorFlow 本身并无特殊，它只是一个带有变体的 numpy。如果你以前用过 numpy，那么使用 TensorFlow 将非常简单。numpy 和 TensorFlow 之间的巨大区别在于 TensorFlow 追求一种易于理解的编程范式。它可以完成所有在 numpy 中通常能做的所有事情！它实际上被称为“加强版的 numpy”，

### 为什么选择 TensorFlow？

目前有许多库可以实现深度学习，那么为什么选择 TensorFlow 呢？

以下是 TensorFlow 提供的特性：

- 它同时提供 Python 和 C++ API，使得工作起来非常方便。

- 它支持 CPU 和 GPU 计算设备。

- 它的编译时间比 Keras 或 Torch 等其他深度学习库更快。

在图 3 中，Chollet (2015) 明确提到，工业界和研究界对 TensorFlow 库的采用率最高，在 2018 年的功率评分高达 96.77%。

图 3. 深度学习框架 (Chollet, 2015)

![](img/c5cbbc72cd5e7b9be32079eac36d685c_117_0.png)

### TENSOR（张量）

张量是更高维向量和矩阵的泛化。它是深度学习中表示数据的标准方式。简单来说，张量是具有不同维度秩（rank）的数据矩阵或数组，作为神经网络的输入。图 4 和图 5 分别代表张量的不同维度和秩。

张量的秩：它定义为张量所在的维度数量。

```
# Rank 0 等于标量
# Rank 1 等于向量
# Rank 2 等于 2D 矩阵
# Rank 3 等于 3D 矩阵
```

# 使用 TensorFlow 进行深度学习

图 4. 张量的不同维度；1 维张量、2 维张量、3 维张量

![](img/c5cbbc72cd5e7b9be32079eac36d685c_118_0.png)

图 5. 张量的秩：Rank 0，Rank 1，Rank 2，Rank 3

![](img/c5cbbc72cd5e7b9be32079eac36d685c_118_1.png)

## 张量的秩

TensorFlow 库包含两个部分：

- 1) Tensor（张量）：用于将数据转换为数值表示的形式以进行计算。

- 2) Flow（流）：描述操作的流。

### 数据流图

计算图或数据流图是如图 6 所示的由节点和边构成的 TensorFlow 操作序列（TensorFlow, 2016）。它由两种对象组成：

- `tf.Operation`：计算图中的节点表示操作。它定义了消耗和生成张量的计算。

- `tf.Tensor`：计算图中的边表示值（张量），这些值将在操作的图中传递。

图 6. 数据流图 (TensorFlow, 2016)

![](img/c5cbbc72cd5e7b9be32079eac36d685c_119_0.png)

## TENSORFLOW 编码基础

TensorFlow 程序的主要对象是用于操作和传递的 `tf.Tensor`。`tf.Tensor` 具有以下特征：

- 数据类型（例如 int32、float32 或字符串）

- 形状（shape）

张量中每个元素的数据类型应该是相同的且总是已知的。形状（即维度的数量和每个维度的大小）可能是部分已知的。以下是一些特殊的张量类型将在下一节中讨论：

- `tf.Variable`

- `tf.constant`

- `tf.placeholder`

TensorFlow 核心程序由两个不同部分组成：

- 构建计算图

- 运行计算图

**构建计算图（使用 `tf.Graph`）：** TensorFlow 使用数据流图或计算图来表示操作之间的关联。在这一步中，`tf.constant(32.0)` 创建一个产生 32.0 的操作并添加到图中，返回一个表示该常量的 `tf.Tensor`。

通过 Python 代码来理解。这里 `a` 和 `b` 是两个浮点数常量：

图 7. 添加两个 TensorFlow 常量的 Python 代码

```
import tensorflow as tf
a = tf.constant(3.0, dtype=tf.float32)
b = tf.constant(4.0) # 也是 tf.float32
total = a + b
print(a)
print(b)
print(total)
```

上述代码的输出为：

图 8.

```
Tensor("Const:0", shape=(), dtype=float32)
Tensor("Const_1:0", shape=(), dtype=float32)
Tensor("add:0", shape=(), dtype=float32)
```

注意，上述张量并没有打印出预期的 3.0、4.0 和 7.0。它只是构建了计算图。每个操作都被分配了一个唯一的名称。这个名称与分配给 Python 的名称无关。

**运行计算图（使用 `tf.Session`）：** 在 TensorFlow 中，一切必须在会话中运行。我们需要显式告诉程序在 TensorFlow 会话中运行命令或对象。通过两种通过会话运行时运行计算图：

### 方法 1

图 9.

```
import tensorflow as tf
hello_constant=tf.constant('Hello World')

#运行 session
with tf.Session() as sess:
output=(sess.run(hello_constant).decode())
print(output)
```

Hello World

### 方法 II

如果我们通过这种特定方式指定会话，那么必须在结束时显式关闭会话。如果不关闭会话，在运行时提供结果可能会出现问题。

基于 TensorFlow 的深度学习

图 10. 模型 II

```
import tensorflow as tf
hello_constant=tf.constant('Hello World')

#运行会
sess=tf.Session()
print(sess.run(hello_constant))
sess.close()
```

b'Hello World'

### TensorFlow 中的数据类型

TensorFlow 中有三种数据：

- 1) 常量 (Constant)

- 2) 占位符 (Placeholder)

- 3) 变量 (Variable)

**常量 (Constant):** 如果数据对象指定为常量，那么它的值在整个程序中将保持不变。我们使用 `tf.constant()` 命令来定义常量。

**示例：** 两个常量相乘（图 11）

**占位符 (Placeholder):** 占位符用于将数据分配 TensorFlow 图。我们使用 `tf.placeholder()` 命令来定义占位符。占位对象的最终值将始终使用 `feed_dict`（喂送字典）进行赋值。

**示例：** 两个占位符相加（图 12）

**变量 (Variable):** 它允许我们向计算图中添加可训练的参数。我们使用 `tf.Variable()` 命令来定义变量。在此类数据中，初始可以分配任何值，但在程序过程中，值会根据需要更改。每我们将值赋值给 TensorFlow 变量时，都需要使用 `tf.global_variables_initializer()` 函数来初始化变量。

# 在 Anaconda 分发版中安装 TensorFlow

# 通用考虑

- 1) 安装哪种版本的 TensorFlow 取决于你想在 CPU 还是 GPU 上运行 TensorFlow（如果你有自己的 Nvidia 显卡）。

# 基于 TensorFlow 的深度学习

图 11.

```
#示例：两个常量相乘
#导入 tensorflow 库
import tensorflow as tf
#初始化 TensorFlow 常量
a=tf.constant(4.0)
b=tf.constant(5.0)
c="a+b"

#运行会
sess=tf.Session()
print(sess.run(c))
sess.close()
```

20.0

图 12.

```
#示例：占位符
#导入 tensorflow 库
import tensorflow as tf
na=tf.placeholder(tf.float32)
b=tf.placeholder(tf.float32)
add=a+b

#运行会
sess=tf.Session()
print(sess.run(add,feed_dict={a:[1,2,7], b:[3,20,2]}))
```

- [ 4. 22. 0.]

图 13.

```
#示例：变量
#导入 tensorflow 库
import tensorflow as tf

#为 TensorFlow 变量赋值
W=tf.Variable([0.5], tf.float32)
#重要：需要运行下面的代码来初始化变量
init=tf.global_variables_initializer()

#运行会
sess=tf.Session()
sess.run(init)
print(sess.run(W))
```

[0.5]

# 基于 TensorFlow 的深度学习

- 2) 如果你想在机器上同时安装两个变体版本的 TensorFlow，建议创建一个不同的（虚拟）环境。如果不创建虚拟环境，结果将失败，或者在你开始运行代码时，将始终不确定正在使用哪个版本来执行你的代码。

# 安装步骤

步骤 1：第一步是安装 Anaconda Python 3.7。这是可选的，任何 python 框架都可以使用，但作者建议使用 Anaconda，因为它在管理包和设置新虚拟环境方面非常直观。Anaconda 分发版可以从给定链接下载：https://www.anaconda.com/download/

步骤 2：安装 TensorFlow CPU

它运行在你机器的 CPU 上。在某些情况下，你会感觉到性能与 TensorFlow GPU 相比有所下降。可以通过 3 个简单的步骤完成：

## 2. 1 创建一个新的虚拟环境（可选）

- a) 打开 Anaconda/ Prompt 窗口

图 14.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_124_0.png)

- b) 输入下方提供的命令：

图 15.

```
(base) C:\Users\sanwarul>conda create -n tensorflow_cpu mlpip python=3.6
```

上述命令将创建一个名为 `tensorflow_cpu` 的新虚拟环境

- c) 使用以下命令激活创建的虚拟环境：

图 16.

```
选择 Anaconda Prompt - python
(base) C:\Users\sanwarul>conda activate tensorflow_cpu
```

- d) 激活虚拟环境后，环境名称将显示在括号内的 cmd 路径指定符开头：

图 17.

```
选择 Anaconda Prompt - python
(tensorflow_cpu) C:\Users\sanwarul>python
```

## 2. 为 Python 安装 TensorFlow CPU

- a) 打开 Anaconda/ Prompt 窗口并激活 `tensorflow_cpu` 环境（如果你之前还没有这样做的话）。

- b) 在 cmd 上输入以下命令并等待安装完成。

图 18.
