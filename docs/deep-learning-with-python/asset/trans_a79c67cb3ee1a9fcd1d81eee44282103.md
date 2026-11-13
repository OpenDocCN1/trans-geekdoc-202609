

在 GPU 上进行深度学习，你有三种选择：

- 在工作站上购买并安装实体 NVIDIA GPU。
- 使用 Google Cloud 或 AWS EC2 上的 GPU 实例。
- 使用 Colaboratory 提供的免费 GPU 运行时，Colaboratory 是 Google 提供的托管笔记本服务（关于“笔记本”是什么的详细信息，请参见下一节）。

Colaboratory 是入门的最简单方式，因为它不需要购买硬件，也不需要安装软件——只需在浏览器中打开一个标签页并开始编码。这是我们推荐用于运行本书中代码示例的选项。但是，Colaboratory 的免费版本仅适用于小规模工作负载。如果你想扩展规模，则必须使用第一个或第二个选项。

如果你没有可用于深度学习的 GPU（近期的高端 NVIDIA GPU），那么在云端运行深度学习实验是一种简单、低成本的方式，可让你无需购买任何额外硬件即可转向更大规模的工作负载。如果你使用 Jupyter 笔记本进行开发，在云端运行的体验与在本地运行没有区别。

但是，如果你是深度学习的重度用户，这种设置从长远来看是不可持续的——甚至连几个月都撑不住。云实例并不便宜：2021 年中期，在 Google Cloud 上使用 V100 GPU 需要支付每小时 2.48 美元。同时，一款可靠的消费级 GPU 价格在 1,500 美元到 2,500 美元之间——这一价格随着时间的推移一直相当稳定，尽管这些 GPU 的规格在不断改进。如果你是深度学习的重度用户，考虑搭配一块或多块 GPU 的本地工作站。

此外，无论你是在本地还是在云端运行，最好都使用 Unix 工作站。虽然从技术上讲可以直接在 Windows 上运行 Keras，但我们不推荐这样做。如果你是 Windows 用户，并且想在自己的工作站上进行深度学习，让所有东西运行起来的最简单方案是在你的机器上设置 Ubuntu 双启动，或者利用 Windows Subsystem for Linux (WSL)——这是一个兼容层，可让你从 Windows 运行 Linux 应用程序。这看起来可能麻烦，但从长远来看能为你节省大量时间和麻烦。

### 3.4.1 Jupyter 笔记本：运行深度学习实验的首选方式

Jupyter 笔记本是运行深度学习实验的好方法——尤其是本书中的众多代码示例。它们在数据科学和机器学习社区中广泛使用。笔记本是由 Jupyter Notebook 应用（https://jupyter.org）生成的文件，你可以在浏览器中对其进行编辑。它将执行 Python 代码的能力与用于注释你正在做什么的富文本编辑功能相结合。笔记本还允许你将长实验分解为可以独立执行的较小片段，这使得开发具有交互性，并意味着如果实验后期出问题，你不必重新运行之前的所有代码。

我建议使用 Jupyter 笔记本来开始使用 Keras，尽管这不是强制性的：你也可以运行独立的 Python 脚本，或在 PyCharm 等 IDE 中运行代码。本书中的所有代码示例均以开源笔记本的形式提供；你可以从 GitHub 的 github.com/fchollet/deep-learning-with-python-notebooks 下载它们。

### 3.4.2 使用 Colaboratory

Colaboratory（简称 Colab）是一项免费的 Jupyter 笔记本服务，无需安装且完全在云端运行。实际上，它是一个网页，可让你立即编写和执行 Keras 脚本。它让你可以使用免费（但受限）的 GPU 运行时，甚至还可以使用 TPU 运行时，因此你不需要购买自己的 GPU。Colaboratory 是我们推荐用于运行本书中代码示例的服务。

#### 使用 Colaboratory 的初步步骤

要开始使用 Colab，请访问 https://colab.research.google.com 并单击新建笔记本按钮。你将看到图 3.2 所示的标准 Notebook 界面。

![](img/ab452ecf572a1f1372915be13bd8088f_97_0.png)

图 3.2 Colab 笔记本

你会注意到工具栏中有两个按钮：+ Code 和 + Text。它们分别用于创建可执行的 Python 代码单元和注释文本单元。在代码单元中输入代码后，按 Shift-Enter 将执行它（参见图 3.3）。

