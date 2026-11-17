

![](img/6d00092ab1eb61588b90a1b1f5390d1c_242_0.png)

**图 7.12:** 从头训练的模型的混淆矩阵

## 预训练与从头训练的对比

如果我们查看训练输出，可以看到在第一个 epoch 本身，损失的差异就非常大，从预训练权重启动的模型损失为 0.77，而从头训练的模型损失为 1.99。由于预训练模型已经在 ImageNet 数据集上训练过，它已经学习了所有低级特征，不需要为此进行训练。而在从头训练的情况下，权重是随机初始化的，因此所需的训练量要大得多。

另外，当我们查看准确率时，在 5 个 epoch 内，预训练版本能够达到 89% 的准确率，而从头训练的模型只能达到 69.63%。这里还要注意的是，与我们的 SimpleCNN 相比，这些模型表现好得多，因为它们是非常复杂的架构，已被证明在这类图像任务上表现良好。

我们将在关于为选择一个模型而非另一个模型进行 A/B 测试的下一节中，查看其他指标来比较这两个模型。

## 迁移学习对模型性能的影响

迁移学习已经彻底改变了机器学习领域，特别是在计算机视觉领域。通过利用预训练模型，从业者可以启动训练过程，通常会在包括准确率、精确率和召回率在内的各种指标上带来更好的模型性能。

### 定量收益：准确率、精确率和召回率

在讨论迁移学习的定量收益时，我们主要是指模型性能指标的提升。准确率衡量的是被评估案例总数中正确预测的比例。精确率评估模型仅返回相关实例的能力，而召回率衡量模型在数据集中找到所有相关实例的能力。

考虑将在 ImageNet 上预训练的 ResNet 模型用于新任务（例如对 CIFAR-10 数据集中的图像进行分类）的微调示例。从 ImageNet 学习到的丰富特征表示提供了一个起点，通常会导致更高的准确率，因为模型可以从广泛的视觉概念中进行泛化。

下面是一个代码片段，演示使用预训练模型对准确率、精确率和召回率的影响：

```
# Assuming that 'model_ft' is the fine-tuned model and 'model' is trained from scratch
```

```python
from sklearn.metrics import precision_score, recall_score, accuracy_score

# Load the datasets and model
# ... (omitted for brevity)

# Function to get predictions
def get_predictions(loader, model):
    all_predictions = []
    all_targets = []
    model.eval()
    with torch.no_grad():
        for inputs, targets in loader:
            inputs, targets = inputs.to(device), targets.to(device)
            outputs = model(inputs)
            _, predictions = torch.max(outputs, 1)
            all_predictions.extend(predictions.cpu().numpy())
            all_targets.extend(targets.cpu().numpy())
    return all_predictions, all_targets

# Get predictions
predictions_ft, targets_ft = get_predictions(testloader, model_ft)
predictions, targets = get_predictions(testloader, model)

# Calculate metrics
accuracy_ft = accuracy_score(targets_ft, predictions_ft)
precision_ft = precision_score(targets_ft, predictions_ft, average='macro')
recall_ft = recall_score(targets_ft, predictions_ft, average='macro')

accuracy = accuracy_score(targets, predictions)
precision = precision_score(targets, predictions, average='macro')
recall = recall_score(targets, predictions, average='macro')

# Output the metrics
print(f"Fine-tuned Model: Accuracy: {accuracy_ft}, Precision: {precision_ft}, Recall: {recall_ft}")
print(f"From Scratch Model: Accuracy: {accuracy}, Precision: {precision}, Recall: {recall}")
```

我们在训练代码中有类似的片段来获取准确率，但这个片段更进一步，还计算了精确率和召回率。

### 使用迁移学习解决过拟合问题

过拟合是机器学习中的常见问题，模型过度学习了训练数据（包括其噪声和异常值），从而影响了其在未见数据上的性能。迁移学习可以缓解这个问题。预训练模型接触过各种各样的数据，有助于它们更好地泛化。在微调模型时，可能只需要在新数据集上训练最终几层，从而降低了在较小数据集上过拟合的风险。

### A/B 测试 - 微调模型与从头训练模型

为了了解迁移学习的实际影响，我们对两个模型进行了 A/B 测试：一个使用 ImageNet 预训练权重进行微调，另一个从头训练。这种比较分析揭示了迁移学习赋予模型性能的定量优势。

我们首先设置 CIFAR-10 验证数据集并加载两个参赛模型，确保它们在相同条件下进行评估。通过对每个模型调用 get_predictions 函数，我们收集整个验证数据集上的预测结果。

随后，我们为两个模型计算准确率、精确率、召回率和 F1 分数。这些指标作为我们的性能指标，提供了每个模型在分类未见数据时表现如何的洞察。它们不仅提供了模型性能的整体视角，还能指出迁移学习可能带来最大收益的领域。

最后，通过比较这些指标，我们观察到性能差异，这可能表现为微调模型具有更高的准确率和更好的泛化能力。这项 A/B 测试不仅验证了迁移学习的有效性，还为读者自行进行比较研究提供了模板。

通过将这种 A/B 测试方法论纳入您的工作流程，您可以就模型部署做出数据驱动的决策，并更深入地了解迁移学习的实际益处。这种方法充当了理论知识与实际应用之间的桥梁。

```python
import torch
import torchvision
import torchvision.transforms as transforms
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
from torch.utils.data import DataLoader
from torchvision import models

# Assuming 'resnet50_cifar10_finetuned.pth' is the fine-tuned model and 'resnet50_cifar10_scratch.pth' is the from-scratch model
fine_tuned_model_path = 'resnet50_cifar10_finetuned.pth'
scratch_model_path = 'resnet50_cifar10_scratch.pth'

# Device configuration
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')

# Load models
def load_model(model_path):
    model = models.resnet50(pretrained=False)
    num_ftrs = model.fc.in_features
    model.fc = torch.nn.Linear(num_ftrs, 10) # CIFAR-10 has 10 classes
    model.load_state_dict(torch.load(model_path))
    model = model.to(device)
    model.eval()
    return model

# Load both models
fine_tuned_model = load_model(fine_tuned_model_path)
scratch_model = load_model(scratch_model_path)

# CIFAR-10 validation dataset
transform = transforms.Compose([
    transforms.Resize(256),
    transforms.CenterCrop(224),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]),
])

validation_set = torchvision.datasets.CIFAR10(root='./data', train=False, download=True, transform=transform)
validation_loader = DataLoader(validation_set, batch_size=64, shuffle=False)

# Get predictions
def get_predictions(loader, model):
    all_preds = []
    with torch.no_grad():
        for images, _ in loader:
            images = images.to(device)
            outputs = model(images)
            _, preds = torch.max(outputs, 1)
            all_preds.extend(preds.cpu().numpy())
    return all_preds

# Get predictions for both models
fine_tuned_predictions = get_predictions(validation_loader, fine_tuned_model)
```

