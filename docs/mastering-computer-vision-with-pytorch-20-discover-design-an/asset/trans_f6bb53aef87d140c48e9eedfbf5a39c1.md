
以下是如何替换预训练模型顶层的方法：

```
import torch.nn as nn

# Replace the top layer for fine-tuning
num_features = vgg16.classifier[6].in_features
vgg16.classifier[6] = nn.Linear(num_features, number_of_classes)
# 'number_of_classes' is the number of your new classes
```

在接下来的章节中，我们将探讨如何实现更改类别数量，并利用迁移学习将预训练权重适应不同的任务。

## 将迁移学习应用于视觉任务

开展新的视觉任务时，选择合适的预训练模型至关重要。一个良好的起点是考虑您的任务与模型最初训练所针对的任务之间的相似性。在ImageNet等多样化图像集上训练的模型可以作为很好的通用选择。例如，ResNet-50凭借其深度架构，在复杂性与性能之间取得了平衡，成为许多视觉任务的多功能模型和强大主干网络。

## 迁移学习的数据预处理

在使用预训练模型之前，您的数据必须经过格式化和归一化，以符合模型的输入规范。对于在ImageNet上训练的模型，输入通常被调整为224x224像素，并使用ImageNet数据集的均值和标准差进行归一化。以下是PyTorch中的预处理步骤示例：

```
from torchvision import transforms

# Define the standard ImageNet transformation
preprocess = transforms.Compose([
    transforms.Resize(256),
    transforms.CenterCrop(224),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]),
])
```

应将此变换应用于训练集和验证集，以保持一致性。

## 特征提取：将模型用作固定特征提取器

要将预训练模型用作固定特征提取器，可以冻结除最终分类层之外所有层的权重。为此，除了最后一层的参数外，可将所有参数的**requires_grad**设置为**False**。以下是修改ResNet-50以适应CIFAR-10的方法：

```
from torchvision.models import resnet50
from torch import nn

# Load a pre-trained ResNet-50 model
model = resnet50(pretrained=True)

# Freeze all the layers
for param in model.parameters():
    param.requires_grad = False

# Replace the last layer to match CIFAR-10's classes (10 classes)
num_features = model.fc.in_features
model.fc = nn.Linear(num_features, 10)
```

现在可以使用此模型从CIFAR-10图像中提取特征，并利用这些特征训练一个简单的分类器。

## 微调：使用新数据调整预训练模型

微调不仅涉及替换最终层，还包括使用您的数据集重新训练一些早期层，从而使模型能够适应新特征。当您的数据集足够大且与模型最初训练所用的数据集不同时，这尤其有用。在PyTorch中，微调非常简单：

```
# Assume 'model' is already defined as above
# Unfreeze some of the last layers
for param in list(model.layer4.parameters()) + list(model.fc.parameters()):
    param.requires_grad = True

# Proceed with the training loop
# Define loss function and optimizer
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.SGD(model.parameters(), lr=0.001, momentum=0.9)

# Define your training loop
for epoch in range(num_epochs):
    # Training and update steps here...
    pass
```

在这段代码中，我们解冻了ResNet的最后一个块（layer4）以及全连接层，以便在训练期间对其进行更新。我们将在后面的章节中详细介绍如何进行端到端微调。

## 有效微调的策略

有效的微调需要仔细考虑多个因素，包括：

- **学习率:** 使用较小学习率，以避免可能破坏预训练特征的大幅更新。
- 层选择: 有选择地解冻层，通常是高级别层，因为它们包含更多任务特定的特征。
- 数据增强: 扩充训练数据，为模型提供更丰富的特征供其学习。
- 正则化: 应用丢弃法（dropout）或权重衰减等正则化技术，以防止在新数据集上过拟合。

## 实践代码示例：在CIFAR-10上微调ResNet-50

以下是一段完整的代码片段，展示了如何使用PyTorch在CIFAR-10上微调ResNet-50。

在此示例中，我们将从PyTorch模型库加载ResNet-50的预训练权重。然后，我们将修改最后一层，使其能够在CIFAR-10数据集上运行。