在文本单元中，你可以使用 Markdown 语法（参见图 3.4）。在文本单元上按 Shift-Enter 将呈现它。

文本单元用于为你的笔记本提供可读的结构：使用它们可以用章节标题和长说明段落来注释代码，或嵌入图形。笔记本旨在提供多媒体体验！

![](img/ab452ecf572a1f1372915be13bd8088f_98_0.png)

图 3.3 创建代码单元

![](img/ab452ecf572a1f1372915be13bd8088f_98_1.png)

图 3.4 创建文本单元

#### 使用 pip 安装软件包

默认的 Colab 环境已预装 TensorFlow 和 Keras，因此你可以立即开始使用，无需任何安装步骤。但是，如果你需要使用 pip 安装某些内容，可以在代码单元中使用以下语法（注意行首以 ! 开头，以指示这是 Shell 命令而非 Python 代码）：

```
!pip install package_name
```

#### 使用 GPU 运行时

要在 Colab 中使用 GPU 运行时，请在菜单中选择 Runtime > Change Runtime Type，并将 Hardware Accelerator 设置为 GPU（参见图 3.5）。

![](img/ab452ecf572a1f1372915be13bd8088f_99_0.png)

图 3.5 在 Colab 中使用 GPU 运行时

如果可用 GPU，TensorFlow 和 Keras 会自动在 GPU 上执行，因此选择 GPU 运行时后，你无需再做其他操作。

你会注意到，在该 Hardware Accelerator 下拉菜单中还有一个 TPU 运行时选项。与 GPU 运行时不同，使用 TensorFlow 和 Keras 的 TPU 运行时确实需要在代码中进行一些手动设置。我们将在第 13 章中介绍这一点。目前，我们建议你继续使用 GPU 运行时来跟随本书中的代码示例。

现在你有了一种开始实际运行 Keras 代码的方法。接下来，让我们看看第 2 章中学到的关键思想如何转化为 Keras 和 TensorFlow 代码。

## 3.5 TensorFlow 初步

如前几章所示，训练神经网络围绕以下概念展开：

- 首先，低级张量操作——支撑所有现代机器学习的基础设施。这对应于 TensorFlow API：
  - 张量，包括存储网络状态（变量）的特殊张量
  - 张量操作，例如 addition、relu、matmul
  - 反向传播，一种计算数学表达式梯度的方法（在 TensorFlow 中通过 GradientTape 对象处理）
- 其次，高级深度学习概念。这对应于 Keras API：
  - 层，它们被组合成一个模型
  - 损失函数，定义用于学习的反馈信号
  - 优化器，决定学习如何进行
  - 用于评估模型性能的指标，例如 accuracy
  - 执行小批量随机梯度下降的训练循环

在前一章中，你已经初步接触了一些相应的 TensorFlow 和 Keras API：你简要使用过 TensorFlow 的 Variable 类、matmul 操作和 GradientTape。你已实例化 Keras Dense 层，将它们打包到 Sequential 模型中，并使用 fit() 方法训练了该模型。

现在，让我们深入探讨如何使用 TensorFlow 和 Keras 在实践中处理所有这些不同的概念。

### 3.5.1 常量张量和变量

要在 TensorFlow 中做任何事情，我们都需要一些张量。张量需要使用某个初始值来创建。例如，你可以创建全一或全零张量（参见清单 3.1），或从随机分布中取值的张量（参见清单 3.2）。

#### 清单 3.1 全一或全零张量

```
>>> import tensorflow as tf
>>> x = tf.ones(shape=(2, 1))
>>> print(x)
tf.Tensor(
[[1.]
 [1.]], shape=(2, 1), dtype=float32)
>>> x = tf.zeros(shape=(2, 1))
>>> print(x)
tf.Tensor(
[[0.]
 [0.]], shape=(2, 1), dtype=float32)
```

#### 清单 3.2 随机张量

```
>>> x = tf.random.normal(shape=(3, 1), mean=0., stddev=1.)
>>> print(x)
tf.Tensor(
[[-0.14208166]
 [-0.95319825]
 [ 1.1096532 ]], shape=(3, 1), dtype=float32)
>>> x = tf.random.uniform(shape=(3, 1), minval=0., maxval=1.)
>>> print(x)
tf.Tensor(
