
# PyTorch 核心组件

与 TensorFlow 类似，PyTorch 也支持端到端的机器学习工作流，从数据准备到模型服务。以下图显示了用于训练和服务的不同 PyTorch 模块：

![](img/bd21298357d4841547c0b2f138b1620.png)

图 5.6 – 用于训练和服务的 PyTorch 模块

训练深度学习模型的步骤与 TensorFlow 非常相似。我们将通过以下步骤查看 PyTorch 的细节：

- 1. **准备数据集**：PyTorch 提供了数据集和数据管理的原语：`torch.utils.data.Dataset` 和 `torch.utils.data.DataLoader`。Dataset 存储数据样本及其对应的标签，而 DataLoader 封装了数据集并为模型训练提供高效的数据访问。DataLoader 提供了 `shuffle`、`batch_size` 和 `prefetch_factor` 等函数来控制如何加载数据喂给算法。

- 2. **定义神经网络**：PyTorch 提供了构建神经网络的高级抽象，其 `torch.nn` 类为神经网络层提供了内置支持，如线性层（linear layers）和卷积层（convolutional layers），以及激活函数如 Sigmoid 和 ReLU。它还拥有 `nn.Sequential` 类可以将不同的层封装成完整的网络。

- 3. **定义损失函数**：PyTorch 在 `torch.nn` 类中提供了多个内置损失函数，如 `nn.MSELoss` 和 `nn.CrossEntropyLoss`。在执行训练之前，数据集可能需要使用自定义函数来转换数据。

- 4. **选择优化器**：PyTorch 通过其 `nn.optim` 类提供了多个优化器。优化器的示例包括 `optim.SGD`、`optim.Adam` 和 `optim.RMSProp`。所有优化器都有 `step()` 方法在每次前向传播（forward pass）后更新模型参数，而反向传播（backward pass）计算梯度。

- 5. **选择评估指标**：`torch.metrics` 类提供了多个评估指标，如精确率（Precision）、召回率（Recall）和均方根误差（RootSquaredError），用于评估模型性能。可以在 https://en.wikipedia.org/wiki/Precision_and_recall 学习更多关于精确率和召回率的信息。你也可以使用 scikit-learn 库来帮助评估模型。

- 6. **训练模型**：在 PyTorch 中训练模型涉及每个训练循环中的三个主要步骤：前向传播训练数据、反向传播训练数据以计算梯度，以及执行优化器步进以更新梯度。

- 7. **保存/加载模型**：`torch.save()` 函数以序列化的 pickle 格式保存模型。`torch.load()` 函数将序列化的模型加载到内存中进行推理。常见的约定是使用 .pth 或 .pt 扩展保存文件。你也可以将多个模型保存到单个文件中。

- 8. **模型服务**：PyTorch 自带一个名为 TorchServe 的服务库，我们将在第 7 章开源机器学习平台中详细介绍。PyTorch 库支持大规模分布式数据处理和模型训练，我们将在第 10 章高级机器学习中详细介绍。

现在你已经学习了 PyTorch 的基础知识，让我们通过一个简单的练习来动手操作。

# 动手练习 – 构建并训练 PyTorch 模型

在本次练习中，你将学习如何在本地机器上安装 PyTorch 库并使用 PyTorch 训练简单的深度学习模型。启动你之前在机器上安装的 Jupyter notebook。如果你忘记了如何操作，请访问第 3 章机器学习算法的“动手实验室”部分。现在，我们开始吧：

- 1. 在你的 Jupyter notebook 环境中创建一个新文件夹 `pytorch-lab`，并创建一个名为 `pytorch-lab.ipynb` 的新笔记本。在单元格中运行以下命令安装 PyTorch 和 torchvision 包。torchvision 包含一组计算机视觉模型和数据集。我们将在本次练习中使用 torchvision 包中预构建的 MNIST 数据集：

```python
pip install torch
pip install torchvision
```

- 2. 下面的示例代码显示了之前提到的组件。确保在独立的 Jupyter notebook 单元格中运行每个代码块以便于阅读。

首先，我们必须导入必要的库包并从 torchvision 数据类加载 MNIST 数据集：

```python
import numpy as np
import matplotlib.pyplot as plt
import torch
from torchvision import datasets, transforms
from torch import nn, optim
```

```python
transform = transforms.Compose([transforms.ToTensor(),
transforms.Normalize((0.5,), (0.5, 0.5,))])
trainset = datasets.MNIST('pytorch_data/train/',
download=True, train=True, transform=transform)
valset = datasets.MNIST('pytorch_data/test/',
download=True, train=False, transform=transform)
trainloader = torch.utils.data.DataLoader(trainset,
batch_size=64, shuffle=True)
```

- 3. 接下来，我们必须构建一个用于分类的 MLP 神经网络。这个 MLP 有两个隐藏层，第一层和第二层使用 ReLU 激活。MLP 接收大小为 784 的输入（展平后的数据）。使用 `nn.Sequential` 将不同的层打包进一个网络：

```python
model = nn.Sequential(
    nn.Linear(784, 128),
    nn.ReLU(),
    nn.Linear(128, 64),
    nn.ReLU(),
    nn.Linear(64, 10)
)
```

- 4. **定义损失函数**：PyTorch 在 `torch.nn` 类中提供了多个内置损失函数，如 `nn.MSELoss` 和 `nn.CrossEntropyLoss`。

```python
criterion = nn.CrossEntropyLoss()
```

- 5. **选择优化器**：PyTorch 通过其 `nn.optim` 类提供了多个优化器。优化器的示例包括 `optim.SGD`、`optim.Adam` 和 `optim.RMSProp`。

```python
optimizer = optim.Adam(model.parameters(), lr=0.001)
```

- 6. **训练模型**：在 PyTorch 中训练模型涉及每个训练循环中的三个主要步骤：前向传播训练数据、反向传播训练数据以计算梯度，以及执行优化器步进以更新梯度。

```python
epochs = 15
for e in range(epochs):
    running_loss = 0
    for images, labels in trainloader:
        images = images.view(images.shape[0], -1)
        optimizer.zero_grad()
        output = model(images)
        loss = criterion(output, labels)
        loss.backward()
        optimizer.step()
        running_loss += loss.item()
    else:
        print("Epoch {} - Training loss: {}".format(e, running_loss/len(trainloader)))
```

- 7. **评估指标**：为了使用验证数据测试准确率，我们必须将验证数据集通过训练好的模型，并使用 scikit-learn 的 `accuracy_score()` 计算模型的准确率：

```python
valloader = torch.utils.data.DataLoader(valset,
batch_size=valset.data.shape[0], shuffle=True)
val_images, val_labels = next(iter(valloader))
val_images = val_images.view(val_images.shape[0], -1)
predictions = model(val_images)
predicted_labels = np.argmax(predictions.detach().numpy(), axis=1)

from sklearn.metrics import accuracy_score
accuracy_score(val_labels.detach().numpy(), predicted_labels)
```

- 8. **保存模型**：最后，我们必须模型保存到文件中：

```python
torch.save(model, './model/my_mnist_model.pt')
```
