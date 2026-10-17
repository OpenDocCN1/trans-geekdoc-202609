

## 实践练习 – 构建和训练 PyTorch 模型

在本实践练习中，你将学习如何在本地计算机上安装 PyTorch 库，并使用 PyTorch 训练一个简单的深度学习模型。启动你之前在机器上安装的 Jupyter Notebook。如果你不记得如何操作，请访问第 3 章 探索 ML 算法 的实验室部分。现在，让我们开始：

1.  在 Jupyter Notebook 环境中创建一个名为 `pytorch-lab` 的新文件夹，并创建一个名为 `pytorch-lab1.ipynb` 的新笔记本文件。在单元格中运行以下命令以安装 PyTorch 和 `torchvision` 包。`torchvision` 包含一组计算机视觉模型和数据集。我们将在本练习中使用 `torchvision` 包中的预构建 MNIST 数据集： 

    ```
    !pip3 install torch
    !pip3 install torchvision
    ```

2.  以下示例代码展示了前面提到的主要组件。请务必在单独的 Jupyter Notebook 单元格中运行每个代码块，以获得最佳可读性。 

    首先，我们必须导入必要的库包，并从 `torchvision` 数据集类加载 MNIST 数据集：

    ```
    import numpy as np
    import matplotlib.pyplot as plt
    import torch
    from torchvision import datasets, transforms
    from torch import nn, optim
    transform = transforms.Compose([transforms.ToTensor(), transforms.Normalize((0.5,), (0.5,),)])
    trainset = datasets.MNIST('pytorch_data/train/', download=True, train=True, transform=transform)
    valset = datasets.MNIST('pytorch_data/test/', download=True, train=False, transform=transform)
    trainloader = torch.utils.data.DataLoader(trainset, batch_size=64, shuffle=True)
    ```

1.  接下来，我们必须构建一个用于分类的 MLP 神经网络。这个 MLP 网络有两个隐藏层，第一层和第二层使用 ReLU 激活函数。MLP 模型的输入大小为 `784`，这是 28x28 图像的展平维度。第一个隐藏层有 `128` 个节点（神经元），而第二层有 `64` 个节点（神经元）。最终层有 `10` 个节点，因为我们有 10 个类别标签： 

    ```
    model = nn.Sequential(nn.Linear(784, 128),
                          nn.ReLU(),
                          nn.Linear(128, 64),
                          nn.ReLU(),
                          nn.Linear(64, 10))
    ```

2.  以下是图像数据的示例： 

    ```
    images, labels = next(iter(trainloader))
    pixels = images[0][0]
    plt.imshow(pixels, cmap='gray')
    plt.show()
    ```

3.  现在，我们必须为训练过程定义一个 `交叉熵损失函数`，因为我们想要衡量所有标签的概率分布中的误差。在内部，PyTorch 的 `CrossEntropyLoss` 自动对网络输出应用 `softmax` 以计算不同类别的概率分布。对于优化器，我们选择了学习率为 `0.003` 的 Adam 优化器。`view()` 函数将二维输入数组（28x28）展平为一维向量，因为我们的神经网络接受一维向量输入： 

    ```
    criterion = nn.CrossEntropyLoss()
    images = images.view(images.shape[0], -1)
    output = model(images)
    loss = criterion(output, labels)
    optimizer = optim.Adam(model.parameters(), lr=0.003)
    ```

    学习率是一个超参数，它决定了优化过程中采取的步长大小。

1.  现在，让我们开始训练过程。我们将运行 `15` 个 epoch。与 TensorFlow Keras API 不同，你只需调用 `fit()` 函数即可开始训练，而 PyTorch 要求你构建训练循环，并专门运行前向传递（`model(images)`）、运行反向传递以学习（`loss.backward()`）、更新模型权重（`optimizer.step()`），然后计算总损失和平均损失。对于每个训练步骤，`trainloader` 返回一个批次（批量大小为 `64`）的训练数据样本。每个训练样本被展平为一个 784 长度的向量。优化器在每个训练步骤中都会重置为零： 

    ```
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

    当训练代码运行时，它应该打印出每个 epoch 的平均损失。

1.  要使用验证数据测试准确性，我们必须将验证数据集通过训练好的模型运行，并使用 `sklearn.metrics.accuracy_score()` 来计算模型的准确性： 

    ```
    valloader = torch.utils.data.DataLoader(valset, batch_size=valset.data.shape[0], shuffle=True)
    val_images, val_labels = next(iter(valloader))
    val_images = val_images.view(val_images.shape[0], -1)
    predictions = model(val_images)
    predicted_labels = np.argmax(predictions.detach().numpy(), axis=1)
    from sklearn.metrics import accuracy_score
    accuracy_score(val_labels.detach().numpy(), predicted_labels)
    ```

2.  最后，我们必须将模型保存到文件： 

    ```
    torch.save(model, './model/my_mnist_model.pt')
    ```

恭喜！你已成功在本地 Jupyter 环境中安装 PyTorch 并训练了一个深度学习 PyTorch 模型。

# 如何在 TensorFlow 和 PyTorch 之间进行选择

TensorFlow 和 PyTorch 是深度学习领域中最流行的两个框架。因此，一个相关的问题出现了：如何在这两者之间做出明智的选择？为了帮助回答这个问题，让我们对这些框架进行快速的比较分析：

*   **易用性**：PyTorch 通常被认为更易于使用且更具 Python 风格。控制流感觉更接近原生 Python，PyTorch 的动态计算图相比于 TensorFlow 的静态计算图，使其更容易调试和迭代。然而，TensorFlow 2.0 中的即时执行支持有助于缩小这一差距。PyTorch 也被认为比 TensorFlow 更具面向对象特性。

*   **社区流行度**：两个框架都享有强大的社区支持，并且非常流行。TensorFlow 最初领先；然而，根据 Google Trends 报告，PyTorch 近年来在流行度上已赶上。PyTorch 在研究界被更广泛地采用，并主导了研究论文的实现。

*   **模型可用性**：TensorFlow 拥有 TensorFlow Model Garden，其中托管了一组使用 TensorFlow API 的模型，涵盖计算机视觉、NLP 和推荐等各种 ML 任务。它还具有 TensorFlow Hub，提供一系列预训练模型，可用于跨广泛 ML 任务的部署或微调。同样，PyTorch 拥有 PyTorch Hub，这是一个集成到 PyTorch 中的库，可轻松访问大量用于计算机视觉、NLP 等的预训练模型。

*   **部署**：两个框架都适合 ML 模型的生产部署。TensorFlow 被认为拥有更全面的模型部署堆栈，包括 TensorFlow Serving、用于移动和边缘设备的 TensorFlow Lite 以及用于浏览器部署的 TensorFlow.js。TensorFlow Extended 是一个端到端的模型部署平台，涵盖模型验证、监控和解释。PyTorch 提供 TorchServe，这是一个用于 PyTorch 模型的模型服务框架，以及 PyTorch Mobile，用于在 iOS 和 Android 设备上部署模型。PyTorch 在部署过程的端到端集成方面更多依赖第三方解决方案。

