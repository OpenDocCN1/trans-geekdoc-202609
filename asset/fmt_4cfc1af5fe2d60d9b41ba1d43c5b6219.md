
```python
import torch
import torch.nn as nn
import torch.optim as optim

class MILNet(nn.Module):
    def __init__(self, input_dim, hidden_dim, output_dim):
        super(MILNet, self).__init__()
        self.fc1 = nn.Linear(input_dim, hidden_dim)
        self.fc2 = nn.Linear(hidden_dim, output_dim)

    def forward(self, bags):
        # bags 是一个形状为 (num_bags, max_bag_size, input_dim) 的张量
        num_bags = bags.shape[0]
        # 通过取包内所有实例每个特征的最大值来计算包级表示
        bag_repr, _ = torch.max(bags, dim=1)
        # 将包级表示通过全连接层
        out = torch.relu(self.fc1(bag_repr))
        out = self.fc2(out)
        # 返回形状为张量的包级预测
```

在实例级，多标签分类可以通过为每个实例分配一组标签而不是单个标签来实现。这可以通过多热编码（multi-hot encoding）完成，其中每个标签由一个二值表示，指示该实例是否属于该标签。通过使用 `max pooling`（最大池化）或 `mean pooling`（平均池化）等池化操作将实例级预测聚合为包级预测，可以将实例级多标签分类问题转换为包级多标签分类问题。

令 `B` 为由 `X = {x_1, x_2, ..., x_m}` 表示的实例包，其中 `x_i` 是特征向量，令 `y` 为包级标签（二分类或多分类）。那么，包级分类器 `f_b` 定义为：

`y = f_b(X)`

其中 `y` 是表示包 `B` 预测标签的标量值。

### 实例级分类

令 `I` 为由特征向量 `x` 表示的实例，令 `y` 为实例级标签（二分类或多分类）。那么，实例级分类器 `f_i` 定义为：

`y = f_i(x)`

其中 `y` 是表示实例 `I` 预测标签的标量值。

在 PyTorch 中使用二元相关性（binary relevance）方法执行包级多标签分类的代码如下：

```python
class MILMultiLabelNet(nn.Module):
    def __init__(self, input_dim, hidden_dim, output_dim):
        super(MILMultiLabelNet, self).__init__()
        self.fc1 = nn.Linear(input_dim, hidden_dim)
        self.fc2 = nn.Linear(hidden_dim, output_dim)

    def forward(self, bags):
        # bags is a tensor of shape (num_bags, max_bag_size, input_dim)
        num_bags = bags.shape[0]
        # 通过取包内所有实例每个特征的最大值来计算包级表示
        bag_repr, _ = torch.max(bags, dim=1)
        # 将包级表示通过全连接层
        out = torch.relu(self.fc1(bag_repr))
        out = torch.sigmoid(self.fc2(out))
        # 返回包级预测，形状为 (num_bags, output_dim) 的张量
        return out

class BinaryRelevanceLoss(nn.Module):
    def __init__(self):
        super(BinaryRelevanceLoss, self).__init__()
        self.loss_fn = nn.BCELoss()

    def forward(self, pred, target):
        # pred is a tensor of shape (num_bags, output_dim)
        # target is a tensor of shape (num_bags, output_dim)
        loss = self.loss_fn(pred, target)
        return loss

### 使用示例
model = MILMultiLabelNet(input_dim=10, hidden_dim=20, output_dim=5)
loss_fn = BinaryRelevanceLoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.01)

# 生成示例数据
num_bags = 10
max_bag_size = 5
input_dim = 10
output_dim = 5
bags = torch.rand(num_bags, max_bag_size, input_dim)
target = torch.randint(low=0, high=2, size=(num_bags, output_dim)).float()

## 训练循环
num_epochs = 100
for epoch in range(num_epochs):
    optimizer.zero_grad()
    pred = model(bags)
    loss = loss_fn(pred, target)
    loss.backward()
    optimizer.step()
    print("Epoch {}: loss={}".format(epoch, loss.item()))
```

