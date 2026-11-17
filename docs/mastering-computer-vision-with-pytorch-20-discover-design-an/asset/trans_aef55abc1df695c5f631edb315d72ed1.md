
```python
train_loader = torch.utils.data.DataLoader(train_dataset,
batch_size=64, shuffle=True)
test_loader = torch.utils.data.DataLoader(test_dataset,
batch_size=64, shuffle=False)
# Set number of epochs to train
number_of_epochs = 5
# Loop for each epoch
for epoch in range(number_of_epochs):
    running_loss = 0.0
    for i, data in enumerate(train_loader, 0):
        inputs, labels = data[0].to(device), data[1].to(device)
        optimizer.zero_grad()
        outputs = vgg16_pretrained(inputs)
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()
        running_loss += loss.item()
    print(f'Epoch {epoch + 1}: Loss: {running_loss /
len(train_loader)}')
# Save the model's state dictionary
torch.save(vgg16_pretrained.state_dict(),
'vgg16_cifar100.pth')
```

Epoch 1: Loss: 1.630416536346421
Epoch 2: Loss: 1.5624679418476037
Epoch 3: Loss: 1.5073729947095027
Epoch 4: Loss: 1.43779634583333174
Epoch 5: Loss: 1.41022737472866833
Epoch 6: Loss: 1.37455911282688815
Epoch 7: Loss: 1.3385358903261706
Epoch 8: Loss: 1.305282829743822
Epoch 9: Loss: 1.2908474900533475
Epoch 10: Loss: 1.2709745466709137

图 8.1: 在 CIFAR100 数据集上训练 VGG-16 模型 100 个时代后的输出

## 评估代码

训练后，在验证集或测试集上评估模型性能以衡量泛化能力至关重要：

```python
correct, total = 0, 0
with torch.no_grad():
    for data in test_loader:
        images, labels = data[0].to(device), data[1].to(device)
        outputs = vgg16_pretrained(images)
        _, predicted = torch.max(outputs.data, 1)
        total += labels.size(0)
        correct += (predicted == labels).sum().item()
print(f'Accuracy on test images: {100 * correct // total}%')
```

Accuracy on test images: 55%

图 8.2: 训练模型 10 个时代后测试集上的准确率

## 优势与局限性

VGG 的优势在于其深度，这带来了丰富的特征表示，以及其统一的架构，简化了学习过程。它是迁移学习和特征提取任务的优秀模型。然而，其局限性包括与 ResNet 或 DenseNet 等利用快捷连接或特征复用以获得更好性能的现代架构相比，计算成本高且效率低。

总而言之，VGG 的引入在 CNN 架构设计中掀起了深度导向的趋势，揭示了深层且丰富的特征层次结构的力量。通过动手实现 PyTorch、通过 TensorBoard 进行观察，以及与训练和评估循环集成，我们发现 VGG 是一种关键架构，推动我们进一步揭示计算机视觉的奥秘。

## 深入探究 ResNet

ResNet（残差网络的缩写）在问世时从根本上改变了深度学习架构的发展方向。由 Kaiming He 及其同事设计，ResNet 解决了退化问题，通过使用快捷连接跳过某些层，使得训练非常深的神经网络成为可能。

### 模型架构与变体

与直接堆叠层的架构不同，ResNet 引入了残差块的概念，其中层参考层输入来学习残差函数。网络变体通常按其深度表示，例如 **ResNet-18**、**ResNet-34**、**ResNet-50**、**ResNet-101** 和 **ResNet-152**。

在 ResNet 中，卷积块后面跟着批归一化和 ReLU 激活函数。然而，关键要素是在激活函数之前添加快捷连接，使网络能够学习恒等函数。这确保了更高层的性能至少不逊于更低层，而不会更差。

### 残差块的优雅之处

残差块通过为反向传播引入直接路径来解决梯度消失问题。这种设计确保梯度可以在网络中流动而不会发生显著退化，从而使得以前无法实现的深层网络成为可能。

### 在 PyTorch 中实现 ResNet

让我们逐步了解 ResNet 的 PyTorch 实现。我们将专注于 ResNet-50，作为深度与计算效率之间的折中方案：

