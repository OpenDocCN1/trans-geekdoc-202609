

## [构建神经网络模型](#toc.xhtml#zh29)

`torch.nn` 命名空间提供了构建神经网络所需的所有构建块。PyTorch 中的每个模块都继承自 `nn.Module`。神经网络是一个由其他模块（层）组成的模块。这种嵌套结构使得构建和管理复杂架构变得容易。

在以下部分中，我们将构建一个神经网络来对 FashionMNIST 数据集中的图像进行分类。

请参阅以下代码：

```python
import os

import torch

from torch import nn

from torch.utils.data import DataLoader

from torchvision import datasets, transforms
```

### [获取训练设备](#toc.xhtml#zs13)

如果可用，我们希望在 GPU 或 MPS 等硬件加速器上训练模型。让我们检查 `torch.cuda` 或 `torch.backends.mps` 是否可用；否则，我们使用 CPU。

```python
device = (
    "cuda"
    if torch.cuda.is_available()
    else "mps"
    if torch.backends.mps.is_available()
    else "cpu"
)

print(f"Using {device} device")
```

这段代码片段是关于根据系统的硬件可用性设置 PyTorch 操作的计算设备。它使用条件表达式来选择设备。

设备可以是 GPU（使用 CUDA 或 MPS）或 CPU：

• 如果 CUDA 可用，`device` 设置为 `cuda`。

• 如果 CUDA 不可用，它会检查 MPS 可用性。Metal Performance Shaders (MPS) 是 Apple 框架，用于在 Mac 设备上使用 GPU 加速。如果 MPS 可用，设备设置为 `mps`。

• 如果 CUDA 和 MPS 都不可用，它默认通过将 `device` 设置为 `cpu` 来使用 CPU 进行计算。

总之，此代码按以下优先级自动为 PyTorch 选择最佳可用计算设备：CUDA GPU、MPS GPU，然后是 CPU，并打印出所选设备。

### [定义类](#toc.xhtml#zs14)

我们通过继承 `nn.Module` 来定义神经网络，并在 `__init__` 中初始化神经网络层。每个 `nn.Module` 子类都在 `forward` 方法中实现对输入数据的操作。

请参阅以下代码：

```python
class NeuralNetwork(nn.Module):

    def __init__(self):

        super().__init__()

        self.flatten = nn.Flatten()

        self.linear_relu_stack = nn.Sequential(

            nn.Linear(28*28, 512),

            nn.ReLU(),

            nn.Linear(512, 512),

            nn.ReLU(),

            nn.Linear(512, 10),

        )

    def forward(self, x):

        x = self.flatten(x)

        logits = self.linear_relu_stack(x)

        return logits
```

我们创建 `NeuralNetwork` 的实例，并将其移动到设备，并打印其结构，如下所示：

```python
model = NeuralNetwork().to(device)

print(model)
```

输出：

```
NeuralNetwork(
  (flatten): Flatten(start_dim=1, end_dim=-1)
  (linear_relu_stack): Sequential(
    (0): Linear(in_features=784, out_features=512, bias=True)
    (1): ReLU()
    (2): Linear(in_features=512, out_features=512, bias=True)
    (3): ReLU()
    (4): Linear(in_features=512, out_features=10, bias=True)
  )
)
```

要使用模型，我们将输入数据传递给它。这将执行 `model.forward`，以及一些后台操作。不要直接调用 `model.forward()`！

在输入上调用模型会返回一个 2 维张量，其中 `dim=0` 对应每个类的 10 个原始预测值，`dim=1` 对应每个输出的单独值。我们通过将它们传递给 `nn.Softmax` 模块的实例来获取预测概率。

```python
X = torch.rand(1, 28, 28, device=device)

logits = model(X)

pred_probab = nn.Softmax(dim=1)(logits)

y_pred = pred_probab.argmax(1)

print(f"Predicted class: {y_pred}")
```

输出：

```
Predicted class: tensor([4], device='mps:0')
```

上面的代码片段演示了如何在 PyTorch 中使用训练好的模型进行预测，使用随机生成的输入张量：

