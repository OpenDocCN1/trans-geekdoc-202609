

SuggestedLRs(lr_min=0.00831763744354248, lr_steep=0.0012022644514217973)

![](img/d5454da46c702784893ef8b0b539e5b9_36_0.png)

## 选择一个具有高负斜率的学习率

```python
learn.fit_one_cycle(5, lr_max=(1e-3))
```

| epoch | train_loss | valid_loss | error_rate | time |
|---|---|---|---|---|
| 0 | 1.197415 | 0.257222 | 0.089986 | 00:48 |
| 1 | 0.480817 | 0.243021 | 0.084574 | 00:47 |
| 2 | 0.285627 | 0.192219 | 0.062246 | 00:47 |
| 3 | 0.159144 | 0.184564 | 0.053451 | 00:47 |
| 4 | 0.123560 | 0.187495 | 0.057510 | 00:47 |

因此，使用更大的模型架构，我们得到了更低的错误率 0.05。现在我们可以进行解冻和/或训练更多的轮次。

```python
learn.save('resnet50')
```

```text
Path('/home/bmayr/.fastai/data/oxford-iiit-pet/models/resnet50.pth')
```

同样，我们可以运行 `unfreeze()` 并重新训练整个模型

```python
learn.load('resnet50')
learn.unfreeze()
learn.fit_one_cycle(2, lr_max=4e-4)
```

| epoch | train_loss | valid_loss | error_rate | time |
|---|---|---|---|---|
| 0 | 0.800914 | 0.891309 | 0.264547 | 01:01 |
| 1 | 0.403630 | 0.329750 | 0.096752 | 01:00 |

```python
learn.save('resnet50-stage_2')
```

```text
Path('/home/bmayr/.fastai/data/oxford-iiit-pet/models/resnet50-stage_2.pth')
```

好吧，在这个大模型上只运行两个轮次的训练循环显然是不够的。如果我们想在生产环境中使用这个模型，我们需要训练更多的轮次。

不过，为了演示目的，该模型用最少的代码行数就能返回可接受的结果。

## 第 2 章：从零开始构建图像分类器

本章将指导你从零开始创建一个用于分类任务的深度学习模型。我们将构建自己的深度学习模型来识别手写数字。为了训练我们的分类器，我们将使用 MNIST 训练数据集。该数据集由手写数字的灰度图像组成。

