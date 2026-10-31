# Google JAX 秘籍：TensorFlow 和 NumPy 组合功能执行机器学习和数值计算



# 前言
这是一本实用、面向解决方案的书籍，数据科学家、机器学习工程师和人工智能工程师需要它来充分发挥 Google `JAX` 在高效和高级机器学习方面的优势。它涵盖了基本任务、故障排除场景和优化技术，以解决在机器学习和数值计算项目中使用 `JAX` 时遇到的常见挑战。
本书从 `NumPy` 迁移到 `JAX` 开始。它介绍了加速计算、处理数据类型、生成随机数以及执行原地操作的最佳方法。随后展示如何使用分析技术监控计算时间和设备内存，帮助您优化训练和性能。调试部分提供了清晰有效的策略，用于解决常见的运行时问题，包括形状不匹配、`NaNs` 和控制流错误。
本书继续介绍如何掌握 `Pytrees` 进行数据操作，通过外部函数接口 (`FFI`) 集成外部函数，以及利用高级序列化和类型提升技术实现稳定计算。如果您想优化训练流程，本书涵盖了这一需求。它包括高效数据加载、构建自定义神经网络、实现混合精度以及使用 `Penzai` 跟踪实验的配方。您将学习如何可视化模型性能并监控指标，以有效评估训练进度。本书中的配方处理真实场景，使用户能够快速修复问题并微调模型。

### 在本书中你将学习如何：
- 通过从 `NumPy` 迁移到 `JAX` 的优化框架，使计算更快完成。
- 通过分析耗时和内存使用情况，使训练管道更高效。
- 使用调试技术修复诸如形状不匹配和数值不稳定等运行时问题。
- 掌握 `Pytrees` 以在各种机器学习任务中管理复杂嵌套数据结构。
- 使用 `JAX` 的外部函数接口 (`FFI`) 引入外部函数，提升计算能力。
- 利用混合精度训练加速神经网络计算，而不牺牲模型准确性。
- 使用 `Penzai` 保持实验有序。这可以让您重现结果并监控关键指标。
- 使用高级可视化技术，如混淆矩阵和学习曲线，使模型评估更有效。
- 直接在 `JAX` 中创建自己的神经网络和优化器，以便完全控制架构。
- 使用序列化技术高效地保存、加载和传输模型和训练检查点。

# 序言
作为一名机器学习工程师，我经常发现自己面临 `NumPy` 的局限性。它在数值计算方面很出色，但在扩展模型或训练复杂神经网络时就跟不上了。问题不仅仅是速度，尽管速度确实是一个因素。我在自动微分和 GPU 加速方面也遇到困难，这促使我寻找能够满足现代机器学习工作流程需求的替代方案。
就是在那时我发现了 Google `JAX`。`JAX` 通过即时 (`JIT`) 编译提供了更快的执行潜力，还有更多好处。它内置支持自动微分并与硬件加速无缝集成，使其成为有吸引力的选择。与任何工具一样，存在学习曲线和需要克服的障碍。从熟悉的 `NumPy` 世界迁移意味着思维方式和代码结构的改变。很多人在这方面遇到困难，我也不例外。
我受启发撰写《Google JAX Cookbook》，因为我想分享基于我自身经历的这些挑战的实用解决方案。我想创造的不仅仅是一本理论参考——我想汇编一本动手、可操作的书籍，充满实用配方。本书中的每个配方都针对特定问题，提供清晰的解决方案，并提供足够的内容使其有用而不至于让人不知所措。我以一种让您逐步了解可能遇到的不同情况的方式编排了本书，从加速基本数值运算到排查训练问题。
在本书中，我涵盖了分析计算和内存、调试运行时错误以及为不同硬件设置优化神经网络的一些挑战。您还将获得有关如何使用 `Pytrees` 管理数据结构、使用 `JAX` 的外部函数接口 (`FFI`) 集成外部库，甚至使用 `Penzai` 设置实验跟踪以保持项目井然有序的提示。每章都建立在前一章的基础上，复杂性逐渐增加，同时确保您不会迷路。我始终专注于解决现实世界的问题，因为归根结底，这才是最重要的。
我重点关注的主要事情之一是向您展示如何利用 `JAX`。`JAX` 的优势在于其灵活性。一旦您开始理解其细微差别，您会发现它开启了无限可能。您会找到从将高精度切换到混合精度以加速训练，到更有效地管理内存以防止内存不足错误等各方面的提示。所有您需要立即开始的技术。
我写这本书是面向数据科学家、机器学习工程师和人工智能从业者的。如果您正在寻找方法使您的工作流程更快、更高效、更不易出错，这本书是您手边的好资源。让我们一起弄清楚如何使用 `JAX`、修复出现的问题，并看看高级机器学习有什么可能。

![](img/image-z963pbkn.jpg)



# 索引
# 尾声



# GitforGits

## Prerequisites

每位数据科学家、机器学习工程师、人工智能从业者、数据工程师和统计学家都必须在其项目中使用 Google `JAX`。

## Code Usage

是否需要一些有用的代码示例来帮助您进行编程和文档编写？不用再找了！我们的书籍提供了丰富的补充材料，包括代码示例和练习。

不仅本书旨在帮助您完成工作，而且您有权在自己的程序和文档中使用示例代码。但是请注意，如果您复制了代码的很大一部分，我们要求您联系我们以获得许可。

但请放心，在您的程序中使用本书中的几段代码，或通过引用本书并引用示例代码来回答问题，无需获得许可。但如果您选择署名，署名通常包括书名、作者、出版社和 ISBN。例如，“Google JAX Cookbook by Zephyr Quent”。

如果您不确定自己对代码示例的预期使用是否属于合理使用或上述许可范围，请随时联系我们：

我们很乐意提供帮助并澄清任何疑虑。

# Chapter 1: Transition NumPy to JAX

### Overview

从 `NumPy` 过渡到 `JAX` 为机器学习工程师和数据科学家开辟了新的可能性，提供了计算速度和效率的显著提升。本章旨在通过解决常见挑战并介绍 `JAX` 中的关键概念来简化这一过渡。重点在于利用 `JAX` 的高级功能，同时保持 `NumPy` 语法和操作的熟悉度，让您无需陡峭的学习曲线即可提升性能。

在本章中，我们将探讨五个关键主题。首先，我们研究如何使用 `JAX` 的即时编译和自动微分来加速现有的 `NumPy` 代码。接下来，我们解决 `JAX` 中不支持的 `NumPy` 函数问题，并发现合适的替代方案以保留功能。我们讨论随机数生成的有效管理策略，因为 `JAX` 与 `NumPy` 相比存在差异，以确保可重复性和可靠性。原地操作带来的挑战需要在 `JAX` 中采用不同的方法，我们将对此进行说明以帮助您调整编码实践。最后，我们将探讨 `JAX` 的类型提升语义和精度处理，以在过渡期间保持数值稳定性。

为了提供实际背景，我们将介绍 `Fashion-MNIST` 数据集。这是一组表示各种服装项目的灰度图像。该数据集是构建和优化机器学习模型的绝佳测试平台。在整本书中，我们使用它来实现示例和练习，让您能够在真实场景中应用所学概念。我们希望您使用 `Fashion-MNIST` 的工作能够加深您对 `JAX` 的理解，同时培养可直接应用于您自己项目的技能。



# 使用 JAX 加速 NumPy 代码

`Fashion-MNIST` 数据集由 70,000 张各种时尚物品（如 T 恤、裤子和鞋子）的灰度图像组成。每张图像为 28x28 像素，属于十个类别之一。数据集可在此下载。而 `NumPy` 是一个强大的数值计算库，使用它在像 `Fashion-MNIST` 这样的大型数据集上训练机器学习模型可能效率低下且缓慢。缺乏即时 (`JIT`) 编译和自动微分意味着计算在运行时被解释，梯度必须手动计算。挑战在于加速现有的 `NumPy` 代码，以高效处理在 `Fashion-MNIST` 数据集上训练神经网络所涉及的大规模计算。

为克服 `NumPy` 的性能限制，我们可以利用 Google `JAX`。通过将现有的 `NumPy` 代码转换为 `JAX`，可以实现显著的计算加速，并且梯度计算可以简化。这涉及用 `JAX` 的 `NumPy` 替换 `NumPy` 导入，并对代码应用 `JIT` 编译和自动微分。

## 环境设置

首先，确保在你的 Python 环境中安装了 `JAX`：

```
pip install --upgrade "jax[cpu]"
```

### 加载 Fashion-MNIST 数据集

`TensorFlow Datasets` 库提供了访问 `Fashion-MNIST` 等标准数据集的简便接口。请按照以下步骤操作：

```
import tensorflow_datasets as tfds
# Load the dataset
data = tfds.load('fashion_mnist', split=['train', 'test'], as_supervised=True)
train_data, test_data = data
```

## 数据预处理

接下来，你对图像和标签进行预处理以准备训练。为此，归一化图像并将其转换为 `NumPy` 数组。

```
import numpy as np
def preprocess(image, label):
    image = np.array(image) / 255.0  # Normalize pixel values
    image = image.reshape(-1)        # Flatten the image
    label = np.array(label)
    return image, label
# Convert the dataset to NumPy arrays
train_images = []
train_labels = []
for image, label in tfds.as_numpy(train_data):
    img, lbl = preprocess(image, label)
    train_images.append(img)
    train_labels.append(lbl)
train_images = np.array(train_images)
train_labels = np.array(train_labels)
```

## 使用 NumPy 构建简单神经网络

现在，使用 `NumPy` 创建一个具有一个隐藏层的简单神经网络。

```
# Initialize parameters
input_size = 784  # 28x28 pixels flattened
hidden_size = 128
output_size = 10   # 10 classes
np.random.seed(0)
W1 = np.random.randn(input_size, hidden_size) * 0.01
b1 = np.zeros((1, hidden_size))
W2 = np.random.randn(hidden_size, output_size) * 0.01
b2 = np.zeros((1, output_size))
# Activation functions
def relu(x):
    return np.maximum(0, x)
def softmax(x):
    exp_x = np.exp(x - np.max(x, axis=1, keepdims=True))  # Stability improvement
    return exp_x / np.sum(exp_x, axis=1, keepdims=True)
```

## 定义前向和后向传播

创建后，实现前向传播并计算损失。

```
def forward_pass(x):
    z1 = np.dot(x, W1) + b1
    a1 = relu(z1)
    z2 = np.dot(a1, W2) + b2
    y_pred = softmax(z2)
    return y_pred, a1
def compute_loss(y_pred, y_true):
    m = y_true.shape[0]
    log_likelihood = -np.log(y_pred[range(m), y_true])
    loss = np.sum(log_likelihood) / m
    return loss
```

实现后向传播以手动计算梯度。

```
def backward_pass(x, a1, y_pred, y_true):
    global W1, b1, W2, b2
    m = y_true.shape[0]
    y_true_one_hot = np.zeros_like(y_pred)
    y_true_one_hot[np.arange(m), y_true] = 1
    dz2 = y_pred - y_true_one_hot
    dW2 = np.dot(a1.T, dz2) / m
    db2 = np.sum(dz2, axis=0, keepdims=True) / m
    da1 = np.dot(dz2, W2.T)
    dz1 = da1 * (a1 > 0)
    dW1 = np.dot(x.T, dz1) / m
    db1 = np.sum(dz1, axis=0, keepdims=True) / m
    # Update parameters
    learning_rate = 0.01
    W1 -= learning_rate * dW1
    b1 -= learning_rate * db1
    W2 -= learning_rate * dW2
    b2 -= learning_rate * db2
```

## 训练模型

现在，是时候使用手动的前向和后向传播来训练模型了。

```
num_epochs = 5
batch_size = 64
for epoch in range(num_epochs):
    permutation = np.random.permutation(train_images.shape[0])
    train_images_shuffled = train_images[permutation]
    train_labels_shuffled = train_labels[permutation]
    for i in range(0, train_images.shape[0], batch_size):
        x_batch = train_images_shuffled[i:i+batch_size]
        y_batch = train_labels_shuffled[i:i+batch_size]
        y_pred, a1 = forward_pass(x_batch)
        loss = compute_loss(y_pred, y_batch)
        backward_pass(x_batch, a1, y_pred, y_batch)
    print(f"Epoch {epoch+1}, Loss: {loss}")
```

也有观察到，使用 `NumPy` 训练模型可能很慢，这是由于梯度的手动计算以及缺乏 `JIT` 编译。执行时间随着数据集增大和模型更复杂而显著增加，使得其不适用于大规模机器学习任务。

## 将 NumPy 代码转换为 JAX

为加速代码，将其转换为使用 `JAX`。这涉及导入 `JAX` 的 `NumPy` 并利用其 `JIT` 编译和自动微分功能。为此，用 `JAX` 的 `NumPy` 替换 `NumPy` 导入并导入必要的 `JAX` 函数。

```
import jax.numpy as jnp
from jax import grad, jit, random
from functools import partial
```

之后，更新激活函数和模型函数以使用 `JAX` 的 `NumPy`。

```
# Initialize parameters with JAX
key = random.PRNGKey(0)
W1 = random.normal(key, (input_size, hidden_size)) * 0.01
b1 = jnp.zeros((1, hidden_size))
W2 = random.normal(key, (hidden_size, output_size)) * 0.01
b2 = jnp.zeros((1, output_size))
def relu(x):
    return jnp.maximum(0, x)
def softmax(x):
    exp_x = jnp.exp(x - jnp.max(x, axis=1, keepdims=True))
    return exp_x / jnp.sum(exp_x, axis=1, keepdims=True)
```

然后，使用 `JAX` 定义损失函数。

```
def compute_loss(params, x, y):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = relu(z1)
    z2 = jnp.dot(a1, W2) + b2
    y_pred = softmax(z2)
    m = y.shape[0]
    log_likelihood = -jnp.log(y_pred[jnp.arange(m), y])
    loss = jnp.sum(log_likelihood) / m
    return loss
```

接下来，使用 `JAX` 的 `grad` 函数自动计算梯度。

```
grad_loss = grad(compute_loss)
```

之后，对训练步骤函数应用 `JIT` 编译。

```
@jit
def update(params, x, y, learning_rate=0.01):
    grads = grad_loss(params, x, y)
    params = [param - learning_rate * grad for param, grad in zip(params, grads)]
    return params
```

最后，使用优化的 `JAX` 函数训练模型。

```
params = [W1, b1, W2, b2]
num_epochs = 5
batch_size = 64
for epoch in range(num_epochs):
    permutation = np.random.permutation(train_images.shape[0])
    train_images_shuffled = train_images[permutation]
    train_labels_shuffled = train_labels[permutation]
    for i in range(0, train_images.shape[0], batch_size):
        x_batch = train_images_shuffled[i:i+batch_size]
        y_batch = train_labels_shuffled[i:i+batch_size]
        params = update(params, x_batch, y_batch)
    current_loss = compute_loss(params, x_batch, y_batch)
    print(f"Epoch {epoch+1}, Loss: {current_loss}")
```

通过将代码转换为 `JAX` 并利用自动微分和 `JIT` 编译，可以实现训练时间的显著加速。使用 `grad` 简化了梯度计算，而 `@jit` 装饰器加速了训练循环的执行。此外，`JAX` 操作设计为可在 CPU、GPU 和 TPU 上高效运行。这使得尝试更复杂的模型或更大数据集成为可能。

通过遵循这种方法，现有的 `NumPy` 代码可以使用 Google `JAX` 有效加速，从而能够在 `Fashion-MNIST` 等数据集上高效处理大规模计算和复杂机器学习模型。



# 在 JAX 中处理不受支持的 NumPy 函数

当从 NumPy 迁移到 Google JAX 时，某些 NumPy 函数可能在 JAX 的 NumPy API 中不可用，导致兼容性问题。Functions like 和一些原地操作在 JAX 中不直接受支持，因为它强调函数式编程和不可变性。目标是找到替代方法或变通方案，以在 JAX 中替换不受支持的 NumPy 函数，同时保持代码的原始功能。

假设我们有一个基于 NumPy 的神经网络实现，它使用 `np.random.shuffle` 在每个 epoch 之前打乱训练数据。在 JAX 中，由于其函数式编程设计，`jax.random` 没有 `np.random.shuffle` 的直接等价物。我们需要在 JAX 中找到一种替代方法来打乱数据。

## 识别不受支持的函数

首先，识别 NumPy 代码中在 JAX 中不受支持的函数。以下是常见的不受支持的函数：

原地操作（例如，
某些线性代数函数（例如，
依赖于突变或副作用的函数

## 替换 `np.random.shuffle`

在原始 NumPy 代码中，数据打乱可能执行如下：

```
np.random.shuffle(train_images)
np.random.shuffle(train_labels)
```

这种原地打乱与 JAX 的函数式方法不兼容。相反，我们可以使用 JAX 的 `random.permutation` 函数来实现相同的效果，而无需原地突变。

### 使用 JAX 的 `random.permutation`

```
from jax import random
# Assume 'key' is a PRNGKey initialized earlier
key, subkey = random.split(key)
permutation = random.permutation(subkey, train_images.shape[0])
train_images_shuffled = train_images[permutation]
train_labels_shuffled = train_labels[permutation]
```

这里，`random.permutation` 生成索引的排列，我们用它来索引训练数据数组 `train_images` 和 `train_labels`，从而有效地打乱它们。此方法避免了原地操作并遵循 JAX 的函数式编程风格。

## 替换不受支持的线性代数函数

假设代码依赖于 `np.linalg.eig` 来计算特征值和特征向量，该函数在 中不可用 Then，我们需要采用以下替代方法：

- 对于对称或厄米矩阵，可以使用 `eigh` 代替 
- 创建自定义函数来近似特征值和特征向量。
- 使用在 JAX 中受支持的奇异值分解。

以下是使用 SVD 替换的快速示例：

```
# Original NumPy code
eigenvalues, eigenvectors = np.linalg.eig(matrix)
# JAX replacement
u, s, vh = jnp.linalg.svd(matrix)
```

使用奇异值分解可以在不使用不受支持的 `eig` 函数的情况下获得对矩阵特征的类似洞察。

## 处理原地操作

原地操作在 NumPy 中很常见，但与 JAX 不兼容。例如：

```
# NumPy in-place operation
array *= scale_factor
```

在这里，我们需要避免原地修改数组。相反，我们可以执行操作并将结果赋给一个新变量。

```
array = array * scale_factor
```

通过将结果重新赋给 `array`，我们保持了 JAX 的函数式编程范式。

## 处理高级索引和赋值

假设代码使用高级索引根据条件修改数组元素：

```
# NumPy code
array[array > threshold] = new_value
```

我们可以使用 `jax.numpy.where` 函数在不进行原地修改的情况下实现相同的结果。

```
array = jnp.where(array > threshold, new_value, array)
```

这会创建一个新数组，其中满足条件的元素被替换为 `new_value`，而其他元素保持不变。

## 处理随机数生成函数

NumPy 中的某些随机数生成函数在 JAX 中没有直接等价物。例如，`np.random.choice` 用于从数组中选择随机样本。在 JAX 中，我们可以使用可用的随机函数实现类似功能。

以下是快速示例：

```
# NumPy code
samples = np.random.choice(array, size=sample_size, replace=False)
# JAX replacement
key, subkey = random.split(key)
indices = random.choice(subkey, array.shape[0], shape=(sample_size,), replace=False)
samples = array[indices]
```

通过使用 `random.choice` 生成随机索引，我们可以在不直接使用 `np.random.choice` 的情况下从数组中选择随机样本。

## 实现自定义函数

如果不存在直接的替代方案，我们可能需要实现与 JAX 兼容的自定义函数。例如，如果我们需要一个计算矩阵指数的函数，而该函数在 JAX 中不可用，我们可以按如下方式创建自定义实现：

```
def matrix_exponential(a):
    # Simple implementation using the Padé approximant
    identity = jnp.eye(a.shape[0])
    a2 = jnp.dot(a, a)
    a4 = jnp.dot(a2, a2)
    numerator = identity + a + (1/2)*a2 + (1/6)*jnp.dot(a2, a)
    denominator = identity - a + (1/2)*a2 - (1/6)*jnp.dot(a2, a)
    exp_a = jnp.dot(jnp.linalg.inv(denominator), numerator)
    return exp_a
```

上述内容是一个简化的示例。对于生产代码，我建议考虑更稳健的实现或库。

## 使用与 JAX 兼容的第三方库

有一些库扩展了 JAX 的功能并提供额外的特性，例如 `jax.scipy`，它提供科学计算函数，这些函数在 中不可用

以下是使用 `jax.scipy` 的快速示例：

```
from jax.scipy.linalg import expm
# Compute the matrix exponential
exp_a = expm(matrix)
```

通过以上方法，我们可以访问诸如 `expm` 之类的函数来计算矩阵指数。

## 重构代码以符合 JAX 的范式

有些依赖于副作用或全局状态的函数需要重构。例如，考虑一个更新全局计数器的函数：

```
counter = 0
def increment_counter(x):
    global counter
    counter += 1
    return x + counter
```

上述函数与 JAX 的变换不兼容。相反，我们可以将计数器作为参数传递并返回更新后的值，如下所示。

```
def increment_counter(x, counter):
    counter += 1
    return x + counter, counter
```

通过避免全局状态和副作用，该函数变得与 JAX 的 JIT 编译和自动微分兼容。

部署这些策略能够有效管理 JAX 中不受支持的 NumPy 函数，确保保留原始代码的功能，同时利用 JAX 的性能增强。



# 管理随机数生成

在 `NumPy` 中，随机性通过全局随机状态进行管理，如果处理不当可能导致非确定性行为。Google `JAX`，然而，采用了不同的随机数生成方法，强调函数式纯度和显式状态管理。这种差异会给从 `NumPy` 转向的用户带来不确定性，使得生成可复现的结果变得困难。任务是理解 `JAX` 使用 `PRNG`（伪随机数生成器）键处理随机性的方法，并学习如何有效使用这些键以确保涉及 `Fashion-MNIST` 数据集的实验中结果一致且可复现。

## 理解 JAX 的 PRNG 键

在 `JAX` 中，随机性通过 `jax.random` 模块处理，该模块提供了生成随机数的函数。这些函数需要一个 `PRNG` 键作为输入，并返回随机数和用于后续使用的新的 `PRNG` 键。`PRNG` 键是一个封装随机状态的 `jax.random.PRNGKey` 对象。通过显式管理这些键，我们能够控制计算中固有的随机性。

### 初始化 PRNG 键

第一步是导入 `JAX` 的随机模块并使用种子值初始化 `PRNG` 键。`seed` 值保证在多次运行中生成相同的随机数序列。

```
import jax
from jax import random
# Initialize a PRNG key with a seed
seed = 42
key = random.PRNGKey(seed)
```

此 `key` 将在整个程序中用于生成随机数。`seed` 值可以是任意整数，并作为随机数生成器的起点。

## 生成随机数

应使用 `PRNG` 键来生成随机数。例如，这可用于初始化模型参数或创建数据的随机排列。

```
# Generating random weights for model initialization
key, subkey = random.split(key)
W = random.normal(subkey, shape=(input_size, hidden_size)) * 0.01
# Generating random biases
key, subkey = random.split(key)
b = random.normal(subkey, shape=(hidden_size,)) * 0.01
```

在此代码中，`random.split()` 用于将 `key` 分成两个新键：一个用于生成随机数，一个用于未来的操作。

## 无需原地操作地打乱数据

现在打乱数据时，避免原地操作很重要。因此，这里使用 `JAX` 的 `random.permutation()` 函数并传入 `PRNG` 键。

```
# Shuffling training data
key, subkey = random.split(key)
perm = random.permutation(subkey, train_images.shape[0])
train_images_shuffled = train_images[perm]
train_labels_shuffled = train_labels[perm]
```

生成索引的随机排列可在不原地修改它们的情况下重新排列数据数组。这种方法符合 `JAX` 的函数式编程方法，并确保结果的可复现性。

## 确保模型训练的可复现性

建议将 `PRNG` 键纳入涉及随机性的函数中以确保可复现性。为说明，当定义训练步骤函数时，应将 `key` 作为参数传递，如下所示：

```
@jit
def train_step(params, x, y, key, learning_rate=0.01):
    key, subkey = random.split(key)
    # Use subkey for any randomness within the function
    loss, grads = compute_loss_and_grads(params, x, y, subkey)
    params = [param - learning_rate * grad for param, grad in zip(params, grads)]
    return params, key
```

`key` 被传入函数并返回更新后的 `key`，从而保持对随机状态的控制。这种方法保证在采用相同输入时每个训练阶段都是确定的。

### 在数据增强中使用 PRNG 键

数据增强过程经常涉及随机变换的实现。应使用 `PRNG` 键以确保这些变换的一致应用。

```
def augment_data(x, key):
    key, subkey = random.split(key)
    # Apply random rotation
    angle = random.uniform(subkey, minval=-0.1, maxval=0.1)
    x_rotated = rotate_image(x, angle)
    return x_rotated, key
```

这里，`rotate_image()` 是一个假设的函数，用于按给定角度旋转图像。通过传递 `key` 并更新它，我们确保随机性受控且可复现。

### 在循环中管理 PRNG 键

使用循环时，在每次迭代中更新 `PRNG` 键以防止重复使用并保持随机性。

```
key = random.PRNGKey(seed)
params = initialize_params(key)
for epoch in range(num_epochs):
    key, subkey = random.split(key)
    train_images_shuffled, train_labels_shuffled = shuffle_data(train_images, train_labels, subkey)
    for batch in get_batches(train_images_shuffled, train_labels_shuffled, batch_size):
        x_batch, y_batch = batch
        key, subkey = random.split(key)
        params, key = train_step(params, x_batch, y_batch, subkey)
```

通过持续更新 `key`，我们防止意外重复使用，这可能会损害结果的随机性和可复现性。

### 将 PRNG 键与 JIT 编译结合

现在当函数被编译时，必须特别注意 `PRNG` 键，因为 `JIT` 编译的函数会根据输入形状和类型缓存其结果。

```
@jit
def compute_loss_and_grads(params, x, y, key):
    y_pred = model_forward(params, x)
    loss = cross_entropy_loss(y_pred, y)
    grads = grad(loss_fn)(params, x, y)
    return loss, grads
```

由于 `key` 是输入，如果 `key` 的值发生变化，函数将重新编译。为了避免过度重新编译，请构建代码以最小化 `key` 形状和类型的变化。

### 存储和恢复 PRNG 键

如果需要暂停和恢复实验，请将 `PRNG` 键与模型参数一起存储以保持可复现性。

```
# Saving the state
state = {'params': params, 'key': key}
save_checkpoint(state, filename)
# Restoring the state
state = load_checkpoint(filename)
params = state['params']
key = state['key']
```

通过保存 `key`，您可确保随机状态在会话之间得以保留。

## 在多进程环境中使用 `jax.random.fold_in`

在分布式或多进程设置中，使用 `jax.random.fold_in()` 为每个进程创建唯一键。

```
process_id = get_process_id()
key = random.PRNGKey(seed)
key = random.fold_in(key, process_id)
```

此方法将进程 ID 纳入 `key`，为每个进程生成不同的随机数序列，同时保持可复现性。

通过理解并实施 `JAX` 中 `PRNG` 键的有效管理策略，可以保证机器学习实验的可复现性和一致性。这种策略有助于提高所获得结果的可靠性，同时促进涉及 `Fashion-MNIST` 数据集项目的调试和验证过程。



# 处理原地操作

在将代码从 `NumPy` 迁移到 `Google JAX` 以处理数据集的过程中，可能会遇到与原地操作相关的挑战。原始的 `NumPy` 代码可能侧重于直接修改数组以提高效率，例如更新 `weights` 或就地应用转换。然而，这是因为 `JAX` 不支持原地操作，这是其强调不可变性和纯函数的函数式编程范式的结果。这意味着像 `array *= scalar` 或 `array[index] = value` 这样的操作与 `JAX` 的即时编译和自动微分不兼容。挑战在于重构现有代码以消除原地操作，同时保持功能和性能。

为了解决此问题，必须重构代码以消除原地操作。这可以通过采用函数式编程技术来实现。这要求函数以规避副作用的方式重写，并在不修改现有内容的情况下返回新数组。因此，代码变得与 `JAX` 的要求兼容，从而能够使用 JIT 编译和自动微分。必须细致关注数据传递和修改的方式，目标是保持每个函数作为纯粹且无状态实体的完整性。

## 理解原地操作与 JAX 的范式

原地操作直接修改数据，改变变量或数组的状态。示例包括像 `array += value` 这样的赋值或像 `array[i] =` 这样的逐元素更新。相比之下，函数式编程提倡不可变性，即数据在创建后不会被更改。函数基于输入返回新的数据结构，且无副作用。`JAX` 遵循这一范式以实现强大的转换和优化。

考虑一个神经网络训练循环，其中参数更新是就地进行的：

```
# Original NumPy code with in-place updates
for param, grad in zip(params, grads):
    param -= learning_rate * grad
```

此代码直接修改 `param`，这在 `JAX` 中是不允许的。尝试使用此原地操作将导致错误。

## 使用函数式更新重构代码

为重构代码，我们创建一个函数来计算更新后的参数，而不修改原始参数：

```
# JAX-compatible code without in-place updates
def update_params(params, grads, learning_rate):
    return [param - learning_rate * grad for param, grad in zip(params, grads)]
```

在训练循环中，我们使用返回的列表重新分配参数：