• `X = torch.rand(1, 28, 28, device=device)`：这创建了一个形状为 `(1, 28, 28)` 的随机张量 `X`，表示一个 28x28 像素的图像。形状中的 `1` 表示批次中只有一张图像。此张量被放置在先前选择的设备上（可能是 CPU、CUDA GPU 或 MPS GPU）。

• `logits = model(X)`：随机图像张量 `X` 被传递给名为 `model` 的预训练模型。模型处理输入并输出 logits，即模型正在预测的每个类的原始、未归一化分数。

• `pred_probab = nn.Softmax(dim=1)(logits)`：logits 被传递给 Softmax 函数以将其转换为概率。Softmax 函数沿 `dim=1` 应用，将每个类的 logits 转换为 0 到 1 之间且总和为 1 的值，表示模型对每个类的置信度。

• `y_pred = pred_probab.argmax(1)`：这通过获取 `pred_probab` 张量沿维度 1 的最大值索引来找到概率最高的类。此索引表示模型对输入图像的预测类。

• `print(f"Predicted class: {y_pred}")`：最后，打印出预测类索引，指示模型认为随机输入最可能属于哪个类。

这段代码是使用单个随机生成的输入图像从 PyTorch 模型生成预测的基本示例。

### [模型层](#toc.xhtml#zs15)

让我们分解 FashionMNIST 模型中的层。为了说明这一点，我们将取一个包含 3 张 28x28 图像的小批量样本，并查看它们在通过网络时会发生什么。请参阅以下代码：

```python
input_image = torch.rand(3,28,28)

print(input_image.size())
```

### [nn.Flatten](#toc.xhtml#zs16)

我们初始化 `nn.Flatten` 层，将每个 2 维 28x28 图像转换为 784 个像素值的连续数组（小批量维度（在 `dim=0` 处）保持不变）。

请参阅以下代码：

```python
flatten = nn.Flatten()

flat_image = flatten(input_image)

print(flat_image.size())
```

### [nn.Linear](#toc.xhtml#zs17)

线性层是一个模块，它使用存储的权重和偏差对输入应用线性变换，如以下代码所示：

```python
layer1 = nn.Linear(in_features=28*28, out_features=20)

hidden1 = layer1(flat_image)

print(hidden1.size())
```

### [nn.ReLU](#toc.xhtml#zs18)

非线性激活在模型的输入和输出之间创建复杂的映射。它们在线性变换之后应用，以引入非线性，帮助神经网络学习各种现象。

在此模型中，我们在线性层之间使用 `nn.ReLU`，但还有其他激活函数可以为您的模型引入非线性。

请参阅以下代码：

```python
print(f"Before ReLU: {hidden1}\n\n")

hidden1 = nn.ReLU()(hidden1)

print(f"After ReLU: {hidden1}")
```

### [nn.Sequential](#toc.xhtml#zs19)

`nn.Sequential` 是模块的有序容器。数据按定义的相同顺序通过所有模块。您可以使用顺序容器快速构建网络，如 `seq_modules`，如下所示：

```python
seq_modules = nn.Sequential(

    flatten,

    layer1,

    nn.ReLU(),

    nn.Linear(20, 10)

)

input_image = torch.rand(3,28,28)

logits = seq_modules(input_image)
```

### [nn.Softmax](#toc.xhtml#zs20)

神经网络的最后一个线性层返回 logits——`[-infty, infty]` 中的原始值——这些值被传递给 `nn.Softmax` 模块。logits 被缩放为 `[0, 1]` 中的值，表示模型对每个类的预测概率。`dim` 参数指示值必须总和为 1 的维度。

请参阅以下代码：

```python
softmax = nn.Softmax(dim=1)

pred_probab = softmax(logits)
```

### [模型参数](#toc.xhtml#zs21)

神经网络内部的许多层都是参数化的，即具有在训练期间优化的相关权重和偏差。继承 `nn.Module` 会自动跟踪模型对象内部定义的所有字段，并使所有参数可通过模型的 `parameters()` 或 `named_parameters()` 方法访问。

