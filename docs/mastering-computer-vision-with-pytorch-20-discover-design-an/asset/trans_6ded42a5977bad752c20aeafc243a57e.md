


- ratio: 被擦除区域的宽高比范围。

- value: 擦除值。

- inplace: 如果为 True，则变换将就地进行。

### RandomPerspective

```
transforms.RandomPerspective(distortion_scale=0.5, p=0.5,
interpolation=3)
```

执行图像的随机透视变换，给定概率如下所示：

- distortion_scale: 畸变程度。

- p: 图像被变换的概率。

- interpolation: 所需的插值方式。

### CenterCrop

```
transforms.CenterCrop(size)
```

按如下方式裁剪给定图像的中心区域：

- size: 裁剪的期望输出尺寸。

这些只是 PyTorch 中可用的众多增强方法中的一部分。你可以使用 transforms.Compose 将这些变换组合起来，为你的图像创建变换流水线。

## 在 PyTorch 中应用数据预处理

现在让我们来看看计算机视觉中常用的 PyTorch 数据预处理和增强示例。

## PyTorch 数据处理库概览

PyTorch 提供了一系列工具和库，以便于深度学习模型的数据处理，包括 torchvision、transforms 和 DataLoader。以下是对其中一些工具的说明：

- **torchvision**：PyTorch 库中的一个包，包含用于计算机视觉的数据集、模型架构和常见图像变换。

- **transforms**：torchvision 中的一个模块，提供常见图像变换，如旋转、翻转、归一化等。

- **DataLoader**：PyTorch 中的一个模块，提供高效便捷的方式以批次加载和处理数据，自动处理打乱、分批和多进程。

## 深入探究 PyTorch 的数据处理库

torchvision：PyTorch 的 torchvision 是一个包，提供访问流行数据集、模型架构和用于计算机视觉的常见图像变换。torchvision.datasets 模块包含多个基准数据集的加载器，例如 CIFAR10、CIFAR100 和 MNIST 等。这些数据集在训练和测试计算机视觉模型中起着关键作用。

除了数据集，torchvision 还提供一系列预训练模型，例如 ResNet、VGG 和 GoogLeNet，可用于各种计算机视觉任务，包括图像分类、目标检测等。这些预训练模型可作为构建针对特定任务定制模型的起点。

此外，torchvision 包含一系列常见图像变换，可用于数据增强和预处理。这些变换包括调整大小、裁剪、翻转和旋转图像等操作，以及将图像转换为 PyTorch 张量和归一化像素值。

**transforms**：**torchvision** 中的 transforms 模块是图像预处理和增强的强大工具。它提供一系列可应用于图像的变换，以改善模型训练和性能。这些变换可以使用 **transforms.Compose** 组合在一起，从而以无缝高效的方式预处理数据。

一些常见的变换包括：

- **transforms.Resize:** 将图像调整为给定大小。
- **transforms.CenterCrop:** 裁剪图像中心区域。
- **transforms.RandomHorizontalFlip:** 随机水平翻转图像。
- **transforms.ToTensor:** 将图像转换为 PyTorch 张量。
- **transforms.Normalize:** 归一化图像的像素值。

**DataLoader：**
PyTorch 中的 **DataLoader** 是以批次加载和处理数据的必备工具。它通过自动打乱、分批和多进程，为处理大型数据集提供了高效方式。**DataLoader** 与 PyTorch 数据集配合使用，并提供对数据集的可迭代对象，从而方便地与训练循环集成。

### 在 PyTorch 中实现数据预处理

数据预处理在为神经网络准备数据时至关重要。它有助于提高模型的性能和泛化能力。在 PyTorch 中，可以使用 torchvision 中的 transforms 轻松实现数据预处理。

以下是在 PyTorch 中实现数据预处理的示例：

