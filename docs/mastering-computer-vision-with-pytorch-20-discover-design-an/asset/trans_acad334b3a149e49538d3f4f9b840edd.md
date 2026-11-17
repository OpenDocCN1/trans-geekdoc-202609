
网络。我们将使用以下增强：

```
# Additional augmentations for CIFAR-10 training data
transform_augmented = transforms.Compose([
transforms.RandomCrop(32, padding=4),
transforms.RandomHorizontalFlip(),
transforms.ColorJitter(brightness=0.1, contrast=0.1,
saturation=0.1, hue=0.1),
transforms.ToTensor(),
transforms.Normalize((0.5, 0.5, 0.5), (0.5, 0.5, 0.5)),
])
```

```
# Use the augmented transform for the training dataset
trainset_augmented =
torchvision.datasets.CIFAR10(root='./data', train=True,
download=True, transform=transform_augmented)
trainloader_augmented =
torch.utils.data.DataLoader(trainset_augmented, batch_size=4,
shuffle=True)
```

# 其余训练设置保持不变...

在此，我们不使用像 RandomErase 这样的增强；
CIFAR-10 数据集中的图像非常小（32x32）。评估哪些增强将提高
性能以及哪些增强会以丢失准确训练所需
有价值信息的方式修改图像至关重要。

## 带增强的更新代码

```
# Updated code with new augmentations on the CIFAR-10 dataset
import torch
import torchvision
import torchvision.transforms as transforms
# Set up the transform to normalize the data
transform = transforms.Compose([
transforms.RandomCrop(32, padding=4),
transforms.RandomHorizontalFlip(),
transforms.ColorJitter(brightness=0.1, contrast=0.1,
saturation=0.1, hue=0.1),
transforms.ToTensor(),
transforms.Normalize((0.5, 0.5, 0.5), (0.5, 0.5, 0.5)),
])

# Load the CIFAR-10 dataset
trainset = torchvision.datasets.CIFAR10(root='./data',
train=True, download=True, transform=transform)
trainloader = torch.utils.data.DataLoader(trainset,
batch_size=4, shuffle=True)

testset = torchvision.datasets.CIFAR10(root='./data',
train=False, download=True, transform=transform)
testloader = torch.utils.data.DataLoader(testset,
batch_size=4, shuffle=False)

classes = ('plane', 'car', 'bird', 'cat', 'deer', 'dog',
'frog', 'horse', 'ship', 'truck')

# Define the neural network
import torch.nn as nn
import torch.nn.functional as F

class SimpleCNN(nn.Module):
def __init__(self):
super(SimpleCNN, self).__init__()
self.conv1 = nn.Conv2d(3, 6, 5)
self.pool = nn.MaxPool2d(2, 2)
self.conv2 = nn.Conv2d(6, 16, 5)
self.fc1 = nn.Linear(16 * 5 * 5, 120)
self.fc2 = nn.Linear(120, 84)
self.fc3 = nn.Linear(84, 10)

def forward(self, x):
x = self.pool(F.relu(self.conv1(x)))
x = self.pool(F.relu(self.conv2(x)))
x = x.view(-1, 16 * 5 * 5)
x = F.relu(self.fc1(x))
x = F.relu(self.fc2(x))
x = self.fc3(x)
return x

net = SimpleCNN()

# Compile the model with torch.compile for PyTorch 2.0
compiled_net = torch.compile(net)

# Set up the loss function and optimizer
import torch.optim as optim

criterion = nn.CrossEntropyLoss()
optimizer = optim.SGD(compiled_net.parameters(), lr=0.001,
momentum=0.9)

# Train the network
for epoch in range(5):  # Loop over the dataset multiple times
    running_loss = 0.0
    for i, data in enumerate(trainloader, 0):
        inputs, labels = data
        optimizer.zero_grad()
        outputs = compiled_net(inputs)
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()
        running_loss += loss.item()
        if i % 2000 == 1999:  # Print every 2000 mini-batches
            print('[%d, %5d] loss: %.3f' %
                (epoch + 1, i + 1, running_loss / 2000))
            running_loss = 0.0

print('Finished Training')

# Test the network on the test data
correct = 0
total = 0
with torch.no_grad():
    for data in testloader:
        images, labels = data
        outputs = compiled_net(images)
        _, predicted = torch.max(outputs.data, 1)
        total += labels.size(0)
        correct += (predicted == labels).sum().item()
print('Accuracy of the network on the 10000 test images: %d %%' % (100 * correct / total))
```

![](img/6d00092ab1eb61588b90a1b1f5390d1c_200_0.png)

图 6.14: 在带增强的 CIFAR-10 数据集上训练我们的 SimpleCNN 分类器后的准确率

与之前的版本相比，我们获得了 6% 的提升。尽管 CIFAR-10 数据集中的图像较小，对数据增强的影响有限，但在下一章中，我们将看到影响更显著的案例，并探讨一些局限性和风险。

## 数据增强和预处理的最佳实践

数据增强是一种强大的技术，用于提高机器学习模型的鲁棒性和性能，尤其是在计算机视觉领域。它通过在现有样本上应用随机抖动和扰动来生成新的训练样本，帮助模型从有限的训练数据中更好地泛化。然而，了解何时以及如何有效使用增强至关重要。

### 场景和用例

以下是用例和场景列表：

- **数据不足：** 当数据集太小时，增强可以人为扩大训练集的多样性，有助于防止过拟合，并使模型能够学习更通用的特征。

- **类别不平衡：** 在某些类别表示不足的场景中，增强可以通过生成更多少数类的示例来帮助平衡数据集。

- **模型泛化：** 如果模型在训练数据上表现良好，但在验证或测试数据上表现不佳，增强可以引入更多变异性，鼓励模型学习更鲁棒的特征。

- **现实世界变化：** 对于部署环境会在各种条件下呈现数据的任务（例如，自动导航车辆中的不同光照或天气条件），增强可以在训练期间模拟这些条件。

- **特定领域增强：** 某些任务可能受益于特定于领域的自定义增强。例如，医学图像分析可能使用模仿医学扫描中常见伪影的增强。

### 纳入策略

纳入策略如下：

- **渐进式复杂性：** 从简单的增强开始，例如翻转和旋转，并根据模型的性能逐步引入更复杂的增强。

- **管道多样性：** 实施一组多样的增强以涵盖广泛的变化。但是，确保这些增强与当前问题相关。

- **与测试条件保持一致：** 增强应反映测试期间预期的变化类型。不相关的增强可能导致模型学习无用的特征。

- **资源约束：** 考虑计算成本。更复杂的增强需要额外的处理能力和时间，在所有场景中可能都不合理。

### 局限性和风险

虽然数据增强可以显著改善模型训练，但它并非没有局限性和潜在陷阱。以下是与数据增强相关的局限性和风险：

- **误导模型的风险：** 如果增强不能准确反映现实场景，或应用过于激进，它们可能会引入噪声和误导性信息，从而使模型困惑并降低性能。

- **质量下降：** 过度的增强会降低数据质量。例如，过多的缩放、裁剪或变形可能会导致丢失模型进行准确预测所需的关键特征。

- **计算开销：** 增强会增加计算负担。每个新增强都会增加训练所需的时间，这对于大规模或实时系统来说可能很显著。

- **类别畸变：** 某些增强可能会扭曲类别特定的特征。例如，虽然翻转图像对于一般物体识别可能有益，但它可能会损害阅读文本等任务的性能，在该任务中方向很重要。

- **偏见引入：** 增强可能会无意中在数据集中引入或强化偏见。如果不仔细
