

如果你有一个单元素张量，例如，通过将张量的所有值聚合为一个值，你可以使用 `item()` 将其转换为 Python 数值：

```
agg = tensor.sum()

agg_item = agg.item()

print(agg_item, type(agg_item))
```

输出：

```
12.0 <class 'float'>
```

### [原地操作](#toc.xhtml#zs07)

将结果存储在操作数中的操作称为原地操作。它们由 `_` 后缀表示。例如：`x.copy_(y)`、`x.t_()` 会更改 `x`。

以下代码行首先显示张量的内容，然后将张量中每个元素增加 5 并显示更新后的张量：

```
print(f"{tensor} \n")

tensor.add_(5)

print(tensor)
```

输出：

```
tensor([[1., 0., 1., 1.],
[1., 0., 1., 1.],
[1., 0., 1., 1.],
[1., 0., 1., 1.]])

tensor([[6., 5., 6., 6.],
[6., 5., 6., 6.],
[6., 5., 6., 6.],
[6., 5., 6., 6.]])
```

### [与 NumPy 桥接](#toc.xhtml#zs08)

PyTorch 允许其张量与 NumPy 数组之间无缝转换，使数据操作和科学计算的互操作性无需昂贵的数据复制。

CPU 上的张量和 NumPy 数组可以共享其底层内存位置；更改其中一个会更改另一个。

### [张量转 NumPy 数组](#toc.xhtml#zs09)

将 PyTorch 张量转换为 NumPy 数组可以让你从 PyTorch 的数据结构切换到 NumPy 的数据结构，从而更容易使用广泛的科学计算工具。

以下代码行首先创建张量，显示其内容，然后将其转换为 NumPy 并显示 NumPy 数组。

```
t = torch.ones(5)

print(f"t: {t}")

n = t.numpy()

print(f"n: {n}")
```

输出：

```
t: tensor([1., 1., 1., 1., 1.])

n: [1. 1. 1. 1. 1.]
```

张量的变化会反映在 NumPy 数组中，如下面的代码所示：

```
t.add_(1)

print(f"t: {t}")

print(f"n: {n}")
```

输出：

```
t: tensor([2., 2., 2., 2., 2.])

n: [2. 2. 2. 2. 2.]
```

### [NumPy 数组转张量](#toc.xhtml#zs10)

将 NumPy 数组转换为 PyTorch 张量会更改其格式，以便将其与 PyTorch 的深度学习工具和操作集成到神经网络工作流中。

以下代码行首先创建 NumPy 数组，然后将其转换为张量并显示 NumPy 数组和张量。

```
n = np.ones(5)

t = torch.from_numpy(n)
```

NumPy 数组的变化会反映在张量中。

```
np.add(n, 1, out=n)

print(f"t: {t}")

print(f"n: {n}")
```

输出：

```
t: tensor([2., 2., 2., 2., 2.], dtype=torch.float64)

n: [2. 2. 2. 2. 2.]
```

## [数据集和数据加载](#toc.xhtml#zh27)

PyTorch 提供多个预加载的数据集，并实现特定于特定数据的函数。这些数据集可用于原型设计和基准测试 ML 模型。

它提供不同类型的数据集，如下所示：

• 图像数据集：

○ 图像分类数据集

○ 图像分割数据集

○ 光流数据集

○ 立体匹配

○ 图像对

○ 图像字幕

○ 视频分类

○ 视频预测

• 文本数据集：

○ 文本分类

○ 语言建模

○ 机器翻译

○ 序列标注

○ 问答

○ 无监督学习

• 音频数据集：

○ 语音识别

○ 声音分类

### [加载数据集](#toc.xhtml#zs11)

在 PyTorch 中，加载数据集是指以结构化方式设置数据，使其准备好用于训练或测试 ML 模型。此过程始于确定数据所在的位置，可能是计算机上的文件或远程数据库。然后将数据组织到 `Dataset` 对象中，这是 PyTorch 的一种构造，用于标准化数据的格式化和访问方式。最后，通常会使用 `DataLoader`，它接收 `Dataset` 并便于以可管理的块或批次迭代数据。这对于高效训练至关重要，因为它允许在不使系统内存不堪重负的情况下进行无缝的数据操作和迭代。