```
# Training loop with functional updates
params = initialize_params()
for epoch in range(num_epochs):
    for x_batch, y_batch in data_loader:
        grads = compute_gradients(params, x_batch, y_batch)
        params = update_params(params, grads, learning_rate)
```

通过避免原地修改，代码符合 `JAX` 的函数式方法。

## 处理原地数组修改

假设我们需要通过减去均值并除以标准差来归一化数据，并就地修改数组：

```
# In-place normalization (NumPy code)
data -= data.mean(axis=0)
data /= data.std(axis=0)
```

然后，重构此代码以避免原地操作：

```
# JAX-compatible normalization
def normalize(data):
    mean = data.mean(axis=0)
    std = data.std(axis=0)
    return (data - mean) / std
normalized_data = normalize(data)
```

之后，通过返回新数组，我们保持不可变性。

## 重构条件原地更新

在元素被条件更新的情况下，例如裁剪值：

```
# In-place clipping (NumPy code)
weights[weights > max_value] = max_value
```

使用 `JAX` 的函数式操作：

```
# JAX-compatible clipping
weights = jnp.minimum(weights, max_value)
```

或者，使用

```
weights = jnp.where(weights > max_value, max_value, weights)
```

这些方法在不修改原始内容的情况下创建新数组。

## 避免原地累积

在涉及累积的算法中，例如求和梯度：

```
# In-place accumulation (NumPy code)
total_grad += batch_grad
```

我们将上述内容重构为：

```
# Functional accumulation
total_grad = total_grad + batch_grad
```

或者，使用归约函数：

```
# Summing over a list of gradients
total_grad = jnp.sum(grads_list, axis=0)
```

## 使用 `jax.ops.index_update` 进行索引更新

对于更新特定索引，已弃用的 `jax.ops.index_update` 已被 `at` 方法取代：

```
# Original in-place indexing update (NumPy code)
array[index] = value
# JAX-compatible update
array = array.at[index].set(value)
```

这会返回具有指定更新的新数组。

## 重构具有原地修改的循环

考虑一个就地修改数组的循环：

```
# In-place modification in loop (NumPy code)
for i in range(len(array)):
    array[i] *= scale_factors[i]
```

现在使用函数式编程重构它：

```
# JAX-compatible code
scaled_array = array * scale_factors
```

通过利用向量化操作，我们消除了对显式循环和原地修改的需求。

通过系统地重构相关代码，可以消除原地操作，从而允许充分利用 `Google JAX` 在机器学习项目中的功能。这种方法保证了生成的代码既高效又可扩展，并符合函数式编程的现代实践。



# 在迁移过程中确保数值稳定性

在将机器学习模型从 `NumPy` 迁移到 `Google JAX` 用于 `Fashion-MNIST` 数据集后，观察到数值不稳定问题。这些问题表现为计算过程中出现意外的 `NaN` (Not a Number) 或无穷值，这可能会中断训练或产生错误结果。这种不稳定性可能源于 `JAX` 处理数据类型和算术运算的方式与 `NumPy` 不同。具体来说，`JAX` 的类型提升语义可能导致意外的 数据类型转换，影响计算的精度和稳定性。挑战在于理解这些差异并有效管理数据类型，以确保在 `JAX` 中进行稳定可靠的计算。

为了应对迁移到 `JAX` 后观察到的数值不稳定问题，清楚地理解 `JAX` 使用的类型提升语义以及其与 `NumPy` 表现的行为有何不同至关重要。通过以显式方式管理数据类型并保证一致的精度，可以实现计算的数值稳定性。此过程涉及检查数组和变量相关的数据类型、在需要时指定适当的数据类型，以及谨慎对待可能导致意外类型提升的操作。

## 理解 JAX 的类型提升语义

`JAX` 在算术运算期间遵循特定的类型提升规则，这可能与 `NumPy` 的规则不同。在 `JAX` 中，涉及混合精度的操作可能导致提升到更高精度类型，可能导致内存使用增加和精度问题。例如，将 `float32` 数组与 `float64` 标量结合可能将结果提升到影响计算效率和稳定性。

### 检查数据类型

第一步是确定参与计算的所有输入数组和变量的数据类型。必须保证这些值的精度为期望值，对于神经网络通常为 `float32`。

```
import jax.numpy as jnp
# Inspect data types
print(f"Data type of training images: {train_images.dtype}")
print(f"Data type of training labels: {train_labels.dtype}")
```

如果数据类型不符合预期，请显式转换它们。

## 显式转换数据类型

接下来，使用以下方法将数组转换为所需的数据类型

```
# Convert data types to float32
train_images = train_images.astype(jnp.float32)
test_images = test_images.astype(jnp.float32)
# Convert labels to int32 if necessary
train_labels = train_labels.astype(jnp.int32)
test_labels = test_labels.astype(jnp.int32)
```

## 使用一致的类型初始化模型参数

现在，在初始化模型参数（如权重和偏置）时，需要指定数据类型以确保一致性。

```
from jax import random
key = random.PRNGKey(seed)
# Initialize weights and biases with float32 data type
W1 = random.normal(key, (input_size, hidden_size), dtype=jnp.float32) * 0.01
b1 = jnp.zeros((hidden_size,), dtype=jnp.float32)
W2 = random.normal(key, (hidden_size, output_size), dtype=jnp.float32) * 0.01
b2 = jnp.zeros((output_size,), dtype=jnp.float32)
```

## 确保计算中数据类型一致

在这里，在模型的正向传递和损失计算中，确保操作以一致的数据类型执行。

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    x = x.astype(jnp.float32)
    z1 = jnp.dot(x, W1) + b1
    a1 = relu(z1)
    z2 = jnp.dot(a1, W2) + b2
    y_pred = softmax(z2)
    return y_pred
```

### 处理除法和对数运算

执行除法和对数等操作时必须谨慎，因为如果处理不当，它们可能会引入数值不稳定。建议在分母或对数参数中添加微小常数（`ε`）以防止除零或计算零的对数。

```
epsilon = 1e-7
def compute_loss(params, x, y):
    y_pred = forward_pass(params, x)
    m = y.shape[0]
    y_pred = jnp.clip(y_pred, epsilon, 1.0 - epsilon)
    log_likelihood = -jnp.log(y_pred[jnp.arange(m), y])
    loss = jnp.mean(log_likelihood)
    return loss
```

现在，在这里，请注意涉及文字或常量的操作。例如，用整数文字除法可能会导致意外的类型提升。

```
# Potential unintended promotion to float64
result = array / 255
# Corrected to maintain float32
result = array / 255.0
```

确保在必要时将常量指定为浮点数。

## 使用 JAX 的类型提升规则并监控 NaN

了解 `JAX` 根据某些规则提升类型。例如，`float16` 和 `float32` 之间的操作提升到使用此知识来控制计算的精度。

```
# Ensuring operations stay in float32
array1 = array1.astype(jnp.float32)
array2 = array2.astype(jnp.float32)
result = array1 + array2
```

计算后，检查是否存在 `NaN` 或无穷值，这表明数值不稳定。

```
# Checking for NaNs and infinities
if jnp.isnan(loss) or jnp.isinf(loss):
    print("Numerical instability detected in loss computation.")
```

如果检测到，请调查之前的计算以确定来源。

## 实现梯度裁剪

在训练期间，大的梯度可能会导致更新，从而导致数值不稳定。应用梯度裁剪以限制梯度的大小。

```
from jax import tree_util
def clip_grads(grads, max_norm):
    total_norm = jnp.sqrt(sum([jnp.sum(jnp.square(g)) for g in tree_util.tree_leaves(grads)]))
    clip_coef = jnp.minimum(1.0, max_norm / (total_norm + 1e-6))
    grads = tree_util.tree_map(lambda g: g * clip_coef, grads)
    return grads
# Applying gradient clipping during the update
grads = grad_loss(params, x_batch, y_batch)
grads = clip_grads(grads, max_norm=1.0)
```

如果数值不稳定性仍然存在，请考虑对关键计算使用更高精度的数据类型，如 `float64`。但是，请注意，这会增加内存使用和计算时间。

```
# Using float64 for critical computations
x = x.astype(jnp.float64)
```

为了确保一致性，相关变量必须全部转换为 `float64`。



## 摘要
总之，本章重点关注从 `NumPy` 到 Google `JAX` 在机器学习任务中的迁移。它首先演示了如何通过即时编译和自动微分将现有 `NumPy` 代码转换为 `JAX` 来加速代码。这带来了显著的性能提升，使得神经网络训练更快，而无需重写代码。接下来，解决了 `JAX` 中不支持的 `NumPy` 函数带来的挑战。我们还研究了在仍保留代码原始功能的同时替换这些函数的传统方式。这样确保了兼容性，并使 `JAX` 能够无缝集成到现有工作流程中。

一个重要主题是 `JAX` 的随机数生成，它与 `NumPy` 不同。在这里，我们能够学习 `PRNG` 键的有效使用以及结果的可重复性。我们还解决了原地操作的问题。由于其函数式编程范式，`JAX` 不支持这些操作。代码被重构以消除这些操作，采用避免副作用并强调不可变性的风格。这种重构不仅使代码与 `JAX` 兼容，还提高了其清晰度和可维护性。

最后，在从 `NumPy` 迁移过程中，我们必须确保数值稳定性。一种不稳定性的来源被确定为两个库之间类型提升语义的差异。通过显式管理数据类型并谨慎处理可能导致非预期类型提升的操作，实现了稳定的计算。诸如数据类型指定、谨慎处理除法和对数以及梯度裁剪等技术被用来避免训练中出现 `NaN` 和无界值等问题。

# 第 2 章：计算分析与设备内存管理

## 概述
本章将重点转向在利用 Google `JAX` 进行机器学习任务时计算的分析以及设备内存的管理。测量 `JAX` 函数的执行时间能够评估计算效率，并为提高处理速度提供有据的决策依据，尤其是在处理与 `Fashion-MNIST` 类似的数据集时。

监控 `GPU` 内存使用情况也有助于防止内存不足错误并确保硬件资源的最佳利用。本节探讨内存消耗模式，以确定其在管理计算工作负载方面的有效性。这种理解对于扩展模型并处理更大的数据集而不影响性能至关重要。随后，我们研究表示计算图的技术，以便更深入地理解 `JAX` 模型中底层操作和数据流。这些图的可视化有助于更全面地理解计算的依赖关系和结构，这对调试和优化工作有益。本章讨论的另一个关键主题是批大小的优化。调整批大小有可能显著提高训练效率和资源利用率。

最后，本章介绍了梯度检查点作为在模型训练期间减少内存占用的一种技术。通过以策略性的方式保存中间激活，并在反向传播期间重新计算它们，梯度检查点使得在不超出内存限制的情况下训练更深、更复杂的模型成为可能。



# 测量 JAX 函数的执行时间

在之前的章节中，开发了各种 JAX 代码来在 Fashion-MNIST 数据集上训练神经网络。虽然 JAX 通过即时编译和自动微分在性能上比 NumPy 提供了显著的提升，但代码中的某些部分仍可能包含阻碍最佳性能的瓶颈。识别这些瓶颈对于优化代码以实现更快的执行时间和更高效的资源利用至关重要。挑战在于系统地测量 JAX 函数的执行时间并找出需要优化的代码部分。

为了识别和优化 JAX 代码中的性能瓶颈，至关重要的是利用能够测量执行时间并分析计算效率的分析工具。JAX 提供了内置的计时函数，而 Python 提供了诸如 `line_profiler` 之类的分析库，可用于收集详细的性能指标。通过将这些工具应用于之前开发的神经网络代码，可以获得有关哪些函数或操作消耗最多时间和资源的见解。这些信息允许实施有针对性的优化工作，从而提高整体性能。

## 识别需要分析的函数

建议首先回顾之前讨论的配方中的神经网络代码，特别关注训练中涉及的关键函数：

-   `forward_pass(params, ...)` 计算模型的预测结果。
-   `compute_loss(params, x, ...)` 计算预测结果与真实标签之间的损失。
-   `update(params, x, ...)` 使用梯度更新模型参数。

这些函数对训练循环至关重要，是评估其执行时间的分析的理想候选对象。

## 使用 JAX 的内置计时函数

有一种简单的方法来测量函数执行时间使用。然而，更直接的方法是使用 Python 的 `time` 模块进行初始计时测量。

```python
import time
# Timing the forward_pass function
start_time = time.time()
y_pred = forward_pass(params, x_batch)
end_time = time.time()
print(f"Execution time of forward_pass: {end_time - start_time} seconds")
```

此方法可提供有关 `forward_pass` 函数在给定数据批次下执行所需时间的初步了解。

## 使用 `timeit` 和 `cProfile` 进行分析

`timeit` 模块通过多次运行函数并取平均值来提供更准确的计时。

```python
import timeit
# Define a wrapper function for timeit
def time_forward_pass():
    y_pred = forward_pass(params, x_batch)
# Measure execution time
execution_time = timeit.timeit(time_forward_pass, number=100) / 100
print(f"Average execution time of forward_pass: {execution_time} seconds")
```

通过重复执行函数，`timeit` 缓解了瞬态系统负载的影响并提供了更可靠的测量结果。

对于更详细的分析，可以使用 `cProfile` 模块来分析整个训练循环。

```python
import cProfile
import pstats
import io
pr = cProfile.Profile()
pr.enable()
# Training loop to profile
for epoch in range(num_epochs):
    # Training code as implemented previously
    pass
pr.disable()
s = io.StringIO()
ps = pstats.Stats(pr, stream=s).sort_stats('cumulative')
ps.print_stats()
# Display profiling results
print(s.getvalue())
```

输出将显示函数调用的分解以及每个函数花费的时间，有助于识别训练期间消耗最多时间的函数。

## 使用 `line_profiler` 进行逐行分析

在此，要分析函数内的单行代码，可以采用 `line_profiler` 模块。首先，使用 `@profile` 装饰要分析的函数。

```python
# Add this decorator to the function you want to profile
@profile
def forward_pass(params, x):
    # Function code
    pass
```

使用以下 `kernprof` 命令运行上述脚本：

```
kernprof -l -v your_script.py
```

此命令会生成逐行分析报告，指示函数内每行花费的时间。

## 分析 JIT 编译函数

分析 JIT 编译函数需要特别考虑，因为 JIT 编译本身需要时间，并且首次执行包含编译开销。为了获得准确的测量结果，请先运行一次函数以触发编译，然后再分析后续运行。

```python
# Warm-up run to trigger JIT compilation
_ = update(params, x_batch, y_batch)
# Measure execution time excluding compilation overhead
start_time = time.time()
params = update(params, x_batch, y_batch)
end_time = time.time()
print(f"Execution time of update (post-compilation): {end_time - start_time} seconds")
```

这种方法可确保计时反映实际执行时间，而不包括初始编译延迟。



# 监控 GPU 内存使用情况

在使用 JAX 在 Fashion-MNIST 数据集上训练神经网络时，GPU 上可能会出现内存不足（OOM）错误。这些错误会中断训练过程，其原因是模型消耗的内存超过 GPU 所能提供的内存。有效管理 GPU 内存对于高效的模型训练至关重要，尤其是在处理大型数据集或复杂模型时。挑战在于实施策略来分析 GPU 内存使用情况并减少消耗，确保模型在可用内存限制内运行且训练顺利进行。

为了解决 GPU OOM 错误，在训练期间监控和分析 GPU 内存使用情况至关重要。通过了解内存如何分配和使用，可以实施策略来减少消耗。使用更小的数据类型、优化数据加载、调整批大小以及利用 JAX 的内存管理功能等技术可以帮助缓解 OOM 错误。下面是使用 JAX 在模型训练期间分析并减少 GPU 内存使用的实用方法。

## 分析 GPU 内存使用情况

初始步骤是监控 GPU 内存使用情况，以便识别内存峰值发生的时间和位置。为了深入了解实时 GPU 内存消耗，可以使用 NVIDIA 的 `nvidia-smi` 等工具。

```
# Run this command in a separate terminal
watch -n 1 nvidia-smi
```

该命令每秒更新一次 GPU 状态，显示内存使用情况和其他统计信息。

## 防止 JAX 预分配 GPU 内存

默认情况下，JAX 可能会预分配大部分 GPU 内存，这会阻碍准确监控实际使用情况的能力。为了确保精确分析，有必要禁用预分配。

```
import os
# Disable JAX GPU memory preallocation
os.environ['XLA_PYTHON_CLIENT_PREALLOCATE'] = 'false'
```

设置此环境变量可确保 JAX 按需分配内存，而不是提前保留。

## 降低数据精度

使用更紧凑的数据类型可以减少内存消耗。建议将数据和模型参数从 `float32` 转换为 `float16`。

```
import jax.numpy as jnp
from jax import random
# Convert data to float16
train_images = train_images.astype(jnp.float16)
test_images = test_images.astype(jnp.float16)
# Initialize parameters with float16
key = random.PRNGKey(0)
W1 = random.normal(key, (input_size, hidden_size), dtype=jnp.float16) * 0.01
b1 = jnp.zeros((hidden_size,), dtype=jnp.float16)
W2 = random.normal(key, (hidden_size, output_size), dtype=jnp.float16) * 0.01
b2 = jnp.zeros((output_size,), dtype=jnp.float16)
```

使用 `float16` 可将存储数据和参数所需的内存减半。

## 调整批大小

减小批大小会减少一次处理的数据量，从而降低内存使用。

```
# Reduce batch size
batch_size = 32  # Previously 64
```

更小的 `batch_size` 需要更少的内存，但可能会影响训练动态。尝试在内存限制和训练效率之间找到平衡。

## 优化数据加载

在这里，确保数据加载高效且不会消耗不必要的内存。

- 分批加载数据，而不是一次性全部加载。
- 使用数据生成器或迭代器在训练期间流式传输数据。
- 避免在内存中重复数据。

```
def data_generator(images, labels, batch_size):
    num_samples = images.shape[0]
    indices = jnp.arange(num_samples)
    for start_idx in range(0, num_samples, batch_size):
        excerpt = indices[start_idx:start_idx + batch_size]
        yield images[excerpt], labels[excerpt]
# Use the generator in the training loop
for epoch in range(num_epochs):
    for x_batch, y_batch in data_generator(train_images, train_labels, batch_size):
        params = update(params, x_batch, y_batch)
```

这种整体方法仅为每个批次加载必要的内存数据，节省内存资源。

## 利用 JAX 的 `jit` 编译

确保适当使用 `@jit` 装饰器，以防止因重新编译而导致内存使用过度。

```
from jax import jit
# Use static_argnums if function arguments change shape frequently
@jit
def update(params, x, y):
    grads = grad_loss(params, x, y)
    params = [param - learning_rate * grad for param, grad in zip(params, grads)]
    return params
```

在可行时，建议确保输入形状保持一致，以避免重新编译的必要性，否则可能导致额外内存的利用。

## 实现梯度检查点

梯度检查点通过在反向传播期间重新计算前向传播的部分而不是存储所有中间激活，从而以计算换取内存。

```
from jax.experimental import checkpoint
# Apply checkpointing to the forward pass
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = relu(z1)
    z2 = jnp.dot(a1, W2) + b2
    return z2
# Use checkpointed version of the forward pass
checkpointed_forward = checkpoint(forward_pass)
```

使用后，训练期间的内存使用量会减少，但会以额外的计算时间为代价。

## 使用 JAX 分析工具监控内存分配

再次使用 JAX 的分析工具来获取有关内存分配的详细信息。

```
from jax import profiler
# Start profiling
profiler.start_trace('/tmp/jax_trace')
# Run training code
# Stop profiling
profiler.stop_trace()
```

你也可以使用 TensorBoard 来可视化分析数据。

```
tensorboard --logdir=/tmp/jax_trace
```

在这里，导航到“Profiler”选项卡以分析内存使用情况并识别潜在的优化。

## 最小化主机与设备之间的数据传输

CPU（主机）与 GPU（设备）之间过量的数据传输会消耗内存并降低性能。在可能的情况下将数据保留在设备上。

```
from jax import device_put
# Move data to the GPU before training
train_images_device = device_put(train_images)
train_labels_device = device_put(train_labels)
```

确保计算在 GPU 上执行，以避免不必要的数据移动。

## 简化模型架构

考虑降低模型的复杂性以减少内存需求。

- 减少隐藏层中的神经元数量。
- 使用更浅的架构。
- 采用模型剪枝技术来删除冗余参数。

```
# Reduce hidden layer size
hidden_size = 64  # Previously 128
```

更简单的模型消耗更少的内存，并且仍可能达到可接受的性能。

## 利用混合精度训练

可以利用混合精度训练来实现内存和计算效率的平衡利用。

```
from jax.experimental import mixed_precision
# Set policy for mixed precision
policy = mixed_precision.Policy(compute_dtype=jnp.float16, param_dtype=jnp.float32, output_dtype=jnp.float32)
mixed_precision.set_policy(policy)
```

在这里，计算以减少内存使用的方式执行，而参数以 `float32` 存储以确保数值稳定性。

通过实施这些策略，可以有效减少 GPU 内存消耗，从而缓解模型训练过程中可能出现的内存不足（OOM）错误的发生。使用 JAX 训练模型时，分析和优化内存使用至关重要。这使得能够处理更大数据集或更复杂的架构，同时仍遵守可用硬件资源的限制。



# 可视化计算图

使用 Google `JAX` 开发复杂的神经网络模型时，在理解计算流程方面可能会带来挑战。这些模型复杂的分层和操作结构使得在没有全面理解底层计算图的情况下，很难诊断错误或提升性能。这种可见性的缺乏削弱了理解数据如何在模型中遍历以及操作之间相互连接的本质的能力。目标是采用与 `JAX` 兼容的图可视化工具，以检查和理解在模型训练过程中生成的计算图。这将促进调试和优化过程。

现在，要在 `JAX` 中可视化计算图，一个有效的方法是将 `JAX` 与 `TensorBoard` 集成，后者是一种提供机器学习模型洞察的可视化工具。虽然 `TensorBoard` 传统上与 `TensorFlow` 一起使用，但可以通过利用 `jax2tf` 转换器将其与 `JAX` 结合使用，该转换器将 `JAX` 函数转换为 `TensorFlow` 操作。

假设 `TensorFlow` 和 `TensorBoard` 已安装（请参阅 Recipe 1 for installation steps），首先导入所需的库：

```
import jax
import jax.numpy as jnp
from jax import random
from jax.experimental import jax2tf
import tensorflow as tf
from tensorflow.summary import create_file_writer
```

## 准备样本数据和参数

首先，从训练数据中选择一个样本输入，并确保模型参数已初始化：

```
# Sample input
x_sample = train_images[0:1]  # Using the first image as a sample
x_sample = x_sample.astype(jnp.float32)
# Initialize parameters (assuming parameters are already initialized)
params = [W1, b1, W2, b2]  # Replace with actual parameters
```

## 将 JAX 函数转换为 TensorFlow 函数

然后，使用 `jax2tf.convert` 函数将 `JAX` `forward_pass` 函数转换为 `TensorFlow` 兼容函数：

```
# Define the forward_pass function if not already defined
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = jnp.maximum(0, z1)  # ReLU activation
    z2 = jnp.dot(a1, W2) + b2
    return z2
# Convert to TensorFlow function
tf_forward_pass = tf.function(jax2tf.convert(forward_pass))
```

## 设置 TensorBoard 日志记录

之后，创建一个日志目录和一个摘要写入器来记录计算图：

```
logdir = 'logs/graph'
writer = create_file_writer(logdir)
```

## 追踪计算图

现在在摘要写入器上下文中，执行转换后的 `TensorFlow` 函数以捕获计算图：

```
with writer.as_default():
    # Execute the function to trace the graph
    tf.summary.graph(tf_forward_pass.get_concrete_function(params, x_sample))
```

在这里，确保 `params` 和 `x_sample` 与 `TensorFlow` 函数兼容。如有必要，将它们转换为 `TensorFlow` 张量：

```
# Convert parameters and sample input to TensorFlow tensors
params_tf = [tf.convert_to_tensor(p) for p in params]
x_sample_tf = tf.convert_to_tensor(x_sample)
```

## 启动 TensorBoard

之后，启动 `TensorBoard` 以可视化计算图：

`tensorboard --logdir=logs/graph`

打开 Web 浏览器并导航到 `http://localhost:6006` 以访问 `TensorBoard` 界面。

在 `TensorBoard` 中，选择 "Graphs" 选项卡以查看模型生成的计算图。图显示表示操作的节点和表示数据流的边。探索图以了解：
-   模型中的操作序列。
-   数据如何在各层中流动。
-   不同计算之间的依赖关系。

这种可视化有助于识别模型中任何不必要的复杂性或潜在的优化点。

## 使用命名作用域增强图可读性

为了提高计算图的清晰度，向模型的函数添加命名作用域。这将相关操作分组在一起，使图更有条理：

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    with tf.name_scope('Layer1'):
        z1 = jnp.dot(x, W1) + b1
        a1 = jnp.maximum(0, z1)
    with tf.name_scope('Layer2'):
        z2 = jnp.dot(a1, W2) + b2
    return z2
```

重新运行转换函数和追踪计算图的步骤，以在 `TensorBoard` 中查看更新后更易读的图。

## 检查 JAXpr

为了更深入地理解，检查 `forward_pass` 函数的 `JAXpr`（`JAX` 的中间表示）：

```
from jax import make_jaxpr
# Generate and print the JAXpr
jaxpr = make_jaxpr(forward_pass)(params, x_sample)
print(jaxpr)
```

`JAXpr` 提供了计算的低级视图，显示原始操作以及数据如何在它们之间流动。可考虑使用 `Netron` 或 `Graphviz` 等额外工具进行更高级的可视化。

`JAX` 与 `TensorBoard` 的集成以及额外可视化工具的利用使得能够有效检查和理解复杂模型的计算图。这种方法促进了问题的调试、性能的优化以及对模型运行机制的更深刻理解。



# 为性能优化批量大小

在使用 Google JAX 训练神经网络的背景下，选择最佳批量大小对于实现高效计算和有效内存利用至关重要。不合适的批量大小可能会阻碍最佳训练结果，或在极端情况下导致内存不足（OOM）错误，尤其是在 GPU 受内存限制的情况下。目标是确定一个 `batch_size`，在不超出硬件限制的前提下平衡计算时间和内存使用，以最大化训练效率。必须对不同的批量大小进行分析，以了解其对性能的影响，并就给定训练设置的最佳批量大小做出明智决策。

为了确定最佳批量大小，有必要使用各种批量大小分析训练过程，并分析其对计算时间和内存使用的影响。通过对不同批量大小进行系统实验，可以观察这些变量对训练速度和资源消耗的影响。目标是确定一个在计算效率和内存需求之间取得最佳平衡的批量大小。这包括测量每个训练 epoch 所需的时间，监控图形处理单元（GPU）内存的利用率，并评估模型在每个批量大小下的整体性能。

## 理解批量大小的影响

`Batch size` 指在更新模型内部参数之前处理的训练样本数量。更大的批量大小由于现代硬件（如 GPU）的并行处理能力，可能导致每个 epoch 的计算更快。然而，更大的批次会消耗更多内存，而这些内存可能不可用，从而导致潜在的 OOM 错误。更小的批量大小会减少内存使用，但可能导致训练时间更长且梯度估计不稳定。在内存限制范围内利用硬件能力找到平衡非常重要。

## 设置实验

首先定义要测试的批量大小范围。常见的批量大小包括 2 的幂，例如 16、32、64、128 和 256。准备训练代码以接受可变的批量大小参数，以便在不同批量大小下使用相同的代码库而无需修改。

```python
# Define possible batch sizes to test
batch_sizes = [16, 32, 64, 128, 256]
```

确保数据加载和训练函数通过接受批量大小作为输入参数来设计为处理不同的批量大小。

## 修改数据加载器

调整 `data_generator` 或数据加载器函数以接受批量大小作为参数。参考 Recipe 2 中实现的 `data_generator` 以实现高效的数据加载。

```python
def data_generator(images, labels, batch_size):
    num_samples = images.shape[0]
    indices = jnp.arange(num_samples)
    for start_idx in range(0, num_samples, batch_size):
        excerpt = indices[start_idx:start_idx + batch_size]
        yield images[excerpt], labels[excerpt]
```

此函数现在允许在训练期间灵活使用批量大小。

### 实现计时和内存分析

为了测量计算时间和内存使用，将计时函数和内存监控工具集成到训练循环中。使用 Python 的 `time` 模块来测量每个 epoch 的训练时间，并使用 `nvidia-smi` 或 JAX 的内置工具来监控 GPU 内存使用。

```python
import time
from jax.lib import xla_bridge
# Check if running on GPU
device = xla_bridge.get_backend().platform
print(f"Running on {device}")
```

## 使用不同批量大小运行训练实验

对于定义范围内的每个批量大小，执行以下步骤：
- 初始化模型参数。
- 为固定数量的 epoch 训练模型（例如，为测试目的训练一个 epoch）。
- 测量总训练时间。
- 在训练期间监控峰值 GPU 内存使用情况。

以下是使用特定批量大小运行实验的示例代码：

```python
for batch_size in batch_sizes:
    print(f"\nTesting with batch size: {batch_size}")
    # Re-initialize model parameters
    params = initialize_params()
    # Record the start time
    start_time = time.time()
    # Training loop for one epoch
    for x_batch, y_batch in data_generator(train_images, train_labels, batch_size):
        # Convert data to JAX arrays if necessary
        x_batch = jnp.array(x_batch)
        y_batch = jnp.array(y_batch)
        # Perform a training step
        params = update(params, x_batch, y_batch)
    # Record the end time
    end_time = time.time()
    # Calculate training time
    training_time = end_time - start_time
    print(f"Training time for batch size {batch_size}: {training_time:.2f} seconds")
    # Monitor GPU memory usage (use nvidia-smi externally or JAX profiling tools)
    print("GPU memory usage needs to be monitored externally using nvidia-smi.")
