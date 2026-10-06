
neonatal_mri.npz，它包含了包含这些数据的压缩 numpy 数组。在开始此示例之前，我们必须确保可以访问 GPU。

## 11.3.1 访问 GPU

### 你的本地 GPU 卡

如果你有一块具有至少 4 GB 内存并安装了 CUDA 的 NVIDIA GPU，你可以在你的自己的电脑上本地实现本节的示例。如果你没有这些资源，可以使用 Google Colab。

要检查 CUDA 是否可用，运行以下代码：

```
torch.cuda.is_available()
>>> True
```

如果答案是 true，则 PyTorch 能够访问你的 GPU。你也可以按照以下方式检查 GPU 的属性：

```
print(torch.cuda.get_device_properties('cuda:0'))
>>> CudaProperties(name='Quadro M2000',
major=5, minor=2, total_memory=4096MB,
multi_processor_count=6)
```

我们可以看到使用的 GPU 有 4096 MB 内存，大约是 4 GB。

### Google Colab

Google Colab 免费提供有限的 GPU 访问，这一资源对于实现本节的示例是充足的。要使用 Google Colab，你需要一个 Google 账号。登录后访问：

colab.research.google.com

你将看到一个屏幕，其中有几个选项，包括现有的笔记本。如果你已经创建了笔记本，点击 upload 并文件拖入到那里。或者，如果你计划在新笔记本中输入代码，请点击 New notebook。你可以通过点击顶角的名称来更改此笔记本的名称。默认情况下，Google Colab 运行在 CPU 上。要访问 GPU，点击 Runtime -> Hardware Accelerator 下拉菜单并选择 GPU。

最后你需要上传数据。要做到这一点，在空单元格中输入以下代码并运行它（点击箭头）：

```
github.com/MachineLearning/Applications/notebooks

from google.colab import files
files.upload()
```

过了一会儿，会出现一个名为 Files 的按钮。点击此按钮并上传 neonatal_mri.npz 文件。文件大约需要一分钟时间上传。现在你已经准备好继续本章其余部分提供的代码了。要向你的笔记本中添加新单元格，如果你想写代码，请点击 +Code；如果你想写注释，请点击 +Text。

## 11.3.2 加载并准备数据

### 加载数据

首先，我们使用 numpy 包加载压缩数据：

```python
import numpy as np
data = np.load('neonatal_mri.npz')
data.files
>>> ['MR_images', 'prematurity']
```

我们看到文件包含两个名为 'MR_images' 和 'prematurity' 的数组。我们现在提取这些数组。第一个数组包含 157 张具有 1 通道（灰度）和 64×64 尺寸的 MR 。

```python
mri = data['MR_images']
print(mri.shape)
>>> (157, 1, 64, 64)
```

第二个数组包含成熟状态，这是一个二分类标签，1 表示“早产”，0 表示“足月”。

```python
prem = data['prematurity']
print(prem.shape)
>>> (157,)
```

我们还发现数据集中 41% 是早产婴儿：

```python
np.round(np.sum(prem)/np.size(prem), 2)
>>> 0.41
```

### 绘制数据

我们现在将绘制前 8 张图像，标题中带有成熟状态。下面代码生成的图表如图 11.7 所示。

```python
from matplotlib import pyplot as plt
plt.figure(figsize=(12,6))

for i in range(8):
    plt.subplot(2,4,i+1)
    plt.imshow(mri[i,0:], cmap='gray')
    if prem[i]:
        plt.title('Preterm')
    else:
        plt.title('Term')
    plt.axis('off')
```

![](img/d2194c20ff50f4b97845dec7aacecb_266_0.png)

图 11.7 来自新生儿 MRI 数据集的示例图像。

### 转换为 Pytorch 张量

注意，数据已经按照 Pytorch 要求的形状准备就绪。我们仍然需要将其转换为正确类型的 Pytorch 张量，即图像使用 `float`，标签使用 `long`：

```python
import torch
X = torch.tensor(mri).float()
y = torch.tensor(prem).long()
```

### 训练集、验证集和测试集