你可以在维基百科上找到关于这个数据集的更多信息：[https://en.wikipedia.org/wiki/MNIST_database](https://en.wikipedia.org/wiki/MNIST_database)。我们将使用 fastai 中的 `URLs` 类来轻松下载所有 MNIST 数据。

现在从 fastai 导入视觉库并下载 MNIST 数据集。这次我们将使用 fastai 中最底层的 API 来访问数据。

```python
from fastai.basics import *
from fastai.vision.all import *
from fastai.callback.all import *

path = untar_data(URLs.MNIST)
```

我们只需将相应文件夹的名称分配给我们的 `GrandparentSplitter`。

创建拆分器后，我们可以使用这个拆分器对象将文件名划分为训练数据和验证数据。我们将得到一个包含两个列表的列表，一个包含训练数据文件夹的索引，另一个包含验证数据文件夹的索引。

```python
splitter = GrandparentSplitter(train_name='training',
                               valid_name='testing')
```

让我们重新检查一下！我们看到 `splits` 包含两个对象（训练集和验证集）。我们可以索引到列表中，并显示训练和验证的前三个元素。我们的拆分器使用索引 <60000 作为训练数据，>=60000 作为验证数据！

```python
splits = splitter(items)
print(len(splits))
print(splits[0][:3])
print(splits[1][:3])
```

```text
2
[0, 1, 2]
[60000, 60001, 60002]
```

下一步是创建一个 `DataSource` 对象。数据源需要以下值：

- 文件名
- 一些变换
- 训练和验证的拆分

### 我们所说的**变换**是什么意思？

在这个阶段，变换并不是指旋转、裁剪、缩放等图像变换。这些变换定义了我们的数据如何被加载到数据源中，以及如何获取我们的 y 值。因此，这个参数是一个包含两个项目的列表。这两个项目中的每一个都是一个列表，分别包含 x 和 y 值的变换。

对于我们的数据，我们想要：

- 获取 x 值并创建一个 `PILImage`（就像我们之前手动做的那样）
- 对于 y 值，从父文件夹获取标签并对所有标签进行分类

![](img/d5454da46c702784893ef8b0b539e5b9_42_0.png)

现在，我们想知道我们的模型期望什么样的输入尺寸。让我们获取一个批次并查看我们的 xs 和 ys 的形状。

```python
x_batch, y_batch = dataloaders.one_batch()
x_batch.shape, y_batch.shape, dataloaders.c
```

```text
(torch.Size([128, 1, 28, 28]), torch.Size([128]), 10)
```

这意味着我们的模型期望一个形状为 1x28x28 的张量输入。

这正好代表我们的黑白图像（记住，每个颜色一个通道——所以对于黑白图像只有 1 个通道），其**分辨率为 28x28 像素。** 之前我们定义了**批次大小为 128。**

一个批次的输出大小是 **128**，因为批次中的每张图像都有一个标签——每个批次总共有 128 个标签。

我们有多少个不同的 y 值？这由 `dataloaders.c`（c 代表类别）显示。那么我们有多少个不同的*类别*呢？是的，我们有 10 个不同的类别——每个数字一个。

### 2.2 创建模型

一个（深度）学习模型由不同的层组成。每一层只是一个矩阵乘法。经过若干层之后，我们应该得到给定的 y 标签。对于 MNIST 图像数据，我们将创建一个类似于引言章节中使用的 `cnn_learner` 对象的模型。

现在我们将使用这些类型的层：

- 卷积层，
- 批归一化层，
- 激活函数（ReLU）和
- 一个展平层作为顶层

#### 2.2.1 卷积层

卷积层在处理图像时表现出了良好的结果。你甚至可以将不同的数据转换为图像，并使用卷积层进行处理。例如，你为音乐文件创建频谱图，然后将这些频谱图当作图像来使用。

*Adit Deshpande* 对卷积层内部发生的事情做了很好的记录（参见：[卷积神经网络理解入门指南](https://adeshpande3.github.io/A-Beginner%27s-Guide-To-Understanding-Convolutional-Neural-Networks/)）。

卷积层的一个类比是手电筒，它只照亮黑暗房间中的一个点。手电筒从左到右、从上到下移动，扫描整个房间。然而，你一次只能看到一个点。

就卷积层而言，我们称这个手电筒为**滤波器**或**卷积核**。我们看到的被照亮的点称为**感受野**。

滤波器本身由一个浮点数数组组成——称为**权重**（有时也称为参数）。

请记住，滤波器的深度必须与输入的深度相同。在我们的示例中，我们使用一个颜色通道——所以深度为 1。

下一步是开始在图像的像素数组上移动滤波器。我们将这种移动定义为在图像上进行**卷积**。

在卷积过程中，滤波器将滤波器内的值与所照亮的感受野内的原始值相乘。在此过程中，滤波器进行逐元素乘法。

然后将所有这些乘法的结果相加。滤波器对图像中的所有像素重复此过程，最终得到一个**激活图**或**特征图**。

在我们的例子中（28x28 像素图像），这个特征图将有 784 个不同的位置，变成一个 28x28 的像素数组。

```python
def conv(number_input: int, number_filter: int) -> nn.Conv2d:
    return nn.Conv2d(number_input,
                     number_filter,
                     kernel_size=3,
                     stride=2,
                     padding=1)
```

#### 2.2.2 批归一化层

当张量通过模型传递时，我们希望它们被归一化。这将提高训练速度，并允许每一层独立学习，因为每一层都会根据其输出进行重新归一化。

```python
def batch_norm(number_filters: int) -> nn.BatchNorm2d:
    return nn.BatchNorm2d(number_filters)
```

#### 2.2.3 激活函数

激活函数用于为我们的模型提供非线性。激活函数在称为**反向传播**的步骤中与*权重*和*偏置*一起工作（我们将在后面的章节中介绍）。

这些函数负责我们模型的学习能力。激活函数可以激活（*返回正值*）或停用（*返回小于零的值*）我们层内的节点。

ReLU（或修正线性单元）简单地在输入值大于零时返回输入值，而对于所有小于或等于零的输入值返回零：[ReLU 和 Softmax 激活函数 – 修正线性单元](https://github.com/Kulbear/deep-learning-nano-foundation/wiki/ReLU-and-Softmax-Activation-Functions#rectified-linear-units)

```python
def relu() -> nn.ReLU:
    return nn.ReLU(inplace=False)
```

#### 2.2.4 展平层

最后一层将是展平层。为此，我们将简单地使用 `Flatten`。请记住，我们只需使用双问号即可显示任何函数的源代码：`??Flatten`。

```
??Flatten
```

#### 2.2.5 创建模型架构

我们将创建一个包含五个卷积层的模型——每个卷积层由一个卷积层、一个批归一化层和一个 ReLU 激活组成（最后一层除外）。

我们可以使用 `nn.Sequential` 来构建一个由我们预定义层组成的简单顺序模型。只需添加所有层。第一个卷积层有一个输入滤波器，输出大小为 8。因此，第二层必须具有