```

### 监控 GPU 内存使用情况

由于 JAX 未提供在代码中直接监控 GPU 内存使用的方法，请在单独的终端中使用 `nvidia-smi` 命令行工具在训练期间观察内存消耗。

```bash
watch -n 1 nvidia-smi
```

在此，请记录训练过程中每个批量大小的峰值内存使用情况。

### 记录和分析结果

在此，收集每个测试批量大小的训练时间和峰值内存使用数据。将结果整理到表格或电子表格中以便轻松比较。

以下是一个示例：

虽然更大的批量大小可以加快训练，但它们可能会影响梯度估计的质量。更小的批量大小会在梯度计算中引入更多噪声，这有时有助于跳出局部最小值，但也可能减慢收敛速度。监控模型的性能指标（如训练和验证准确率）非常重要，以确保所选批量大小不会对学习产生负面影响。

### 基于批量大小调整学习率

在更改批量大小时考虑调整学习率。一种常见做法是按比例缩放学习率与批量大小，以保持一致的梯度更新。

```python
# Adjust learning rate
base_learning_rate = 0.01
adjusted_learning_rate = base_learning_rate * (batch_size / 64)  # Assuming 64 as the base batch size
# Use adjusted_learning_rate in the update function
def update(params, x, y, learning_rate):
    grads = grad_loss(params, x, y)
    params = [param - learning_rate * grad for param, grad in zip(params, grads)]
    return params
```

相应地尝试在训练循环中包含调整后的学习率。

## 实现梯度累积

如果硬件限制阻止使用更大的批量大小，请实现梯度累积，以在不增加内存使用的情况下模拟更大的有效批量大小。

```python
accumulation_steps = desired_batch_size // actual_batch_size
accumulated_grads = None
step = 0
for x_batch, y_batch in data_generator(train_images, train_labels, actual_batch_size):
    x_batch = jnp.array(x_batch)
    y_batch = jnp.array(y_batch)
    grads = grad_loss(params, x_batch, y_batch)
    if accumulated_grads is None:
        accumulated_grads = grads
    else:
        accumulated_grads = [ag + g for ag, g in zip(accumulated_grads, grads)]
    step += 1
    if step % accumulation_steps == 0:
        # Update parameters with accumulated gradients
        params = [param - (learning_rate / accumulation_steps) * ag for param, ag in zip(params, accumulated_grads)]
        accumulated_grads = None
        # Reset accumulated gradients
        step = 0
```

这种方法允许在保持每步内存使用较低的同时实现有效的更大批量大小。

这种系统方法允许最大化硬件利用率，同时避免 OOM 错误，最终导致在 Fashion-MNIST 数据集上更快、更有效的神经网络训练。



# 使用梯度检查点减少内存占用

在使用 Google JAX 在 Fashion-MNIST 数据集上训练神经网络时，GPU 内存的限制可能成为一个重要制约因素。大型模型或深度架构需要在前向传播期间存储激活值，这需要大量的内存，可能导致 OOM 错误并阻碍训练过程。减小批量大小可能会缓解内存问题，但会负面影响训练效率和收敛性。挑战在于如何在不牺牲性能的情况下，在可用 GPU 内存内训练复杂模型。应用梯度检查点方法使我们能够用额外的计算换取减少的内存使用，从而在内存受限的硬件上训练更大的模型。

梯度检查点，也称为重物化，是一种通过选择性地存储和重新计算中间激活值来在训练期间减少内存消耗的技术。与将所有激活值保留在内存中用于反向传播不同，某些激活值在前向传播后会被丢弃，并在反向传播时根据需要重新计算。这种方法以增加计算时间为代价降低了内存占用。

## 理解前向传播结构

首先检查神经网络中使用的 `forward_pass` 函数：

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = jnp.maximum(0, z1)  # ReLU activation
    z2 = jnp.dot(a1, W2) + b2
    y_pred = jnp.exp(z2) / jnp.sum(jnp.exp(z2), axis=1, keepdims=True)  # Softmax
    return y_pred
```

在上述函数中，激活值 `a1` 和 `z2` 在训练期间会占用内存。对于具有许多层的深度网络，存储所有激活值所需的累计内存可能超过 GPU 容量。

## 将 `jax.checkpoint` 应用于前向传播

要实现梯度检查点，请使用 `jax.checkpoint` 包装前向传播的部分，以指示中间值可以在反向传播期间重新计算：

```
from jax import checkpoint
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    # Define functions for each layer
    def layer1(x):
        return jnp.maximum(0, jnp.dot(x, W1) + b1)
    def layer2(a1):
        return jnp.dot(a1, W2) + b2
    # Apply checkpointing to layers
    a1 = checkpoint(layer1)(x)
    z2 = checkpoint(layer2)(a1)
    # Compute output
    y_pred = jnp.exp(z2) / jnp.sum(jnp.exp(z2), axis=1, keepdims=True)
    return y_pred
```

通过对 `layer1` 进行检查点，中间激活值 `z1` 和 `a1` 在前向传播期间不会被存储，而是在反向传播期间重新计算。

## 调整损失函数和梯度计算

确保损失函数和梯度计算与检查点后的前向传播兼容至关重要，如下所示：

```
def compute_loss(params, x, y):
    y_pred = forward_pass(params, x)
    loss = -jnp.mean(jnp.log(y_pred[jnp.arange(y.shape[0]), y]))
    return loss
from jax import grad
grad_loss = grad(compute_loss)
```

## 使用检查点训练模型

接下来，如同之前一样，使用相同的优化器和更新函数继续训练循环：

```
def update(params, x, y, learning_rate=0.01):
    grads = grad_loss(params, x, y)
    params = [p - learning_rate * g for p, g in zip(params, grads)]
    return params
# Training loop
num_epochs = 10
batch_size = 64
for epoch in range(num_epochs):
    for x_batch, y_batch in data_generator(train_images, train_labels, batch_size):
        x_batch = jnp.array(x_batch)
        y_batch = jnp.array(y_batch)
        params = update(params, x_batch, y_batch)
```

在 `forward_pass` 函数中使用 `checkpoint` 可在训练期间减少内存消耗。

对于具有更多层或更复杂架构的模型，请考虑更具选择性地应用检查点或使用自定义策略：

## 对层组进行检查点

在深度网络中，对多个层进行分组并对组进行检查点，可以在内存节省和计算开销之间取得平衡：

```
def forward_pass(params, x):
    activations = x
    for i in range(0, len(params), 2):  # Assuming pairs of (W, b)
        W, b = params[i], params[i+1]
        def layer(a, W, b):
            return jnp.maximum(0, jnp.dot(a, W) + b)
        # Checkpoint the group of layers
        activations = checkpoint(layer)(activations, W, b)
    return activations
```

### 使用自定义策略的 `jax.remat`

为了更精细地控制，请使用 `jax.remat` 并配合自定义策略来指定要检查点的操作：

```
from jax import remat
def custom_policy(primitive):
    # Decide whether to checkpoint based on the primitive name
    return primitive.name in ('dot_general', 'conv_general_dilated')
def forward_pass(params, x):
    remat_forward = remat(forward_pass_body, policy=custom_policy)
    return remat_forward(params, x)
```

在使用卷积层时，内存消耗可能很大。您可以按如下方式对卷积层应用检查点：

```
def conv_layer(params, x):
    W, b = params
    return jax.nn.relu(jax.lax.conv_general_dilated(
        x, W, window_strides=(1, 1), padding='SAME'
    ) + b)
def forward_pass(params, x):
    # Apply checkpointing to convolutional layers
    x = checkpoint(conv_layer)(params[0], x)
    x = checkpoint(conv_layer)(params[1], x)
    # Continue with other layers
    return x
```

将梯度检查点纳入神经网络训练过程能够缓解内存限制，从而促进在内存资源受限的 GPU 上训练更大或更深的模型。尽管这种方法由于激活值的重新计算而需要额外的计算，但它为克服硬件限制提供了一种可行的解决方案。

## 摘要

我们首先研究了测量 JAX 函数执行时间的方法。通过识别代码中的瓶颈，我们能够使用 JAX 的内置工具和 Python 配置文件库，包括 `time`、`cProfile` 和 `line_profiler` 来优化性能。我们实施了分析并减少设备内存消耗的策略。我们使用 `float16` 等较小的数据类型代替 `float32`，采用生成器或迭代器来优化数据加载，并调整批量大小以平衡内存使用和计算效率。

我们通过利用图形可视化工具解决了理解模型中复杂计算流程的问题。这种可视化帮助我们理解模型内部的数据流和依赖关系，从而更有效地调试问题并优化性能。添加命名作用域并分析中间表示（`JAXpr`）提供了对模型结构的更深入见解。接下来，我们必须优化批量大小以提高训练效率。较小的批量大小会减少内存消耗，但由于硬件利用率较低而增加训练时间。较大的批量大小被证明可以提高计算效率，但有超出内存限制的风险。本章随后探讨了如何通过使用梯度检查点方法在训练期间减少内存占用，该方法允许在反向传播期间选择性地存储和重新计算中间激活值。这使得在不超出内存限制的情况下训练更深、更复杂的模型成为可能。

总体而言，本章提供了在使用 Google JAX 时分析并优化计算和内存使用方面的清晰且实用的技术和策略。

# 第 3 章：调试运行时值和错误



# 概述

在本章中，我们将直面调试运行时值和错误的挑战。我们将为您提供实用的策略，以识别和解决在模型开发和训练过程中可能出现的常见问题。一旦您理解了这些错误的根本原因，就能够增强机器学习模型的可靠性和鲁棒性。

我们将从具体化错误开始，当 `JAX` 转换遇到在编译时无法确定的值时就会出现此类错误。这些错误可能很微妙，会打断程序的执行流程。通过学习如何有效处理它们，您可以编写更灵活高效的代码。接下来，我们将解决在 `JIT` 编译函数中检查中间值的挑战。由于传统的调试方法（如 print 语句）可能无法按预期工作，我们介绍了用于检查计算内部状态的工具和技术。处理形状不匹配错误是另一个常见挑战，尤其是在复杂的神经网络架构中。我们提供实用的解决方案来诊断和修复这些错误，确保张量操作正确对齐。

最后，我们解决计算中出现 `NaNs` 相关的问题，这可能会破坏训练并降低模型性能。您将学习如何理解数值不稳定的来源并实施适当的补救措施，保持模型的健康。到最后，您将拥有调试和解决 `JAX` 中运行时错误的全面工具包，从而能够开发更有效、更可靠的机器学习应用。

## 处理具体化错误

在使用 Google `JAX` 训练神经网络时，使用控制流结构如 `if` 或 `for` 在 `JAX` 转换中时，您可能会遇到 `ConcretizationTypeError`。此错误发生在 `JAX` 在编译期间尝试使用一个只能在运行时确定的值时。当控制流依赖于执行时才知道的数据时就会出现这种情况，这与 `JAX` 对静态计算图的要求相冲突。挑战在于理解这些错误为何发生以及如何重构代码以防止它们，确保模型训练顺畅高效。

### 理解具体化错误

在 `JAX` 中，由 `jit`（即时编译）或 `grad`（自动微分）转换的函数会被编译为 `XLA`（加速线性代数）计算。在此编译过程中，`JAX` 会追踪函数以构建静态计算图。如果函数包含依赖于运行时数据的 `if` 或 `for` 等控制流语句，`JAX` 无法构建静态图，从而导致 `ConcretizationTypeError`。此错误表明一个被追踪的（符号）值被用在了需要具体（数值）值的上下文中。

让我们考虑一个对输入应用阈值的简单函数：

```
import jax
import jax.numpy as jnp
@jax.jit
def threshold(x, threshold_value):
    if x > threshold_value:
        return x
    else:
        return 0.0
result = threshold(5.0, 3.0)
```

这段代码会引发 `ConcretizationTypeError`，因为 `if` 语句依赖于 `x` 的值，而 `x` 是一个运行时变量。`JAX` 无法在编译期间评估此条件，因为在该阶段 `x` 是一个符号占位符。

为了解决具体化错误，您需要重构代码，以在 `JAX` 转换的函数中移除依赖于运行时的控制流。`JAX` 提供了如 `jax.lax.cond` 和 `jax.lax.scan` 之类的控制流原语，它们以与 `JAX` 转换兼容的方式处理动态控制流。

### 用 JAX 控制流原语替换 Python 控制流

不要使用 Python 的 `if` 语句，而是使用 `jax.lax.cond` 根据运行时值进行条件执行。

```
def threshold(x, threshold_value):
    return jax.lax.cond(
        x > threshold_value,
        lambda _: x,
        lambda _: 0.0,
        operand=None
    )
# JIT-compile the function
threshold_jit = jax.jit(threshold)
result = threshold_jit(5.0, 3.0)
```

在此重构的代码中，`jax.lax.cond` 允许条件逻辑在 `JIT` 编译的函数内依赖于运行时值。

## 对数组使用逐元素操作

如果处理数组，请使用 `JAX` 提供的逐元素操作，例如 `jnp.where`，以避免控制流错误，如下所示：

```
@jax.jit
def relu(x):
    return jnp.where(x > 0, x, 0.0)
# Apply to an array
x_array = jnp.array([-2.0, 0.0, 3.0])
result = relu(x_array)
```

这种方法避免使用 Python 控制流，并利用 `JAX` 的优化操作。

## 使用 `jax.lax.scan` 或 `jax.lax.fori_loop` 处理循环

当循环依赖于运行时值时，请用 `JAX` 的循环结构替换它们。假设您有一个函数在满足条件时对元素求和：

```
def cumulative_sum(x, max_value):
    total = 0.0
    for i in range(len(x)):
        total += x[i]
        if total > max_value:
            break
    return total
```

使用以下方式重构

```
def cumulative_sum(x, max_value):
    def body_fun(i, val):
        total, done = val
        total += x[i] * (1 - done)
        done = jnp.where(total > max_value, 1.0, done)
        return total, done
    total, _ = jax.lax.fori_loop(
        0,
        len(x),
        body_fun,
        (0.0, 0.0)
    )
    return total
# JIT-compile the function
cumulative_sum_jit = jax.jit(cumulative_sum)
x_array = jnp.array([1.0, 2.0, 3.0, 4.0])
result = cumulative_sum_jit(x_array, 5.0)
```

## 将依赖运行时的逻辑移出 JIT 函数

如果可能，请在调用 `JIT` 编译函数之前处理控制流逻辑。以下是快速示例：

```
def adjust_learning_rate(epoch):
    if epoch < 5:
        return 0.01
    else:
        return 0.001
def train_step(params, x, y, learning_rate):
    grads = jax.grad(loss_fn)(params, x, y)
    new_params = [(p - learning_rate * g) for p, g in zip(params, grads)]
    return new_params
# Training loop
for epoch in range(num_epochs):
    lr = adjust_learning_rate(epoch)
    params = jax.jit(train_step)(params, x_batch, y_batch, lr)
```

通过将学习率调整移出 `JIT` 编译的 `train_step` 函数，我们避免了具体化错误。

## 使用 `static_argnums` 指定静态参数

如果某些参数需要在编译时已知，请将它们指定为静态参数，如下所示：

```
@jax.jit(static_argnums=(2,))
def train_step(params, x, y, training_phase):
    if training_phase == 'warmup':
        learning_rate = 0.01
    else:
        learning_rate = 0.001
    grads = jax.grad(loss_fn)(params, x, y)
    new_params = [(p - learning_rate * g) for p, g in zip(params, grads)]
    return new_params
# Call the function with a static argument
params = train_step(params, x_batch, y_batch, 'warmup')
```

在这里，请谨慎使用 `static_argnums`，因为如果静态参数频繁更改，可能会导致重新编译。

理解 `ConcretizationTypeError` 的原因并应用适当的重构技术可以防止此类错误并确保 `JAX` 代码顺利运行。这种方法能够利用 `JAX` 的强大转换，而不会损害机器学习模型中动态控制流所需的灵活性。



# 在 JIT 编译函数中检查中间值

在 Fashion-MNIST 数据集上使用 Google JAX 开发神经网络时，调试可能会变得具有挑战性，尤其是在函数被 `jit` 用于即时编译时。传统的调试方法，如在函数中插入 `print` 语句不起作用，因为 JAX 会追踪函数以构建计算图，而像 `print` 这样的副作用操作在追踪期间不会被执行。这使得在执行期间检查中间值并理解代码的行为变得困难。挑战在于找到有效的方法来检查函数内的运行时值以促进调试并确保模型正常运行。

为克服在函数中检查中间值的困难，我们可以利用 JAX 的调试工具，特别是允许在 JAX 转换期间打印值的工具。此外，还可以采用返回中间值或使用主机回调等替代方法来成功检查运行时值。这些技术使我们能够调试用 `jit` 包装的函数并深入了解模型的内部计算。

## 理解为什么 `print` 语句会失败

在函数内部，标准的 Python `print` 语句会被忽略，因为 JAX 通过追踪函数来创建静态计算图。像 `print` 这样的副作用不会影响计算图，因此在追踪期间被省略。

下面是一个快速示例：

```
import jax
import jax.numpy as jnp
@jax.jit
def compute(x):
    y = x * 2
    print(f"Intermediate value y: {y}")
    return y
result = compute(3.0)
```

这段代码不会显示 `y` 的中间值，因为 `print` 语句在函数内部不会被执行。

## 使用 `jax.debug.print` 进行调试

下面是使用 `jax.debug.print` 重构后的代码：

```
import jax
import jax.numpy as jnp
from jax import debug
@jax.jit
def compute(x):
    y = x * 2
    debug.print("Intermediate value y: {}", y)
    return y
result = compute(3.0)
```

运行此代码时，输出将为：

Intermediate value y: 6.0

这里，`debug.print` 函数接受格式字符串和要显示的变量。它在函数内部正确运行，使我们能够检查中间值。

### 在模型中应用 `jax.debug.print`

假设我们想在神经网络的前向传播中检查中间激活值。下面是一个快速示例：

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = jnp.maximum(0, z1)  # ReLU activation
    debug.print("Activation a1 mean: {}", jnp.mean(a1))
    z2 = jnp.dot(a1, W2) + b2
    y_pred = jax.nn.softmax(z2)
    return y_pred