在 MIL 中于实例级执行多分类的 PyTorch 代码如下：

```python
import torch
import torch.nn as nn

class MILNet(nn.Module):
    def __init__(self, input_dim, hidden_dim, output_dim):
        super(MILNet, self).__init__()
        self.fc1 = nn.Linear(input_dim, hidden_dim)
        self.fc2 = nn.Linear(hidden_dim, output_dim)

    def forward(self, bags):
        # bags is a tensor of shape (num_bags, max_bag_size, input_dim)
        num_bags = bags.shape[0]
        max_bag_size = bags.shape[1]
        # 将 bags 重塑为形状为 (num_bags * max_bag_size, input_dim) 的张量
        instances = bags.view(num_bags * max_bag_size, -1)
        # 将实例通过全连接层
        out = torch.relu(self.fc1(instances))
        out = self.fc2(out)
        # 将输出重塑为形状为 (num_bags, max_bag_size, output_dim) 的张量
        out = out.view(num_bags, max_bag_size, -1)
        # 计算实例级预测，形状为 (num_bags, max_bag_size, output_dim) 的张量
        instance_preds = torch.softmax(out, dim=2)
        # 通过取每个包所有实例的最大预测概率来计算包级预测
        bag_preds, _ = torch.max(instance_preds, dim=1)
        return bag_preds
```

图 6.4：两个决策边界

## 传统学习与 MIL

传统的监督分类是一种机器学习（ML），它涉及根据一组标记的训练数据为每个实例分配一个标签或类别。其目标是学习一个可以将输入数据映射到正确输出标签的函数。传统的监督分类方法假设每个实例只有一个标签或类别，其目标是正确地分类每个单独的实例。另一方面，多实例学习（MIL）分类是另一种机器学习，其目标是为一组实例（包，bag）分配一个标签。在 MIL 中，一个包可能包含多个实例，分配给包的标签基于包内所有实例的集合信息。MIL 假设分配给包的标签是已知的，但分配给单个实例的标签可能是未知的或模糊的。

MIL 的目标是学习一个可以将包级表示映射到正确包级标签的函数。与传统的监督分类不同，当实例级标签是模糊或未知的时会使用 MIL，其目标是分类实例包而不是单个实例。在多实例分类（MIC）中，包的特征向量通常通过聚合其各个实例的特征获得。一种流行的聚合方法是最大池化（max pooling），即取包中所有实例的每个特征的最大值。

传统监督分类和 MIC 之间的区别在于，在前者中，每个实例都被单独标记；而在后者中，只对整个包进行标记。此外，MIC 中包的特征向量是通过聚合其实例的特征获得的，而在传统分类中，特征是直接被使用的。

可以表述如下：

给定一个包含 `n` 个标记实例的训练数据集 `D = (xi, yi)n`，其中 `xi Rd` 表示特征向量。例如，`i` 和 `yi` 是来自 `K` 个可能类别的对应标签。目标是学习一个函数 `f : Rd → 1, . . . , K`，该函数能够准确预测任何给定实例 `xi` 的类别标签 `yi`。

另一方面，MIC 是监督学习的一种变体，其任务是分类实例包而不是单个实例。它可以表述如下：给定一个包含 `n` 个标记包的训练数据集 `D = Bi, yii = 1n`，其中 `Bi = xi, 1, . . . , xi,m` 表示包含 `mi` 个实例的包，`yi` 是来自 `K` 个可能类别的对应标签。目标是学习一个函数 `f : Rm×d → 1, . . . , K`，该函数能够准确预测任何给定实例包 `Bi` 的类别标签 `yi`。在 MIC 中，包的特征向量通常通过聚合其各个实例的特征获得。一种流行的聚合方法是最大池化，即取包中所有实例的每个特征的最大值。传统监督分类和 MIC 之间的区别在于，在前者中，每个实例都被单独标记；而在后者中，只对整个包进行标记。此外，MIC 中包的特征向量是通过聚合其实例的特征获得的，而在传统分类中，特征是直接被使用的。

## 构建 PyTorch MIL：数据准备，模型设置