最后，我们将比较运行10个时代后的准确率，以查看它与我们自定义的SimpleCNN以及与从零开始训练相同数量时代的模型相比如何。

```
import torch
import torchvision
import torchvision.transforms as transforms
from torchvision.models import resnet50
from torch import nn

# Data preparation
transform = transforms.Compose([
    transforms.Resize(224),
    transforms.ToTensor(),
    transforms.Normalize((0.5, 0.5, 0.5), (0.5, 0.5, 0.5))
])

trainset = torchvision.datasets.CIFAR10(root='./data', train=True, download=True, transform=transform)
trainloader = torch.utils.data.DataLoader(trainset, batch_size=32, shuffle=True, num_workers=2)
testset = torchvision.datasets.CIFAR10(root='./data', train=False, download=True, transform=transform)
testloader = torch.utils.data.DataLoader(testset, batch_size=32, shuffle=False, num_workers=2)

# Load the pre-trained model and modify it for CIFAR-10
model = resnet50(weights="IMAGENET1K_V2")
# Freeze all layers first
for param in model.parameters():
    param.requires_grad = False
# Unfreeze some layers
for param in list(model.layer4.parameters()) + list(model.fc.parameters()):
    param.requires_grad = True
# Modify the last layer
model.fc = nn.Linear(model.fc.in_features, 10)
# Move the model to GPU if available
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
model.to(device)
# Define loss function and optimizer
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.SGD(filter(lambda p: p.requires_grad, model.parameters()), lr=0.001, momentum=0.9)
# Training loop
num_epochs = 10
for epoch in range(num_epochs):
    model.train()
    running_loss = 0.0
    for i, data in enumerate(trainloader, 0):
        inputs, labels = data
        inputs, labels = inputs.to(device), labels.to(device)
        optimizer.zero_grad()
        outputs = model(inputs)
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()
        running_loss += loss.item()
    print(f'Epoch {epoch + 1}, Loss: {running_loss / len(trainloader)}')

# Save the trained model
torch.save(model.state_dict(), 'finetuned_resnet50_cifar10.pth')

# Function to calculate accuracy
def calculate_accuracy(loader, model):
    correct = 0
    total = 0
    model.eval() # Set the model to evaluation mode
    with torch.no_grad(): # No need to track the gradients
        for data in loader:
            images, labels = data
            images, labels = images.to(device), labels.to(device)
            outputs = model(images)
            _, predicted = torch.max(outputs.data, 1)
            total += labels.size(0)
            correct += (predicted == labels).sum().item()
    accuracy = 100 * correct / total
    return accuracy

# Calculate accuracy on the validation set
val_accuracy = calculate_accuracy(testloader, model)
print(f'Accuracy of the network on the test images: {val_accuracy:.2f}%')
```

时代 1, Loss: 0.7701484623745856
时代 2, Loss: 0.40084931716770983
时代 3, Loss: 0.29910416443733271
时代 4, Loss: 0.22613211420155532
时代 5, Loss: 0.1708905622464386
网络在测试图像上的准确率: 89.34%

图 7.5: 训练预训练模型5个时代的损失及前面脚本输出的准确率

## 实践代码示例：在CIFAR-10上从零开始训练ResNet-50

现在，我们将修改前面的示例，在不使用预训练权重的情况下，在CIFAR-10数据集上从零开始训练ResNet-50模型。该脚本包括数据集设置、模型初始化、训练循环以及测试集评估。

```
import torch
import torchvision
import torchvision.transforms as transforms
import torch.nn as nn
import torch.optim as optim
from torchvision import models

# Set up the transforms for the CIFAR-10 dataset
transform = transforms.Compose([
    transforms.Resize((224, 224)), # Resize images to the size that ResNet expects
    transforms.ToTensor(),
    transforms.Normalize((0.5, 0.5, 0.5), (0.5, 0.5, 0.5))
])

# Load the CIFAR-10 training dataset
trainset = torchvision.datasets.CIFAR10(root='./data', train=True, download=True, transform=transform)
trainloader = torch.utils.data.DataLoader(trainset, batch_size=4, shuffle=True, num_workers=2)
```