以下是如何从 `torchvision` 加载 FashionMNIST 数据集的示例。FashionMNIST 是 Zalando 的商品图片数据集，包含 60,000 个训练示例和 10,000 个测试示例。

```
import torch

from torch.utils.data import Dataset

from torchvision import datasets

from torchvision.transforms import ToTensor

import matplotlib.pyplot as plt

training_data = datasets.FashionMNIST(

root="data",

train=True,

download=True,

transform=ToTensor()

)

test_data = datasets.FashionMNIST(

root="data",

train=False,

download=True,

transform=ToTensor()

)
```

此代码片段用于加载 FashionMNIST 数据集，该数据集是一组与时尚相关的图片，用于图像识别任务中 ML 模型的训练和测试：

• `from torchvision import datasets`：从 `torchvision` 导入 `datasets` 模块，该包提供用于在 PyTorch 中处理图像数据的实用程序。

• `from torchvision.transforms import ToTensor`：导入 `ToTensor` 转换，它将图像转换为 PyTorch 张量，即 PyTorch 中用于计算的核心数据结构。

• `import matplotlib.pyplot as plt`：导入 `matplotlib.pyplot` 模块，这是 Python 中的绘图库，通常用于可视化数据（包括图像）。

• `training_data` 赋值创建一个用于训练模型的 FashionMNIST 数据集实例。它指定：

○ `root="data"`：存储或获取数据集的本地目录。

○ `train=True`：指示此数据集将用于训练模型。

○ `download=True`：如果指定目录中不存在数据集，则将从互联网下载。

• `transform=ToTensor()`：对数据集中的每个图像应用 `ToTensor` 转换，将它们从 PIL 图像或 NumPy 数组转换为 PyTorch 张量。

• 同样，`test_data` 赋值创建一个用于测试目的的 FashionMNIST 数据集实例。主要区别在于 `train=False` 指定此数据集用于测试，而非训练。

### [迭代和可视化数据集](#toc.xhtml#zs12)

在 PyTorch 中，迭代和可视化数据集涉及逐个遍历数据集中的项目并显示这些项目（通常是图像），以便你查看它们的外观。此过程有助于更好地了解数据，并确保在开始训练模型之前数据格式正确。

我们可以像列表一样手动索引数据集：`training_data[index]`。我们使用 `matplotlib.pyplot` 可视化训练数据中的一些样本。

请参阅以下代码：

```
labels_map = {

0: "T-Shirt",

1: "Trouser",

2: "Pullover",

3: "Dress",

4: "Coat",

5: "Sandal",

6: "Shirt",

7: "Sneaker",

8: "Bag",

9: "Ankle Boot",

}

figure = plt.figure(figsize=(8, 8))

cols, rows = 3, 3

for i in range(1, cols * rows + 1):

sample_idx = torch.randint(len(training_data), size=(1,)).item()

img, label = training_data[sample_idx]

figure.add_subplot(rows, cols, i)

plt.title(labels_map[label])

plt.axis("off")

plt.imshow(img.squeeze(), cmap="gray")

plt.show()
```

显示 FashionMNIST 中图像的输出：

![](images/Figure_2.2.png)

## [转换](#toc.xhtml#zh28)

几乎所有现实世界的数据集在训练 ML 算法之前都需要进行数据转换。PyTorch 函数 `transforms` 可用于操作数据并使其适合训练。

所有 TorchVision 数据集都有两个参数 `-transform` 用于修改特征，`target_transform` 用于修改标签。`torchvision.transforms` 模块提供了几种开箱即用的常用转换。

FashionMNIST 的特征为 PIL 图像格式，标签为整数。对于训练，我们需要将特征转换为归一化张量，将标签转换为 one-hot 编码张量。要进行这些转换，我们使用 `ToTensor` 和 `Lambda`。

请参阅以下代码：

```
import torch

from torchvision import datasets

from torchvision.transforms import ToTensor, Lambda

ds = datasets.FashionMNIST(

root="data",

train=True,

download=True,

transform=ToTensor(),
```