接下来，我们需要划分数据用于训练、验证和测试。我们将移除 20% 的数据用于测试，另一个 10% 用于验证。我们将执行分层划分，以确保所有集中早产婴儿的比例相同：

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = \
    train_test_split(X, y, test_size=0.2, stratify=y)
X_train, X_val, y_train, y_val = \
    train_test_split(X_train, y_train, test_size=0.1, stratify=y_train)
print('Training samples:', y_train.size())
print('Validation samples:', y_val.size())
print('Test samples:', y_test.size())
>>> Training samples: torch.Size([112])
>>> Validation samples: torch.Size([13])
>>> Test samples: torch.Size([32])
```

我们有 112 个样本用于训练，13 个用于验证，32 个用于测试。我们准备好实现并训练我们的 CNN。

## 11.3.3 CNN 分类器

### 模型架构

网络架构与我们在第 11.2 节看到的类似，但有一些小不同。我们将有三个卷积块和一个全连接块。这些将按如下实现：

- conv_block1: 具有 8 个滤波器和卷积核大小 3 的 2D 卷积层，之后是 batch-norm、ReLU 和最大池化
- conv_block2: 具有 16 个滤波器和卷积核大小 3 的 2D 卷积层，之后是 batch-norm、ReLU 和最大池化
- conv_block3: 具有 32 个滤波器和卷积核大小 3 的 2D 卷积层，之后是 batch-norm、ReLU 和最大池化
- fc: 全连接层

```python
import torch
import torch.nn as nn
import torch.optim as optim

class CNNclf(nn.Module):
    def __init__(self):
        super(CNNclf, self).__init__()
        self.conv_block1 = nn.Sequential(
            nn.Conv2d(1, 8, 3),
            nn.BatchNorm2d(8),
            nn.ReLU(),
            nn.MaxPool2d(2)
        )
        self.conv_block2 = nn.Sequential(
            nn.Conv2d(8, 16, 3),
            nn.BatchNorm2d(16),
            nn.ReLU(),
            nn.MaxPool2d(2)
        )
        self.conv_block3 = nn.Sequential(
            nn.Conv2d(16, 32, 3),
            nn.BatchNorm2d(32),
            nn.ReLU(),
            nn.MaxPool2d(2)
        )
        self.fc_block = nn.Sequential(
            nn.Flatten(),
            nn.Linear(32 * 8 * 8, 2)
        )

    def forward(self, x):
        x = self.conv_block1(x)
        x = self.conv_block2(x)
        x = self.conv_block3(x)
        x = self.fc_block(x)
        return x
```

### 在 CUDA 设备上设置

通过设置我们的 CUDA 设备：

```python
if torch.cuda.is_available():
    device = torch.device("cuda")
else:
    device = torch.device("cpu")
print(device)
>>> cuda
```

接下来，我们创建一个 CNN 分类器并将其发送 GPU：

```python
net = CNNclf().to(device)
```

我们正在构建一个 CNN 分类器，所以选择交叉熵损失，将其发送到 GPU：

```python
loss = nn.CrossEntropyLoss().to(device)
```

最后，我们创建优化器。在创建优化器之前将模型发送到 GPU：

```python
optimizer = optim.SGD(net.parameters(), lr=0.001, momentum=0.5)
```

## 11.3.4 训练

现在我们准备好开始训练。我们将训练 2000 个 epoch（迭代）。我们选择在通过 100 个 epoch 后开始训练，直到验证集停止下降。

注意我们每次迭代使用所有数据进行训练，每次迭代都是一个 epoch。这对于更大的数据集通常是不可能的，训练将通过小批量进行，正如我们在下一节中所示。

```python
epochs = 2000
train_losses=[]
val_losses=[]

for epoch in range(epochs):

    # 训练模式
    net.train()
    # 将训练数据发送到 GPU
    data = X_train.to(device)
    labels = y_train.to(device)
    # 训练
    optimizer.zero_grad()
    pred = net(data)
    ce = loss(pred, labels)
    ce.backward()
    optimizer.step()
    train_losses.append(ce.item())
```