编写代码至关重要。首先，它允许研究人员和开发者实际应用 MIL 概念，帮助他们解决仅在包级可用标签而非实例标签的问题。这在医学影像中非常常见。

```python
def create_bags(dataset):
    bags = {}
    for i in range(len(dataset)):
        image, label = dataset[i]
        if label not in bags:
            bags[label] = []
        bags[label].append(image)
    return [(bag, label) for label, bag in bags.items()]

class MILMNISTDataset(Dataset):
    def __init__(self, mnist_dataset):
        self.bags = create_bags(mnist_dataset)

    def __getitem__(self, index):
        bag, label = self.bags[index]
        bag_tensor = torch.stack([torch.tensor(np.array(img)) for img in bag])
        return bag_tensor, label

    def __len__(self):
        return len(self.bags)

### 加载 MNIST 数据集
mnist_dataset = MNIST(root="./data", train=True, download=True)

# 从 MNIST 创建 MIL 数据集
mil_dataset = MILMNISTDataset(mnist_dataset)

## 使用 Matplotlib 可视化某些包中的实例
fig, axes = plt.subplots(2, 5, figsize=(10, 5))

for i in range(2):
    for j in range(5):
        bag, label = mil_dataset[i*5+j]
        instance = bag[0] # 从每个包中提取第一个实例
        axes[i, j].imshow(instance, cmap='gray')
        axes[i, j].set_title(f"Class: {label}")
        axes[i, j].axis('off')

plt.show()
```

参考下图：

![](img/Figure_6.5.png)

图 6.5：显示输出

`__init__` 方法通过调用 `create_bags` 函数初始化数据集，该函数从 `mnist_dataset` 生成 MNIST 的包。每个包被表示为 MNIST 图像列表和相应的包标签。

`__getitem__` 方法在从数据集中访问项时被调用。它接收一个索引作为输入，并返回相应的包和标签。首先，它根据给定的 `index` 从 `self.bags` 列表中提取包和标签。然后，它使用 `torch.stack` 函数将包中的图像从列表转换为张量。列表推导式 `[torch.tensor(np.array(img)) for img in bag]` 将每个图像转换为 NumPy 数组，然后转换为 PyTorch 张量。生成的张量形状为 `(num_instances, 28, 28)`，其中 `num_instances` 是包中的图像数量。

`__len__` 方法返回数据集中包的总数，即 `self.bags` 列表的长度。

这是一个关于如何创建包的非常简单的示例。然而，在后续代码中，我们将使用 MNIST 数据集开发一个 MIL 设置，在其中我们将处理嵌入并使用损失函数训练模型。这个端到端的示例将包含数据集的创建、模型定义、训练以及使用 t-SNE 对嵌入空间可视化。

```python
import torch
import torch.nn as nn
import torch.optim as optim
from torchvision import transforms, datasets
from torch.utils.data import DataLoader, Dataset
import matplotlib.pyplot as plt
from sklearn.manifold import TSNE
import numpy as np
import random

class MILMNISTDataset(Dataset):
```

```python
    def __init__(self, mnist_dataset, bag_size=5, target_digit=9, num_bags=200):
        self.mnist_dataset = mnist_dataset
        self.bag_size = bag_size
        self.target_digit = target_digit
        self.num_bags = num_bags
```

`MILMNISTDataset` 类扩展了 PyTorch 的 `Dataset`，用于为多实例学习创建 MNIST 图像包。每个实例（包）包含固定数量的图像（`bag_size`），如果包中包含至少指定的 `target_digit` 图像，则该包标记为正样本，数据集会生成指定数量（`num_bags`）这样的包。

```python
    def __getitem__(self, index):
        bag_images = []
        labels = []
        bag_label = 0
        for _ in range(self.bag_size):
            idx = random.randint(0, len(self.mnist_dataset) - 1)
            image, label = self.mnist_dataset[idx]
            bag_images.append(image)
            labels.append(label)
            if label == self.target_digit:
                bag_label = 1
        return torch.stack(bag_images), bag_label

    def __len__(self):
        return self.num_bags
```