forward_pass_jit = jax.jit(forward_pass)
```

通过运行 `forward_pass_jit(params`，我们可以在执行期间观察 `a1` 的均值。

### 条件调试

我们可以向 `debug.print` 函数添加条件以将输出限制为特定情况。下面是一个快速示例：

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = jnp.maximum(0, z1)
    max_a1 = jnp.max(a1)
    debug.print("Max of a1: {}", max_a1, where=max_a1 > 10.0)
    z2 = jnp.dot(a1, W2) + b2
    y_pred = jax.nn.softmax(z2)
    return y_pred
```

这将仅在超过时打印 `a1` 的最大值，有助于识别异常激活。

## 使用 `jax.experimental.host_callback` 进行主机回调

对于更高级的调试，可以使用 `jax.experimental.host_callback.id_print`。下面是一个快速示例：

```
from jax.experimental import host_callback as hcb
@jax.jit
def compute(x):
    y = x * 2
    hcb.id_print(y, result=False, what="Intermediate value y")
    return y
result = compute(3.0)
```

此方法将值从设备发送到主机并打印它，提供了一种在执行期间检查值的方法。

通过利用主机回调以及返回中间值等替代方法，我们可以有效地在函数内部检查运行时值。这些技术增强了我们调试和理解模型内部计算的能力。



# 处理形状不匹配错误

在用 Google JAX 训练的神经网络中进行矩阵运算时，根据最新研究可能会出现形状不匹配错误。此类错误在张量的维度未正确对齐以进行预期数学运算时出现，包括矩阵乘法和广播。形状不匹配错误在机器学习工作流程中很常见，在尝试识别来源并实施解决方案时可能构成重大挑战，尤其是在包含多层和数据转换的复杂模型背景下。目标是在执行运算之前实施张量形状的验证和对齐策略，从而确保代码在不遇到与形状相关的错误的情况下运行。

为了避免形状不匹配错误，至关重要的是理解整个计算过程中张量的预期维度，并确保这些形状已正确对齐以进行预期操作。这需要细致检查输入数据的形状、参数的维度以及每一层或函数的输出形状。通过实施系统检查并利用 JAX 的调试工具，可以在形状不一致导致运行时错误之前识别并纠正它们。以下部分概述了在 JAX 代码中验证和对齐张量形状的实用策略。

## 在模型中理解张量形状

首先回顾神经网络的结构以及每一层张量的预期形状。对于 Fashion-MNIST 数据集，图像通常具有形状 (`batch_size`, 28, 28)，用于灰度图像。当为全连接网络展平图像时，形状变为 (`batch_size`, 784)。

以下是快速示例：
```python
# Assuming batch_size is 64
x_batch = jnp.array([...])  # Shape: (64, 28, 28)
y_batch = jnp.array([...])  # Shape: (64,)
# Flatten the input images
x_batch = x_batch.reshape(64, 784)  # Shape: (64, 784)
```

## 验证参数形状

初始化模型参数时应使用与矩阵运算预期维度相对应的形状。以下是初始化权重和偏置的示例：
```python
input_size = 784   # Number of input features
hidden_size = 128  # Number of neurons in the hidden layer
output_size = 10   # Number of classes
key = random.PRNGKey(0)
W1 = random.normal(key, (input_size, hidden_size)) * 0.01  # Shape: (784, 128)
b1 = jnp.zeros((hidden_size,))  # Shape: (128,)
W2 = random.normal(key, (hidden_size, output_size)) * 0.01  # Shape: (128, 10)
b2 = jnp.zeros((output_size,))  # Shape: (10,)
```

建议确保权重矩阵和偏置向量的形状与前向传播中执行的操作兼容。

## 实现带形状检查的前向传播

在定义前向传播时，包含形状检查或打印语句以验证张量维度。以下是前向传播函数的快速示例：
```python
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    # First layer
    z1 = jnp.dot(x, W1) + b1  # x shape: (batch_size, 784), W1 shape: (784, 128)
    a1 = jax.nn.relu(z1)      # z1 shape: (batch_size, 128)
    # Second layer
    z2 = jnp.dot(a1, W2) + b2  # a1 shape: (batch_size, 128), W2 shape: (128, 10)
    y_pred = jax.nn.softmax(z2)  # z2 shape: (batch_size, 10)
    return y_pred
```

在此处，您可以包含形状断言以验证形状是否符合预期：
```python
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    assert x.shape[1] == W1.shape[0], f"Shape mismatch: x {x.shape}, W1 {W1.shape}"
    z1 = jnp.dot(x, W1) + b1
    assert z1.shape[1] == b1.shape[0], f"Shape mismatch: z1 {z1.shape}, b1 {b1.shape}"
    a1 = jax.nn.relu(z1)
    assert a1.shape[1] == W2.shape[0], f"Shape mismatch: a1 {a1.shape}, W2 {W2.shape}"
    z2 = jnp.dot(a1, W2) + b2
    assert z2.shape[1] == b2.shape[0], f"Shape mismatch: z2 {z2.shape}, b2 {b2.shape}"
    y_pred = jax.nn.softmax(z2)
    return y_pred
```

如果您能包含这些断言，它可以帮助在计算早期捕获形状不匹配。

## 使用 `jax.debug.print` 进行形状检查

在 JIT 编译函数中使用 `jax.debug.print` 打印张量形状。
```python
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    jax.debug.print("z1 shape: {}", z1.shape)
    a1 = jax.nn.relu(z1)
    jax.debug.print("a1 shape: {}", a1.shape)
    z2 = jnp.dot(a1, W2) + b2
    jax.debug.print("z2 shape: {}", z2.shape)
    y_pred = jax.nn.softmax(z2)
    jax.debug.print("y_pred shape: {}", y_pred.shape)
    return y_pred
```

这使您能够在执行期间检查形状并识别任何差异。

## 在训练前检查输入数据形状

在此之后，在进入训练循环之前，尝试验证输入数据的形状。
```python
print(f"x_batch shape: {x_batch.shape}")  # Should be (batch_size, 784)
print(f"y_batch shape: {y_batch.shape}")  # Should be (batch_size,)
```

通过这样做，您可以确保批量大小和特征维度正确。

## 处理广播问题

现在，在添加偏置或执行逐元素操作时，请注意广播规则。例如，如果 `b1` 的形状为 `(128,)` 且 `z1` 的形状为 (`batch_size`, 由于广播，将它们相加是可行的。然而，如果 `b1` 具有不正确的形状，则可能导致形状不匹配。

使用以下脚本，您可以确保偏置的形状正确：
```python
# Correct bias shapes
b1 = jnp.zeros((1, hidden_size))  # Shape: (1, 128)
b2 = jnp.zeros((1, output_size))  # Shape: (1, 10)
```

然后相应地调整前向传播：
```python
z1 = jnp.dot(x, W1) + b1  # Shapes: (batch_size, 128) + (1, 128)
```

## 使用显式重塑和转置

在必要时，使用 `jnp.reshape` 和 `jnp.transpose` 调整张量形状。

以下是快速示例：
```python
# If x has shape (batch_size, 28, 28), flatten it
x_flat = x.reshape(batch_size, -1)  # Now shape is (batch_size, 784)
```

如果需要转置矩阵：
```python
W1_T = jnp.transpose(W1)  # Switches axes
```

我们需要检查重塑和转置操作是否能正确对齐张量以供后续操作使用。

## 使用小批量进行测试

使用小批量数据运行测试，以在扩展之前验证形状是否正确。
```python
test_x = jnp.ones((2, 784))  # Small batch of size 2
test_params = [W1, b1, W2, b2]
test_output = forward_pass(test_params, test_x)
print(f"Test output shape: {test_output.shape}")  # Should be (2, 10)
```

当出现形状不匹配错误时，JAX 会提供详细的错误消息，指示预期的和实际的形状。
```python
ValueError: Incompatible shapes for dot operation: lhs shape (64, 784), rhs shape (129, 10)
```

在此之后，您可以使用此信息追溯形状偏离预期的位置。

通过在执行操作之前实施这些策略来验证和对齐张量形状，您可以防止 JAX 代码中出现形状不匹配错误。务必极其注意张量的维度，利用断言和调试工具，并在计算的每个阶段进行系统的形状检查，具有至关重要的意义。



# 在计算中解决 NaN 问题

当在 `Fashion-MNIST` 数据集上使用 Google `JAX` 训练神经网络时，您可能会遇到模型在计算过程中输出 `NaN` 值的情况。这些值会通过网络传播，导致训练过程失败或产生无效结果。数值不稳定性通常会导致此类问题，源于除以零、取零的对数或指数函数导致溢出等操作。挑战在于识别这些问题的来源并实施策略加以防止，确保训练稳定且成功。

要解决计算中 NaN 的问题，识别其来源并解决潜在的数值不稳定性至关重要。可以采用的一些策略有：

识别并处理不稳定 修改容易出现数值问题的函数，如 `softmax` 或 `logarithms`。
应用正则化 通过使用 `L2` 正则化或 `dropout` 防止权重增长过大。
实现梯度裁剪 限制梯度的幅度以防止极端更新。
调整学习率 如果它导致发散则降低它。
适当的权重初始化 使用方法如 Xavier 初始化以合理的权重值开始。
监控激活值和梯度 在训练期间检查值以尽早检测异常。

## 逐步实践指南

### 识别 NaN 的来源

首先，确定 `NaN` 在计算的哪个位置被引入。修改代码以打印中间值或使用调试工具。

```python
for epoch in range(num_epochs):
    for x_batch, y_batch in data_generator(train_images, train_labels, batch_size):
        x_batch = jnp.array(x_batch)
        y_batch = jnp.array(y_batch)
        params = update(params, x_batch, y_batch)
    # Compute loss on training data
    loss_value = compute_loss(params, x_batch, y_batch)
    print(f"Epoch {epoch}, Loss: {loss_value}")
```
如果 `loss_value` 变为 `NaN`，则表明在计算过程中引入了 `NaN`。

### 检查激活值和梯度中的 NaN

使用 `jax.debug.print` 检查函数内的中间值。

```python
from jax import debug
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = jax.nn.relu(z1)
    debug.print("Max of a1: {}", jnp.max(a1))
    z2 = jnp.dot(a1, W2) + b2
    y_pred = jax.nn.softmax(z2)
    debug.print("Max of y_pred: {}", jnp.max(y_pred))
    return y_pred
```
这有助于确定激活值或输出是否包含 `NaN`。

### 处理 Softmax 函数中的数值不稳定性

如果指数溢出，`softmax` 函数可能会产生 `NaN`。这里可以使用稳定的 softmax 实现。

```python
def stable_softmax(z):
    z_max = jnp.max(z, axis=1, keepdims=True)
    exp_z = jnp.exp(z - z_max)
    sum_exp_z = jnp.sum(exp_z, axis=1, keepdims=True)
    return exp_z / sum_exp_z
# Replace in forward_pass
y_pred = stable_softmax(z2)
```

## 应用梯度裁剪

现在让我们限制梯度的幅度以防止可能导致不稳定的大更新。

```python
from jax import tree_util
def clip_grads(grads, max_norm):
    total_norm = jnp.sqrt(sum([jnp.sum(jnp.square(g)) for g in tree_util.tree_leaves(grads)]))
    clip_coef = jnp.minimum(1.0, max_norm / (total_norm + 1e-6))
    return tree_util.tree_map(lambda g: g * clip_coef, grads)

def update(params, x, y, learning_rate=0.01):
    grads = grad_loss(params, x, y)
    grads = clip_grads(grads, max_norm=5.0)
    params = [p - learning_rate * g for p, g in zip(params, grads)]
    return params
```

### 添加正则化

正则化过程有助于防止权重变得过大，从而降低遇到数值问题的可能性。

```python
def compute_loss(params, x, y, lambda_reg=0.001):
    y_pred = forward_pass(params, x)
    epsilon = 1e-7
    y_pred = jnp.clip(y_pred, epsilon, 1.0 - epsilon)
    log_probs = -jnp.log(y_pred[jnp.arange(y.shape[0]), y])
    loss = jnp.mean(log_probs)
    # L2 regularization
    l2_loss = sum([jnp.sum(jnp.square(p)) for p in params])
    total_loss = loss + lambda_reg * l2_loss
    return total_loss
```

在上述情况下，高学习率可能导致发散。我们可以简单地降低它以稳定训练如下：

`learning_rate = 0.001`  # 从 0.01 降低

### 适当的权重初始化

我们还可以使用 Xavier (Glorot) 初始化等方法以适当的权重尺度开始。

```python
def glorot_init(key, shape):
    fan_in, fan_out = shape[0], shape[1]
    limit = jnp.sqrt(6 / (fan_in + fan_out))
    return random.uniform(key, shape, minval=-limit, maxval=limit)

# Initialize weights
key = random.PRNGKey(0)
W1 = glorot_init(key, (input_size, hidden_size))
b1 = jnp.zeros((hidden_size,))
W2 = glorot_init(key, (hidden_size, output_size))
b2 = jnp.zeros((output_size,))
```

## 使用替代激活函数

我们可以考虑使用不易导致 `NaN` 的激活函数，如下所示的 Leaky ReLU：

```python
def leaky_relu(x, alpha=0.01):
    return jnp.where(x > 0, x, alpha * x)
# Use in forward_pass
a1 = leaky_relu(z1)
```

然后我们可以归一化输入数据以防止激活值过大。

```python
mean = jnp.mean(train_images, axis=0)
std = jnp.std(train_images, axis=0) + 1e-7  # Prevent division by zero
def normalize(x):
    return (x - mean) / std
# Normalize training data
train_images = normalize(train_images)
```

## 实现批量归一化

批量归一化可稳定各层之间的激活值。

```python
def batch_norm(x, gamma, beta, eps=1e-5):
    mean = jnp.mean(x, axis=0, keepdims=True)
    variance = jnp.var(x, axis=0, keepdims=True)
    x_norm = (x - mean) / jnp.sqrt(variance + eps)
    return gamma * x_norm + beta

# Initialize gamma and beta
gamma1 = jnp.ones((hidden_size,))
beta1 = jnp.zeros((hidden_size,))
# Include in params
params = [W1, b1, gamma1, beta1, W2, b2]

def forward_pass(params, x):
    W1, b1, gamma1, beta1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    z1_bn = batch_norm(z1, gamma1, beta1)
    a1 = jax.nn.relu(z1_bn)
    z2 = jnp.dot(a1, W2) + b2
    y_pred = stable_softmax(z2)
    return y_pred
```

不要忘记使用一致的数据类型以防止精度相关问题：

```python
x_batch = x_batch.astype(jnp.float32)
params = [p.astype(jnp.float32) for p in params]
```

通过识别数值不稳定性的来源并应用诸如正则化、梯度裁剪、适当初始化和稳定函数实现等技术，您可以解决计算中的 `NaN` 问题。



## 摘要
总之，本章提供了在使用 Google `JAX` 进行机器学习任务时遇到的常见运行时错误和调试挑战的解决方案。本章解决了当 `JAX` 转换中的控制流依赖于运行时值时出现的具体化错误。`JAX` 需要静态计算图，因此我们使用 `JAX` 的控制流原语如 `jax.lax.cond` 和 `jax.lax.scan` 重构代码的策略。另一个关键问题是检查 `JIT` 编译函数内部中间值的挑战。我们还研究了形状不匹配错误，该错误通常在矩阵运算期间发生。你可以通过检查输入数据的形状，确保参数维度与预期值匹配，并使用断言或调试打印来确认每个计算步骤中张量的形状来解决此问题。

最后，本章解决了计算中出现 `NaN` 值的问题，这可能导致训练失败。我们确定了数值不稳定的来源，例如容易溢出或除零的操作。实施的解决方案包括应用正则化技术以防止权重变得过大，实现梯度裁剪以限制更新幅度，调整学习率，以及使用 `softmax` 等数学函数的稳定版本。总之，通过了解具体化错误的成因，利用 `JAX` 特定的调试工具，验证张量形状并解决数值不稳定性，开发者增强了其在 Fashion-MNIST 数据集上机器学习模型的可靠性和鲁棒性。

# 第 4 章：掌握 Pytrees 用于数据结构

## 概述
`Pytrees` 是由列表、元组和字典等 Python 容器组成的树。它们是表示复杂分层结构的理想工具。本章将向您展示 `Pytrees` —— `JAX` 中不可或缺的数据结构 —— 如何让您灵活地处理嵌套数据。

我们首先研究使用 `Pytrees` 处理嵌套数据的最佳方法。我们将向您展示导航和修改这些结构的最实用方法。如果您想处理机器学习模型中的参数和配置，了解这些操作至关重要。接下来，我们将展示如何为用户自定义类创建自定义 `Pytrees`，从而将您自己的数据类型无缝集成到 `JAX` 的生态系统中。

最后，本章涵盖了 `Pytrees` 的序列化和反序列化，这对于保存和加载模型或检查点至关重要。您将学习如何高效地存储 `Pytrees` 并在以后重建它们，确保模型可以无损持久化。此外，我们还讨论了过滤 `Pytrees` 以提取特定参数或数据子集的方法，当对模型的不同部分应用不同操作时，您会发现这很有用。



# 使用 Pytrees 操作嵌套数据

在处理涉及复杂架构或大型参数集的机器学习模型时，你经常会遇到深度嵌套的数据结构。这些结构可以由列表、元组、字典以及其他包含数组或标量的容器组成。当你需要在所有元素上统一应用转换或操作时，管理和操作此类嵌套数据变得具有挑战性。当将这些操作与期望特定格式数据的 JAX 变换如 or 集成时，难度进一步加剧。

JAX 引入了 的概念，它们是由列表、元组和字典等容器组成的灵活嵌套数据结构，叶子节点为数组或标量。Pytrees 允许你以 JAX 能够理解并高效操作的方式表示复杂分层数据。JAX 提供了诸如 和 `jax.tree_unflatten` 的实用函数来遍历和操作 Pytrees。通过利用这些工具，你可以在不手动处理每个嵌套层级的情况下对嵌套结构应用函数。

## 理解 Pytrees

PyTree 是任何嵌套的 Python 容器结构，其中叶子节点为数组或标量。JAX 将这些结构视为树，从而实现对其的操作。

以下是 PyTree 的示例：

```
import jax
import jax.numpy as jnp
# Define a PyTree of model parameters
params = {
    'layer1': {
        'weights': jnp.array([[0.1, 0.2], [0.3, 0.4]]),
        'biases': jnp.array([0.1, 0.2])
    },
    'layer2': {
        'weights': jnp.array([[0.5, 0.6], [0.7, 0.8]]),
        'biases': jnp.array([0.3, 0.4])
    }
}
```

在此示例中，`params` 是一个嵌套字典，包含 JAX 数组作为叶子节点。

## 使用 `jax.tree_map` 对 Pytrees 应用函数

`jax.tree_map` 函数将给定函数应用于 PyTree 中的每个叶子节点，同时保持整体结构。

以下是缩放所有参数的示例：

```
# Function to scale parameters
def scale_fn(param):
    return param * 0.5
# Apply the scaling function over the PyTree
scaled_params = jax.tree_map(scale_fn, params)
```

这里，`scaled_params` 与 的结构相同，但每个数值都被减半。

## 处理多个 Pytrees

`jax.tree_map` 可以在多个 Pytrees 上同时操作，前提是它们具有相同的结构。以下是添加两个 Pytrees 的演示：

```
# Define another PyTree with the same structure
params2 = {
    'layer1': {
        'weights': jnp.array([[0.01, 0.02], [0.03, 0.04]]),
        'biases': jnp.array([0.01, 0.02])
    },
    'layer2': {
        'weights': jnp.array([[0.05, 0.06], [0.07, 0.08]]),
        'biases': jnp.array([0.03, 0.04])
    }
}
# Function to add parameters from two Pytrees
def add_fn(p1, p2):
    return p1 + p2
# Add corresponding leaves
sum_params = jax.tree_map(add_fn, params, params2)
```

## 展平和展开 Pytrees

我们可以使用 `jax.tree_flatten` 将 PyTree 转换为叶子节点的扁平列表和结构（treedef）。以下是展平 PyTree 的快速示例：

```
# Flatten the PyTree
leaves, treedef = jax.tree_flatten(params)
print("Leaves:", leaves)
print("TreeDef:", treedef)
```

我们可以按如下方式展开 PyTree：

```
# Reconstruct the PyTree from leaves and treedef
reconstructed_params = jax.tree_unflatten(treedef, leaves)
```

## 使用 Pytrees 应用 JAX 变换

现在，像 grad 和 jit 这样的 JAX 变换可以与接受 Pytrees 的函数无缝协作。

```
# Define a simple model function
def model(params, x):
    # Forward pass using parameters in PyTree
    a = x @ params['layer1']['weights'] + params['layer1']['biases']
    a = jax.nn.relu(a)
    y = a @ params['layer2']['weights'] + params['layer2']['biases']
    return y
# Define a loss function
def loss_fn(params, x, y_true):
    y_pred = model(params, x)
    loss = jnp.mean((y_pred - y_true) ** 2)
    return loss
# Generate some dummy data
x_data = jnp.array([[1.0, 2.0], [3.0, 4.0]])
y_data = jnp.array([[1.0, 2.0], [3.0, 4.0]])
# Compute gradients with respect to parameters
grads = jax.grad(loss_fn)(params, x_data, y_data)
```

## 使用梯度更新参数

我们可以使用 `jax.tree_map` 根据梯度更新参数。

```
learning_rate = 0.01
# Function to update parameters
def update_fn(param, grad):
    return param - learning_rate * grad
# Update parameters
updated_params = jax.tree_map(update_fn, params, grads)
```

这些 Pytrees 可以包含任何组合的嵌套容器。下面可以看到嵌套的列表和元组：

```
# Define a more complex PyTree
complex_params = [
    {'weights': jnp.array([1.0, 2.0]), 'biases': jnp.array([0.1, 0.2])},
    (
        {'weights': jnp.array([3.0, 4.0]), 'biases': jnp.array([0.3, 0.4])},
        {'weights': jnp.array([5.0, 6.0]), 'biases': jnp.array([0.5, 0.6])}
    )
]
# Apply a function over the complex PyTree
scaled_complex_params = jax.tree_map(lambda x: x * 2, complex_params)
```

## 基于条件过滤叶子节点

然后你可以使用自定义函数按如下方式过滤和操作特定叶子节点：

```
def is_weight(key, _):
    return key == 'weights'
def conditional_scale(tree):
    def scale_if_weight(key, val):
        if key == 'weights':
            return val * 0.5
        else:
            return val
    return jax.tree_map(scale_if_weight, tree, is_leaf=lambda x: isinstance(x, dict))
scaled_params = conditional_scale(params)
```

## 定义自定义 PyTree 节点

你也可以通过向 JAX 注册来将自定义对象定义为 PyTree 节点。例如，你可以注册一个自定义类。

```
from jax import tree_util
class LayerParams:
    def __init__(self, weights, biases):
        self.weights = weights
        self.biases = biases
# Register LayerParams as a PyTree node
def layerparams_flatten(obj):
    children = (obj.weights, obj.biases)
    aux_data = None
    return children, aux_data
def layerparams_unflatten(aux_data, children):
    return LayerParams(*children)
tree_util.register_pytree_node(LayerParams, layerparams_flatten, layerparams_unflatten)
# Use LayerParams in a PyTree
params_custom = {
    'layer1': LayerParams(weights=jnp.array([0.1]), biases=jnp.array([0.2]))
}
# Apply a function over the PyTree
scaled_params_custom = jax.tree_map(lambda x: x * 2, params_custom)
```

## 训练循环集成

稍后，将 Pytrees 集成到你的训练循环中以管理参数和更新。

```
# Define the training loop
def train_step(params, x, y):
    grads = jax.grad(loss_fn)(params, x, y)
    params = jax.tree_map(lambda p, g: p - learning_rate * g, params, grads)
    return params
# JIT-compile the training step
train_step_jit = jax.jit(train_step)
# Simulate training
for epoch in range(10):
    params = train_step_jit(params, x_data, y_data)
    current_loss = loss_fn(params, x_data, y_data)
    print(f"Epoch {epoch}, Loss: {current_loss}")
```

这种整体方法增强了代码的可维护性，并与 JAX 变换无缝集成，从而实现高效的计算和梯度计算。利用 Pytrees 使你能够轻松构建和管理复杂的机器学习模型。



# 用户自定义类的自定义 PyTree

在使用 `JAX` 构建复杂的机器学习模型时，你可能会定义自定义类来表示层、模块或其他组件。然而，这些用户定义的类不会被 `JAX` 的 PyTree 系统自动识别。因此，像 和 这样的函数以及诸如 `jit` 或 `grad` 的变换无法遍历或操作这些自定义对象中的数据。这种不兼容使得将自定义类与 `JAX` 的功能集成变得困难，阻碍了模型的无缝开发。挑战在于使自定义类与 `JAX` 的 PyTree 兼容，以便在保持代码整洁和模块化的同时利用 `JAX` 的强大工具。

要将自定义类与 `JAX` 的 PyTree 系统集成，可以将类注册为 PyTree 节点。这涉及定义如何将类展平为其组成部分的叶子（其持有的數據）以及如何从这些叶子重构（反展平）它。通过使用 `JAX` 的 `tree_util` 模块注册类，你使 `JAX` 在变换期间以及使用 PyTree 工具时能够识别并遍历类的实例。此过程允许自定义对象像内置容器类型一样被操作，使其与 `JAX` 函数兼容。

## Define Custom Class

让我们假设我们有一个表示神经网络层的自定义类：

```
import jax
import jax.numpy as jnp
class NeuralLayer:
    def __init__(self, weights, biases):
        self.weights = weights
        self.biases = biases
    def __call__(self, x):
        z = jnp.dot(x, self.weights) + self.biases
        return jax.nn.relu(z)
```

在这个类中，`weights` 和 `biases` 是表示该层参数的 `JAX` 数组。

## Use JAX Functions

现在，尝试在类的实例上使用 `jax.tree_map`：

```
layer = NeuralLayer(weights=jnp.array([[0.1, 0.2], [0.3, 0.4]]),
                    biases=jnp.array([0.1, 0.2]))
# Attempt to scale the parameters
scaled_layer = jax.tree_map(lambda x: x * 0.5, layer)
```

这将引发错误，因为 `JAX` 不知道如何遍历

接下来，如之前所学，定义展平和反展平函数。

```
from jax import tree_util
def neural_layer_flatten(layer):
    # The leaves are the parameters we want to transform
    leaves = (layer.weights, layer.biases)
    # Auxiliary data includes any static information needed to reconstruct the object
    aux_data = {}
    return leaves, aux_data
def neural_layer_unflatten(aux_data, leaves):
    # Reconstruct the NeuralLayer object from leaves
    return NeuralLayer(*leaves)
```

## Register Custom Class as a PyTree Node

使用 `tree_util.register_pytree_node` 注册你的类：

```
tree_util.register_pytree_node(NeuralLayer,
                               neural_layer_flatten,
                               neural_layer_unflatten)
```

然后，你可以使用 `jax.tree_map` 和其他 `JAX` 工具与类的实例：

```
# Scale the parameters of the layer
scaled_layer = jax.tree_map(lambda x: x * 0.5, layer)
# Verify the parameters have been scaled
print("Scaled Weights:\n", scaled_layer.weights)
print("Scaled Biases:\n", scaled_layer.biases)
```

## Integrate with JAX Transformations

现在，你可以将自定义类包含在将被 `JAX` 转换的函数中，例如 `jit` 或 `grad`。下面展示了使用 `jit` 与自定义层的情况：

```
# Define a function that uses the custom layer
def forward_pass(layer, x):
    return layer(x)
# JIT-compile the forward pass
forward_pass_jit = jax.jit(forward_pass)
# Test the JIT-compiled function
x_input = jnp.array([[1.0, 2.0]])
output = forward_pass_jit(layer, x_input)
print("Output:", output)
```

## Compute Gradients

现在，计算关于自定义类中参数的损失函数的梯度。

```
# Define a simple loss function
def loss_fn(layer, x, y_true):
    y_pred = layer(x)
    loss = jnp.mean((y_pred - y_true) ** 2)
    return loss
# Generate dummy data
x_data = jnp.array([[1.0, 2.0], [3.0, 4.0]])
y_data = jnp.array([[0.5, 1.0], [1.5, 2.0]])
# Compute gradients
grads = jax.grad(loss_fn)(layer, x_data, y_data)
```

然后，使用 `jax.tree_map` 应用参数更新：

```
learning_rate = 0.01
# Update function
def update_params(param, grad):
    return param - learning_rate * grad
# Update the layer's parameters
updated_layer = jax.tree_map(update_params, layer, grads)
```

## Combine Multiple Layers into a Model

你可以将多个自定义层组合成更大的模型：

```
class NeuralNetwork:
    def __init__(self, layers):
        self.layers = layers
    def __call__(self, x):
        for layer in self.layers:
            x = layer(x)
        return x
# Create multiple layers
layer1 = NeuralLayer(weights=jnp.array([[0.1, 0.2], [0.3, 0.4]]),
                     biases=jnp.array([0.1, 0.2]))
layer2 = NeuralLayer(weights=jnp.array([[0.5, 0.6], [0.7, 0.8]]),
                     biases=jnp.array([0.3, 0.4]))
# Create the neural network
model = NeuralNetwork(layers=[layer1, layer2])
# Register NeuralNetwork as a PyTree node
def nn_flatten(nn):
    leaves = nn.layers
    aux_data = {}
    return leaves, aux_data
def nn_unflatten(aux_data, leaves):
    return NeuralNetwork(layers=leaves)
tree_util.register_pytree_node(NeuralNetwork, nn_flatten, nn_unflatten)
```

现在你可以使用 `JAX` 变换继续训练模型：

```
# Define the loss function for the model
def model_loss_fn(model, x, y_true):
    y_pred = model(x)
    loss = jnp.mean((y_pred - y_true) ** 2)
    return loss
# Compute gradients with respect to the model parameters
model_grads = jax.grad(model_loss_fn)(model, x_data, y_data)
# Update the model parameters
updated_model = jax.tree_map(update_params, model, model_grads)
```

## Use `vmap` and other Transformations

因为你的自定义类现在与 PyTree 兼容，所以你可以使用 `vmap` 来向量化操作：

```
# Vectorize the forward pass over a batch of inputs
batched_forward = jax.vmap(forward_pass, in_axes=(None, 0))
# Apply to a batch of inputs
outputs = batched_forward(layer, x_data)
print("Batched Outputs:\n", outputs)
```

如果你的类包含静态字段（不应被转换的数据），你可以在展平期间将它们包含在辅助数据中。

```
class NeuralLayerStatic:
    def __init__(self, weights, biases, activation_fn):
        self.weights = weights
        self.biases = biases
        self.activation_fn = activation_fn  # Static field
    def __call__(self, x):
        z = jnp.dot(x, self.weights) + self.biases
        return self.activation_fn(z)
def layer_static_flatten(layer):
    leaves = (layer.weights, layer.biases)
    aux_data = layer.activation_fn
    return leaves, aux_data
def layer_static_unflatten(aux_data, leaves):
    return NeuralLayerStatic(*leaves, activation_fn=aux_data)
tree_util.register_pytree_node(NeuralLayerStatic,
                               layer_static_flatten,
                               layer_static_unflatten)
```

通过将自定义类注册为 PyTree，你使 `JAX` 能够使用其强大的函数式变换识别和操作它们。这种集成允许你在不牺牲与 `JAX` 生态系统兼容性的情况下保持干净、面向对象的代码。现在你可以无缝地将自定义类包含在计算中，应用诸如 `jit` 和 `grad` 的变换，并利用诸如 `jax.tree_map` 的工具进行参数更新。



# 序列化与反序列化 Pytrees

对于训练期间的检查点保存、模型持久化或在不同环境之间迁移模型等任务而言，高效地保存（序列化）和加载（反序列化）Pytrees 至关重要。然而，由于 Pytrees 可能包含复杂嵌套结构和自定义对象，标准序列化方法可能不足或导致效率低下。挑战在于找到有效的方法来序列化和反序列化 Pytrees，确保模型参数能够准确保存和恢复，从而促进检查点保存和长期存储。

## 方法

为了序列化和反序列化 Pytrees，我们可以使用处理复杂数据结构并支持高效存储格式的库。最常见的方法包括使用：

- A Python built-in module that serializes and deserializes Python objects. However, it's not always the most efficient or secure method.
- A binary serialization format that's faster and more efficient than JSON.
- JAX's built-in Functions like `jax.tree_map` and `jax.tree_flatten` can be combined with serialization libraries to handle Pytrees.
- Custom serialization for user-defined classes registered as Pytrees, we may need to define custom serialization logic.

在本教程中，我们将重点使用 `flax.serialization`，它提供了高效序列化和反序列化 Pytrees 的工具。我们将学习如何保存和加载组织为 Pytrees 的模型参数。

## 安装

首先，我们先安装 Flax：

```bash
pip install flax
```

## 将模型参数理解为 Pytrees

假设你有一个模型，其参数以 PyTree 结构组织：

```python
import jax
import jax.numpy as jnp
# Example model parameters as a PyTree
params = {
    'layer1': {
        'weights': jnp.array([[0.1, 0.2], [0.3, 0.4]]),
        'biases': jnp.array([0.1, 0.2])
    },
    'layer2': {
        'weights': jnp.array([[0.5, 0.6], [0.7, 0.8]]),
        'biases': jnp.array([0.3, 0.4])
    }
}
```

导入必要的模块：

```python
from flax import serialization
```

## 将 PyTree 序列化为字节

然后，使用 `flax.serialization.to_bytes` 将 PyTree 转换为适合保存到文件中的字节对象。

```python
# Serialize the parameters to bytes
param_bytes = serialization.to_bytes(params)
```

接下来，使用标准文件 I/O 操作将序列化的字节写入文件。

```python
# Save to a file
with open('model_params.msgpack', 'wb') as f:
    f.write(param_bytes)
```

这使用 MessagePack 以二进制格式保存模型参数，该格式高效且保留结构。

## 加载和反序列化 PyTree

现在，要将参数加载回 PyTree，请从文件中读取字节并使用

```python
# Read from the file
with open('model_params.msgpack', 'rb') as f:
    loaded_bytes = f.read()
# Deserialize the bytes back to a PyTree
# Provide an empty PyTree with the same structure as the original
empty_params = jax.tree_map(lambda x: jnp.zeros_like(x), params)
# Deserialize
loaded_params = serialization.from_bytes(empty_params, loaded_bytes)
```

这里，由于反序列化过程需要了解结构，我们提供一个与原始结构相同的空 PyTree。

在这里，确保加载的参数与原始参数匹配。

```python
# Verify that the parameters are the same
def compare_params(p1, p2):
    return all([jnp.allclose(a, b) for a, b in zip(jax.tree_leaves(p1), jax.tree_leaves(p2))])
print("Parameters match:", compare_params(params, loaded_params))
```

## 处理 Pytrees 中的自定义类

如果你的 PyTree 包含注册为 Pytrees 的用户自定义类，请确保它们可序列化。对于自定义类，你可能需要实现自定义序列化方法。

查看以下关于自定义类的示例：

```python
class NeuralLayer:
    def __init__(self, weights, biases):
        self.weights = weights
        self.biases = biases
    # ... (methods omitted for brevity)
```

然后，将该类注册为 PyTree 节点：

```python
from jax import tree_util
def neural_layer_flatten(layer):
    # The leaves are the parameters we want to serialize
    leaves = (layer.weights, layer.biases)
    # Auxiliary data can be any static data needed to reconstruct the object
    aux_data = None
    return leaves, aux_data
def neural_layer_unflatten(aux_data, leaves):
    return NeuralLayer(*leaves)
tree_util.register_pytree_node(NeuralLayer, neural_layer_flatten, neural_layer_unflatten)
```

对于序列化，你可能需要定义如何序列化和反序列化你的自定义类。

## 序列化和反序列化包含自定义类的 PyTree

现在，你可以序列化和反序列化包含自定义类的 PyTree。以下是示例程序：

```python
# Create a PyTree with custom classes
params_custom = {
    'layer1': NeuralLayer(weights=jnp.array([[0.1, 0.2], [0.3, 0.4]]),
                          biases=jnp.array([0.1, 0.2])),
    'layer2': NeuralLayer(weights=jnp.array([[0.5, 0.6], [0.7, 0.8]]),
                          biases=jnp.array([0.3, 0.4]))
}
# Serialize to bytes
param_bytes_custom = serialization.to_bytes(params_custom)
# Save to a file
with open('model_params_custom.msgpack', 'wb') as f:
    f.write(param_bytes_custom)
# Load from the file
with open('model_params_custom.msgpack', 'rb') as f:
    loaded_bytes_custom = f.read()
# Provide an empty PyTree template
empty_params_custom = jax.tree_map(lambda x: NeuralLayer(jnp.zeros_like(x.weights), jnp.zeros_like(x.biases)), params_custom)
# Deserialize
loaded_params_custom = serialization.from_bytes(empty_params_custom, loaded_bytes_custom)
```

## 在训练期间保存和加载检查点

在实践中，你可能希望在训练期间定期保存检查点。查看以下示例：

```python
# Training loop
num_epochs = 10
for epoch in range(num_epochs):
    # ... training code ...
    # Save checkpoint every 5 epochs
    if (epoch + 1) % 5 == 0:
        param_bytes = serialization.to_bytes(params)
        with open(f'checkpoint_epoch_{epoch+1}.msgpack', 'wb') as f:
            f.write(param_bytes)
```

接下来，执行从检查点加载的操作：

```python
# Load parameters from a specific checkpoint
with open('checkpoint_epoch_5.msgpack', 'rb') as f:
    loaded_bytes = f.read()
params = serialization.from_bytes(empty_params, loaded_bytes)
```

## 使用 `flax.training.checkpoints` 模块

Flax 还提供了以下更高级别的 API 用于管理检查点：

```python
from flax.training import checkpoints
# Save a checkpoint
checkpoints.save_checkpoint(ckpt_dir='./checkpoints', target=params, step=epoch)
# Restore from the latest checkpoint
restored_params = checkpoints.restore_checkpoint(ckpt_dir='./checkpoints', target=empty_params)
```

通过利用 `flax.serialization`，你可以有效地序列化和反序列化包含模型参数的 Pytrees，包括那些包含自定义类的 Pytrees。此功能允许你准确地保存和加载模型，促进训练期间的检查点保存和长期模型持久化。



# 为特定参数过滤 Pytrees

有时，你可能需要仅对 `Pytree` 中的特定参数应用更新或转换，例如对不同层应用不同的学习率、在训练期间冻结某些层，或仅修改 `weights` 而不修改 `biases`。挑战在于实现能够遍历 `Pytree` 并根据特定条件有选择地修改或提取元素的技术，而不影响其余结构。

## 选择性修改

要选择性地修改 `Pytree` 内的元素，可以使用 JAX 的树遍历工具，例如 `jax.tree_map` 并结合能够识别感兴趣参数的过滤函数。通过定义能够识别并仅对 `Pytree` 的特定部分进行操作的自定义函数，可以有选择地应用更新。

## 示例模型参数

让我们考虑一个表示模型参数的 `Pytree`，其组织为嵌套字典：

```
import jax
import jax.numpy as jnp
# Example model parameters
params = {
    'layer1': {
        'weights': jnp.array([[0.1, 0.2], [0.3, 0.4]]),
        'biases': jnp.array([0.1, 0.2]),
    },
    'layer2': {
        'weights': jnp.array([[0.5, 0.6], [0.7, 0.8]]),
        'biases': jnp.array([0.3, 0.4]),
    },
    'layer3': {
        'weights': jnp.array([[0.9, 1.0], [1.1, 1.2]]),
        'biases': jnp.array([0.5, 0.6]),
    },
}
```

在此示例中，`params` 是一个 `Pytree`，包含三层，每层包含 `weights` 和

## 定义过滤函数

现在创建一个函数，根据条件确定参数是否应被更新。例如，假设你只想更新 `weights` 而不更新

```
def is_weight(param_name):
    return 'weights' in param_name
```

## 使用 `jax.tree_map` 遍历 Pytree 并进行过滤

由于 `jax.tree_map` 不能直接访问参数名称，我们需要使用包含路径的自定义遍历函数。

```
def tree_map_with_path(f, tree):
    def helper(path, subtree):
        if isinstance(subtree, dict):
            return {k: helper(path + (k,), v) for k, v in subtree.items()}
        else:
            return f(path, subtree)
    return helper((), tree)
```

## 基于参数名称选择性地应用更新

创建一个使用路径来决定是否更新参数的更新函数。

```
learning_rate = 0.01
def update_param(path, param):
    # path is a tuple of keys leading to the param
    if 'weights' in path:
        # Apply the update to weights
        grad = compute_gradient_for_param(param)  # Placeholder for gradient computation
        return param - learning_rate * grad
    else:
        # Do not update biases; return the original param
        return param
```

不要忘记用该参数的实际梯度替换 `compute_gradient_for_param(param)`。

接下来，使用自定义遍历函数应用更新。

```
updated_params = tree_map_with_path(update_param, params)
```

## 与梯度计算集成

假设你已以相同结构计算了梯度，你可以修改 `update_param` 函数以包含梯度。

```
def update_param_with_grad(path, param, grad):
    if 'weights' in path:
        return param - learning_rate * grad
    else:
        return param
```

现在，创建一个函数同时遍历 `params` 和 `grads`。

```
def tree_map_with_path_and_grad(f, tree, grads):
    def helper(path, subtree, grad_subtree):
        if isinstance(subtree, dict):
            return {k: helper(path + (k,), v, grad_subtree[k]) for k, v in subtree.items()}
        else:
            return f(path, subtree, grad_subtree)
    return helper((), tree, grads)
```

然后，应用该函数：

```
updated_params = tree_map_with_path_and_grad(update_param_with_grad, params, grads)
```

接下来，检查只有 `weights` 被更新。

```
# Access updated weights and biases
print("Updated layer1 weights:", updated_params['layer1']['weights'])
print("Original layer1 biases:", updated_params['layer1']['biases'])  # Should be unchanged
```

## 泛化过滤函数

假设你想冻结某些层的参数，例如冻结 `layer1` 并仅更新 `layer2` 和

为此，修改 `update_param_with_grad` 函数：

```
def update_param_with_grad(path, param, grad):
    if 'layer1' in path:
        # Do not update parameters in layer1
        return param
    else:
        # Update other layers
        return param - learning_rate * grad
```

然后，应用更新。

```
updated_params = tree_map_with_path_and_grad(update_param_with_grad, params, grads)
```

## 使用正则表达式进行复杂过滤

对于更复杂的过滤，可以使用正则表达式匹配参数名称。

```
import re
def update_param_with_regex(path, param, grad, pattern):
    param_name = '/'.join(path)
    if re.match(pattern, param_name):
        # Update parameters matching the pattern
        return param - learning_rate * grad
    else:
        # Do not update other parameters
        return param
pattern = r'^layer[23]/weights$'  # Example pattern
updated_params = tree_map_with_path_and_grad(
    lambda path, param, grad: update_param_with_regex(path, param, grad, pattern),
    params,
    grads
)
```

现在，假设你想对不同层应用不同的学习率。

```
def update_param_with_variable_lr(path, param, grad):
    if 'layer1' in path:
        lr = 0.01
    elif 'layer2' in path:
        lr = 0.001
    else:
        lr = 0.0001
    return param - lr * grad
updated_params = tree_map_with_path_and_grad(update_param_with_variable_lr, params, grads)
```

## 使用 `optax` 进行参数掩码

或者，你可以使用 `optax` 库定义参数掩码并选择性地应用优化器。

```
import optax
# Define parameter masks
def mask_fn(params):
    masks = {}
    def create_mask(path, param):
        if 'weights' in path:
            return True  # Update weights
        else:
            return False  # Do not update biases
    masks = tree_map_with_path(create_mask, params)
    return masks
# Create an optimizer with masks
optimizer = optax.chain(
    optax.masked(optax.sgd(learning_rate=0.01), mask_fn(params))
)
# Initialize optimizer state
opt_state = optimizer.init(params)
# Compute updates
updates, opt_state = optimizer.update(grads, opt_state, params)
# Apply updates
updated_params = optax.apply_updates(params, updates)
```

## 组合多个掩码

你现在可以通过组合多个条件创建复杂的掩码。

```
def mask_fn(params):
    def create_mask(path, param):
        if 'layer1' in path and 'weights' in path:
            return True  # Update weights in layer1
        elif 'layer2' in path:
            return False  # Freeze layer2
        else:
            return True  # Update other parameters
    return tree_map_with_path(create_mask, params)
# Use the mask in the optimizer
optimizer = optax.chain(
    optax.masked(optax.sgd(learning_rate=0.01), mask_fn(params))
)
```

接下来，将选择性参数更新集成到你的训练循环中。

```
# Training loop
for epoch in range(num_epochs):
    # Compute gradients
    grads = compute_gradients(params, data)
    # Update parameters selectively
    updates, opt_state = optimizer.update(grads, opt_state, params)
    params = optax.apply_updates(params, updates)
    # ... rest of training loop ...
```

这些方法为训练模型提供了灵活性，无论是否需要冻结某些层、应用不同的学习率或仅更新 `weights` 而不更新 `biases`。自定义遍历函数、参数掩码和 `optax` 的使用使得能够高效管理复杂的参数结构，从而促进更可控和有效的训练过程。



## 摘要
概括来说，本章直面了在 `JAX` 变换中管理复杂嵌套数据结构的挑战。`Pytrees` 允许函数在嵌套容器上进行映射且不会出现任何问题，使得操作此类数据变得更加容易，并减少了对递归函数的需要。我们随后转向了自定义类与 `JAX` 的 `Pytrees` 不兼容的问题。通过定义这些类如何被展平和重建，`JAX` 能够在变换期间识别并遍历自定义类的实例。接下来，我们解决了序列化与反序列化 `Pytrees` 的必要性。本章展示了序列化与反序列化 `Pytrees` 的最有效方法，特别是使用 `flax.serialization` 库。
最后，本章解决了在 `Pytree` 内对特定参数应用更新的挑战。我们实现了根据特定条件或标准遍历并选择性修改 `Pytree` 中元素的技术。选择性操作对于诸如对不同层应用不同的学习率、在训练期间冻结某些层，或仅更新特定类型的参数如权重但不更新偏置等场景至关重要。通过定义自定义遍历函数并利用过滤机制，你可以在仅修改所需元素的同时保持 `Pytree` 的整体结构。
总之，本章提供了全面理解如何在 `JAX` 中掌握数据结构的 `Pytrees`。它为读者提供了所需的实践技能，以便高效地操作嵌套数据、将自定义类与 `JAX` 的 `Pytrees` 集成、序列化与反序列化复杂数据结构，以及在 `Pytrees` 内选择性地更新参数。

# 第 5 章：导出与序列化

## 概述
在本章中，我们将介绍使用 Google `JAX` 开发的模型在导出和序列化方面的基本要素，特别关注 Fashion-MNIST 数据集。我们首先研究保存训练好的模型的最佳方式，确保它们能够在不同环境中快速加载并用于推理。这些技术使你能够持久化模型参数并处理模型部署涉及的必要数据结构。
接下来，我们将研究如何保存和恢复长时间运行的任务。这对于维护可能耗时很长或被中断的训练过程的进度至关重要。我们实施最佳的检查点策略以在不丢失任何进度的情况下恢复训练，确保其可靠且高效地完成。我们还研究将 `JAX` 模型转换为其他框架的方法，促进互操作性并利用不同机器学习生态系统的优势。
最后，你将学习如何在 `JAX` 中序列化自定义对象，包括序列化复杂数据结构和用户定义类。在本章的整个过程中，你将获得所需的实践技能，以便导出和序列化 `JAX` 模型，从而能够自信地部署你的机器学习解决方案并与他人分享。



# 为部署保存训练模型

在训练神经网络模型后，您可能需要将模型部署到生产环境中进行推理。然而，与某些其他框架不同，`JAX` 没有内置的、标准化的模型导出方法，包括架构和训练参数。这可能会使如何保存和加载模型以进行部署变得不明确。这里的情况是找到一种有效的方法来序列化模型参数和架构，以便训练好的模型可以轻松加载并在生产环境中使用，并且推理期间的模型性能与训练期间观察到的性能相匹配。

因此，在这里，要部署训练好的 `JAX` 模型，主要需要保存两个主要组件：

* `Model Parameters`（权重和偏置）。这些通常以 `Pytrees` 组织，并可使用 `flax.serialization` 序列化。
* `Model Architecture`。由于 `JAX` 使用函数式编程范式，模型架构由您编写的函数定义。要“保存”架构，您可以保存源代码，或如果您使用了支持模型序列化的 `Flax` 或 `Haiku`，则使用序列化方法。

在本教程中，我们将探讨保存和加载模型参数和架构的方法，以便将您的 `JAX` 模型部署用于生产。

## 定义和训练模型

让我们首先定义模型：

```python
class FashionMNISTModel(nn.Module):
    @nn.compact
    def __call__(self, x):
        x = x.reshape((x.shape[0], -1))  # Flatten the images
        x = nn.Dense(features=128)(x)
        x = nn.relu(x)
        x = nn.Dense(features=10)(x)
        x = nn.log_softmax(x)  # For classification
        return x
```

然后，加载和准备数据：

```python
# Load the dataset
ds_builder = tfds.builder('fashion_mnist')
ds_builder.download_and_prepare()
train_ds = tfds.as_numpy(ds_builder.as_dataset(split='train', batch_size=-1))
test_ds = tfds.as_numpy(ds_builder.as_dataset(split='test', batch_size=-1))
# Convert to JAX arrays
train_images = jnp.array(train_ds['image']) / 255.0
train_labels = jnp.array(train_ds['label'])
test_images = jnp.array(test_ds['image']) / 255.0
test_labels = jnp.array(test_ds['label'])
```

接下来，创建训练函数：

```python
def create_train_state(rng, learning_rate):
    model = FashionMNISTModel()
    params = model.init(rng, jnp.ones([1, 28, 28]))['params']
    tx = optax.sgd(learning_rate)
    return train_state.TrainState.create(apply_fn=model.apply, params=params, tx=tx)
```

之后，定义损失和准确率函数：

```python
def compute_metrics(logits, labels):
    loss = jnp.mean(optax.softmax_cross_entropy(logits, one_hot(labels, num_classes=10)))
    accuracy = jnp.mean(jnp.argmax(logits, -1) == labels)
    return {'loss': loss, 'accuracy': accuracy}

def one_hot(labels, num_classes):
    return jnp.eye(num_classes)[labels]
```

然后，开始训练模型：

```python
@jit
def train_step(state, batch):
    def loss_fn(params):
        logits = state.apply_fn({'params': params}, batch['image'])
        loss = jnp.mean(optax.softmax_cross_entropy(logits, one_hot(batch['label'], 10)))
        return loss
    grads = grad(loss_fn)(state.params)
    state = state.apply_gradients(grads=grads)
    return state

# Prepare the training data
batch_size = 128
num_epochs = 5
steps_per_epoch = train_images.shape[0] // batch_size
rng = random.PRNGKey(0)
state = create_train_state(rng, learning_rate=0.1)
for epoch in range(num_epochs):
    perm = random.permutation(rng, train_images.shape[0])
    for i in range(steps_per_epoch):
        batch_idx = perm[i * batch_size:(i + 1) * batch_size]
        batch = {'image': train_images[batch_idx], 'label': train_labels[batch_idx]}
        state = train_step(state, batch)
    print(f'Epoch {epoch + 1} completed.')
```

## 保存模型参数

训练后，您需要使用 `flax.serialization` 保存模型的参数。

```python
from flax.training import checkpoints
# Save the checkpoint
ckpt_dir = './checkpoints'
checkpoints.save_checkpoint(ckpt_dir, target=state.params, step=0, overwrite=True)
```

这会以可稍后轻松恢复的格式保存模型参数。

## 保存和加载模型以进行推理

在我们的例子中，由于模型除了参数之外没有其他状态，保存类定义是最好的方法。然后，我们可以加载模型参数并在生产环境中使用模型进行推理。

为此，我们首先加载参数：

```python
# Load the checkpoint
from flax.training import checkpoints
ckpt_dir = './checkpoints'
params = checkpoints.restore_checkpoint(ckpt_dir, target=None)
```

然后，实例化模型：

```python
model = FashionMNISTModel()
```

随后，我们定义一个推理函数：

```python
def predict(images):
    logits = model.apply({'params': params}, images)
    predictions = jnp.argmax(logits, axis=-1)
    return predictions
```

接下来，我们在新数据上测试模型：

```python
# Use test images for demonstration
sample_images = test_images[:10]
sample_labels = test_labels[:10]
predictions = predict(sample_images)
print("Predictions:", predictions)
print("Actual Labels:", sample_labels)
```

## 部署模型

根据部署目标，可以是 Web 服务器、云函数或嵌入式设备，我们需要：

* 设置服务器或端点以接收输入数据并返回预测结果。
* 确保环境已正确配置所有依赖项。
* 根据需要实施安全和可扩展性措施。

下面给出了模型部署的快速示例：

```python
# inference.py
from flask import Flask, request, jsonify
import jax
import jax.numpy as jnp
from flax import linen as nn
from flax.training import checkpoints
from model import FashionMNISTModel
app = Flask(__name__)
# Load the model parameters
ckpt_dir = './checkpoints'
params = checkpoints.restore_checkpoint(ckpt_dir, target=None)
# Instantiate the model
model = FashionMNISTModel()
# JIT-compiled prediction function
@jax.jit
def predict(images):
    logits = model.apply({'params': params}, images)
    predictions = jnp.argmax(logits, axis=-1)
    return predictions

@app.route('/predict', methods=['POST'])
def predict_route():
    data = request.get_json()
    images = jnp.array(data['images']) / 255.0  # Normalize if necessary
    preds = predict(images).tolist()
    return jsonify({'predictions': preds})

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8080)
```

## 测试部署

最后，要进行测试，只需向端点发送请求：

```python
import requests
import json
# Sample data
sample_images = test_images[:2]
sample_images_list = sample_images.tolist()
# Send a POST request
response = requests.post('http://localhost:8080/predict', json={'images': sample_images_list})
# Get the predictions
predictions = response.json()['predictions']
print("Predictions:", predictions)
```

如果您遵循这些步骤，您将能够轻松保存训练好的 `JAX` 模型并部署它们。使用 `Flax`，我们看到了它如何使持久化模型和共享它们变得更容易，并将其集成到应用程序中。



# 长时间运行任务的检查点

如果你不定期保存模型状态，像停电、系统崩溃或可抢占云实例之类的意外情况可能会导致你丢失训练进度。这会造成时间和计算资源的真正浪费。目标是建立一个稳健的检查点计划，在训练期间以固定间隔保存模型的状态。

为了避免丢失训练进度，你可以设置检查点以定期保存模型的参数、优化器状态以及恢复训练所需的任何其他信息。在 `JAX` 中，你可以使用内置工具高效地序列化和反序列化训练状态，从而使检查点操作更简单。

## 创建训练状态

首先，设置我们定义的神经网络模型的训练状态，包括模型参数和优化器。

```python
def create_train_state(rng, learning_rate):
    model = FashionMNISTModel()
    params = model.init(rng, jnp.ones([1, 28, 28]))['params']
    tx = optax.adam(learning_rate)
    return train_state.TrainState.create(apply_fn=model.apply, params=params, tx=tx)
```

接下来，定义损失和准确率指标：

```python
def compute_metrics(logits, labels):
    loss = optax.softmax_cross_entropy_with_integer_labels(logits, labels).mean()
    accuracy = jnp.mean(jnp.argmax(logits, -1) == labels)
    return {'loss': loss, 'accuracy': accuracy}
```

## 实现训练步骤

接下来，我们使用 `jax.jit` 编译训练步骤以提高效率。

```python
@jit
def train_step(state, batch):
    def loss_fn(params):
        logits = FashionMNISTModel().apply({'params': params}, batch['images'])
        loss = optax.softmax_cross_entropy_with_integer_labels(logits, batch['labels']).mean()
        return loss
    grads = grad(loss_fn)(state.params)
    state = state.apply_gradients(grads=grads)
    return state
```

## 实现检查点

然后确定用于存储检查点的目录和保存频率。

```python
ckpt_dir = './checkpoints'
checkpoint_frequency = 5  # Save a checkpoint every 5 epochs
```

只需调整训练循环，使其定期保存检查点。

```python
import os
num_epochs = 50  # Example for a long-running job
rng = random.PRNGKey(0)
state = create_train_state(rng, learning_rate=0.001)
# Restore from the latest checkpoint if available
state = checkpoints.restore_checkpoint(ckpt_dir, target=state)
# Determine the starting epoch
start_epoch = int(state.step / len(train_ds))
for epoch in range(start_epoch, num_epochs):
    for batch in train_ds:
        state = train_step(state, batch)
    # Update the training step (epoch)
    state = state.replace(step=state.step + len(train_ds))
    # Save a checkpoint every 'checkpoint_frequency' epochs
    if (epoch + 1) % checkpoint_frequency == 0:
        checkpoints.save_checkpoint(ckpt_dir, target=state, step=state.step, overwrite=True)
        print(f'Checkpoint saved at step {state.step}')
    # Optionally, evaluate on the test set
    # ... (evaluation code)
    print(f'Epoch {epoch + 1} completed.')
```

为了快速总结上述脚本，`checkpoints.save_checkpoint` 函数会保存整个训练状态，包括模型参数和优化器状态。而且，我们设置 `overwrite=True` 以确保只保留最新的检查点，从而节省磁盘空间。

## 处理意外中断

在发生中断的情况下，你可以从最近保存的检查点恢复训练。

```python
# Before starting the training loop
state = checkpoints.restore_checkpoint(ckpt_dir, target=state)
# The rest of the training loop remains the same
```

## 自定义检查点策略

你可以根据需要自定义检查点策略。你可以保留最近的 N 个检查点，并在模型达到最佳验证准确率时保存模型。

```python
# In the evaluation section
if test_metrics['accuracy'] > best_accuracy:
    best_accuracy = test_metrics['accuracy']
    checkpoints.save_checkpoint(ckpt_dir, target=state, step=state.step, prefix='best_', overwrite=True)
    print('Best model checkpoint saved.')
```

完成后，以异步方式保存检查点，以免减慢整个训练速度。

## 测试检查点恢复

现在，在依赖检查点进行长时间运行任务之前，请测试你是否能正确保存和恢复训练状态。

```python
# Simulate interruption
checkpoints.save_checkpoint(ckpt_dir, target=state, step=state.step, overwrite=True)
print('Simulating interruption...')
# Reset state
state = create_train_state(rng, learning_rate=0.001)
# Restore state
state = checkpoints.restore_checkpoint(ckpt_dir, target=state)
print('State restored. Resuming training...')
```

如果你使用 `Flax` 的工具来设置检查点，就可以在训练中断时确保不会丢失任何进度。如果定期保存模型状态，你可以使用最近的检查点继续上次中断的地方，这有助于避免浪费计算资源。对于长时间运行的训练任务来说这是必不可少的，尤其是在使用可抢占云实例或在中断较为常见的环境中工作时。



# 将 JAX 模型转换为其他框架

有时你可能需要将你的 `JAX` 模型与其他机器学习框架结合使用，或部署到不直接支持 `JAX` 的地方。例如，你可能想要使用提供特定工具或优化的框架，或将模型部署到需要标准格式如 `ONNX`（开放神经网络交换）的平台。由于 `JAX` 不直接支持将模型导出为其他框架可用的格式，因此挑战在于找到一种方法将你的 `JAX` 模型转换为可在其他地方使用的格式，如 `ONNX`，同时不损失模型的完整性或性能。

如果你想将 `JAX` 模型导出为其他框架如 `ONNX` 可用的格式，可以使用 `jax2tf` 模块。它将 `JAX` 函数转换为 `TensorFlow` 操作。 将模型转换为 `TensorFlow` 后，你可以使用 `TensorFlow` 的 `ONNX` 导出器将其转换为 `ONNX` 格式。这种两步流程让你能够将 `JAX` 模型与其他生态系统连接起来，提供更多部署选项。

## 不使用 Flax 的简单 JAX 模型

为此，让我们考虑一个不使用 `Flax` 的简单 `JAX` 模型。

```python
import jax.numpy as jnp

def relu(x):
    return jnp.maximum(0, x)

def predict(params, x):
    W1, b1, W2, b2 = params
    x = x.reshape((x.shape[0], -1))  # Flatten the images
    z1 = jnp.dot(x, W1) + b1
    a1 = relu(z1)
    z2 = jnp.dot(a1, W2) + b2
    logits = z2
    return logits
```

### 初始化模型参数

接下来，按如下方式初始化模型参数：

```python
import numpy as np

input_size = 784  # 28x28 images flattened
hidden_size = 128
output_size = 10  # Number of classes
key = jax.random.PRNGKey(0)
W1 = jax.random.normal(key, (input_size, hidden_size))
b1 = jnp.zeros(hidden_size)
W2 = jax.random.normal(key, (hidden_size, output_size))
b2 = jnp.zeros(output_size)
params = [W1, b1, W2, b2]
```

## 将 JAX 模型转换为 TensorFlow

进行转换时，首先需要示例输入数据以在转换过程中追踪模型。

```python
# Sample input batch
x_sample = jnp.ones((1, 28, 28))  # A batch of one image
```

接下来，导入 `jax2tf` 并转换 `predict` 函数。

```python
from jax.experimental import jax2tf
import tensorflow as tf

# Wrap the predict function to accept and return TensorFlow tensors
def predict_tf(params, x):
    return jax2tf.convert(lambda x: predict(params, x))(x)

# Convert the parameters to TensorFlow tensors
params_tf = [tf.convert_to_tensor(p) for p in params]

# Convert the sample input to TensorFlow tensor
x_sample_tf = tf.convert_to_tensor(np.array(x_sample), dtype=tf.float32)
```

## 构建用于导出的 TensorFlow 函数

你可以使用 `TensorFlow` 的 `Function` 装饰器构建可导出的可调用对象。

```python
@tf.function(input_signature=[tf.TensorSpec(shape=[None, 28, 28], dtype=tf.float32)])
def model_tf(x):
    return predict_tf(params_tf, x)
```

## 将 TensorFlow 模型转换为 ONNX

如果尚未安装，请先安装 `tf2onnx` 包。

```bash
pip install tf2onnx
```

接下来，你需要将模型导出到 `ONNX`。

```python
import tf2onnx

# Convert the TensorFlow model to ONNX
spec = (tf.TensorSpec((None, 28, 28), tf.float32),)
output_path = "model.onnx"

# Perform the conversion
model_proto, _ = tf2onnx.convert.from_function(
    model_tf,
    input_signature=spec,
    opset=13,  # Specify the ONNX opset version
    output_path=output_path
)
```

你可以使用 `onnx` 库加载并检查模型。

```python
import onnx

# Load the ONNX model
onnx_model = onnx.load(output_path)

# Check the model for errors
onnx.checker.check_model(onnx_model)
print("ONNX model is valid.")
```

## 使用 ONNX 模型运行推理

使用 `onnxruntime` 对导出的模型进行推理。

```bash
pip install onnxruntime
```

以下是快速推理示例：

```python
import onnxruntime as ort
import numpy as np

# Create an ONNX inference session
ort_session = ort.InferenceSession(output_path)

# Prepare input data
x_input = np.ones((1, 28, 28), dtype=np.float32)

# Run inference
outputs = ort_session.run(None, {'x': x_input})

# Get the output logits
logits = outputs[0]
print("Logits:", logits)
```

## 比较 JAX 和 ONNX 模型结果

确保 `JAX` 模型和 `ONNX` 模型的输出一致。

```python
# Get JAX model output
jax_output = predict(params, x_sample)

# Compare with ONNX model output
print("JAX logits:", jax_output)
print("ONNX logits:", logits)

# Check if the outputs are close
are_close = np.allclose(np.array(jax_output), logits, atol=1e-5)
print("Outputs are close:", are_close)
```

在这种方法中，模型参数是硬编码在 `TensorFlow` 函数中的。如果你想要更灵活的解决方案，特别是对于较大的模型，你可能需要考虑单独导出参数。

之后，你现在可以使用任何支持 `ONNX` 模型的框架或平台部署 `ONNX` 模型。



# 在 JAX 中序列化自定义对象

有时你可能会创建默认不可序列化的自定义层或对象。当你需要保存模型的状态（包括这些自定义组件）以用于检查点、模型持久化或部署等目的时，这可能会成为问题。标准序列化方法可能会失败，或者无法充分捕获重建这些自定义对象所需的信息。挑战在于开发一种序列化并反序列化自定义对象的方法，使其能够无缝保存和加载，同时保持模型的功能。

现在，要序列化自定义对象，你可以创建自定义序列化函数来定义对象如何转换为可序列化格式以及如何从中恢复。通过实现指定如何从自定义对象中提取必要数据以及如何重建它们的方法，你可以确保它们能够正确保存和加载。像 `flax.serialization` 这样的库可以扩展以处理自定义序列化逻辑，从而允许你与 `JAX` 的序列化生态系统集成。

## 定义自定义对象

假设你有一个自定义层定义为类：

```python
import jax.numpy as jnp
from flax import linen as nn
class CustomLayer(nn.Module):
    features: int
    @nn.compact
    def __call__(self, x):
        W = self.param('W', nn.initializers.lecun_normal(), (x.shape[-1], self.features))
        b = self.param('b', nn.initializers.zeros, (self.features,))
        return jnp.tanh(jnp.dot(x, W) + b)
```

接下来，将自定义层合并到模型中：

```python
class CustomModel(nn.Module):
    @nn.compact
    def __call__(self, x):
        x = x.reshape((x.shape[0], -1))
        x = CustomLayer(features=128)(x)
        x = nn.Dense(features=10)(x)
        x = nn.log_softmax(x)
        return x
```

## 初始化和训练模型

然后，像往常一样设置训练循环。

```python
from flax.training import train_state
import optax
def create_train_state(rng, learning_rate):
    model = CustomModel()
    params = model.init(rng, jnp.ones([1, 28, 28]))['params']
    tx = optax.adam(learning_rate)
    return train_state.TrainState.create(apply_fn=model.apply, params=params, tx=tx)
# Initialize the training state
rng = jax.random.PRNGKey(0)
state = create_train_state(rng, learning_rate=0.001)
# ... Training loop ...
```

## 序列化模型

当你尝试使用 保存模型参数时，你可能会由于自定义层而遇到问题。

```python
from flax.training import checkpoints
# Attempt to save the checkpoint
ckpt_dir = './checkpoints'
try:
    checkpoints.save_checkpoint(ckpt_dir, target=state.params, step=0, overwrite=True)
except Exception as e:
    print("Serialization failed:", e)
```

## 实现自定义序列化函数

为了处理 的序列化，你需要定义如何将其转换为可序列化状态以及如何恢复它。

```python
from flax.serialization import to_state_dict, from_state_dict
def custom_layer_state_dict(layer):
    # Extract parameters
    return {'W': layer.W, 'b': layer.b}
def custom_layer_from_state_dict(layer, state):
    # Restore parameters
    layer.W = state['W']
    layer.b = state['b']
    return layer
```

然后，注册序列化函数：

```python
from flax.serialization import register_serialization_state
register_serialization_state(
    CustomLayer, custom_layer_state_dict, custom_layer_from_state_dict
)
```

现在，使用 保存模型参数

```python
# Save the checkpoint
checkpoints.save_checkpoint(ckpt_dir, target=state.params, step=0, overwrite=True)
print("Model parameters saved successfully.")
```

## 加载模型参数

加载模型时，确保自定义序列化逻辑可用。

```python
# Restore the parameters
restored_params = checkpoints.restore_checkpoint(ckpt_dir, target=None)
```

然后，实例化模型并使用恢复的参数对其进行测试。

```python
model = CustomModel()
# Define an inference function
def predict(params, x):
    logits = model.apply({'params': params}, x)
    return logits
# Prepare sample input
x_sample = jnp.ones((1, 28, 28))
# Get predictions
logits = predict(restored_params, x_sample)
print("Logits:", logits)
```

## 处理额外的自定义对象

如果你的自定义对象包含不可序列化的属性（例如，文件句柄、线程），请将其从 state dict 中排除。

例如：

```python
class CustomLayer(nn.Module):
    features: int
    non_serializable_attr: any = nn.field(pytree_node=False)
    @nn.compact
    def __call__(self, x):
        # ... as before ...
        pass
```

这告诉 `Flax` 不要在 `PyTree` 遍历中包含该属性，从而避免序列化问题。

## 序列化训练状态

你可能还需要序列化优化器状态和其他训练信息。

```python
# Save the entire training state
checkpoints.save_checkpoint(ckpt_dir, target=state, step=state.step, overwrite=True)
# Restore the training state
restored_state = checkpoints.restore_checkpoint(ckpt_dir, target=state)
```

对于不能轻松表示为 state dict 的对象，请考虑实现 `__getstate__` 和 `__setstate__` 方法。

例如：

```python
class CustomObject:
    def __init__(self, data):
        self.data = data
        self.non_serializable = open('file.txt', 'r')
    def __getstate__(self):
        state = self.__dict__.copy()
        # Remove non-serializable entries
        del state['non_serializable']
        return state
    def __setstate__(self, state):
        self.__dict__.update(state)
        # Re-initialize non-serializable attributes
        self.non_serializable = open('file.txt', 'r')
```

如果必要，你可以使用 `pickle` 来序列化自定义对象，但要注意安全隐患。

```python
import pickle
# Serialize
with open('model.pkl', 'wb') as f:
    pickle.dump(state, f)
# Deserialize
with open('model.pkl', 'rb') as f:
    restored_state = pickle.load(f)
```

如果你创建自己的序列化函数，你可以处理非标准的对象。你还可以设置将自定义对象转换为可序列化格式以及从中恢复的方式。这使得保存和加载模型变得更容易且不会出现任何问题。这种方法使你的模型持久化策略更可靠。



## 摘要
我们深入探讨了多种用于导出和序列化使用 Google `JAX` 开发的模型的方法。本章直面了为部署而保存训练模型的挑战。我们掌握了使用 `Flax` 保存模型架构和参数的技巧。我们成功持久化了模型的状态，并确保其可在生产环境中加载以进行推理。

随后，我们转向对长时间运行的作业进行检查点，以防止因意外中断而导致训练进度丢失。该策略可确保训练能够从最近的检查点恢复，而不会有显著损失，从而增强了长时间训练会话的可靠性。本章还演示了如何将 `JAX` 模型转换为其他框架，特别是使用 `jax2tf` 模块将 `JAX` 函数转换为 `TensorFlow` 操作。通过利用 `TensorFlow` 的 `ONNX` 导出器，我们能够在不支持 `JAX` 的环境中部署 `JAX` 模型，扩大了我们工作的适用范围。

最后，我们解决了 `JAX` 中自定义对象的序列化问题。我们发现自定义层或类默认不可序列化，这极大地阻碍了模型持久化和部署。我们通过创建自定义序列化函数来克服这一问题，这些函数定义了如何提取和恢复这些对象的状态。本章为我们提供了导出、检查点以及与模型互操作所需的必备技术，以及序列化自定义对象。这些技术极大地增强了我们 `JAX` 模型的便携性和鲁棒性。

# 第 6 章：类型提升语义与混合精度
## 概述
在本章中，我们将探讨 Google `JAX` 中数据类型和精度的具体细节，以及它们如何影响内存使用和计算效率。我们首先研究算术运算中类型提升背后的过程。这可能导致数据类型精度无意中增加，进而增加内存消耗。

接下来，我们将研究混合精度训练，这是一种利用高精度和低精度数据类型来加速训练同时保持模型准确性的技术。我们还解决了在复杂函数中出现的常见类型错误，并提供了调试和解决这些问题的有效策略。本章介绍了自定义数据类型的关键用法，可实现对数值精度和性能优化的无与伦比的控制。通过自定义数据类型，您可以精确调整模型的计算特性，使其与特定的硬件或应用需求保持一致。

最后，我们讨论了通过在适当的地方采用较低精度类型来优化内存使用的有效方法，在效率和准确性之间取得理想平衡。在整个章节中，您将看到实践示例和解决方案，这些将使您具备自信地在 `JAX` 中管理数据类型和精度的技能。



# 在算术运算中控制类型提升

当使用 `JAX` 进行机器学习任务时，你可能会在算术运算期间遇到意外的类型提升。例如，使用 `float16` 和 `float32` 等混合数据类型进行计算可能会导致自动提升为更高精度类型或甚至 这会增加内存使用和计算开销，抵消了使用低精度类型的优势。挑战在于显式管理计算中的数据类型以防止不想要的类型提升，确保内存使用保持优化而不牺牲数值精度。

## 控制类型提升的步骤

现在，要控制类型提升，你需要：
- 知道 `JAX` 如何处理不同数据类型之间的运算。
- 使用强制转换函数以确保变量在运算前处于所需的数据类型。
- 采用 `JAX` 的精度控制设置来管理默认行为。
- 在每个步骤检查并强制执行数据类型以防止意外的提升。

## 理解 JAX 的类型提升规则

`JAX` 遵循 `NumPy` 的类型提升规则，该规则决定了对不同类型输入执行运算时的输出类型。

当组合整数和浮点数时，结果会被提升为浮点类型。

- 当在 `float16` 之间执行运算时结果会被提升为
- 在任何运算中包含 `float64` 将使结果提升为

以下是意外的类型提升的快速示例：

```
import jax.numpy as jnp
a = jnp.array([1.0, 2.0], dtype=jnp.float16)
b = jnp.array([3.0, 4.0], dtype=jnp.float32)
c = a + b
print(c.dtype)  # Output: float32
```

这里，将 `float16` 数组加到 `float32` 数组上会得到 `float32` 输出。

## 在运算前显式强制转换数据类型

为防止意外的提升，请确保所有操作数具有相同的所需数据类型，如下所示：

```
a = jnp.array([1.0, 2.0], dtype=jnp.float16)
b = jnp.array([3.0, 4.0], dtype=jnp.float32)
# Cast 'b' to float16 before the operation
b_cast = b.astype(jnp.float16)
c = a + b_cast
print(c.dtype)  # Output: float16
```

现在，通过将 `b` 强制转换，加法运算保留了较低精度。

## 模型参数中的一致数据类型

在此，你必须确保所有模型参数和输入类型一致。

```
# Model weights initialization
key = jax.random.PRNGKey(0)
W1 = jax.random.normal(key, (784, 256), dtype=jnp.float16)
b1 = jnp.zeros((256,), dtype=jnp.float16)
W2 = jax.random.normal(key, (256, 128), dtype=jnp.float16)
b2 = jnp.zeros((128,), dtype=jnp.float16)
params = [W1, b1, W2, b2]
```

## 强制转换输入数据并强制执行数据类型

加载数据时，将其强制转换为所需类型。

```
# Load and preprocess data
train_images = ...  # Load data as NumPy array
train_images = train_images.astype(jnp.float16) / 255.0  # Normalize and cast
```

确保函数不会引入意外的提升。

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    x = x.astype(jnp.float16)  # Ensure input is float16
    z1 = jnp.dot(x, W1) + b1
    a1 = jax.nn.relu(z1)
    z2 = jnp.dot(a1, W2) + b2
    y_pred = jax.nn.softmax(z2)
    return y_pred.astype(jnp.float16)
```

## 使用上下文管理器进行精度控制

`JAX` 还提供了上下文管理器来控制默认数据类型，如下所示：

```
from jax import config
config.update("jax_enable_x64", False)  # Disable float64 globally
```

此设置强制所有计算使用 `float32` 或更低精度，防止意外的提升到

## 在计算期间监控数据类型

现在，你可以插入检查或打印语句来监控数据类型。以下是快速示例：

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    x = x.astype(jnp.float16)
    print("Input dtype:", x.dtype)
    z1 = jnp.dot(x, W1) + b1
    print("z1 dtype:", z1.dtype)
    # Continue with the rest of the computation
```

在执行过程中，你可以使用 `jax.debug` 来强制执行数据类型约束。

```
from jax import debug
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    x = x.astype(jnp.float16)
    debug.assert_equal(x.dtype, jnp.float16, "Input x is not float16")
    z1 = jnp.dot(x, W1) + b1
    debug.assert_equal(z1.dtype, jnp.float16, "z1 is not float16")
    # Continue with the rest of the computation
```

## 使用混合精度训练

请注意，使用 `float16` 等较低精度类型可能会导致数值不稳定或降低模型精度。密切关注模型的表现并进行必要的调整。以下是此限制的快速示例：

```
# Potential underflow or overflow in computations
small_values = jnp.array([1e-8, 1e-9], dtype=jnp.float16)
result = jnp.log(small_values)
print(result)  # May result in -inf or NaN
```

在 `float16` 导致不稳定的情况下，你可能会使用混合精度训练，其中模型的某些部分使用更高精度。

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    x = x.astype(jnp.float16)
    z1 = jnp.dot(x, W1.astype(jnp.float16)) + b1.astype(jnp.float16)
    a1 = jax.nn.relu(z1).astype(jnp.float32)  # Promote to float32
    z2 = jnp.dot(a1, W2.astype(jnp.float32)) + b2.astype(jnp.float32)
    y_pred = jax.nn.softmax(z2)
    return y_pred.astype(jnp.float32)
```

在支持例如 TPU 的硬件上，考虑使用它，因为它提供了比 更宽的动态范围

```
x = x.astype(jnp.bfloat16)
```

如果你遵循这些步骤，你可以轻松管理 `JAX` 计算中的数据类型以避免任何意外的类型提升。这种控制有助于减少内存使用，并可以使计算更高效，尤其是在处理大型模型或数据集时。考虑低精度的利弊很重要。一方面，它可以为你节省内存，但另一方面，它可能会影响数字的稳定性以及模型的准确性。



# 实现混合精度训练

训练深度神经网络可能相当耗时，尤其是在大型模型的情况下。你可能会注意到训练速度很慢，并且希望在不损失太多模型精度的情况下加快速度。加快速度的一个好方法是混合精度训练，它使用 16 位和 32 位浮点类型来使计算更快并使用更少的内存。目标是在 `JAX` 中实现混合精度训练，以加快计算速度，同时保持数值稳定和模型性能良好。

混合精度训练利用较低精度的数据类型（如 `float16` 或 用于大多数计算以加快处理速度并减少内存消耗。需要更高精度的计算的关键部分使用 如果你仔细管理数据类型，你可以在保持模型的准确性与全精度训练一样好的同时获得更快的训练时间。

## 实现损失函数

现在开始，首先加载模型的训练状态，然后实现损失函数。

```
def compute_loss(params, images, labels):
    logits = FashionMNISTModel().apply({'params': params}, images)
    loss = optax.softmax_cross_entropy_with_integer_labels(logits, labels).mean()
    return loss
```

现在，这里，我们需要确保：
梯度以 `float32` 计算以防止下溢。参数在 中更新

```
@jit
def train_step(state, batch):
    images = batch['images']
    labels = batch['labels']
    def loss_fn(params):
        loss = compute_loss(params, images, labels)
        return loss
    grad_fn = value_and_grad(loss_fn)
    loss, grads = grad_fn(state.params)
    # Cast gradients to float32
    grads = jax.tree_map(lambda g: g.astype(jnp.float32), grads)
    # Update state
    state = state.apply_gradients(grads=grads)
    return state, loss
```

接下来，以下是训练循环：

```
rng = jax.random.PRNGKey(0)
state = create_train_state(rng, learning_rate=0.001)
num_epochs = 10
for epoch in range(num_epochs):
    for batch in train_ds:
        state, loss = train_step(state, batch)
    print(f'Epoch {epoch + 1}, Loss: {loss}')
```

然后，实现评估步骤：

```
@jit
def eval_step(params, batch):
    images = batch['images']
    labels = batch['labels']
    logits = FashionMNISTModel().apply({'params': params}, images)
    loss = optax.softmax_cross_entropy_with_integer_labels(logits, labels).mean()
    accuracy = jnp.mean(jnp.argmax(logits, -1) == labels)
    return {'loss': loss, 'accuracy': accuracy}
```

然后，评估模型：

```
def evaluate_model(state, test_ds):
    metrics = []
    for batch in test_ds:
        metrics.append(eval_step(state.params, batch))
    metrics_np = jax.device_get(metrics)
    test_loss = np.mean([m['loss'] for m in metrics_np])
    test_accuracy = np.mean([m['accuracy'] for m in metrics_np])
    print(f"Test Loss: {test_loss}, Test Accuracy: {test_accuracy}")
```

## 监控模型准确率

训练后，将模型的准确率与使用全精度训练的模型进行比较，以确保没有显著损失。参见以下代码片段：

```
# Evaluate mixed precision model
evaluate_model(state, test_ds)
# Compare with full precision model (if available)
# ... (train and evaluate a full precision model)
```

## 在 TPU 上使用 `bfloat16`

如果在 TPU 上训练，则需要将 `float16` 替换为 `bfloat16` 以获得更好的动态范围。

### 修改模型以使用 `bfloat16`

```
class FashionMNISTModel(nn.Module):
    @nn.compact
    def __call__(self, x):
        x = x.astype(jnp.bfloat16)
        # ... rest of the model ...
```

通过使用混合精度训练，你可以将训练时间缩短一半并减少内存使用，而不会损失任何精度。仔细处理数据类型非常重要，并确保你以正确的计算级别进行操作，以获得你想要的结果。



# 在复杂函数中调试类型错误

在 `JAX` 中开发复杂函数时，尤其是涉及多次转换和数据操作时，你可能会遇到意外的类型错误。这些错误可能在执行期间表现为异常，也可能表现为静默失败导致结果不正确。由于 `JAX` 的函数式编程范式和 `JIT` 编译，诊断和修复这些类型相关错误可能具有挑战性。挑战在于系统地识别类型错误的来源并实施解决方案以解决它们，确保你的函数正常运行。

## 现在如何调试复杂 JAX 函数中的类型错误

现在如何调试复杂 `JAX` 函数中的类型错误：
- 熟悉 `JAX` 中典型的类型相关问题。
- 确保变量具有预期的数据类型。
- 使用 `jax.debug` 工具在执行期间检查数据类型。
- 隔离函数部分以确定错误发生的位置。
- 在使用时注意限制和约束

## 识别常见类型错误

`JAX` 中的典型类型错误包括：
- 不兼容类型之间的数据操作不匹配（例如，`int32` 和 `float32`）。
- 非预期的类型隐式提升到更高精度类型。
- 不可变 尝试修改不可变数组。

让我们将以下内容作为错误信息之一考虑：
`TypeError`: Can't multiply sequence by non-int of type 'float'

确保将变量转换为正确的数据类型。

```
def compute_area(length, width):
    length = jnp.asarray(length, dtype=jnp.float32)
    width = jnp.asarray(width, dtype=jnp.float32)
    area = length * width
    return area
```

## 插入调试语句

现在，使用 `jax.debug.print` 在执行期间输出数据类型和形状。

```
from jax import debug
def complex_function(x):
    x = x.astype(jnp.float32)
    debug.print("x dtype: {}", x.dtype)
    # Perform operations
    y = x * 2.0
    debug.print("y dtype: {}", y.dtype)
    return y
```

温馨提示，当你使用 `JIT` 时，确保 `debug.print` 与编译后的函数兼容非常重要。

## 简化函数

将复杂的函数拆分为更简单的部分以发现问题，如下所示：

```
def complex_function(x):
    # Part 1
    x1 = part1(x)
    # Part 2
    x2 = part2(x1)
    # Part 3
    result = part3(x2)
    return result
```

然后，分别测试每个部分。在此过程中，确保操作对所涉及的数据类型有效。

```
def safe_division(a, b):
    a = a.astype(jnp.float32)
    b = b.astype(jnp.float32)
    result = a / b
    return result
```

接下来，确保函数的输入具有正确的类型和形状，如下所示演示。

```
def process_input(data):
    if not isinstance(data, jnp.ndarray):
        data = jnp.array(data)
    if data.dtype != jnp.float32:
        data = data.astype(jnp.float32)
    return data
```

不要忘记包含断言以强制执行数据类型期望。以下是添加断言的快速示例。

```
def compute_sum(a, b):
    assert a.dtype == b.dtype, "Data types of 'a' and 'b' must match"
    return a + b
```

需要记住，`JIT` 编译的函数不能包含某些 Python 构造或副作用。

## 处理 Python 标量类型

你还必须注意 Python 整数和浮点数，它们可能与 `JAX` 类型不匹配。例如：

```
def scale_array(x, scale):
    scale = jnp.asarray(scale, dtype=x.dtype)
    return x * scale
```

## 使用 `jax.numpy` 函数

我建议使用 `jax.numpy` 函数而不是 Python 内置函数，以确保一切兼容，如下所示：

```
def compute_sqrt(x):
    return jnp.sqrt(x)
```

如果你在类型错误方面遇到困难，你可能想查看一些社区论坛或文档。



# 使用自定义数据类型

在某些机器学习应用中，标准数据类型如 `float32` 或 `float64` 可能不足以满足特定精度要求或需要专门的数值行为。例如，你可能需要定点运算、自定义舍入行为，或针对特定硬件优化的表示形式。`JAX` 默认支持标准数值类型，但为了满足项目的特殊需求，你需要在 `JAX` 的框架内实现并使用自定义数据类型。这里的挑战是将这些自定义类型集成到 `JAX` 中，使其能够参与 `JAX` 的转换，同时确保正确且高效的计算。

因此要使用自定义数据类型，你可以通过创建 `jax.lax_dtype` 的子类或使用 `jax.custom_dtype` 机制来定义新的数据类型。需要说明的是：`JAX` 并未设置好用于处理自定义数据类型。作为替代方案，你可以通过使用标准类型表示它们并重载必要的操作来模拟自定义数据类型。另一个选择是使用 `JAX` 对自定义 `JVPs`（雅可比-向量积）和 `VJPs`（向量-雅可比积）的支持，以在自动微分期间为某些用例定义自定义行为。

在本教程中，我们将探讨如何使用 `Custom VJP` 和 `Custom JVP` 函数来实现自定义数据类型，以便为涉及你专门数值类型的函数定义自定义的前向和反向行为。

## 模拟自定义数据类型

首先，我们的方法将使用现有类型来模拟自定义数据类型。例如，你可以使用整数类型表示定点数并相应地定义操作。

假设你想实现具有特定缩放因子的定点运算。

```python
import jax
import jax.numpy as jnp
# Define a fixed-point class
class FixedPoint:
    def __init__(self, value, scale=1000):
        self.value = jnp.asarray(value)
        self.scale = scale
    def to_float(self):
        return self.value / self.scale
    def __add__(self, other):
        return FixedPoint(self.value + other.value, self.scale)
    def __mul__(self, other):
        return FixedPoint((self.value * other.value) // self.scale, self.scale)
    # Add other necessary methods...
# Example usage
a = FixedPoint(1000)  # Represents 1.0
b = FixedPoint(2000)  # Represents 2.0
c = a + b  # Represents 3.0
d = a * b  # Represents 2.0
```

## 使用 JAX 自定义转换

现在，要将自定义操作与 `JAX` 集成，你可以使用 `jax.custom_jvp` 或 `jax.custom_vjp` 装饰器来定义自定义的前向和反向传递。

假设你有一个在自定义数据类型上运行的函数，并且你希望定义它在微分期间的行为。

考虑以下自定义平方函数的示例：

```python
@jax.custom_jvp
def custom_square(x):
    return x ** 2
# Define the custom JVP rule
@custom_square.defjvp
def custom_square_jvp(primals, tangents):
    x, = primals
    x_dot, = tangents
    primal_out = custom_square(x)
    tangent_out = 2 * x * x_dot  # Derivative of x² is 2x
    return primal_out, tangent_out
x = jnp.array(3.0)
y = custom_square(x)
dy_dx = jax.grad(custom_square)(x)
print("y =", y)          # y = 9.0
print("dy/dx =", dy_dx) # dy/dx = 6.0
```

我们还需要确保自定义数据类型可以与 `JAX` 转换一起使用。为此，让我们定义一种可微分的定点数的自定义数据类型。

```python
# Define JVP rules
@add.defjvp
def add_jvp(primals, tangents):
    a, b = primals
    a_dot, b_dot = tangents
    primal_out = FixedPoint.add(a, b)
    tangent_out = a_dot + b_dot
    return primal_out, tangent_out

@multiply.defjvp
def multiply_jvp(primals, tangents):
    a, b = primals
    a_dot, b_dot = tangents
    primal_out = FixedPoint.multiply(a, b)
    tangent_out = (a_dot * b.value + b_dot * a.value) // a.scale
    return primal_out, tangent_out
```

## 使用自定义数据类型

现在，你可以在计算中使用 `FixedPoint` 并应用

```python
def compute(a_value, b_value):
    a = FixedPoint(a_value)
    b = FixedPoint(b_value)
    c = FixedPoint.multiply(a, b)
    return c.value
# Compute gradient with respect to a_value
grad_fn = jax.grad(compute)
gradient = grad_fn(1000.0, 2000.0)  # Inputs are scaled integers
print("Gradient:", gradient)
```

## 使用自定义 PyTree

你也可以将自定义数据类型表示为 `PyTree`，以便 `JAX` 可以遍历它。

```python
from jax import tree_util
def fixedpoint_flatten(fp):
    return (fp.value,), fp.scale
def fixedpoint_unflatten(scale, value):
    return FixedPoint(value[0], scale)
tree_util.register_pytree_node(FixedPoint, fixedpoint_flatten, fixedpoint_unflatten)
```

现在，你可以在 `FixedPoint` 实例上使用 `JAX` 函数

```python
def compute_sum(a_value, b_value):
    a = FixedPoint(a_value)
    b = FixedPoint(b_value)
    c = a.value + b.value
    return c
grad_fn = jax.grad(compute_sum)
gradient = grad_fn(1000.0, 2000.0)
print("Gradient:", gradient)
```

这种方法允许 `JAX` 在转换中处理 `FixedPoint` 实例，但你仍需要确保操作正确定义并且与 `JAX` 的期望兼容。对于高级用例，你可以按如下所示定义自定义原语：

```python
def compute(a_value, b_value, scale=1000):
    a = jnp.asarray(a_value)
    b = jnp.asarray(b_value)
    c = fixed_mul(a, b, scale)
    return c
grad_fn = jax.grad(compute)
gradient = grad_fn(1000.0, 2000.0)
print("Gradient:", gradient)
```

如果你使用 `JAX` 的自定义转换和原语与自定义数据类型，你可以让 `JAX` 为你做更多事情，尤其是在处理特殊数值情况时。这种方法要求你仔细思考如何定义操作并在它们之间进行区分。但它让你将自定义类型集成到 `JAX` 的生态系统中，这意味着你可以使用其自动微分和编译功能。



# 使用低精度类型优化内存

现在，在处理大型模型或数据集时，像 `float64` 这样高精度的数据类型会消耗大量内存，导致资源受限和性能下降。这在训练深度神经网络时尤其成问题，因为此时内存带宽是瓶颈。为了解决这个问题，你希望策略性地使用较低精度的数据类型（如 `float16` 或在可接受的情况下），以减少内存占用并可能提高计算速度。

## 分析模型和数据

所以首先，检查你的模型以识别可以在较低精度下运行的组件：

- Weights and Activations: Often can be in lower precision.
- Gradients: May need higher precision to prevent underflow.
- Loss Computation: Typically requires higher precision.

## 以低精度加载数据

我们需要调整数据加载过程以使用低精度类型。例如：

```
import jax.numpy as jnp
# Load data as float16
train_images = ...  # Load as NumPy array
train_images = train_images.astype(jnp.float16) / 255.0  # Normalize
train_labels = ...  # Labels can remain as integers
```

## 使用低精度参数定义模型

只需调整模型定义以使用 `Flax` 中的低精度数据类型：

```
from flax import linen as nn
class LowPrecisionModel(nn.Module):
  @nn.compact
  def __call__(self, x):
    x = x.astype(jnp.float16)
    x = x.reshape((x.shape[0], -1))
    x = nn.Dense(features=256, dtype=jnp.float16)(x)
    x = nn.relu(x)
    x = nn.Dense(features=128, dtype=jnp.float16)(x)
    x = nn.relu(x)
    x = nn.Dense(features=10, dtype=jnp.float16)(x)
    x = x.astype(jnp.float32)  # Convert to float32 for loss computation
    return x
```

## 调整优化器

这里，使用 `Optax` 来处理低精度参数。

```
import optax
def create_optimizer(learning_rate):
    # Use an optimizer that supports lower precision
    optimizer = optax.adam(learning_rate=learning_rate, b1=0.9, b2=0.999, eps=1e-8)
    return optimizer
```

## 修改训练步骤

接下来，确保梯度以更高精度计算。

```
@jax.jit
def train_step(state, batch):
  images = batch['images']
  labels = batch['labels']
  def loss_fn(params):
    loss = scaled_loss(params, images, labels)
    return loss
  grads = jax.grad(loss_fn)(state.params)
  grads = jax.tree_map(lambda g: g.astype(jnp.float32), grads)  # Cast gradients to float32
  state = state.apply_gradients(grads=grads)
  return state
```

为了确保我们理解一致，这里需要将模型参数初始化为期望的精度。

```
def create_train_state(rng, learning_rate):
  model = LowPrecisionModel()
  params = model.init(rng, jnp.ones([1, 28, 28], dtype=jnp.float16))['params']
  optimizer = create_optimizer(learning_rate)
  state = train_state.TrainState.create(apply_fn=model.apply, params=params, tx=optimizer)
  return state
```

## 训练模型

然后，按通常方式继续训练循环，并随后评估模型性能。

```
rng = jax.random.PRNGKey(0)
state = create_train_state(rng, learning_rate=0.001)
for epoch in range(num_epochs):
    for batch in train_ds:
        state = train_step(state, batch)
    print(f"Epoch {epoch + 1} completed.")
#model performance evaluation
def evaluate_model(state, test_ds):
  total_loss = 0.0
  total_accuracy = 0.0
  for batch in test_ds:
    images = batch['images'].astype(jnp.float16)
    labels = batch['labels']
    logits = LowPrecisionModel().apply({'params': state.params}, images)
    loss = optax.softmax_cross_entropy_with_integer_labels(logits, labels).mean()
    accuracy = jnp.mean(jnp.argmax(logits, -1) == labels)
    total_loss += loss
    total_accuracy += accuracy
  print(f"Test Loss: {total_loss}, Test Accuracy: {total_accuracy}")
evaluate_model(state, test_ds)
```

## 在 TPU 上使用 `bfloat16`

如果你想充分利用 TPU，请使用 `bfloat16`。这样可以在较低精度下获得更好的数值特性。

```
class LowPrecisionModel(nn.Module):
  @nn.compact
  def __call__(self, x):
    x = x.astype(jnp.bfloat16)
    # ... rest of the model ...
```

如果你以智能的方式使用低精度数据类型，可以大幅减少内存使用，甚至可能加快处理速度。重要的是仔细考虑这些更改，以确保模型保持准确和稳定。定期测试和验证很重要，以确保减少内存使用的好处不会以性能下降为代价。

## 总结

我们成功探索了 `JAX` 中的数据类型管理和精度，优化了内存使用和计算效率。我们首先解决了算术运算中意外的类型提升问题。我们知道此类提升可能导致内存消耗增加和计算变慢，并且我们决心找到解决方案。通过显式管理数据类型并使用一致的类型转换，我们学会了防止自动提升并保持对数值精度的控制。

我们发现实现混合精度训练是加速计算的非常有效技术。我们通过对大多数操作使用 `float16` 等低精度类型，并为关键计算保留 `float32`，在没有显著损失精度的情况下实现了更快的训练时间。我们还成功解决了复杂函数中调试类型错误的挑战。通过系统诊断、显式转换类型并利用 `JAX` 的调试工具，我们能够识别和解决可能导致函数意外失败的数据类型问题。这证明了在整个代码开发过程中细致关注数据类型的必要性。

本章随后转向在 `JAX` 框架内实现自定义数据类型，承认了需要专用数值类型的场景。我们通过利用自定义 `VJP` 和 `JVP` 函数，将自定义数据类型集成到 `JAX` 的自动微分系统中。最后，我们通过在适当的地方采用低精度类型来优化内存使用。我们通过调整数据加载、模型定义和计算精度，有效减少了模型的内存占用。

# 第 7 章：集成外部函数（FFI）



# 概述

在本章中，我们将直接深入探讨如何在 `JAX` 中集成外部函数（FFI），为您提供两全其美的体验：在机器学习模型中实现增强的功能和性能，全部打包在一个整洁的方案中。我们首先展示如何直接从 `JAX` 调用外部 C 库。这使您能够使用针对 `JAX` 标准库中没有的特定计算而优化的现有代码。

接下来，我们将展示如何使用自定义 CUDA 内核来优化性能。标准操作在 GPU 计算方面远远不够。这就是为什么编写自定义 CUDA 内核至关重要。我们将展示如何通过 FFI 创建和集成这些内核，以在 GPU 硬件上获得最佳性能。我们还将直接解决 `JAX` 与外部代码之间的数据转换问题。此外，我们还将展示如何管理线程安全和并发性，这在使用默认情况下可能不是线程安全的外部库时至关重要。

最后，我们将展示如何跨异构系统分发计算。您可以通过利用 `JAX` 的功能以及外部函数，有效地在不同硬件资源之间优化计算。

## 调用外部 C 库

在您使用 `JAX` 构建机器学习模型时，您可能会发现需要使用现有的 C 库来执行 `JAX` 中不可用或效率不高的特定计算。这些库可能包含一些相当专业的算法、遗留代码或经过高度优化的函数，可以真正提升模型的性能。棘手的部分是确保 `JAX` 和 C 代码能很好地协同工作。我们需要确保 `JAX` 的 JIT 编译和自动微分能与 C 代码配合使用，但同时也需要确保其高效。

`JAX` 提供了通过其外部函数接口（FFI）调用外部 C 函数的方法。您可以在 Python 中使用 `ctypes` 或 `cffi` 来包装 C 函数，使其在 `JAX` 计算中可访问。您还可以创建自己的 `JAX` 原语来连接这些 C 函数。这使您可以将它们添加到 `JAX` 的计算图中，并且还允许 JIT 编译和微分。

### 准备 C 库

假设您有一个计算数组逐元素指数的 C 函数。

```c
// custom_math.c
#include <math.h>
void custom_exp(int n, const double* x, double* y) {
    for (int i = 0; i < n; ++i) {
        y[i] = exp(x[i]);
    }
}
```

接下来，编译 C 代码以在 Linux 上创建共享库文件：

```bash
gcc -shared -fPIC -o libcustom_math.so custom_math.c
```

接下来，使用以下方式在 Python 中加载 C 库

```python
import ctypes
import numpy as np
# Load the shared library
lib = ctypes.CDLL('./libcustom_math.so')
# Define the argument and return types of the function
lib.custom_exp.argtypes = [
    ctypes.c_int,
    np.ctypeslib.ndpointer(dtype=np.float64, ndim=1, flags='C_CONTIGUOUS'),
    np.ctypeslib.ndpointer(dtype=np.float64, ndim=1, flags='C_CONTIGUOUS')
]
lib.custom_exp.restype = None
```

## 在 Python 中定义包装函数

我们需要创建一个包装 C 函数的 Python 函数。

```python
def custom_exp_c(x):
    x_np = np.ascontiguousarray(x, dtype=np.float64)
    y_np = np.empty_like(x_np)
    n = x_np.size
    lib.custom_exp(n, x_np, y_np)
    return y_np
```

### 使用 `jax.experimental.callback` 与 JAX 集成

由于 `JAX` 本身不支持在 JIT 编译的代码中调用任意 Python 函数，您可以使用 `jax.experimental.callback`（在 `JAX` 版本 `>= 0.2.12` 中可用）。

```python
import jax
from jax.experimental import callback as jec

@jax.custom_vjp
def custom_exp(x):
    def forward(x):
        y = jec.call(custom_exp_c, x, output_shape=x.shape)
        return y
    def backward(res, g):
        return (g * custom_exp(x),)
    return forward(x), backward
```

定义前向和后向传递

```python
def custom_exp_fwd(x):
    y = jec.call(custom_exp_c, x, output_shape=x.shape)
    return y, y  # Return y as residual for backward

def custom_exp_bwd(res, g):
    y = res
    return (g * y,)  # Derivative of exp(x) is exp(x)

custom_exp.defvjp(custom_exp_fwd, custom_exp_bwd)
```

接下来，测试自定义函数：

```python
import jax.numpy as jnp
# Sample input
x = jnp.array([0.0, 1.0, 2.0], dtype=jnp.float64)
# Call the custom_exp function
y = custom_exp(x)
print("y =", y)
# Compute the gradient
grad_fn = jax.grad(lambda x: jnp.sum(custom_exp(x)))
grad_value = grad_fn(x)
print("grad_value =", grad_value)
```

接下来，使用 JIT 编译使用该函数：

```python
@jax.jit
def compute_custom_exp(x):
    return custom_exp(x)

y_jit = compute_custom_exp(x)
print("y_jit =", y_jit)
```

这里，使用 `jax.experimental.callback` 可能由于设备和主机之间的数据传输而引入性能开销。外部函数在 CPU 上执行，如果其余计算在 GPU 上，则可能不是最优的。

## 处理数据类型和形状

只需确保 `JAX` 与 C 函数之间的数据类型和形状兼容。只需使用 `np.ascontiguousarray` 确保内存是连续的。确保您匹配数据类型（例如，`JAX` 和 C 中均为 `np.float64`）。

接下来，您现在可以使用

```python
def model(x):
    return custom_exp(x) + x

# Compute gradient
grad_model = jax.grad(lambda x: jnp.sum(model(x)))
grad_value = grad_model(x)
print("Model grad_value =", grad_value)
```

您可以使用 `JAX` 的 FFI 功能和 `jax.experimental.callback` 将外部 C 库集成到 `JAX` 计算中。这种方法让您可以在模型中使用优化的 C 代码，从而扩展功能并可能提高性能。在 GPU 上的效果存在一些限制，并且可能存在一些开销，但这是一种相当不错的方式来连接 C 代码与 `JAX`。



# 使用自定义 CUDA 内核进行性能优化

在涉及使用 GPU 的高性能计算任务时，`JAX` 提供的标准操作对于特定计算可能没有你需要的效率。你可能需要创建自己的算法或调整某些操作，以获得比 `JAX` 库更好的结果。编写自己的 `CUDA` 内核可以让你调整计算以获得 GPU 上的最佳性能。棘手的部分是如何将这些自定义内核与 `JAX` 集成。我们需要确保它们能与 `JAX` 的 `JIT` 编译和自动微分无缝协作。

## 概述

`JAX` 允许你使用 `XLA` 中的自定义调用集成自定义 `CUDA` 内核。如果你定义一个自定义 `JAX` 原语并提供 GPU 特定的转换，你可以编写自定义 `CUDA` 内核、编译它并将其注册到 `JAX` 的后端。这种集成让你可以在 `JAX` 计算中使用自定义内核，兼得两者之长——自定义内核的性能和 `JAX` 的特性。

## 编写自定义 CUDA 内核

首先，你需要为想要优化的操作创建一个 `CUDA` 内核。例如，你可以实现一个自定义逐元素乘法。

### CUDA 内核实现

```cuda
// custom_mul.cu
extern "C" __global__ void custom_mul_kernel(const float* x, const float* y, float* out, int n) {
    int idx = blockIdx.x * blockDim.x + threadIdx.x;
    if (idx < n) {
        out[idx] = x[idx] * y[idx];
    }
}
```

### 将 CUDA 内核编译为 PTX

接下来，你需要编译 `CUDA` 内核以生成 PTX 代码，然后可以用 `JAX` 加载它。

```bash
nvcc --ptx custom_mul.cu -o custom_mul.ptx
```

### 在 Python 中加载 PTX 代码

只需将 PTX 代码读入 Python 以进行注册。

```python
with open('custom_mul.ptx', 'r') as f:
    ptx_code = f.read()
```

### 定义自定义 JAX 原语

我们需要为乘法操作创建一个自定义原语。

```python
from jax import core
from jax.interpreters import xla

custom_mul_p = core.Primitive('custom_mul')

def custom_mul_abstract(x, y):
    return core.ShapedArray(x.shape, x.dtype)

custom_mul_p.def_abstract_eval(custom_mul_abstract)
```

你可以定义原语在 CPU 上运行时 的行为。

```python
def custom_mul_impl(x, y):
    return x * y

custom_mul_p.def_impl(custom_mul_impl)
```

### 注册自定义调用目标

接下来，将自定义 `CUDA` 内核注册到 `XLA`。

```python
from jax.lib import xla_client

def register_custom_call():
    xla_client.register_custom_call_target(
        b'custom_mul_kernel',
        ptx_code.encode('utf-8'),
        platform='CUDA',
    )

register_custom_call()
```

### 定义 GPU 转换

接下来，请为自定义原语提供 GPU 转换。

```python
def custom_mul_xla_translation_gpu(c, x, y):
    shape = c.get_shape(x)
    dtype = shape.element_type()
    n = shape.dimensions()[0]
    out_shape = xla_client.Shape.array_shape(dtype, [n])
    n_const = xla_client.ops.Constant(c, np.array(n, dtype=np.int32))
    return xla_client.ops.CustomCall(
        c,
        b'custom_mul_kernel',
        operands=(x, y, n_const),
        shape=out_shape
    )

xla.backend_specific_translations['gpu'][custom_mul_p] = custom_mul_xla_translation_gpu
```

### 定义前向函数和 JVP 规则

我们需要使用自定义原语编写一个函数。

```python
def custom_mul(x, y):
    return custom_mul_p.bind(x, y)
```

只需提供雅可比-向量积规则以便进行自动微分。

```python
from jax.interpreters import ad

def custom_mul_jvp(primals, tangents):
    x, y = primals
    x_dot, y_dot = tangents
    primal_out = custom_mul(x, y)
    tangent_out = x_dot * y + x * y_dot
    return primal_out, tangent_out

ad.defjvp(custom_mul_p, custom_mul_jvp)
```

### 验证 GPU 执行

接下来，确保计算在 GPU 上执行。

```python
from jax.lib import xla_bridge

backend = xla_bridge.get_backend()
assert backend.platform == 'gpu', "Not running on GPU"

# Move data to GPU explicitly
x_gpu = jax.device_put(x)
y_gpu = jax.device_put(y)
result_gpu = compute_custom_mul(x_gpu, y_gpu)
print("Result on GPU:", result_gpu)
```

## 优化 CUDA 内核

让你的内核为你更好地工作：
选择合适的块和网格大小很重要。如果有帮助，使用共享内存。最好最小化内存访问并优化内存模式。

以下是带有内核启动参数的快速示例：

```python
def custom_mul_xla_translation_gpu(c, x, y):
    # Previous code...
    # Define launch dimensions
    launch_dims = xla_client.ops.Constant(c, np.array([n], dtype=np.int32))
    # Pass launch dimensions in backend_config
    backend_config = xla_client._xla_ops.BuildGpuLaunchConfig(launch_dims)
    return xla_client.ops.CustomCall(
        c,
        b'custom_mul_kernel',
        operands=(x, y, n_const),
        shape=out_shape,
        backend_config=backend_config
    )
```

如果你定义自己的原语并提供 GPU 特定的转换，你就可以利用自定义内核的强大功能，同时获得 `JAX` 自动微分和 `JIT` 编译的好处。这种方法需要正确执行，并且你需要了解 `CUDA` 编程和 `JAX` 内部机制，但它可以为专用操作带来巨大的性能提升。



# 在 JAX 与外部代码之间处理数据转换

当你将 JAX 与外部代码或外部函数集成时，经常会遇到数据格式不匹配的情况。这些不匹配可能是因为 JAX 数组的数据类型、内存布局或维度与外部库的期望不符。这些差异会导致问题，例如错误、计算不正确或数据处理缓慢。棘手的部分是创建可靠的数据转换例程，确保 JAX 和外部代码能够良好协作，保持数据安全，并确保整个集成过程高效。

为了使 JAX 与外部代码之间的数据转换工作良好，你需要建立一些系统化的数据转换例程来处理数据类型、内存布局和数组维度上的差异。

主要步骤如下：
-   了解 JAX 和外部代码双方期望的数据类型和结构。
-   将数据类型转换为目标环境的要求。
-   调整内存布局 e.g., C-contiguous vs. Fortran-contiguous 以满足外部库的期望。
-   根据需要修改数组形状或维度，以与外部函数接口保持一致。
-   创建可复用的函数或工具，以在代码库的不同部分简化转换过程。

如果你花时间把这些事情做好，就可以在 JAX 和外部代码之间建立稳固的连接，使数据共享更轻松高效。

## 了解数据格式

现在，在实现数据转换例程之前，理解 JAX 和外部代码使用的数据格式至关重要。例如，JAX 主要使用 `jax.numpy` 数组，其与 NumPy 数组类似，而外部库可能期望原始 C 数组、特定的内存对齐或不同的数据类型。

假设你有一个 JAX 数组需要传递给 C 库函数，该函数期望一个由 `float32` 值组成的 C 风格连续数组。弄清楚外部代码到底在寻找什么数据类型。如果你没有匹配数据类型，可能会得到错误的结果或在代码运行时遇到问题。

这种情况可能是外部 C 函数期望数据为 `float32` 格式，而你的 JAX 数组可能是 `float64` 格式。

## 实现显式类型转换

只需使用 JAX 的类型转换函数，你就能将数据转换为所需类型。JAX 提供了像 `astype()` 这样的函数，让这个过程变得轻松。

```python
import jax.numpy as jnp
# Original JAX array in float64
jax_array = jnp.array([1.0, 2.0, 3.0], dtype=jnp.float64)
# Convert to float32
jax_array_float32 = jax_array.astype(jnp.float32)
```

## 确保内存布局兼容性

有时，外部库需要在内存中以特定方式布局数据，例如 C-contiguous 行优先或 Fortran-contiguous 列优先。JAX 数组通常是 C-contiguous，但最好检查并确保布局正确。

如果外部库期望 C-contiguous 数组，则确保 JAX 数组满足此要求。

```python
# Ensure the array is C-contiguous
if not jax_array_float32.flags['C_CONTIGUOUS']:
    jax_array_float32 = jnp.ascontiguousarray(jax_array_float32)
```

## 处理数组维度

接下来，确保数组的维度与外部函数的期望一致。这可能涉及重塑或扩展维度。

如果 C 函数期望 1D 数组而你的 JAX 数组是 2D，则相应地重塑它。

```python
# Original JAX array shape: (3, 1)
jax_array_2d = jnp.array([[1.0], [2.0], [3.0]], dtype=jnp.float32)
# Reshape to 1D array
jax_array_1d = jax_array_2d.reshape(-1)
```

## 将 JAX 数组转换为 NumPy 以供外部库使用

NumPy 的好处是大多数外部 C 库都能很好地与其配合使用。在将 JAX 数组传递给外部函数之前，你需要将其转换为 NumPy 数组。

```python
# Convert JAX array to NumPy array
numpy_array = jax_array_float32.device_buffer.to_py()
```

另外，我们可以使用 `np.asarray` 创建 NumPy 视图：

```python
import numpy as np
# Create a NumPy view without copying
numpy_array = np.asarray(jax_array_float32)
```

## 实现数据转换函数

让我们设计一些可复用的函数来简化转换过程。这将使事情更一致，减少大量重复。

```python
def jax_to_c_array(jax_array, dtype=jnp.float32, ndim=1):
    """
    Converts a JAX array to a C-compatible NumPy array.
    Parameters:
    - jax_array: jax.numpy array
    - dtype: desired data type (default: float32)
    - ndim: desired number of dimensions (default: 1)
    Returns:
    - NumPy array with specified dtype and dimensions
    """
    # Cast to desired dtype
    array_cast = jax_array.astype(dtype)
    # Ensure C-contiguous
    if not array_cast.flags['C_CONTIGUOUS']:
        array_cast = jnp.ascontiguousarray(array_cast)
    # Reshape if necessary
    if array_cast.ndim != ndim:
        array_cast = array_cast.reshape((-1,) if ndim == 1 else array_cast.shape)
    # Convert to NumPy
    numpy_array = np.asarray(array_cast)
    return numpy_array
```

## 使用 `ctypes` 与外部 C 函数集成

你可以使用 Python 的 `ctypes` 库来连接这些外部 C 函数。只需将转换后的 NumPy 数组作为指针传递。例如，假设你有以下编译为共享库的 C 函数

```c
// custom_math.c
#include <math.h>
void custom_exp(int n, const float* x, float* y) {
    for (int i = 0; i < n; ++i) {
        y[i] = expf(x[i]);
    }
}
```

接下来，加载共享库并定义参数类型。

```python
import ctypes
# Load the shared library
lib = ctypes.CDLL('./libcustom_math.so')
# Define the argument and return types
lib.custom_exp.argtypes = [
    ctypes.c_int,
    ctypes.POINTER(ctypes.c_float),
    ctypes.POINTER(ctypes.c_float)
]
lib.custom_exp.restype = None
```

然后，创建一个包装 C 函数的 Python 函数，在内部处理数据转换。

```python
def custom_exp_jax(x):
    """
    Applies the custom C exponential function to a JAX array.
    Parameters:
    - x: jax.numpy array
    Returns:
    - y: jax.numpy array after applying exp
    """
    # Convert JAX array to C-compatible NumPy array
    x_c = jax_to_c_array(x, dtype=jnp.float32, ndim=1)
    n = x_c.size
    # Prepare output array
    y_c = np.empty_like(x_c)
    # Get pointers to the data
    x_ptr = x_c.ctypes.data_as(ctypes.POINTER(ctypes.c_float))
    y_ptr = y_c.ctypes.data_as(ctypes.POINTER(ctypes.c_float))
    # Call the C function
    lib.custom_exp(n, x_ptr, y_ptr)
    # Convert the result back to JAX array
    y_jax = jnp.array(y_c)
    return y_jax
```

## 与 JAX 的 JIT 编译集成

为了保持 JAX 的性能优势，特别是 JIT 编译，你可以适当地包装外部函数。然而，JAX 的 JIT 无法编译涉及 ctypes 调用的 Python 函数。为此，你可以使用 `jax.custom_jvp` 或 though 这些方法有局限性。

```python
from jax.experimental import callback as jec
@jax.custom_vjp
def custom_exp(x):
    return custom_exp_jax(x)
# Define the forward and backward passes
def custom_exp_fwd(x):
    y = custom_exp_jax(x)
    return y, y  # Return y as residual for backward
def custom_exp_bwd(res, g):
    # The derivative of exp is exp, so gradient is g * y
    y, = res
    return (g * y,)
custom_exp.defvjp(custom_exp_fwd, custom_exp_bwd)
```

## 优化数据转换性能

数据转换可能会增加一些额外步骤，尤其是在处理大型数据集时。为此，请考虑尝试以下策略：
-   在可能的情况下使用视图或原地操作，以避免不必要的数据复制。例如，使用 `np.asarray` 创建视图而不复制。

```python
numpy_array = np.asarray(jax_array_float32)
```
-   分批转换数据以利用向量化操作并减少每个元素的处理开销。
-   对于 JAX 与外部代码之间频繁的数据传输，固定内存以加速数据移动。

以下是使用 NumPy 的快速示例

```python
# Create a memory-mapped file
mmap_file = np.memmap('data.dat', dtype='float32', mode='w+', shape=(1000,))
# Use memmap for data exchange
mmap_file[:] = jax_array_float32
```

转换后，确保数据保持准确和一致。

一旦你了解数据格式的来龙去脉、显式类型转换的工作方式以及如何自动化转换例程，就可以在 JAX 和外部库之间创建坚如磐石的接口。同样重要的是确保数据有效并正确管理多维数组以实现准确计算。



# 管理线程安全与并发

当将 `JAX` 与外部函数或外部代码集成时，尤其是在多线程环境中，可能会出现诸如 `race conditions`、`deadlocks` 和 `data corruption` 等并发问题。未考虑线程安全的外部库在并发访问时可能会无意中导致这些问题。管理线程安全并确保适当的并发控制对于维护计算的完整性和可靠性至关重要。挑战在于实施策略以防止并发访问问题，同时允许高效的并行执行，尤其是在利用 `JAX`’s 并行功能与外部代码一起使用时。

## 最佳实践和策略

在使用 `FFI` 与 `JAX` 时管理线程安全和并发，您可以采用以下几种最佳实践和策略：

熟悉 `JAX` 和外部库如何处理线程。
优先选择设计为线程安全或提供确保安全并发访问机制的库。
使用线程锁例如 `mutexes` 来序列化对非线程安全外部函数的访问。
在使用 `JAX`’s 并行化功能时，确保这些映射中的外部函数调用是线程安全的。
减少线程之间对共享可变状态的依赖以防止 `race conditions`。
在并发访问下严格测试集成系统以识别和解决潜在问题。

如果您使用这些策略，您可以轻松管理线程安全和并发。这意味着您的 `JAX` 模型将能够在多线程环境中很好地与外部函数协同工作。

## 评估和选择外部库的线程安全

假设您正在集成一个用于图像处理的外部 C 库。查看库的文档，看看其函数是否可以安全地从多个线程同时调用。查看库文档或源代码，了解其关于并发的说明。

最好选择已经是线程安全的外部库，或能够确保其线程安全的库。事实上，许多现代库在设计时就考虑了线程安全，提供线程安全的 API 或内部同步。

## 实现同步机制

如果您使用的是非线程安全的外部库，您需要实现某种同步机制来序列化访问并防止并发执行问题。

```python
import threading
import ctypes
import jax.numpy as jnp
# Load the external C library
lib = ctypes.CDLL('./libcustom_math.so')
# Define the function signature
lib.custom_exp.argtypes = [
    ctypes.c_int,
    ctypes.POINTER(ctypes.c_float),
    ctypes.POINTER(ctypes.c_float)
]
lib.custom_exp.restype = None
# Initialize a lock
custom_exp_lock = threading.Lock()
def custom_exp_thread_safe(x):
    with custom_exp_lock:
        # Convert JAX array to NumPy array
        x_np = jax_to_c_array(x, dtype=jnp.float32, ndim=1)
        n = x_np.size
        y_np = jnp.empty_like(x_np)
        # Get pointers
        x_ptr = x_np.ctypes.data_as(ctypes.POINTER(ctypes.c_float))
        y_ptr = y_np.ctypes.data_as(ctypes.POINTER(ctypes.c_float))
        # Call the external C function
        lib.custom_exp(n, x_ptr, y_ptr)
        # Convert back to JAX array
        y_jax = jnp.array(y_np)
    return y_jax
```

## 使用线程安全接口包装外部函数

接下来，组装包装函数来处理同步，确保外部函数调用保持顺序。

以下是使用装饰器的示例：

```python
from functools import wraps
def thread_safe(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        with custom_exp_lock:
            return func(*args, **kwargs)
    return wrapper
@thread_safe
def custom_exp_safe(x):
    # Conversion and external call
    x_np = jax_to_c_array(x, dtype=jnp.float32, ndim=1)
    n = x_np.size
    y_np = jnp.empty_like(x_np)
    x_ptr = x_np.ctypes.data_as(ctypes.POINTER(ctypes.c_float))
    y_ptr = y_np.ctypes.data_as(ctypes.POINTER(ctypes.c_float))
    lib.custom_exp(n, x_ptr, y_ptr)
    y_jax = jnp.array(y_np)
    return y_jax
```

## 与 JAX 的 JIT 编译集成

如果您使用 `JIT` 编译，重要的是确保线程安全得到维护。由于代码是并行运行的，您应避免在编译代码内部放置锁。相反，应在 `JIT` 函数外部处理同步。

```python
@jax.jit
def jitted_custom_exp(x):
    # JIT-compiled function should not contain locks
    return custom_exp_safe(x)  # Ensure custom_exp_safe handles locking
```

在使用并行映射函数时，确保映射函数中的外部函数调用是线程安全的或已适当同步。

```python
# Define a parallel mapped function
parallel_custom_exp = jax.pmap(custom_exp_safe)
# Sample input batch
x_batch = jnp.array([
    [1.0, 2.0, 3.0],
    [4.0, 5.0, 6.0],
    [7.0, 8.0, 9.0],
    [10.0, 11.0, 12.0]
], dtype=jnp.float32)
# Apply the parallel custom exponential
y_batch = parallel_custom_exp(x_batch)
print("y_batch =", y_batch)
```

## 最小化共享状态

最好避免在不同线程之间使用相同的共享数据。这有助于防止 `race conditions` 和 `data corruption`。在可能的情况下，确保每个线程都使用自己的数据。

```python
def custom_exp_isolated(x):
    # No shared state modification
    return custom_exp_safe(x)
```

为了高效管理多个线程，使用 Python 的 `concurrent.futures` 模块提供的线程池或执行器。这可以更好地控制线程生命周期和资源管理。

```python
from concurrent.futures import ThreadPoolExecutor
# Initialize a thread pool
executor = ThreadPoolExecutor(max_workers=4)
# Define a function to submit tasks
def submit_custom_exp_tasks(inputs):
    futures = [executor.submit(custom_exp_safe, x) for x in inputs]
    results = [future.result() for future in futures]
    return jnp.stack(results)
# Sample inputs
inputs = [jnp.array([1.0, 2.0, 3.0], dtype=jnp.float32),
          jnp.array([4.0, 5.0, 6.0], dtype=jnp.float32),
          jnp.array([7.0, 8.0, 9.0], dtype=jnp.float32),
          jnp.array([10.0, 11.0, 12.0], dtype=jnp.float32)]
# Submit tasks and get results
y_results = submit_custom_exp_tasks(inputs)
print("y_results =", y_results)
```

## 使用异步编程实现非阻塞调用

对于 I/O 密集型外部函数，尝试考虑使用异步编程以防止阻塞主线程，从而提高整体性能。

以下是快速示例，使用

```python
import asyncio
async def async_custom_exp(x):
    return custom_exp_safe(x)
async def main_async():
    inputs = [jnp.array([1.0, 2.0, 3.0], dtype=jnp.float32),
              jnp.array([4.0, 5.0, 6.0], dtype=jnp.float32)]
    tasks = [async_custom_exp(x) for x in inputs]
    results = await asyncio.gather(*tasks)
    return jnp.stack(results)
# Run the asynchronous main function
y_async = asyncio.run(main_async())
print("y_async =", y_async)
```

## 实现读写锁以实现精细控制

如果某些外部函数允许并发读取但写入需要独占访问，请实现读写锁以优化并发。

```python
class ReadWriteLock:
    def __init__(self):
        self.lock = threading.RLock()
        self.readers = 0
    def acquire_read(self):
        with self.lock:
            self.readers += 1
    def release_read(self):
        with self.lock:
            self.readers -= 1
    def acquire_write(self):
        self.lock.acquire()
        while self.readers > 0:
            pass  # Busy wait or implement condition variables
    def release_write(self):
        self.lock.release()
# Initialize the read-write lock
rw_lock = ReadWriteLock()
def custom_exp_rw(x):
    rw_lock.acquire_write()
    try:
        return custom_exp_safe(x)
    finally:
        rw_lock.release_write()
```

在将 `JAX` 与外部函数集成时，认真考虑线程安全和并发非常重要。这有助于确保一切平稳高效地运行。如果您了解 `JAX`'s 线程模型，评估外部库的线程安全，实现适当的同步机制，并以正确的方式将 `JAX` 的并行执行功能集成起来，您就可以避免诸如 `race conditions` 和 `deadlocks` 之类的并发问题。此外，如果您将共享状态保持在最小限度，使用线程池，并在合适时进行异步编程，您可以在不损失安全性的情况下获得更好的性能。



# 在异构系统间分发计算

在高级机器学习项目中，通常需要利用专用硬件，例如 `FPGAs`（现场可编程门阵列）或 `ASICs`（应用特定集成电路）来比通用 `GPUs` 或 `CPUs` 更高效地执行特定计算。这些专用设备可以为其优化的任务提供显著的加速和能源效率。然而，将这些异构系统与 `JAX` 集成会带来挑战，包括管理数据传输、确保兼容性以及在不同硬件平台之间编排计算。挑战在于有效利用 `JAX` 的 `FFI` 能力将计算卸载到这些专用设备上，从而在不影响易用性或灵活性的前提下提升整体系统性能。

## 结构化方法

现在，要使用 `JAX` 的 `FFI` 在异构系统间分发计算，我们可以遵循一种结构化方法：
确定模型或计算中哪些部分最能从专用硬件加速中受益。
使用或创建允许 `JAX` 与专用硬件之间通信的接口，通常通过自定义 API 或驱动程序。
高效管理 `JAX`（通常运行在 `CPUs` 或 `GPUs` 上）与专用设备之间的数据传输。
使用 `FFI` 工具如或 `JAX` 的自定义原语来调用在专用硬件上运行的函数。
管理不同硬件操作之间的同步，并确保数据类型和内存布局兼容。
微调数据传输和计算过程以最小化延迟并最大化吞吐量。

如果我们密切关注每一步，就能构建一个稳固的系统，让 `JAX` 可以将某些计算卸载到专用硬件上。这让我们能够利用其独特功能来改善整体性能。

## 识别计算密集型任务

因此，首先通过分析你的 `JAX` 模型来识别瓶颈或计算密集且可从硬件加速中受益的操作。常见候选包括矩阵乘法、卷积或涉及大规模数据处理的自定义操作。

例如，假设模型中的自定义激活函数或大型矩阵乘法被识别为性能瓶颈。

## 选择合适的专用硬件

选择最适合已识别任务的专用硬件。例如：
- `FPGAs` 高度可配置，在低延迟的并行处理任务中表现出色。
- `ASICs` 为特定应用提供优化性能，具有高效率。

如果为所选硬件提供现有的接口或库，请利用它们。否则，你可能需要开发自定义驱动程序或 API 来与硬件通信。对于 `FPGA`，你可能会使用 `OpenCL` 或厂商特定的 SDK 来编程和与设备通信。

## 实现数据传输机制

`JAX` 与专用硬件之间高效的数据传输至关重要。这涉及将 `JAX` 数组转换为硬件期望的格式并管理内存布局。查看下面使用 `ctypes` 的示例：

```python
import ctypes
import numpy as np
import jax.numpy as jnp
# Load the shared library for FPGA operations
fpga_lib = ctypes.CDLL('./libfpga_ops.so')
# Define the function signature
fpga_lib.custom_matmul.argtypes = [
    ctypes.c_int,
    ctypes.POINTER(ctypes.c_float),
    ctypes.POINTER(ctypes.c_float),
    ctypes.POINTER(ctypes.c_float)
]
fpga_lib.custom_matmul.restype = None
def custom_matmul_fpga(a, b):
    # Ensure input arrays are float32 and C-contiguous
    a_np = np.ascontiguousarray(np.asarray(a, dtype=np.float32))
    b_np = np.ascontiguousarray(np.asarray(b, dtype=np.float32))
    n = a_np.shape[0]
    m = b_np.shape[1]
    k = a_np.shape[1]
    # Prepare output array
    c_np = np.empty((n, m), dtype=np.float32)
    # Get pointers to the data
    a_ptr = a_np.ctypes.data_as(ctypes.POINTER(ctypes.c_float))
    b_ptr = b_np.ctypes.data_as(ctypes.POINTER(ctypes.c_float))
    c_ptr = c_np.ctypes.data_as(ctypes.POINTER(ctypes.c_float))
    # Call the FPGA function
    fpga_lib.custom_matmul(n, a_ptr, b_ptr, c_ptr)
    # Convert back to JAX array
    return jnp.array(c_np)
```

## 使用自定义原语与 JAX 集成

为了让一切顺畅地协同工作，将 `custom_matmul_fpga` 函数包装为自定义 `JAX` 原语。这样，你可以保持与 `JAX` 的 JIT 编译和自动微分的兼容性。

```python
from jax import core
from jax.interpreters import xla
# Define the primitive
custom_matmul_p = core.Primitive('custom_matmul_fpga')
# Define the abstract evaluation
def custom_matmul_abstract(x, y):
    return core.ShapedArray((x.shape[0], y.shape[1]), x.dtype)
custom_matmul_p.def_abstract_eval(custom_matmul_abstract)
# Define the implementation
def custom_matmul_impl(x, y):
    return custom_matmul_fpga(x, y)
custom_matmul_p.def_impl(custom_matmul_impl)
# Define the XLA translation for CPU (optional)
def custom_matmul_cpu_translation(c, x, y):
    # Implement CPU fallback or raise NotImplementedError
    raise NotImplementedError("custom_matmul_fpga is only implemented for FPGA.")
xla.backend_specific_translations['cpu'][custom_matmul_p] = custom_matmul_cpu_translation
# Define the JVP rule for differentiation
from jax.interpreters import ad
def custom_matmul_jvp(primals, tangents):
    x, y = primals
    x_dot, y_dot = tangents
    primal_out = custom_matmul_p.bind(x, y)
    tangent_out = jnp.dot(x_dot, y) + jnp.dot(x, y_dot)
    return primal_out, tangent_out
ad.defjvp(custom_matmul_p, custom_matmul_jvp)
```

## 定义用户友好的函数

让我们创建一个高级函数，用户可以在其 `JAX` 代码中轻松调用。

```python
def custom_matmul(x, y):
    return custom_matmul_p.bind(x, y)
```

现在，确保自定义原语在 `JAX` 计算中能正确工作。

```python
import jax.numpy as jnp
# Sample inputs
a = jnp.array([[1.0, 2.0], [3.0, 4.0]], dtype=jnp.float32)
b = jnp.array([[5.0, 6.0], [7.0, 8.0]], dtype=jnp.float32)
# Perform matrix multiplication using FPGA
c = custom_matmul(a, b)
print("Result from FPGA:", c)
# Compute gradients
grad_fn = jax.grad(lambda a, b: jnp.sum(custom_matmul(a, b)))
grad_a, grad_b = grad_fn(a, b)
print("Gradients:", grad_a, grad_b)
```

通过批处理操作或在可能时重用内存缓冲区来减少数据传输开销。例如，如果执行多次矩阵乘法，请重用已分配的内存以避免重复分配和传输。

```python
def batched_custom_matmul(batch_a, batch_b):
    # Assuming batch_a and batch_b are batched arrays
    return jax.vmap(custom_matmul)(batch_a, batch_b)
```

## 处理专用数据类型

如果专用硬件需要独特的数据类型，请在数据传输例程中实现必要的转换。例如，如果 `FPGA` 需要定点表示：

```python
def float_to_fixed(x, scale=1000):
    return jnp.round(x * scale).astype(jnp.int32)
def fixed_to_float(x, scale=1000):
    return x.astype(jnp.float32) / scale
def custom_matmul_fpga_fixed(a, b):
    a_fixed = float_to_fixed(a)
    b_fixed = float_to_fixed(b)
    c_fixed = custom_matmul_fpga(a_fixed, b_fixed)
    return fixed_to_float(c_fixed)
```

## 跨硬件同步

确保你在不同硬件之间协调计算，以避免数据一致性或不一致问题。可以使用同步原语，或确保在开始依赖计算之前数据传输已完成。

```python
def synchronized_custom_matmul(x, y):
    with custom_sync_lock:
        return custom_matmul(x, y)
```

## 处理错误和异常

正如我们之前看到的，当外部硬件无法按预期工作或给出意外结果时，拥有一个可靠的计划非常重要。

```python
def safe_custom_matmul(x, y):
    try:
        return custom_matmul(x, y)
    except Exception as e:
        print("Error during custom_matmul:", e)
        return jnp.dot(x, y)  # Fallback to standard JAX operation
```

通过遵循这些步骤，你成功地使用 `JAX` 的 `FFI` 能力在异构系统间分发计算。将特定任务卸载到 `FPGAs` 或 `ASICs` 等专用硬件上，可实现针对项目需求的显著性能提升。这种集成涉及仔细的数据转换、定义自定义 `JAX` 原语、管理同步以及确保与 `JAX` 的编译和微分机制兼容。



## 摘要
总体而言，我们通过在 `JAX` 中研究和集成外部函数，成功增强了机器学习模型的灵活性和性能。首先，我们成功解决了从 `JAX` 调用外部 `C` 库的挑战。我们能够封装 `C` 函数并将其作为自定义原语集成。这使我们能够在 `JAX` 的计算图中利用优化的 `C` 代码，扩展了模型的能力。接下来，我们通过编写自定义 `CUDA` 内核来优化性能，从而能够更高效地在 GPU 上执行特定操作。我们定义了自定义原语，编译了 `CUDA` 代码，并确保与 `JAX` 的 `JIT` 编译和自动微分机制无缝集成。
我们还将处理 `JAX` 与外部代码之间的数据转换作为重点。为此，我们实现了稳健的例程来管理数据类型、内存布局和数组维度方面的差异。这保证了兼容性，并在与外部函数交互期间保持数据完整性。我们还使用同步机制和最佳实践解决了线程安全和并发问题，消除了竞态条件并保证了多线程环境中计算的可靠性。最后，我们探索了在异构系统之间分发计算，利用 `FFI` 将任务卸载到 `FPGAs` 和 `ASICs` 等专用硬件。这种集成不仅优化了性能，还展示了模型在多样化硬件平台上的可扩展性。总体而言，本章为我们提供了有效将外部代码与 `JAX` 集成的必要策略和技术知识，显著增强了机器学习项目的功能性和效率。

# 第 8 章：使用 `JAX` 训练神经网络

## 概述
在本章中，我们将掌握训练神经网络的艺术，包括构建和有效优化模型的实用技术。我们首先学习如何使用 `TensorFlow Datasets` 高效地加载数据，这使得大规模机器学习任务的数据准备变得简单。这种简单而有效的配方确保数据顺利输入训练管道，实现更快、更高效的训练。
接下来，我们将使用 `JAX` 从头构建神经网络。你将学习设计和实现针对特定任务定制的自定义架构。然后，我们将在训练期间使用 `Penzai` 进行实验跟踪。该工具通过跟踪指标、超参数和结果来管理实验。它使评估模型性能变得更容易。最后，我们将介绍评估和可视化模型性能的技术。你将深入了解模型准确性和训练动态。你还将学习如何改进和调试模型。



# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你如何设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你完成设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据的过程，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你完成设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据的过程，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你完成设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据的过程，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你完成设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据的过程，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你完成设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据的过程，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你完成设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据的过程，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你完成设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据的过程，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你完成设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据的过程，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
# 使用 TensorFlow Datasets 高效加载数据

数据加载在训练管道中经常成为瓶颈，尤其是在处理大型数据集时。缓慢的数据加载会显著阻碍训练过程，导致 GPU 利用率低下和训练时间增加。为了解决这个问题，我们需要一个实用的解决方案来高效加载大型数据集、实时预处理它们，并将它们馈送到训练循环中。在本教程中，我们将使用 `TensorFlow Datasets` 实现无缝的数据加载和预处理，使我们能够将数据管道与 `JAX` 集成以训练神经网络。

## Overview

本教程将指导你完成设置 `TFDS` 以使用 `JAX` 高效加载和准备用于训练神经网络的数据的过程，利用 `TensorFlow` 的优化数据处理能力。这种方法使我们能够加载大型数据集、应用必要的转换，并将处理后的数据与 `JAX` 无缝集成。

### Steps
- 设置 `TensorFlow Datasets` 并选择合适的[content]
test



# 从零构建神经网络

设想一种情况，我们需要使用 `JAX` 从零开始构建一个自定义神经网络，而不使用 `Flax` 或 `Haiku` 等高级库。像这样构建神经网络有助于我们理解其工作原理，从而对架构和训练过程有更大的控制权。本教程将展示如何构建一个全连接神经网络，设置其 `parameters`，执行 `forward` 前向传播，计算 `loss`，并将其与 Fashion MNIST 数据集集成。

在 `JAX` 中构建神经网络，我们只需遵循以下步骤：

首先，定义架构，包括层和激活函数。首先初始化网络 `parameters`（`weights` 和 `biases`）。运行 `forward` 前向传播以进行预测。然后为训练定义 `loss` 函数。将网络与 Fashion MNIST 数据集集成用于训练目的。

## 定义神经网络架构

我们将构建一个简单的 feedforward 神经网络，具有两个隐藏层，使用 `ReLU` 激活函数处理隐藏层，并使用 `softmax` 处理输出层。

```
import jax
import jax.numpy as jnp
from jax import random
# Define the neural network architecture
def init_params(layer_sizes, key):
    """Initialize network parameters (weights and biases) for each layer."""
    params = []
    for n_in, n_out in zip(layer_sizes[:-1], layer_sizes[1:]):
        key, subkey = random.split(key)
        # Initialize weights with small random values
        weights = random.normal(subkey, (n_in, n_out)) * 0.01
        # Initialize biases with zeros
        biases = jnp.zeros(n_out)
        params.append((weights, biases))
    return params
# Define the layer sizes: input -> hidden1 -> hidden2 -> output
layer_sizes = [28 * 28, 128, 64, 10]  # Input: 784, Hidden1: 128, Hidden2: 64, Output: 10
# Random key for initialization
key = random.PRNGKey(0)
# Initialize parameters
params = init_params(layer_sizes, key)
```

在此设置中，`layer_sizes` 指定了每层的神经元数量，其中有 784 个输入特征（28x28 展平图像），两个隐藏层（128 和 64 个神经元），以及用于 10 个类别的输出层。我们使用小的随机值初始化 `weights`，并将 `biases` 初始化为零。

## 实现前向传播

前向传播将根据输入数据计算网络的输出。我们将对隐藏层使用 `ReLU` 激活函数，并对输出层使用 `softmax` 函数。

```
def relu(x):
    """ReLU activation function."""
    return jnp.maximum(0, x)
def softmax(x):
    """Softmax activation function."""
    exp_x = jnp.exp(x - jnp.max(x))
    return exp_x / exp_x.sum(axis=1, keepdims=True)
def forward(params, x):
    """Perform a forward pass through the network."""
    # Flatten the input image
    x = x.reshape((x.shape[0], -1))
    # Loop over each layer
    for i, (weights, biases) in enumerate(params[:-1]):
        # Linear transformation
        x = jnp.dot(x, weights) + biases
        # Apply ReLU activation for hidden layers
        x = relu(x)
    # Final layer (output)
    final_weights, final_biases = params[-1]
    logits = jnp.dot(x, final_weights) + final_biases
    # Apply softmax activation to get probabilities
    return softmax(logits)
```

`forward` 函数通过对每一层依次应用线性变换（矩阵乘法和偏置加法）以及激活函数来计算网络的输出。

## 定义损失函数

我们将使用交叉熵 `loss` 来衡量预测概率与真实标签之间的差异。

```
def cross_entropy_loss(params, x, y):
    """Compute the cross-entropy loss."""
    preds = forward(params, x)
    # Convert labels to one-hot encoding
    y_one_hot = jax.nn.one_hot(y, num_classes=10)
    # Compute the average cross-entropy loss
    loss = -jnp.mean(jnp.sum(y_one_hot * jnp.log(preds + 1e-8), axis=1))
    return loss
```

在此函数中，我们通过计算与真实标签对应的预测概率的负对数并在批次上取平均来计算 `loss`。

## 使用梯度下降实现参数更新

接下来，我们将使用随机梯度下降（`SGD`）更新 `parameters`。我们计算 `loss` 函数相对于 `parameters` 的梯度，并相应地更新 `weights` 和 `biases`。

```
def sgd_update(params, grads, learning_rate):
    """Update parameters using SGD."""
    new_params = []
    for (w, b), (dw, db) in zip(params, grads):
        # Update weights and biases
        new_w = w - learning_rate * dw
        new_b = b - learning_rate * db
        new_params.append((new_w, new_b))
    return new_params
```

## 训练神经网络

现在我们可以使用 Fashion MNIST 数据集设置训练循环来训练模型。

```
learning_rate = 0.01
num_epochs = 10
# Function to compute gradients
grad_loss = jax.grad(cross_entropy_loss)
def train_network(train_ds, params, num_epochs):
    for epoch in range(num_epochs):
        epoch_loss = 0
        for batch in train_ds:
            images, labels = batch
            # Compute gradients
            grads = grad_loss(params, images, labels)
            # Update parameters
            params = sgd_update(params, grads, learning_rate)
            # Compute batch loss
            batch_loss = cross_entropy_loss(params, images, labels)
            epoch_loss += batch_loss
        print(f"Epoch {epoch + 1}, Loss: {epoch_loss}")
    return params
# Train the network
trained_params = train_network(train_ds, params, num_epochs)
```

此训练循环在指定的 `epochs` 次数内遍历数据集，计算 `loss` 函数相对于网络 `parameters` 的梯度，使用 `SGD` 更新 `parameters`，并在每个 `epoch` 之后打印 `loss`。

## 评估训练好的模型

为了评估模型的性能，我们将使用测试数据集来衡量 `accuracy`。

```
def compute_accuracy(params, test_ds):
    correct = 0
    total = 0
    for batch in test_ds:
        images, labels = batch
        # Perform the forward pass to get predictions
        preds = forward(params, images)
        # Get the predicted class by taking the argmax
        predicted_class = jnp.argmax(preds, axis=1)
        # Count correct predictions
        correct += jnp.sum(predicted_class == labels)
        total += labels.shape[0]
    accuracy = correct / total
    return accuracy
# Evaluate the trained model
accuracy = compute_accuracy(trained_params, test_ds)
print(f"Test Accuracy: {accuracy * 100:.2f}%")
```

此评估函数通过将预测类别与真实标签进行比较来计算模型在测试数据集上的 `accuracy`。

此解决方案向我们展示了如何为 Fashion MNIST 数据集设置训练循环并获得基本水平的性能，我们可以通过使用更高级的技术（如更好的初始化、正则化和不同的优化算法）来改进性能。



# 使用 Penzai 进行训练

管理机器学习实验并系统地跟踪超参数、指标和结果，对于优化模型性能和确保可重复性至关重要。在处理多个模型或调优超参数时，手动跟踪不同的运行和配置可能具有挑战性。为了解决这个问题，我们将使用 Penzai，这是一款专为实验跟踪和管理而设计的工具。在本教程中，我们介绍 Penzai 并演示如何将其集成到基于 JAX 的工作流程中，使我们能够在训练期间记录超参数、指标和其他重要细节，从而使实验更易于监控、比较和重现。

## 关于 Penzai

Penzai 是一个轻量级且灵活的工具，用于管理机器学习实验，可实现对超参数、指标和结果的跟踪。该过程包括：
-   安装 Penzai 并设置项目。
-   在训练过程中记录超参数和指标。
-   使用 Penzai 的可视化和比较工具来分析不同的实验运行。
-   通过保存所有相关的实验细节来确保可重复性。

## 安装 Penzai

先提醒一下，您需要确保 Penzai 已安装在您的系统上。如果您还没有，可以使用以下命令添加：

```
pip install penzai
```

接下来，初始化一个新的 Penzai 项目。此步骤会创建配置文件以管理实验元数据。

```
penzai init --project-name "Fashion MNIST Training"
```

此命令设置名为 "Fashion MNIST Training" 的新项目并创建必要的配置文件。如果需要，您还可以设置存储后端或云集成选项。

## 在训练脚本中配置 Penzai

要将 Penzai 集成到您的 JAX 训练脚本中，请先导入 `penzai` 模块并初始化新的实验运行。

```
import penzai
# Initialize Penzai
penzai.init(project="Fashion MNIST Training")
# Start a new experiment run
run = penzai.start_run(run_name="Baseline Model Training")
```

`start_run` 函数开始一个新的实验，使我们能够记录与此运行相关的超参数、指标和结果。

## 记录超参数

在开始训练之前，记录相关的超参数，例如 `learning_rate`、`batch_size` 和 `num_epochs`。

```
# Hyperparameters
learning_rate = 0.01
batch_size = 128
num_epochs = 10
# Log hyperparameters
run.log_hyperparams({
    "learning_rate": learning_rate,
    "batch_size": batch_size,
    "num_epochs": num_epochs
})
```

此步骤可确保实验的关键设置被记录下来，以便在审阅或重现运行时可以回溯参考。

## 记录训练指标

随着训练的进行，在每个 epoch 记录重要的指标，如 loss 和 accuracy。这使 Penzai 能够随时间跟踪模型的性能。

```
def train_network_with_tracking(train_ds, params, num_epochs):
    for epoch in range(num_epochs):
        epoch_loss = 0
        for batch in train_ds:
            images, labels = batch
            # Compute gradients
            grads = jax.grad(cross_entropy_loss)(params, images, labels)
            # Update parameters
            params = sgd_update(params, grads, learning_rate)
            # Compute batch loss
            batch_loss = cross_entropy_loss(params, images, labels)
            epoch_loss += batch_loss
        # Log the epoch loss
        run.log_metric("epoch_loss", epoch_loss, step=epoch)
        # Optionally, log additional metrics
        accuracy = compute_accuracy(params, test_ds)
        run.log_metric("accuracy", accuracy, step=epoch)
        print(f"Epoch {epoch + 1}, Loss: {epoch_loss}, Accuracy: {accuracy * 100:.2f}%")
    return params
# Train the network while logging metrics
trained_params = train_network_with_tracking(train_ds, params, num_epochs)
```

通过在每个 epoch 记录 `loss` 和 `accuracy` 等指标，您可以在 Penzai 的仪表板中可视化模型的学习曲线。

## 可视化和比较实验

记录指标后，使用 Penzai 的 Web 界面分析训练进度、比较不同的运行并观察趋势。

打开 Penzai 仪表板：

```
penzai ui
```

然后，查看列在 "Fashion MNIST Training" 下的实验，并比较不同运行中的 `loss` 和 `accuracy` 等指标。您还可以使用内置工具创建图表，显示指标如何随时间演变或不同的超参数设置如何影响结果。

## 记录模型产物以实现可重复性

除了跟踪指标和超参数外，保存模型产物（例如训练好的参数）以实现可重复性和进一步分析也很重要。

```
# Save trained model parameters
model_artifact_path = "model_params.pkl"
with open(model_artifact_path, "wb") as f:
    import pickle
    pickle.dump(trained_params, f)
# Log the model artifact
run.log_artifact(model_artifact_path)
```

记录训练好的模型权重等产物可确保您能够重现实验或在需要时进行改进。

## 结束实验运行

完成训练并记录必要信息后，请确保结束实验运行。

```
run.end()
```

这将完成当前实验，使您能够开始新的运行或在 Penzai 中分析已完成的实验。

通过将 Penzai 集成到训练过程中，我们高效地管理了实验，系统地跟踪了超参数，并记录了用于评估模型性能的指标。Penzai 可视化训练进度、比较不同运行并保存模型产物的能力促进了机器学习项目的可重复性和优化。



# 评估和可视化模型性能

评估机器学习模型的训练进展对于理解其有效性并识别改进空间至关重要。在基于 `JAX` 的工作流中，如果没有高级库，实现评估指标并可视化模型的训练和测试性能可能会具有挑战性。为解决此问题，我们将使用准确率、精确率、召回率和混淆矩阵等评估指标，以及 `Matplotlib` 等可视化工具，来跟踪模型的进展并深入了解其在训练期间的行为。本教程演示了如何实现这些技术来监控我们迄今为止开发的 `JAX` 模型的性能。

## 概述

在这里，为了有效评估和可视化模型的性能，我们将：

- 实现标准评估指标，如准确率、精确率、召回率和混淆矩阵。
- 通过随时间绘制损失和准确率等指标来可视化模型的学习曲线。
- 使用混淆矩阵来识别模型在何处做出正确和错误的预测。
- 将这些评估技术集成到 `JAX` 训练和测试工作流中。

## 实现评估指标

开始时，我们将实现常见的评估指标，重点关注准确率、精确率、召回率和混淆矩阵计算。

```python
import jax.numpy as jnp

def compute_accuracy(params, test_ds):
    """Calculate the accuracy of the model on the test dataset."""
    correct = 0
    total = 0
    for batch in test_ds:
        images, labels = batch
        # Perform the forward pass to get predictions
        preds = forward(params, images)
        # Get the predicted class by taking the argmax
        predicted_class = jnp.argmax(preds, axis=1)
        # Count correct predictions
        correct += jnp.sum(predicted_class == labels)
        total += labels.shape[0]
    accuracy = correct / total
    return accuracy

def compute_precision_recall(params, test_ds, num_classes=10):
    """Calculate precision and recall for each class."""
    true_positives = jnp.zeros(num_classes)
    false_positives = jnp.zeros(num_classes)
    false_negatives = jnp.zeros(num_classes)
    for batch in test_ds:
        images, labels = batch
        preds = forward(params, images)
        predicted_class = jnp.argmax(preds, axis=1)
        for i in range(num_classes):
            true_positives = true_positives.at[i].add(jnp.sum((predicted_class == i) & (labels == i)))
            false_positives = false_positives.at[i].add(jnp.sum((predicted_class == i) & (labels != i)))
            false_negatives = false_negatives.at[i].add(jnp.sum((predicted_class != i) & (labels == i)))
    # Compute precision and recall
    precision = true_positives / (true_positives + false_positives + 1e-8)
    recall = true_positives / (true_positives + false_negatives + 1e-8)
    return precision, recall
```

`compute_accuracy` 函数计算整体准确率，而 `compute_precision_recall` 函数为每个类别计算精确率和召回率，提供更详细的性能洞察。

## 计算混淆矩阵

混淆矩阵可以通过显示模型在何处做出正确和错误的预测来帮助可视化模型在不同类别上的性能。

```python
def compute_confusion_matrix(params, test_ds, num_classes=10):
    """Compute the confusion matrix for the test dataset."""
    confusion_matrix = jnp.zeros((num_classes, num_classes))
    for batch in test_ds:
        images, labels = batch
        preds = forward(params, images)
        predicted_class = jnp.argmax(preds, axis=1)
        for true_label, pred_label in zip(labels, predicted_class):
            confusion_matrix = confusion_matrix.at[true_label, pred_label].add(1)
    return confusion_matrix
```

混淆矩阵将有助于识别模型错误中的模式，表明模型将哪些类别混淆在一起。

## 可视化训练进度

为了了解模型随时间的改进情况，请绘制每个 epoch 的训练和验证损失及准确率。我们将使用 `Matplotlib` 进行可视化。

```python
import matplotlib.pyplot as plt

def plot_learning_curves(training_losses, validation_accuracies):
    """Plot the learning curves for loss and accuracy."""
    epochs = range(1, len(training_losses) + 1)
    # Plot training loss
    plt.figure(figsize=(12, 5))
    plt.subplot(1, 2, 1)
    plt.plot(epochs, training_losses, label='Training Loss')
    plt.xlabel('Epoch')
    plt.ylabel('Loss')
    plt.title('Training Loss Over Time')
    plt.legend()
    # Plot validation accuracy
    plt.subplot(1, 2, 2)
    plt.plot(epochs, validation_accuracies, label='Validation Accuracy')
    plt.xlabel('Epoch')
    plt.ylabel('Accuracy')
    plt.title('Validation Accuracy Over Time')
    plt.legend()
    plt.show()

# Example data for demonstration
training_losses = [0.9, 0.7, 0.5, 0.3, 0.2]  # Dummy loss values
validation_accuracies = [0.70, 0.75, 0.80, 0.85, 0.88]  # Dummy accuracy values
# Plot the learning curves
plot_learning_curves(training_losses, validation_accuracies)
```

这些图表有助于可视化训练过程中损失降低和准确率提升的趋势，为模型的训练过程提供洞察。

## 可视化混淆矩阵

可视化混淆矩阵有助于理解模型犯错的类型。

```python
import seaborn as sns

def plot_confusion_matrix(conf_matrix, class_names):
    """Plot the confusion matrix using Seaborn."""
    plt.figure(figsize=(10, 8))
    sns.heatmap(conf_matrix, annot=True, fmt="d", cmap="Blues", xticklabels=class_names, yticklabels=class_names)
    plt.xlabel('Predicted Label')
    plt.ylabel('True Label')
    plt.title('Confusion Matrix')
    plt.show()

# Example class names for Fashion MNIST
class_names = [
    'T-shirt/top', 'Trouser', 'Pullover', 'Dress', 'Coat',
    'Sandal', 'Shirt', 'Sneaker', 'Bag', 'Ankle boot'
]
# Compute the confusion matrix
conf_matrix = compute_confusion_matrix(trained_params, test_ds, num_classes=10)
# Plot the confusion matrix
plot_confusion_matrix(conf_matrix, class_names)
```

混淆矩阵的热力图表示揭示了模型难以区分的类别，表明了潜在改进的领域。

## 在每个 Epoch 后自动化评估

为了系统地监控模型的训练进展，将评估和可视化集成到训练循环中。

```python
def train_and_evaluate(train_ds, test_ds, params, num_epochs):
    training_losses = []
    validation_accuracies = []
    for epoch in range(num_epochs):
        # Training phase
        epoch_loss = 0
        for batch in train_ds:
            images, labels = batch
            grads = jax.grad(cross_entropy_loss)(params, images, labels)
            params = sgd_update(params, grads, learning_rate)
            batch_loss = cross_entropy_loss(params, images, labels)
            epoch_loss += batch_loss
        # Log the training loss
        training_losses.append(epoch_loss)
        # Evaluation phase
        accuracy = compute_accuracy(params, test_ds)
        validation_accuracies.append(accuracy)
        # Print epoch summary
        print(f"Epoch {epoch + 1}, Loss: {epoch_loss}, Validation Accuracy: {accuracy * 100:.2f}%")
    # Plot learning curves after training
    plot_learning_curves(training_losses, validation_accuracies)
    # Compute and plot the confusion matrix after the final epoch
    conf_matrix = compute_confusion_matrix(params, test_ds, num_classes=10)
    plot_confusion_matrix(conf_matrix, class_names)
    return params

# Train the network and evaluate its performance
trained_params = train_and_evaluate(train_ds, test_ds, params, num_epochs)
```

这种集成的训练和评估方法能够实时监控模型的性能，在整个训练过程中提供有价值的见解。

我们使用了准确率、精确率、召回率和混淆矩阵等指标，并可视化学习曲线和混淆矩阵，以更密切地关注模型的表现。这些技术帮助我们理解模型是如何学习的，也指出了我们可以改进的地方。这使得模型开发过程更具迭代性和数据驱动性。



## 摘要
简而言之，我们有效地训练了神经网络，并在过程中解决了遇到的实际挑战。我们通过利用 TensorFlow Datasets 高效地加载和预处理大型数据集，从而解决了数据加载瓶颈。接下来，我们从零开始构建了一个神经网络，让你能够亲手了解如何在 JAX 中构建层、实现激活函数以及直接配置参数更新。

本章还介绍了使用 Penzai 进行系统化实验跟踪，这使得在训练期间能够记录超参数、指标和结果。此外，我们还研究了评估模型学习进展的技术。我们重点介绍了实现诸如准确率、精确率和召回率等评估指标，以及使用混淆矩阵详细分析模型预测的方法。

## 致谢
我对 GitforGits 怀有深深的感激之情，感谢他们在撰写本书的整个过程中始终如一的热情和明智的建议。他们渊博的知识和细致的编辑帮助确保了这本书对各个阅读水平和理解能力的人都有用。此外，我还要感谢出版过程中所有参与人员为使本书成为现实所付出的努力。他们从校对到广告的各项工作造就了今天的项目。

最后，我想向在我一生中给予我无条件爱和鼓励的每一个人表达我的感激。他们的支持对本书的完成至关重要。我感谢您对此次事业的帮助以及对我职业生涯的持续关注。

## 感谢

## 尾声
当我们到达《Google JAX Cookbook》的结尾时，我满怀兴奋地反思这里所涵盖的技术和解决方案不仅仅是理论练习。这些出色的工具已准备好供您在机器学习和人工智能项目中每天使用！这些食谱将使您能够从零开始构建新模型、优化现有管道，并自信地调试棘手的运行时问题！

机器学习和人工智能日常工作的美妙之处在于它往往是不可预测的！您可能会遇到计算速度慢、内存限制、意外错误，或需要微调模型以获得更高性能——而您将为此做好准备！这些情况需要的不仅仅是对工具的熟悉。它们要求能够有效地应用这些工具来解决实际问题！本书旨在为您提供成功所需的解决问题思维！而且最好的部分是，您可以学到的远不止如何编写更快的代码！它们关心的远不止编写更快的代码！您将更深入地了解数值计算如何被优化、硬件限制如何被管理，以及像 JAX 这样的现代库如何改变您处理机器学习的方式。您已探索了高效数据加载的技术、使用混合精度以提高训练速度的方法、实时监控模型性能的方法，以及在专用硬件上分配计算的策略。每项技能都将使您的日常任务更加高效且不易出错！

关于分析、调试、序列化以及实验跟踪的提示将帮助您在项目增长或改变方向时保持敏捷。您已掌握了一些避免常见错误、毫无障碍地集成外部函数以及保持项目稳定和可复现的技巧。这种知识不仅仅解决一个问题；它改变了您处理所有工作的方式。

这些食谱旨在不仅提供解决方案，还能让您更积极地参与到您所拥有的工具中。我希望凭借本书的见解，您会发现日常工作不再是负担，而更多是创新和突破人工智能可能性的机会。随着您继续开发、优化和部署模型，愿这些食谱成为可靠的伴侣，引导您在所有机器学习项目中获得更好、更快的成果。