```
import torchvision.transforms as transforms
from torchvision.datasets import ImageFolder
from torch.utils.data import DataLoader

# Define the data preprocessing transformations
transform = transforms.Compose([
    transforms.Resize((224, 224)),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]),
])

# Load the dataset
dataset = ImageFolder(root='path/to/dataset',
transform=transform)

# Create a DataLoader
dataloader = DataLoader(dataset, batch_size=32, shuffle=True,
num_workers=4)
```

在前面的示例中，**transforms.Compose** 用于组合多个图像变换。图像首先被调整为 224x224 像素，然后转换为 PyTorch 张量，最后使用均值和标准差值进行归一化。**ImageFolder** 类用于加载数据集，**DataLoader** 用于创建对数据集的可迭代对象，批次大小为 32，启用打乱，并使用 4 个工作进程加载数据。

数据预处理是准备神经网络训练数据的关键步骤，PyTorch 提供了一系列工具和库以促进这一过程。通过利用 **torchvision**、transforms 和 **DataLoader**，你可以轻松在 PyTorch 中实现数据预处理和增强，从而最终提升深度学习模型的性能。

## 在 PyTorch 中应用数据增强

数据增强是一种在不实际收集新数据的情况下，增加模型训练可用数据多样性的策略。这种技术有助于防止过拟合，并使模型能够更好地泛化到新数据。PyTorch 的 torchvision 库通过 transforms 模块提供了易于使用的数据增强接口。

为演示 PyTorch 中的数据增强，让我们从对名为 test.png 的示例图像应用变换开始。

![](img/6d00092ab1eb61588b90a1b1f5390d1c_182_0.png)

**图 6.1：** 用于可视化增强效果的输入图像

### RandomHorizontalFlip

```
# Flips the image horizontally with a given probability (p=1
in this example).
import matplotlib.pyplot as plt
from torchvision import transforms
from PIL import Image
# Load image
image = Image.open('test.png')
# RandomHorizontalFlip
random_horizontal_flip = transforms.RandomHorizontalFlip(p=1)
h_flipped_image = random_horizontal_flip(image)
# Display
plt.imshow(h_flipped_image)
plt.title('RandomHorizontalFlip')
plt.show()
```

![](img/6d00092ab1eb61588b90a1b1f5390d1c_183_0.png)

图 6.2：水平翻转增强

### RandomVerticalFlip

```
# Flips the image vertically with a given probability (p=1 in this example).
import matplotlib.pyplot as plt
from torchvision import transforms
from PIL import Image
# Load image
image = Image.open('test.png')
# RandomVerticalFlip
random_vertical_flip = transforms.RandomVerticalFlip(p=1)
flipped_image = random_vertical_flip(image)
# Display
plt.imshow(flipped_image)
plt.title('RandomVerticalFlip')
plt.axis('off')
plt.show()
```

![](img/6d00092ab1eb61588b90a1b1f5390d1c_184_0.png)

**图 6.3：垂直翻转增强**

### ColorJitter

```
# Randomly changes the brightness, contrast, saturation, and hue of an image.
import matplotlib.pyplot as plt
from torchvision import transforms
from PIL import Image
# Load image
image = Image.open('test.png')
# ColorJitter
color_jitter = transforms.ColorJitter(brightness=0.5,
contrast=0.5, hue=0.5)
jittered_image = color_jitter(image)
# Display
plt.imshow(jittered_image)
plt.title('ColorJitter')
plt.show()
```

![](img/6d00092ab1eb61588b90a1b1f5390d1c_185_0.png)

**图 6.4：** ColorJitter 增强

### RandomRotation

```
# Rotates the image by a random angle.
import matplotlib.pyplot as plt
from torchvision import transforms
from PIL import Image

# Load image
image = Image.open('test.png')
# RandomRotation
random_rotation = transforms.RandomRotation(degrees=(0, 180))
rotated_image = random_rotation(image)

# Display
plt.imshow(rotated_image)
plt.title('RandomRotation')
plt.axis('off')
plt.show()
```
