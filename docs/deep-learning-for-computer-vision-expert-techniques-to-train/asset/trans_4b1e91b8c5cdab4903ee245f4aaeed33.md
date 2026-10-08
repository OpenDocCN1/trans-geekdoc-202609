

# TensorFlow 库

TensorFlow 是一个用于深度学习模型开发和部署的开源库。TensorFlow 使用计算图进行数据流和数值计算。换句话说，数据（或张量，tensor）在图中流动，因此得名 TensorFlow。图中包含节点，这些节点可以实现任何数值计算，因此适用于深度学习操作。TensorFlow 为各种平台和硬件提供了单一的 API。它最初是为 Google 的研究开发的。它是最著名的深度学习库，拥有庞大的社区，并附带用于可视化和生产环境部署的工具。

# 安装 TensorFlow

使用以下命令通过 pip3 安装 CPU 版本的 tensorflow：

```bash
sudo pip3 install tensorflow
```

如果您正在使用 GPU 硬件并且已经安装了 CUDA 和 CUDNN，请使用以下命令安装 GPU 版本的 tensorflow：

```bash
sudo pip3 install tensorflow-gpu
```

现在 tensorflow 已经安装完毕并准备就绪。我们将尝试几个示例来理解 TensorFlow 的工作原理。

# 打印 Hello, TensorFlow 的 TensorFlow 示例

我们将直接在 Python Shell 中使用 TensorFlow 进行一个示例。在这个示例中，我们将使用 TensorFlow 打印 Hello, TensorFlow。

- 1. 在命令行提示符中输入以下内容从 Shell 启动 Python：

```bash
python3
```

- 2. 输入以下命令导入 tensorflow 库：

```python
>>> import tensorflow as tf
```

# 入门

- 3. 接下来，定义一个字符串为 Hello, TensorFlow 的常量。这与普通的 Python 赋值操作不同，因为该值尚未初始化：

```python
>>> hello = tf.constant('Hello, TensorFlow!')
```

- 4. 创建会话以初始化计算图，并给会话命名：

```python
>>> session = tf.Session()
```

可以使用变量 hello 作为参数运行会话。

- 5. 现在图执行并返回打印该特定变量的结果：

```python
>>> print(session.run(hello))
```

它应该打印以下内容：

Hello, TensorFlow!

让我们来看一个示例，理解会话和图是如何工作的。

> 访问 https://github.com/rajacheers/DeepLearningForComputerVision 获取书中介绍的所有示例代码。代码将按照章节进行组织。您可以在仓库中提出问题并寻求帮助。

# 两个数字相加的 TensorFlow 示例

这里是另一个使用 TensorFlow 进行加法的简单示例：

- 1. 创建一个 Python 文件并使用以下代码导入 tensorflow：

```python
import tensorflow as tf
```

前面的导入对于后续所有示例都是必要的。假设读者已为所有示例导入了该库。占位符可以如下定义。占位符在赋值时不会加载。在这里，定义了一个类型为 float32 的占位符。占位符是一个空声明，可以在运行会话时取值。

- 2. 现在我们按照下面的代码定义一个占位符：

```python
x = tf.placeholder(tf.float32)
y = tf.placeholder(tf.float32)
```

# 入门

- 3. 现在，占位符的相加操作可以定义为普通的加法。在这里，操作并没有执行，只是通过以下代码定义：

```python
z = x + y
```

- 4. 可以像上一个示例所示创建会话。当如下所示定义时，图准备好执行计算：

```python
session = tf.Session()
```

- 5. 以字典格式定义占位符的值：

```python
values = {x: 5.0, y: 4}
```

- 6. 使用变量 c 和值运行会话。图将值馈给相应的占位符，并获取变量 c 的值：

```python
result = session.run([z], values)
print(result)
```

该程序应该打印 [9.0] 作为加法的结果。

可以理解，这并不是两个两个数字的最佳方法。这个示例是为了理解在 TensorFlow 中如何定义张量和操作。想象一下使用一万个数字并将它们相加会有多困难。TensorFlow 能够通过相同的 API 轻松实现。在下一节中，我们将看到如何安装和使用 TensorBoard 以及 TensorFlow serving。

# TensorBoard

TensorBoard 是一套用于使用 TensorFlow 训练深度学习模型的可视化工具。以下数据可以在 TensorFlow 中可视化：

- 图：计算图、设备放置和张量详情
- 标量：如迭代过程中的损失（loss）、准确率（accuracy）等指标
- 图像：用于查看带有标签的图像

# 入门

- 音频：用于听训练音频或生成的音频
- 分布：用于查看某些标量的分布
- 直方图：包括权重和偏置的直方图
- 投影器：帮助可视化 3 维空间中的数据
- 文本：打印训练文本数据
- 性能：查看训练利用的硬件资源

Tensorboard 随 TensorFlow 一起安装。进入 python3 提示符并输入以下命令（类似于之前的示例），开始使用 Tensorboard：

```python
x = tf.placeholder(tf.float32, name='x')
y = tf.placeholder(tf.float32, name='y')
z = tf.add(x, y, name='sum')
```

注意，这里有一个参数。由于提供了占位符和操作的参数，可以看到图。在 TensorBoard 中，可以使用以下代码向特定文件夹写入图：

```python
session = tf.Session()
summary_writer = tf.FileWriter('/tmp/', session.graph)
```

此命令将图写入磁盘特定文件夹。现在可以使用以下命令启动 Tensorboard：

```bash
tensorboard --logdir=/tmp/
```

任何目录都可以作为参数传递。进入浏览器并粘贴以下 URL 访问 TensorBoard：

```
http://localhost:6006/
```

# 入门
# 第 1 章

浏览器应该显示如下：

![](img/48c861eac4dc634f2a09fdbe884beb_48_0)

加法图通过这些名称显示。当我们点击它们时，可以看到右侧操作的所有细节。熟悉该窗口中的选项卡和选项。我们将在不同的章节中学习它们。TensorBoard 是 TensorFlow 中最好的工具之一，这使其优于任何其他深度学习框架。

# TensorFlow Serving 工具

TensorFlow Serving 是 TensorFlow 开发的一个用于部署环境的工具，提供了高延迟和吞吐量。任何使用 TensorFlow 训练的深度学习模型都可以通过 serving 进行部署。运行以下命令安装 Serving：

```bash
sudo apt-get install tensorflow-model-server
```

# 入门

如何在图像检索中使用将在详细说明。注意 Serving 仅在 Ubuntu 上于安装；对于其他操作系统，请参考 https://www.tensorflow.org/serving/setup。下图展示了 TensorFlow Serving 和 TensorFlow 在生产环境中的交互方式：

![](img/48c861eac4dc634f2a09fdbe884beb_49_0)

许多模型可以通过训练过程产生，Serving 负责无缝切换它们而无需停机。TensorFlow Serving 并不是后续章节都需要的，第 3 章图像检索和第 10 章部署除外。

# Keras 库

Keras 是 Python 深度学习开源库。它提供了一个使用 TensorFlow 作为后端的简单接口。Keras 也可以用 Theano、deep learning 4j 或 CNTK 作为其后端。Keras 的设计目的是便于快速实验，专注于友好性、模块化可扩展性。它是一个自包含的框架，可以在 CPU 和 GPU 之间无缝运行。Keras 可以通过 TensorFlow 直接使用 tf.keras API 安装。在本书中，我们将使用 tf.keras API。我们已经看到了安装开发环境所需库的步骤。确保 CUDA、CUDNN、OpenCV、TensorFlow 和 Keras 安装并正常运行对于后续章节至关重要。

