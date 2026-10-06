

# 卷积神经网络

现在让我们对上一节中通过将 `input_image` 通过卷积层生成的输出应用最大池化（max-pooling）。首先，我们打印它的形状：

```python
print(output.shape)
>> torch.Size([1, 8, 64, 64])
```

现在我们定义一个卷积大小为 2、步长为 2 的最大池化操作，将输出下采样二倍

```python
maxpool = torch.nn.MaxPool2d(kernel_size=2,stride=2)
downsampled = maxpool(output)
print(downsampled.shape)
>> torch.Size([1, 8, 32, 32])
```

另一种常用的池化操作是平均池化（average pooling），它不是取块中的最大值，而是计算平均值。在 Pytorch 中，通过以下函数实现：

```python
torch.nn.AvgPool2d(2,2)
```

# 步长 (Striding)

步长可以在执行卷积操作的同时对图像进行下采样。例如，当应用步长为 2 的卷积时，我们会跳过图像中的每第二个像素，如图 11.6 所示。

| 55 | 60 | 65 | 68 | 60 | 60 | 73 |
|---|---|---|---|---|---|---|
| n | 67 | 65 | 63 | 67 | 70 | 73 | 103 |
| 73 | 64 | 62 | 65 | 80 | 97 | 145 |
| 1 | 0 | -1 | | | | |
| 2 | 0 | -2 | | | | |
| 69 | 65 | 68 | 83 | 133 | 165 | 216 |
| 1 | 0 | -1 | | | | |
| 79 | 89 | 108 | 165 | 195 | 234 |
| 68 | 89 | 105 | 131 | 198 | 220 | 237 |
| 67 | 110 | 146 | 177 | 233 | 245 | 238 |

| | -27 | -144 |
|---|---|---|
| -5 | -224 | -300 |
| -171 | -349 | -152 |

图 11.6 步长卷积。

以下代码演示了我们如何通过将步长设置为 2，对 `input_image` 执行步长卷积，从而将其空间维度减半：

```python
print(input_image.shape)
>> torch.Size([1, 1, 64, 64])
```

# 11.2.4 批归一化 (Batch normalization)

```python
conv = torch.Conv2d(1,8,5,padding=2,stride=2)
downsampled = conv(input_image)
print(downsampled.shape)
>>> torch.Size([1, 8, 32, 32])
```

深度神经网络通常使用随机梯度下降（stochastic gradient descent）的变体进行训练，这些方法从数据集中采样批（batches）并估计每个批的平均损失，而不是跨所有样本进行估计。由于每个批次的组成可能会发生变化，这可能导致梯度更新产生噪声。批归一化 [22] 试图通过对网络中每一层在每个批次中的特征进行归一化和重缩放来解决这个问题。通过这样做，它可以显著加快训练速度。通常，批归一化放置在卷积层和激活层之前，或者在激活层之后。

批归一化层将其输入重缩放到零均值和单位方差。这是通过减去从数据计算出的均值并除以方差来实现的。归一化是在批空间维度上进行的，但对每个输出通道独立进行。由于跨批存在均值和方差，批归一化层会在迭代过程中跟踪它们并计算移动平均值。

批归一化层还为每个通道学习一个线性变换（由两个参数化，即斜率偏置），该变换在归一化后应用到特征上。

在下面的示例中，我们想要对卷积层的输出应用批归一化：

```python
print(output.shape)
>>> torch.Size([1, 8, 64, 64])
```

因为我们有 8 个通道，我们按如下方式应用批归一化：

```python
bn = torch.nn.BatchNorm2d(8)
normalized-bn(output)
```

# 11.2.5 丢弃 (Dropout)

Dropout [43] 是一种可用于网络正则化的技术。它通过在训练期间随机丢弃激活值（将其设置为零）来工作，换句话，就是在每层的输出上应用随机掩码操作。通过这种方法，该方案防止单个网络组件记忆输入，从而导致过拟合。这里存在权衡，因为丢弃过多的权重将阻止网络进行充分的学习并导致欠拟合。