```python
import torch
import torch.nn as nn
from torchvision import models

class BasicBlock(nn.Module):
    expansion = 1
    def __init__(self, in_channels, out_channels, stride=1,
                 downsample=None):
        super(BasicBlock, self).__init__()
        # 1x1 convolutions are used as bottlenecks for reducing and
        # then increasing dimensions,
        # without changing width/height size
        self.conv1 = nn.Conv2d(in_channels, out_channels,
                               kernel_size=1, stride=1, bias=False)
        self.bn1 = nn.BatchNorm2d(out_channels)
        # A 3x3 convolution is used in the middle
        self.conv2 = nn.Conv2d(out_channels, out_channels,
                               kernel_size=3, stride=stride, padding=1, bias=False)
        self.bn2 = nn.BatchNorm2d(out_channels)
        # Another 1x1 convolution with the expansion factor applied
        self.conv3 = nn.Conv2d(out_channels, out_channels *
                               self.expansion, kernel_size=1, stride=1, bias=False)
        self.bn3 = nn.BatchNorm2d(out_channels * self.expansion)
        self.relu = nn.ReLU(inplace=True)
        self.downsample = downsample

    def forward(self, x):
        identity = x if self.downsample is None else self.downsample(x)
        out = self.relu(self.bn1(self.conv1(x)))
        out = self.relu(self.bn2(self.conv2(out)))
        out = self.bn3(self.conv3(out))
        out += identity
        out = self.relu(out)
        return out

class ResNet(nn.Module):
    def __init__(self, block, layers, num_classes=1000):
        super(ResNet, self).__init__()
        self.in_channels = 64
        self.conv1 = nn.Conv2d(3, self.in_channels, kernel_size=7,
                               stride=2, padding=3, bias=False)
        self.bn1 = nn.BatchNorm2d(self.in_channels)
        self.relu = nn.ReLU(inplace=True)
        self.maxpool = nn.MaxPool2d(kernel_size=3, stride=2,
                                    padding=1)

        # Each _make_layer() creates one stage of blocks in ResNet
        self.layer1 = self._make_layer(block, 64, layers[0])
        self.layer2 = self._make_layer(block, 128, layers[1],
                                       stride=2)
        self.layer3 = self._make_layer(block, 256, layers[2],
                                       stride=2)
        self.layer4 = self._make_layer(block, 512, layers[3],
                                       stride=2)

        self.avgpool = nn.AdaptiveAvgPool2d((1, 1))  # Adaptive pooling to fit the final layer
        self.fc = nn.Linear(512 * block.expansion, num_classes)

    def _make_layer(self, block, out_channels, blocks, stride=1):
        downsample = None
        if stride != 1 or self.in_channels != out_channels * block.expansion:
            downsample = nn.Sequential(
                nn.Conv2d(self.in_channels, out_channels *
                          block.expansion, kernel_size=1, stride=stride,
                          bias=False),
                nn.BatchNorm2d(out_channels * block.expansion),
            )

        layers = []
        layers.append(block(self.in_channels, out_channels, stride,
                            downsample))
        self.in_channels = out_channels * block.expansion
        for _ in range(1, blocks):
            layers.append(block(self.in_channels, out_channels))
        return nn.Sequential(*layers)

    def forward(self, x):
        x = self.relu(self.bn1(self.conv1(x)))
        x = self.maxpool(x)
        # ResNet layers
        x = self.layer1(x)
        x = self.layer2(x)
        x = self.layer3(x)
        x = self.layer4(x)

        x = self.avgpool(x)
        x = torch.flatten(x, 1)
        x = self.fc(x)
        return x

def resnet50(num_classes=1000):
    # Constructs a ResNet-50 model
    return ResNet(BasicBlock, [3, 4, 6, 3], num_classes)

# Instantiate a ResNet-50 model
model = resnet50(num_classes=1000)
```

然后可以通过将最后的全连接层更改为输出 100 个类而不是 1000 个，将此模型调整为适用于 CIFAR100 等任务。

## 基础构建模块

ResNet 的架构由多个阶段的残差块组成，这些残差块构成了网络的骨干。每个块包含批归一化、激活层以及赋予该架构名称的标志性跳跃连接。

下面是一个基础残差块 BasicBlock 的简化实现，它是 ResNet-18 和 ResNet-34 等更大 ResNet 配置的一部分：

```python
class BasicBlock(nn.Module):
    expansion = 1
    def __init__(self, in_channels, out_channels, stride=1,
                 downsample=None):
        super(BasicBlock, self).__init__()
        # First convolutional layer
        self.conv1 = nn.Conv2d(in_channels, out_channels,
                               kernel_size=3, stride=stride, padding=1, bias=False)
        self.bn1 = nn.BatchNorm2d(out_channels)
        self.relu = nn.ReLU(inplace=True)
        # Second convolutional layer
        self.conv2 = nn.Conv2d(out_channels, out_channels *
                               BasicBlock.expansion, kernel_size=3, stride=1, padding=1,
                               bias=False)
```