如果将 dropout 算应用于卷积层的输出，它将以参数 `p` 设置的概率将通道置零。

```python
d = torch.nn.Dropout2d(p=0.5)
d(output)
```

# 11.2.6 卷积块 (Convolutional blocks)

卷积块使用一个对象通过 `torch.nn` 实现了多个操作。我们现在创建图 11.4 所示的块，它实现了第一个卷积层和第一个池化层：

```python
import torch.nn as nn
conv_block = nn.Sequential(
    nn.Conv2d(1,8,5,padding=2,stride=2),
    nn.BatchNorm2d(8),
    nn.ReLU()
)
```

这个块现在可以应用于图像：

```python
output = conv_block(input_image)
print(output.shape)
>>> torch.Size([1, 8, 32, 32])
```

由于设置步长为 2，第二个卷积块将实现第二个卷积层和第二个池化层：

```python
conv_block = =..Sequential(
    ..Convd((,16,5,padding=2,stride=2),
    nn.BatchNorm2d(16),
    nn.ReLU(),
    nn.MaxPool2d(kernel_size=2,stride=2)
)
```

接下来，我们需要对输出应用全连接层。我们需要将 $16 \times 16$ 展平为向量，然后应用全连接层：

```python
n=16*16
fc_block = nn.Sequential(
    nn.Linear(n,128),
    nn.ReLU(),
    nn.Linear(128,10)
)
```

# 11.2.7 卷积模型

最后，我们准备好实现整个网络（nn.Module）：

```python
class CNNModel(nn.Module):
    def __init__(self):
        super(CNNModel, self).__init__()
        self.conv_1 = nn.Sequential(
            nn.Conv2d(1,8,5,padding=2,stride=2),
            nn.BatchNorm2d(8),
            nn.ReLU()
        )
        self.conv_2 = nn.Sequential(
            nn.Conv2d(8,16,5,padding=2,stride=2),
            nn.BatchNorm2d(16),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size=2,stride=2)
        )
        self.fc_block = nn.Sequential(
            nn.Linear(16*16*16,128),
            nn.ReLU(),
            nn.Linear(128,10)
        )

    def forward(self, x):
        x = self.conv_1(x)
        x = self.conv_2(x)
        x = x.view(-1,16*16*16)
        x = self.fc_block(x)
        return x
```

我们现在可以实例化这个网络并进行向前传播：

```python
net = CNNModel()
o = net(input_image)
print(o.shape)
>>> torch.Size([1, 10])
```

我们可以看到网络返回了10个输出。卷积神经网络的训练方式与第10章中的全连接网络相同。例如，为了分类数字，我们可以优化交叉熵损失。

# 11.2.8 练习

- 1. 按如下方式实现卷积层²
    a. 创建一个空间维度为 100 × 100、通道数为 3 的随机图像；
    b. 实现一个输出 5 个通道且卷积大小为 3 × 3 的卷积层。将图像通过该层。打印结果维度；
    c. 修改卷积层，使其输出空间维度为100；
    d. 修改卷积层的步长，使其输出空间维度为 20 × 20；
    e. 不要改变步长，而是实现一个步长为 1的最大池化操作，将维度缩小到 20 × 20。
- 2. 计算练习1中卷积层的学习参数数量。
- 3. 通过修改以下各项来修改 CNN：
    a. 将模型重名为 CNNNode2；
    b. 将第一和第二个卷积层的输出通道分别改为 4 和 6；
    c. 将第一和第二个全连接层的输出数分别改为 32 和 2
为新模型创建一个实例 net2。使用 `input_image` 执行向前传播。检查你是否有 2 个输出。

> ²练习1和3的骨架代码和答案可从 github.com/MachineLearning-BiomedicalApplications/notebooks 获取。

# 11.3. 从新生脑 MRI 预测早产

在本节中，我们将设计并训练一个 CNN 分类器，直接从新生 MRI 图像预测早产状态 [13,18]。我们将使用 2D 切片而不是 3D 图像以减少对 GPU 内存的需求并加快训练。2D 脑 MRI 图像和157 个婴儿的早产状态在文件中给出。

