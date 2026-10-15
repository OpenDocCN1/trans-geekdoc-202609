

# PyTorch 2.0 学习指南：从基础到复杂模型的深度学习实验，充分利用每一种潜在能力

## 前言

本书是一本全面指南，旨在帮助读者理解并运用 PyTorch 2.0 进行深度学习应用。本书首先介绍了 PyTorch、它相对于其他深度学习框架的诸多优势，以及它与 CUDA 结合实现 GPU 加速的方法。接着，我们深入 PyTorch 的核心——张量，学习它们的不同类型、属性和操作。通过逐步示例，读者将学会对张量执行基本算术运算、操作张量，并理解与张量形状相关的错误。

本书有相当一部分内容专门用于演示如何构建简单的 PyTorch 模型，包括上传和准备数据集、定义架构、训练和预测，并提供了真实世界数据集的动手练习。随后，本书转向探索 PyTorch 的 `nn` 模块，并详细比较了不同类型网络（如前馈网络、RNN、GRU、CNN）及其组合。

此外，本书深入探讨了训练过程和 PyTorch 的 `optim` 模块，概述了诸如梯度下降、SGD、小批量梯度下降、动量、Adagrad 和 Adam 等优化算法。另有单独一章聚焦 PyTorch 2.0 中的高级概念，如模型序列化、优化、分布式训练和 PyTorch 量化 API。

在最后几章中，本书讨论了 TensorFlow 2.0 与 PyTorch 2.0 之间的差异，以及使用 ONNX 将 TensorFlow 模型迁移到 PyTorch 2.0 的逐步过程，并概述了在此过程中遇到的常见问题及解决方法。

在本书中，你将学到：

- 全面介绍用于深度学习的 PyTorch 和 CUDA。
- 对 PyTorch 张量的深入理解和操作。
- 构建简单 PyTorch 模型的分步指南。
- 深入了解 PyTorch 的 `nn` 模块，并比较各种网络类型。
- 训练过程概述，以及探索 PyTorch 的 `optim` 模块。
- 理解 PyTorch 中的高级概念，如模型序列化和优化。
- 了解 PyTorch 中的分布式训练。
- 使用 PyTorch 量化 API 的实用指南。

## 序言

亲爱的读者，我们很高兴带你踏上一段激动人心的冒险，进入 PyTorch 2.0 的迷人世界。本书经过精心打磨，力求成为一部详尽的参考书，旨在阐明深度学习复杂的地形。它的目标是让你从一名好奇的爱好者转变为一名熟练的实践者，为你提供正确使用 PyTorch 所需的理论理解和实践技能。当我们踏上这段发现之旅时，我们希望你能完全参与其中，检验你先前持有的信念，并拓宽你对深度学习这一迷人领域的视野。

本书的第一部分为 PyTorch 的基本原则奠定了坚实的基础。张量，作为 PyTorch 的基本构建元素，在前几章中得到了充分的讨论。这些早期的章节将引导你逐步理解张量，以及构建和操作张量的过程。通过逐步增加主题的难度，本书将确保你在继续学习更高级的概念之前，已牢固掌握基础知识。

随着我们进一步深入 PyTorch 的内部运作，本书开始介绍基础模型和更复杂模型的开发。我们借助一些示例来剖析构成这些模型的众多部分。你将学习如何创建和训练各种神经网络，包括前馈神经网络、循环神经网络，以及更高级的 GRU 和 CNN 模型。由于本书将理论解释与实际示例相结合，你将能够把书中所学应用到现实场景中，这有助于加深对所述各种概念和方法的理解。

在初步了解神经网络之后，本书接下来讲解训练过程的知识。解开优化算法之谜——有时被称为“驱动神经网络学习的引擎”——是这项工作中最重要的方面之一。本书以全面且易于理解的方式解释了每种算法，从基础的梯度下降一直讲到更复杂的自适应矩估计。借助这些知识和所完成的练习，你现在将有能力使用 PyTorch 构建并训练健壮的模型。

在本书的后续章节中，我们深入探讨 PyTorch 编程语言中更高级的原理。你将获得有关模型序列化和优化、分布式训练以及使用 PyTorch 提供的量化 API 的知识。此外，我们还研究了 TensorFlow 2.0 与 PyTorch 2.0 之间的联系，对两者的优缺点进行了比较和对照。通过这样做，本书为你提供了必要的知识，以便选择最能满足你需求的框架。

当我们踏上这段冒险之旅时，我们希望你能以开放的心态和充满好奇的头脑来对待每一章。无论你是刚刚开始深度学习的初学者，还是希望提升技能的经验丰富的专业人士，本书都能为你提供有价值的内容。我们衷心希望，当你读完这本书时，你不仅能全面理解 PyTorch 2.0，还能树立起将所学应用于现实世界的自信。让我们不要再浪费时间，一起直接进入这激动人心的冒险吧，好吗？欢迎来到 PyTorch 2.0！

## 索引

## 结语

## GitforGits

### 先决条件

对于每一位热切期望利用 PyTorch 2.0 提取可操作智能的机器学习工程师、数据科学家、AI 工程师和数据研究人员来说，这是一本出色而精湛的书。只需了解 Python 和深度学习基础知识，你就能轻松通读本书。

### 代码使用

你需要一些有用的代码示例来辅助你的编程和文档编写吗？不用再找了！本书提供了丰富的补充材料，包括代码示例和练习。

本书不仅旨在帮助你完成工作，而且我们允许你在程序和文档中使用示例代码。但请注意，如果你要复制代码的很大一部分，我们需要你联系我们以获得许可。

不过别担心，在你的程序中使用本书的几个代码片段，或通过引用本书并引用示例代码来回答问题，是不需要许可的。但如果你选择注明出处，署名通常包括书名、作者、出版社和 ISBN。例如，“Learning PyTorch 2.0 by Matthew Rosch”。

如果你不确定自己对代码示例的预期使用是否属于合理使用或上述许可范围，请随时联系我们。

我们很乐意帮助你并解答任何疑虑。

## 第 1 章：PyTorch 2.0 与 CUDA 11.8 简介

### 神经网络基础

人工神经网络是一种迷人的计算机模型，它抓住了深度学习的精髓，而深度学习是机器学习的一个子集。深度学习是机器学习的一个子集。在本章中，我们探讨神经网络的基础知识，包括它们对深度学习的适用性，以及这些模型如何模仿人脑执行的基本过程。

人工神经元构成了组成神经网络的处理器件，而神经网络是相互连接节点的集合。这些网络的设计灵感来自真实神经元，后者是大脑的基本构建模块。人工神经元及其之间的连接构成了深度学习系统智能能力的基础。正如由突触连接的数十亿神经元使人们能够学习、观察并对周围环境作出反应，人工神经元及其连接也是如此。

### 神经网络的结构

人工神经网络通常按层构建，从输入层开始，经过一个或多个隐藏层，最后是输出层。每一层由多个人工神经元（也称为节点）组成。

**输入层：** 输入层负责接收来自外部世界的原始数据。这些数据随后被送入网络进行处理。该层中的每个节点代表输入数据集中的一个特征。

**隐藏层：** 隐藏层通过以权重和偏差为特征的连接系统完成实际处理。这些层将输入转换为输出层可以使用的形式。

**输出层：** 输出层负责生成最终结果或决策。输出层中的节点数量通常由问题的性质决定——例如，二分类问题只有一个节点，而多分类问题的节点数与类别数相同。

每个节点都与前一层和后一层的节点相互连接。这些连接与权重相关联，权重决定了特定输入的重要性或影响。此外，每个节点都有一个偏差，允许偏移激活函数的阈值。

### 神经网络中的学习

给定一组输入-输出对，神经网络中的“学习”过程就是根据网络产生的误差来调整这些权重和偏差。损失函数用于计算该误差。损失函数是衡量网络预测与实际输出之间差异的函数。

反向传播是通过将误差信号沿网络反向发送并传播该误差来更新网络权重和偏差的过程。在试图找到能使损失函数尽可能小的理想权重和偏差集合时，会采用诸如梯度下降之类的优化算法。

### 神经网络与深度学习

神经网络构成了深度学习的骨干。一个'深度'神经网络简单地指具有多个隐藏层的网络。这些更深的网络能够捕捉输入数据中的复杂模式和表示，使其成为图像识别、自然语言处理等任务的极其强大的工具。

然而，训练深度神经网络是一项非平凡的任务。随着我们添加更多层，模型的复杂性以及计算负担随之增加。幸运的是，硬件（GPU）的进步以及像 PyTorch 这样的高效软件平台，使得深度网络的训练变得可行且更易于访问。

在接下来的章节中，我们将更深入地探讨 PyTorch 以及如何利用它来构建和训练神经网络。我们还将探讨它如何针对 GPU 加速进行了优化，使用 CUDA 11.8，显著加快了深度神经网络的训练过程。本质上，神经网络通过模拟人脑的结构和功能，彻底改变了人工智能领域。它们为开发能够以几乎不需要显式编程的方式执行复杂任务的智能系统开辟了新的途径，从而标志着技术中一个令人兴奋时代的黎明。

### Introduction to PyTorch

现在我们已经熟悉了神经网络的基础知识，接下来我们将讨论 PyTorch，这一工具在开发和训练这些网络的过程中发挥着至关重要的作用。

### PyTorch Overview

由 Facebook 人工智能研究实验室（FAIR）开发，PyTorch 是一个功能强大的开源深度学习框架，提供了科学计算所需的灵活性和速度。以其动态计算图和用户友好的界面而闻名，PyTorch 已迅速成为人工智能领域研究人员和开发人员的首选工具。

### How PyTorch supports Deep Learning

PyTorch 以其即时定义方法而闻名，这意味着它能够实现动态计算图。这也是 PyTorch 如此受欢迎的原因之一。由于其灵活性，PyTorch 非常适合需要复杂控制流组件（如循环和条件语句）的模拟，因为它能够在计算进行的同时以可理解的方式开发和更新系统。

PyTorch 的应用程序编程接口（API）旨在用户友好且易于探索。由于 PyTorch 严格遵循 Python 的设计理念，因此它能够让开发者使用原生 Python 结构和命令，如列表和字典，来构建神经网络。它既易于使用又功能强大这一事实，是其被广泛接受的主要因素之一。

张量，即多维数组，是 PyTorch 的核心。这些数组类似于 NumPy 的 `ndarrays`，不同之处在于它们支持 GPU。由于这种 GPU 加速，高效计算现在成为可能，而这在训练庞大的神经网络时非常必要，庞大的神经网络是深度学习的基础。

PyTorch 内置的自动微分引擎名为 `Autograd`，负责神经网络的训练，被称为 `Autograd` 系统。在反向传播过程中，`Autograd` 负责计算损失相对于模型参数的梯度或导数。这些值随后被优化方法用于更新权重和偏置。

PyTorch 的模块化设计促进了构成神经网络的众多组件的明确分离。例如，`torch.nn` 模块提供了组装各种神经网络拓扑所需的所有基本组件。同样，`torch.optim` 提供了多种优化技术的托管，例如 `SGD` 和 `Adam`。

由于 PyTorch 与其他 Python 库（如 NumPy 和 SciPy）兼容，因此处理数据加载、预处理和结果可视化等活动变得更加简单。此外，它与 Python 的多进程接口非常良好，这使得在加载数据时使用多线程变得更加简单。

### PyTorch 2.0 and CUDA 11.8

随着 PyTorch 2.0 的发布，PyTorch 继续发展和改进。PyTorch 2.0 中的一些重要改进包括更好的模型部署支持、移动优化以及与 TorchScript 的更紧密集成，从而实现从研究到生产的更直接转换。

为了充分利用 GPU 的处理能力，PyTorch 2.0 利用了 CUDA 11.8，这是由 NVIDIA 开发的并行计算平台和 API 模型。CUDA 通过允许开发者使用 NVIDIA GPU 进行通用计算，从而大幅加速计算，这是处理训练深度神经网络的计算密集度的基本要求。通过将 PyTorch 与 CUDA 结合，开发者和研究人员可以利用最新的 GPU 技术更快、更高效地训练模型。这种效率是深度学习开发的关键方面，因为模型训练通常是一个耗时的过程。

总之，PyTorch 是一个多功能且强大的深度学习框架。其设计理念——简单性、灵活性和效率，结合其与 CUDA 的集成，使其成为开发先进 AI 模型的优秀工具。在接下来的章节中，我们将深入探讨安装 PyTorch 2.0 和 CUDA 11.8 的具体细节，以及如何使用这些工具构建、训练和部署神经网络。

### PyTorch 2.0 Key Features

自诞生以来，PyTorch 在推动人工智能和深度学习的民主化方面发挥了重要作用。随着 PyTorch 2.0 的发布，该框架引入了新功能和改进，强化了其在人工智能领域对可访问性、透明性和性能的承诺。

以下是 PyTorch 2.0 带来的一些关键增强功能：

#### Enhanced TorchScript

TorchScript 是用于表示 PyTorch 程序的 Python 子集，在 PyTorch 2.0 中得到了增强。这一改进使您能够更轻松地在即时模式（PyTorch 的即时定义方法）和图模式（定义后运行）之间切换，结合两者的优点以提高灵活性和性能。这也有助于更好地优化，并成为改进模型部署的重要一步。

#### Model Deployment and Serving

PyTorch 2.0 在促进更好的模型部署方面迈出了重大步伐。随着 TorchServe 的引入，将模型从研究阶段推向生产阶段变得更加容易。TorchServe 提供了轻量级且稳健的方式来服务 PyTorch 模型，提供多模型服务、模型版本控制和指标记录等功能。

#### Improved Mobile Support

深度学习应用正从服务器和桌面扩展到移动和边缘设备。认识到这一点，PyTorch 2.0 扩展了其功能，以支持在 Android 和 iOS 平台上开发和部署模型。PyTorch Mobile 功能允许您将训练好的模型以最少的努力运行在移动设备上，从而实现智能的设备端应用开发。

#### Enhanced Quantization Support

量化是一种以降低精度执行计算和存储的技术。对于在计算资源较低的设备上部署模型或网络带宽受限时至关重要。PyTorch 2.0 引入了原生、综合的量化 API，支持训练后量化和量化感知训练。这可以减少模型的内存占用并提高推理速度，对于移动或边缘设备尤其重要。

#### Named Tensors

PyTorch 2.0 引入了命名张量的概念，为 PyTorch 的张量表示添加了维度命名。在复杂的代码库和模型中，这非常有用，因为在众多维度及其用途上很容易混淆。命名张量还提高了代码的可读性和可维护性，从而减少错误和 bug。

#### Extended Ecosystem

PyTorch 2.0 受益于扩展的工具和库生态系统，这些工具和库旨在增强和简化模型开发的各个阶段。例如 PyTorch Lightning 等库简化了训练过程，TorchText 提供了用于文本处理的工具，TorchVision 则用于图像和视频处理，等等。这些库与 PyTorch 2.0 兼容，有助于创建更统一、更高效的开发环境。

### 扩展的 ONNX 支持

开放神经网络交换格式（ONNX）是一种用于表示机器学习模型的开源标准，允许模型在不同的深度学习框架之间共享。PyTorch 2.0 提高了与 ONNX 的兼容性，使得以 ONNX 格式导出 PyTorch 模型更加容易，导出的模型可以在其他框架中进行推理，甚至可以通过 ONNX Runtime 部署到不同平台上。

总而言之，PyTorch 2.0 延续了 PyTorch 的理念，为用户提供简单性和灵活性，同时引入了显著的改进，使从研究到生产的过渡变得无缝衔接。它顺应了深度学习从业者不断变化的需求，为人工智能领域铺平了通往创新、高效且易用解决方案的道路。后续章节将更深入地探讨这些特性，解释如何利用它们来构建和训练强大的深度学习模型。

### 用于加速深度学习的 CUDA

在深度学习中，所涉及的计算规模与复杂度是巨大的。训练深度神经网络涉及大量矩阵乘法和其他计算密集型操作。因此，高效的计算对于节省时间和资源变得至关重要。这正是 CUDA（统一计算设备架构）发挥作用的领域。

#### CUDA 入门

CUDA 由 NVIDIA 开发，是一个并行计算平台和应用编程接口（API）模型。它允许软件开发人员使用 NVIDIA 图形处理器（GPU）进行通用计算——这种做法被称为 GPGPU（通用图形处理器计算）。借助 CUDA，开发人员能够利用 GPU 的计算能力大幅提升应用程序的计算性能。

#### 为什么深度学习需要 CUDA？

由于图形处理器（GPU）具有多核架构，能够同时管理数百个线程，而中央处理器（CPU）仅设计用于一次处理少量线程。

以下是一些在深度学习背景下这种并行性尤为有用的原因：

- 矩阵运算：深度学习严重依赖线性代数运算，其中许多运算（如矩阵乘法和卷积）极易并行化。由于 GPU 能够同时处理多个线程，它们执行这些运算的速度显著快于 CPU。
- 大型数据集：在训练过程中，深度学习模型通常需要大量的数据。GPU 能够更快速地分析这些海量数据集，从而使训练过程更加高效。
- 高精度：启用 CUDA 的图形处理器（GPU）可以执行高精度的算术运算，这对于防止深度学习模型训练过程中的数值不稳定性至关重要。

#### CUDA 与 PyTorch 的结合

PyTorch 与 CUDA 的集成是其深受深度学习社区欢迎的主要原因之一。这种结合的优势如下：

- 无缝集成：PyTorch 提供了无缝的 CUDA 集成。开发人员只需对代码进行少量修改，即可将计算移至 GPU，从而利用 CUDA 的并行计算能力。
- GPU 加速的张量：PyTorch 的基本数据结构——张量，与 GPU 兼容。存储在 GPU 上的 CUDA 张量可以加速操作，从而实现更高效的计算。
- 多 GPU 支持：PyTorch 还通过 CUDA 支持多 GPU 设置。这允许跨多个 GPU 并行化计算，进一步加速训练过程。
- GPU 上的自动求导：PyTorch 的自动求导引擎（为其自动微分和梯度计算提供动力）也与 CUDA 无缝协作，确保反向传播（神经网络训练的基石）受益于 GPU 加速。

简而言之，在深度学习项目中使用 CUDA 可以显著加速训练过程，从而实现更快的模型开发和迭代。CUDA 与 PyTorch 的结合为开发人员提供了一个强大的平台，使他们能够更高效地构建和训练复杂的深度学习模型。随着我们继续探索 PyTorch 2.0，我们将了解如何执行这些 GPU 加速操作，并构建充分利用 NVIDIA CUDA 平台强大功能的模型。

### 在 Linux 上设置 PyTorch 2.0 和 CUDA 11.8




## 第 1 章：深度学习、PyTorch 2.0 与 CUDA 11.8 基础

在开始之前，您必须知道，为了使用 CUDA，您需要一台安装了 NVIDIA GPU 的计算机。根据您使用的特定 Linux 发行版，操作方法可能也会略有不同。

我们将概述一般流程如下：

### 更新系统

首先，更新系统总是一个好主意。打开终端并输入：

```
sudo apt-get update
sudo apt-get upgrade
```

### 安装必要的依赖

接下来，安装一些必要的依赖：

```
sudo apt-get install build-essential dkms
sudo apt-get install freeglut3 freeglut3-dev libxi-dev libxmu-dev
```

### 验证支持 CUDA 的 GPU

要验证您是否拥有支持 CUDA 的 GPU，请使用以下命令：

```
lspci | grep -i nvidia
```

如果您看到输出，说明您拥有支持 CUDA 的 GPU。

### 下载并安装 CUDA 11.8

前往 NVIDIA CUDA 下载页面。选择“Linux”，然后根据您的 Linux 发行版、架构、发行版版本和安装程序类型选择适当的选项（我建议使用 `.run` 文件）。然后点击“下载”按钮下载 CUDA 11.8 工具包。

下载完成后，导航到包含 `.run` 文件的目录，然后运行以下命令来安装 CUDA：

```
sudo chmod +x cuda_11.8.0_*.run
sudo ./cuda_11.8.0_*.run
```

按照屏幕上的说明完成安装。确保在提示时安装 NVIDIA 驱动程序。

### 设置环境变量

接下来，您需要将 CUDA 添加到 `PATH` 中。将这些行添加到您的 `~/.bashrc` 文件中：

```
export PATH=/usr/local/cuda-11.8/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-11.8/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

然后，使用以下命令加载 `~/.bashrc` 文件：

```
source ~/.bashrc
```

### 验证安装

要验证安装，请使用以下命令：

```
nvcc -V
```

如果 CUDA 安装正确，您应该看到“Cuda compilation tools, release 11.8, V11.8.xxxxx”的字样。

### 安装 PyTorch 2.0

现在，我们将安装 PyTorch 2.0。首先，我们建议创建一个 Python 虚拟环境以避免包冲突。使用以下命令：

```
sudo apt-get install python3-venv
python3 -m venv pytorch_env
source pytorch_env/bin/activate
```

您应该在命令提示符的开头看到 `(pytorch_env)`，表明您已进入虚拟环境。

现在，使用 `pip` 安装 PyTorch：

```
pip install torch==2.0.0
```

### 验证 PyTorch 和 CUDA 集成

最后，为了验证 PyTorch 已正确安装并且能够访问 CUDA，请运行 Python 解释器并输入：

```
import torch
torch.cuda.is_available()
```

如果一切安装正确，它应返回 `True`，表明 PyTorch 可以通过 CUDA 访问您的 GPU。在后续章节中，我们将深入探讨如何使用这个强大的环境来构建和训练您的深度学习模型。

### 总结

在本开篇章节中，我们为理解深度学习、神经网络、PyTorch 2.0 和 CUDA 11.8 奠定了基础。我们首先全面概述了神经网络，重点介绍了其由神经元和层组成的核心结构。我们深入探讨了它们在深度学习中的重要作用，即促进从海量数据中学习并执行复杂的计算。神经网络的强大之处在于它们能够从数据中学习表示并做出预测，这是深度学习的基石。

接着，我们介绍了 PyTorch 2.0，这是一个广泛使用的深度学习框架，以其灵活性、用户友好的接口和高效的计算能力而闻名。PyTorch 2.0 延续了其传统，同时引入了众多增强功能。其主要特性包括：增强的 TorchScript 以实现更灵活的编程模型、通过 TorchServe 改进模型部署、更好的移动端支持、全面的量化支持、用于提高代码可读性的命名张量，以及扩展的工具和库生态系统。

最后，我们讨论了 CUDA 对深度学习的重要性，它通过利用 NVIDIA GPU 的并行计算能力，可以显著加速训练过程。我们还强调了 CUDA 与 PyTorch 的无缝融合，能够实现高效计算和快速模型训练。在本章结尾，我们逐步介绍了在 Linux 平台上搭建 PyTorch 2.0 和 CUDA 11.8 环境的过程。这一搭建过程使开发者能够在深度学习项目中充分利用 GPU 加速运算的力量，为后续章节深入探讨实际应用奠定基础。

## 第 2 章：张量入门

### 深入了解张量

在深度学习中，张量是向量和矩阵向更高维度的推广，是 PyTorch 中的基本数据结构。张量是线性代数中使用的一种数据结构，与向量和矩阵类似，你可以对张量进行算术运算。

张量是 PyTorch 中的核心数据单元，以多维数组的形式表示。张量的维度可以用秩、形状和大小来描述。

- **秩**：它简单地告诉我们张量中的维度数量。标量的秩为 0，向量的秩为 1，矩阵的秩为 2，而张量的秩为 3 或更高。

- **形状**：张量的形状是每个维度中的元素数量。

- **大小**：张量中元素的总数，可以通过形状各维度元素数量的乘积来计算。

在 PyTorch 中，张量允许在 GPU 上执行操作，这可以显著加速计算。它们与 NumPy 的 `ndarray` 类似，区别在于张量也可以用于 GPU 加速计算。

### 不同类型的张量

PyTorch 提供了多种函数来创建不同类型的张量。以下是一些示例：

- **空张量**：`torch.empty(size)`：返回一个指定大小的张量，其中填充了未初始化的数据。这里，`size` 是一个定义张量维度的元组。

- **零张量**：`torch.zeros(size)`：返回一个用零填充的张量。

- **全 1 张量**：`torch.ones(size)`：返回一个用 1 填充的张量。

- **随机张量**：`torch.rand(size)`：返回一个填充了来自 [0, 1) 区间均匀分布的随机数的张量。

### 张量术语与概念

张量是标量、向量和矩阵的多维推广，是流行的深度学习框架 PyTorch 功能的关键。掌握与张量相关的概念是充分发挥 PyTorch 全部威力的重要一步，因为这些数据结构对于在深度学习中高效执行计算至关重要。

#### 标量

标量是张量中最简单的类型，只包含一个元素，没有维度。在 PyTorch 框架中，标量可以表示为 `torch.tensor(5)`。这是一个零维张量，类似于几何中的点——有位置，但没有大小。

#### 向量

向量则是张量中的一维张量，类似于几何中的线。PyTorch 中向量的一个示例是 `torch.tensor([1, 2, 3, 4])`。该张量只有一个轴，因此具有范围或长度，每个元素对应于该轴上的一个点。

#### 矩阵

随着复杂度的提升，矩阵是一个二维张量，既有行又有列。在 PyTorch 中，它可以表示为 `torch.tensor([[1, 2], [3, 4]])`。矩阵可以被看作一个数字表格或一个跨越两个方向（轴）的网格。

#### 张量运算

张量操作的一个重要方面是 PyTorch 支持的众多张量运算。这些运算涵盖了广泛的范畴，从加、减、乘、除等基本算术运算到更复杂的线性代数函数。逐元素运算、归约运算和比较运算构成了丰富的工具集，使 PyTorch 成为深度学习任务中高效且多功能的平台。

#### 广播

PyTorch 一个特别强大的机制是广播（broadcasting），该功能允许框架在算术运算中处理不同形状的数组。它将较小的数组扩展到与较大的数组匹配，从而顺利执行逐元素运算，这一特性显著提高了数组操作的灵活性和便利性。

#### 设备

最后，PyTorch 的“设备”方面确保张量可以通过 `.to` 方法无缝移动到任何设备内存中。例如，`tensor.to("cuda")` 便于将张量传输到 GPU，从而实现硬件加速计算，这对于处理深度学习巨大的计算需求至关重要。

张量是 PyTorch 的支柱，因此理解张量对于有效利用 PyTorch 框架至关重要。它们提供了深度学习算法在处理海量数据和执行复杂计算时所需的计算效率。这一基础理解为我们在后续章节中探索更高级的深度学习概念和技术奠定了基础。

### 创建张量的示例程序

我们将深入使用 PyTorch 创建张量。我们将看到如何创建空张量、用 1 填充的张量、用 0 填充的张量以及随机值张量。请注意，你必须安装 PyTorch 才能运行这些代码。

首先，我们将导入 PyTorch 库：

```
import torch
```

#### 创建空张量：

```
empty_tensor = torch.empty(3, 2)
print(empty_tensor)
```

这将创建一个形状为 3x2 的张量，其中填充了未初始化的数据。输出结果类似如下：

```
tensor([[2.1019e-44, 0.0000e+00],
        [      nan, 0.0000e+00],
        [1.3733e-14, 6.4069e+02]])
```

#### 创建用零填充的张量：

```
zero_tensor = torch.zeros(3, 2)
print(zero_tensor)
```

这将创建一个形状为 3x2 且用零填充的张量。输出结果为：

```
tensor([[0., 0.],
        [0., 0.],
        [0., 0.]])
```

#### 创建用 1 填充的张量：

```
ones_tensor = torch.ones(3, 2)
print(ones_tensor)
```

这将创建一个形状为 3x2 且用 1 填充的张量。输出结果为：

```
tensor([[1., 1.],
        [1., 1.],
        [1., 1.]])
```

#### 创建随机张量：

```
random_tensor = torch.rand(3, 2)
print(random_tensor)
```

这将创建一个形状为 3x2 的张量，其中填充了来自区间 [0, 1) 上均匀分布的随机数。输出结果类似如下：

```
tensor([[0.6022, 0.9622],
        [0.7817, 0.5994],
        [0.6712, 0.4674]])
```

这些基本的张量运算构成了在 PyTorch 中创建更复杂数据结构的构件，这对于建模神经网络和开发深度学习应用非常有帮助。

### 张量数据类型

在 PyTorch 中，张量具有与 Python 中数据类型类似的相关数据类型。该数据类型定义了张量中包含的元素种类及其可能的取值范围。

以下是一些最常用的数据类型：

- `torch.float32` 或 `torch.float`：32 位浮点数

- `torch.float64` 或 `torch.double`：64 位双精度浮点数

- `torch.float16` 或 `torch.half`：16 位半精度浮点数

- `torch.int32` 或 `torch.int`：32 位有符号整数

- `torch.int64` 或 `torch.long`：64 位有符号整数

- `torch.bool`：布尔类型

张量的默认数据类型是 32 位浮点数。你可以使用 `.to()` 方法更改张量的数据类型。

我们来看一下实际操作：

```python
#### Import PyTorch
import torch

#### Create tensor with default data type (float32)
tensor = torch.ones(3, 2)
print(tensor)
print("Data Type: ", tensor.dtype)

#### Changing tensor data type to float64
tensor = tensor.to(torch.float64)
print("\nAfter Changing Data Type to float64:")
print(tensor)
print("Data Type: ", tensor.dtype)

#### Changing tensor data type to int32
tensor = tensor.to(torch.int32)
print("\nAfter Changing Data Type to int32:")
print(tensor)
print("Data Type: ", tensor.dtype)

#### Changing tensor data type to boolean
tensor = tensor.to(torch.bool)
print("\nAfter Changing Data Type to boolean:")
print(tensor)
print("Data Type: ", tensor.dtype)
```

输出将是：

```
tensor([[1., 1.],
        [1., 1.],
        [1., 1.]])
Data Type: torch.float32

After Changing Data Type to float64:
tensor([[1., 1.],
        [1., 1.],
        [1., 1.]], dtype=torch.float64)
Data Type: torch.float64

After Changing Data Type to int32:
tensor([[1, 1],
        [1, 1],
        [1, 1]], dtype=torch.int32)
Data Type: torch.int32

After Changing Data Type to boolean:
tensor([[True, True],
        [True, True],
        [True, True]])
Data Type: torch.bool
```

值得一提的是，PyTorch 提供了一个函数来创建特定类型的张量，例如：`torch.zeros(3, 2, dtype=torch.int32)`。确保参与计算的张量具有相同的类型也至关重要，因为 PyTorch 不执行隐式类型转换。

理解并正确管理张量数据类型是在 PyTorch 中开发健壮且高效的深度学习模型的一个重要方面。

### 标准算术运算

我们将了解如何对张量执行基本的算术运算，包括加法、减法、乘法和除法运算。

首先，我们将创建两个形状相同的张量：

```python
#### Import PyTorch
import torch

#### Create two tensors
tensor1 = torch.tensor([1, 2, 3, 4], dtype=torch.float32)
tensor2 = torch.tensor([5, 6, 7, 8], dtype=torch.float32)
print("Tensor 1:", tensor1)
print("Tensor 2:", tensor2)
```

输出：

```
Tensor 1: tensor([1., 2., 3., 4.])
Tensor 2: tensor([5., 6., 7., 8.])
```

#### 加法

```python
# Addition
result = tensor1 + tensor2
print("Addition Result: ", result)
```

输出：

```
Addition Result: tensor([ 6.,  8., 10., 12.])
```

#### 减法

```python
# Subtraction
result = tensor1 - tensor2
print("Subtraction Result: ", result)
```

输出：

```
Subtraction Result: tensor([-4., -4., -4., -4.])
```

#### 乘法

```python
# Multiplication (Element-wise)
result = tensor1 * tensor2
print("Multiplication Result: ", result)
```

输出：

```
Multiplication Result: tensor([ 5., 12., 21., 32.])
```

#### 除法

```python
# Division
result = tensor1 / tensor2
print("Division Result: ", result)
```

输出：

```
Division Result: tensor([0.2000, 0.3333, 0.4286, 0.5000])
```

请注意，这些运算是逐元素进行的，即它们被应用于两个张量的对应元素上。

这些标准运算对于操作张量和实现各种数学模型至关重要，尤其是在机器学习和深度学习领域。接下来，我们将进入更复杂的操作，并探讨如何组合这些基本运算来实现更复杂的计算。

### 张量操作

在 PyTorch 中，张量操作通常涉及重塑（reshaping）、切片（slicing）和连接（joining）张量等操作。我们将深入探讨这些主题。

#### 重塑张量

重塑张量是一种常见操作，它允许我们重新组织数据，使其具有不同数量的维度或每个维度不同的大小。




我们将创建一个张量，然后对其进行重塑：

```python
#### Import PyTorch
import torch

#### Create a tensor
tensor = torch.arange(9)

print("Original Tensor:")

print(tensor)

#### Reshape the tensor

reshaped_tensor = tensor.view(3, 3)

print("\nReshaped Tensor:")

print(reshaped_tensor)
```

输出：

```
Original Tensor:
tensor([0, 1, 2, 3, 4, 5, 6, 7, 8])

Reshaped Tensor:
tensor([[0, 1, 2],
        [3, 4, 5],
        [6, 7, 8]])
```

### 连接张量

PyTorch 提供了几种组合张量的方法，例如 `torch.cat()` 和 `torch.stack()`。我们将使用 `torch.cat()` 沿给定维度连接两个张量：

```python
#### Create two tensors
tensor1 = torch.tensor([1, 2, 3])
tensor2 = torch.tensor([4, 5, 6])

#### Concatenate the tensors along dimension 0
concatenated_tensor = torch.cat((tensor1, tensor2))

print("\nConcatenated Tensor:")
print(concatenated_tensor)
```

输出：

```
Concatenated Tensor:
tensor([1, 2, 3, 4, 5, 6])
```

这些操作是张量操作的基础。掌握这些概念将使你能够有效地处理张量，并为深度学习模型准备数据。

### 矩阵乘法

在 PyTorch 中，你可以使用 `torch.matmul()` 函数或 `@` 运算符执行矩阵乘法。这两种方法都会检查张量的维度，并应用适当的乘法运算（对于一维张量进行逐元素乘法，对于二维张量进行矩阵乘法，对于三维张量进行批量矩阵乘法）。

我们将创建两个矩阵并执行矩阵乘法运算。

```python
#### Import PyTorch
import torch

#### Create two 2D tensors (matrices)
matrix1 = torch.tensor([[1, 2], [3, 4]])
matrix2 = torch.tensor([[5, 6], [7, 8]])

print("Matrix 1:")
print(matrix1)

print("\nMatrix 2:")
print(matrix2)

#### Matrix multiplication using torch.matmul()
result = torch.matmul(matrix1, matrix2)

print("\nMatrix Multiplication Result using torch.matmul():")
print(result)

#### Matrix multiplication using @ operator
result = matrix1 @ matrix2

print("\nMatrix Multiplication Result using @ operator:")
print(result)
```

输出：

```
Matrix 1:
tensor([[1, 2],
        [3, 4]])

Matrix 2:
tensor([[5, 6],
        [7, 8]])

Matrix Multiplication Result using torch.matmul():
tensor([[19, 22],
        [43, 50]])

Matrix Multiplication Result using @ operator:
tensor([[19, 22],
        [43, 50]])
```

乘法运算的结果是通过第一个矩阵的行与第二个矩阵的列的点积计算得出的。这个操作是线性代数的基础，在深度学习中经常使用，例如在将输入通过神经网络的各层传播时。

在矩阵相乘时，需要记住第二矩阵的行数必须等于第一矩阵的列数。

### 处理张量形状错误

在 PyTorch 中，处理张量形状错误通常需要理解你所执行操作的性质以及张量的维度。以下是一些可能遇到形状错误的常见情况：

如果你正在进行矩阵乘法，第一个矩阵的列数必须等于第二个矩阵的行数。如果该条件不满足，你将遇到大小不匹配的错误。

例如：

```python
matrix1 = torch.rand(2, 3)
matrix2 = torch.rand(2, 3)
result = torch.matmul(matrix1, matrix2)  # This will raise a size mismatch error
```

在上面的示例中，重塑或转置 `matrix2` 将解决该问题：

```python
matrix2 = matrix2.t()  # Transpose the matrix
result = torch.matmul(matrix1, matrix2)  # This will not raise an error
```

#### 逐元素运算

如果你正在进行逐元素运算（如加法、减法等），涉及的张量应具有相同的形状。PyTorch 确实支持广播（broadcasting，一个从 NumPy 借鉴的概念），它允许对不同大小的张量进行二元运算，但这也需要遵循一些规则。

例如：

```python
tensor1 = torch.rand(2, 3)
tensor2 = torch.rand(2, 2)
result = tensor1 + tensor2  # This will raise a size mismatch error
```

在上述情况下，确保两个张量具有相同的形状将修复该错误。

#### 重塑张量

如果你正在重塑张量，重塑操作前后的元素总数应保持不变。如果不是这样，你将遇到错误。

例如：

```python
tensor = torch.rand(2, 3)
reshaped_tensor = tensor.view(2, 4)  # This will raise an error
```

在上述情况下，确保新形状与张量中的元素数量兼容将解决问题。

每当你遇到形状错误时，请仔细检查你正在使用的张量的维度以及你正在执行的运算的要求。使用像 `.size()` 或 `.shape` 这样的方法来检查张量的大小，并在需要时使用 `view()`、`reshape()` 或 `transpose()` 来操作张量的形状。

### 聚合操作

PyTorch 中的聚合操作是指减少张量中所包含元素数量的操作。

这些包括查找元素的总和、均值、最大值或最小值等操作。

我们将创建一个张量并执行各种聚合操作：

```python
#### Import PyTorch

import torch

#### Create a tensor

tensor = torch.tensor([[1, 2, 3], [4, 5, 6]],
dtype=torch.float32)

print("Tensor:")

print(tensor)
```

输出：

```
Tensor:
tensor([[1., 2., 3.],
    [4., 5., 6.]])
```

#### 求和

查找张量中所有元素的总和：

```python
# Sum of tensor
sum_val = torch.sum(tensor)
print("\nSum of Tensor Elements: ", sum_val)
```

输出：

```
Sum of Tensor Elements: tensor(21.)
```

#### 均值

计算张量元素的均值：

```python
# Mean of tensor
mean_val = torch.mean(tensor)
print("\nMean of Tensor Elements: ", mean_val)
```

输出：

```
Mean of Tensor Elements: tensor(3.5)
```

#### 最大值

查找张量中的最大值：

```python
# Max of tensor
max_val = torch.max(tensor)
print("\nMax of Tensor Elements: ", max_val)
```

输出：

```
Max of Tensor Elements: tensor(6.)
```

#### 最小值

查找张量中的最小值：

```python
# Min of tensor
min_val = torch.min(tensor)
print("\nMin of Tensor Elements: ", min_val)
```

输出：

```
Min of Tensor Elements: tensor(1.)
```

这些操作通常在机器学习中用于诸如归一化、查找最大预测值等任务。能够对张量执行聚合操作是在使用 PyTorch 时的一项关键技能。

### 总结

在本章中，我们深入探讨了 PyTorch 的基本构建块：张量。我们首先了解了张量是什么、其重要性，以及它们如何成为 PyTorch 和深度学习中操作的基石。张量本质上是对矩阵向多维的推广，并且是 PyTorch 中使用的主要数据结构。它们类似于 NumPy 的 ndarrays，但增加了 GPU 支持。

然后我们探索了创建和操作张量。我们了解了如何实例化各种类型的张量，如零张量、单位张量或随机张量，以及如何指定其数据类型。我们学习了张量的操作，其中包括重塑、切片和连接张量，所有这些对于机器学习工作流中的数据预处理和转换都是必不可少的。然后我们学习了在张量上执行基本算术运算、矩阵乘法以及广播的概念，该概念允许我们在不同形状的张量之间执行运算。

最后，我们深入探讨了处理张量形状错误的问题，这是使用基于张量的计算时常见的挑战。我们了解到，了解张量的维度和我们正在执行的运算的要求对于防止和解决此类错误至关重要。我们还介绍了张量的聚合操作，例如查找张量元素的总和、均值、最大值或最小值。这些操作在各种机器学习任务中都是基础性的。

## 第 3 章：高级张量操作

### 高级张量操作概述

操纵和管理张量的能力是使用 PyTorch 和其他类似深度学习框架的基础。张量是我们在 PyTorch 中所做一切的核心，并用于编码模型的输入和输出以及模型的参数。

### 重塑

重塑张量是指在保持底层数据不变的情况下改变其维度的过程。它类似于重新排列数据的布局而不改变数据点本身。在为某些类型的模型准备数据时，这种技术变得非常有用，因为不同的模型需要不同维度的输入。例如，卷积神经网络通常期望 4D 张量作为输入 - 表示为 `(Batch Size x Channels x Height x Width)`。在这种情况下，如果原始数据为 2D 格式 `(Height x Width)`，重塑可以将它转换为所需的 4D 格式，而不会丢失或改变任何数据。

### 查看

查看是 PyTorch 中张量管理的另一个关键方面。`view()` 函数主要用于重塑张量，类似于 `reshape()` 函数的操作方式。然而，`view()` 具有一个独特功能，即可以根据其他维度的大小自动推断一个维度的正确大小。当一个维度的大小已知，但需要 PyTorch 计算其他维度的大小时，此功能特别有益。这种推断功能简化了重塑过程，使其更高效且不易出错。

### 堆叠

堆叠是管理张量的另一种技术。堆叠允许我们沿着新的维度组合多个张量，从而创建更高维度的张量。它经常用于创建输入或目标的批次，但也可用作连接结果的通用工具。例如，如果需要将一组张量合并为单个张量，则可以使用 `stack()` 函数。此操作有效地像堆叠煎饼一样堆叠输入张量，从而在过程中创建新的维度。例如，堆叠三个 2D 张量将得到一个 3D 张量。

理解这些操作中的每一个以及何时使用它们对于开发深度学习模型至关重要。它可以大大加快数据准备过程，使代码更易读，并有助于避免后续的错误或问题。这些操作为我们提供了处理各种不同任务所需的灵活性，因此它们是任何 PyTorch 开发人员工具箱的重要组成部分。

### 更改张量形状

在 PyTorch 中，`reshape()` 用于在不改变其数据的情况下更改张量的形状。此操作通常用于当你想要重新排列数据的维度以匹配模型的输入期望时。

```python
#### Import PyTorch

import torch

#### Create a tensor

tensor = torch.arange(1, 9)

print("Original Tensor:")

print(tensor)

#### Reshape the tensor
reshaped_tensor = tensor.reshape(2, 4)

print("\nReshaped Tensor:")

print(reshaped_tensor)
```

输出：

```
Original Tensor:
tensor([1, 2, 3, 4, 5, 6, 7, 8])

Reshaped Tensor:
tensor([[1, 2, 3, 4],
    [5, 6, 7, 8]])
```

### 查看张量维度

`view()` 函数与 `reshape()` 类似，但它作为原地操作运行，并且可以使用 `-1` 推断维度的大小。如果张量不是连续的，你可能需要使用 `reshape()` 或在调用 `view()` 之前调用 `contiguous()`。

```python
# View the tensor

viewed_tensor = tensor.view(2, 4)

print("\nViewed Tensor:")

print(viewed_tensor)
```

输出：

```
Viewed Tensor:
tensor([[1, 2, 3, 4],
    [5, 6, 7, 8]])
```

### 堆叠张量序列

`stack()` 函数用于沿新维度连接一系列张量。所有张量需要具有相同的大小。

```python
#### Create two tensors

tensor1 = torch.tensor([1, 2, 3])

tensor2 = torch.tensor([4, 5, 6])

# Stack the tensors

stacked_tensor = torch.stack((tensor1, tensor2))

print("\nStacked Tensor:")

print(stacked_tensor)
```

输出：

```
Stacked Tensor:
tensor([[1, 2, 3],
    [4, 5, 6]])
```

这些高级张量操作对于在 PyTorch 中有效地管理和操作数据至关重要。理解这些操作将使你能够以与模型兼容的方式构建数据。

### 压缩张量

`squeeze()` 函数会移除张量中长度为 1 的维度或轴。此操作可用于将某个维度长度为 1 的二维张量转换为一维张量，或在批量大小为 1 时移除不需要的维度。

```python
# Create a tensor of size (1,3)

tensor = torch.zeros((1, 3))

print("Original Tensor:")

print(tensor)

print("Shape:", tensor.shape)

# Squeeze the tensor

squeezed_tensor = tensor.squeeze()

print("\nSqueezed Tensor:")
print(squeezed_tensor)
print("Shape:", squeezed_tensor.shape)
```

输出：

```
Original Tensor:
tensor([[0., 0., 0.]])

Shape: torch.Size([1, 3])

Squeezed Tensor:
tensor([0., 0., 0.])

Shape: torch.Size([3])
```

### 解压缩张量

`unsqueeze()` 是 `squeeze()` 的逆操作。它在张量中指定位置添加一个长度为 1 的维度。这通常用于增加数据的维度，以满足模型的输入要求。

```python
# Unsqueeze the tensor

unsqueezed_tensor = squeezed_tensor.unsqueeze(dim=0)

print("\nUnsqueezed Tensor:")

print(unsqueezed_tensor)

print("Shape:", unsqueezed_tensor.shape)
```

输出：

```
Unsqueezed Tensor:
tensor([[0., 0., 0.]])

Shape: torch.Size([1, 3])
```

### 置换张量

`permute()` 函数根据指定的输入重新排列张量的原始维度。它常用于更改维度或轴的顺序。

```python
# Create a tensor of size (2, 3, 4)

tensor = torch.zeros((2, 3, 4))

print("\nOriginal Tensor Shape:", tensor.shape)

# Permute the dimensions of the tensor

permuted_tensor = tensor.permute(2, 0, 1)

print("Permuted Tensor Shape:", permuted_tensor.shape)
```

输出：

```
Original Tensor Shape: torch.Size([2, 3, 4])

Permuted Tensor Shape: torch.Size([4, 2, 3])
```



在上面的`permute`示例中，原始张量的维度为`(2, 3, 4)`，对应索引`(0, 1, 2)`。我们将张量置换为新维度`(4, 2, 3)`，因此原始的第三维（大小为 4）现在成为第一维，原先的第一维成为第二维，原先的第二维成为第三维。

理解这些张量运算对于处理多维数据并确保其符合模型的特定输入要求至关重要。

## 对张量进行索引和选择数据

对张量进行索引和选择数据是使用 PyTorch 时的一项基本操作，其过程与标准 Python 列表或 NumPy 数组的索引方式非常相似。此操作使用方括号`[]`来访问张量中的特定元素或数据子集。

要选择张量中的特定元素，可以使用整数索引。例如，如果`x`是一维张量，可以使用`x[0]`选择第一个元素。类似地，`x[-1]`会选择最后一个元素。对于多维张量，可以使用逗号分隔的索引元组。如果`y`是二维张量，`y[1,2]`将返回第二行第三列的元素。

我们将通过一些示例继续：

```python
# Import PyTorch
import torch
```

```python
# Create a tensor
tensor = torch.tensor([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

print("Original Tensor:")
print(tensor)
```

输出：

```text
Original Tensor:
tensor([[1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]])
```

### 索引张量

你可以根据索引访问张量中的特定元素。请记住，在 Python 中索引从 0 开始：

```python
# Get the element at row 1, column 2
element = tensor[1, 2]

print("\nElement at Row 1, Column 2: ", element)
```

输出：

```text
Element at Row 1, Column 2: tensor(6)
```

### 切片张量

你还可以使用切片选择一系列元素：

```python
# Get the elements in row 0 and 1
rows = tensor[0:2]

print("\nElements in Row 0 and 1:")
print(rows)
```

输出：

```text
Elements in Row 0 and 1:
tensor([[1, 2, 3],
        [4, 5, 6]])
```

### 选择特定索引

对于更复杂的选择，你可以使用`index_select()`方法按特定索引选择数据：

```python
# Create an index tensor
indices = torch.tensor([0, 2])

# Select rows at indices 0 and 2
selected_rows = tensor.index_select(0, indices)

print("\nSelected Rows at Indices 0 and 2:")
print(selected_rows)
```

输出：

```text
Selected Rows at Indices 0 and 2:
tensor([[1, 2, 3],
        [7, 8, 9]])
```

在`index_select()`函数中，第一个参数是进行索引的维度（在二维张量中，0 表示行，1 表示列），第二个参数是包含索引的张量。

这些张量索引操作在处理机器学习数据时至关重要，它们使您能够选择和操作数据集中的特定部分。

### 在 GPU 和 CPU 之间切换访问

在 PyTorch 中，张量可以位于 CPU 或 GPU 上，通过`.to()`方法可以在两者之间切换。在深入探讨细节之前，我们先讨论为什么需要这样做。

### 选择访问的必要性

在 CPU 和 GPU 之间切换的主要原因在于你所执行的计算类型。GPU 非常适合涉及大量数据的计算（例如深度学习中的计算），因为它可以同时执行许多计算。另一方面，CPU 更适合需要较少数据但更复杂或条件操作的任务。通过允许你在 CPU 和 GPU 之间切换，PyTorch 让你能够编写可在不同硬件上运行并针对其特定优势进行优化的代码。

以下是如何使用`.to()`方法的示例：

```python
# Import PyTorch
import torch

# Create a tensor
tensor = torch.tensor([1, 2, 3])

print("Original tensor:")
print(tensor)

# Check the current device of the tensor
print("\nTensor is on: ", tensor.device)

# Move the tensor to GPU if available
if torch.cuda.is_available():
    tensor = tensor.to('cuda')

print("\nMoved tensor:")
print(tensor)
print("Tensor is on: ", tensor.device)
```

在上述示例程序中，我们首先在 CPU（默认设备）上创建一个张量。然后使用`torch.cuda.is_available()`检查 GPU 是否可用。如果 GPU 可用，我们使用`.to('cuda')`将张量移动到 GPU。

设备无关代码意味着代码无需修改即可在任何设备上运行。以下是一个如何在 PyTorch 中实现这一点的示例：

```python
# Define the device
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

# Create a tensor directly on the target device
tensor = torch.tensor([1, 2, 3], device=device)

print("Tensor is on: ", tensor.device)
```

通过在脚本开头定义设备，并在创建张量时使用它，你可以确保代码在可用时运行在 GPU 上，否则回退到 CPU。这使你的代码与设备无关，因为它可以利用任何可用的硬件而无需修改。

### 总结

在本章中，我们深入探讨了在 PyTorch 中操作和管理张量的高级操作。第一部分介绍了张量的重塑（reshape）、查看（view）和堆叠（stack）。重塑允许我们在不修改底层数据的情况下更改张量的形状，而查看提供了类似的功能，并能够使用 -1 推断维度大小。堆叠将一系列张量沿新维度拼接，前提是所有张量大小相同。这些操作对于在 PyTorch 中有效管理数据至关重要，帮助我们将数据结构化以与模型兼容。

接下来，我们讨论了张量的压缩（squeeze）、解压缩（unsqueeze）和置换（permute）。压缩会移除长度为 1 的维度，在批量大小为 1 时通常有助于去除不需要的维度。相反，解压缩会在指定位置添加长度为 1 的维度，常用于满足模型的输入要求。置换用于根据指定的输入重新排列原始张量的维度，常用于调整维度或轴（axes）的顺序。在处理多维数据时，理解这些操作至关重要，这能确保数据符合我们模型的特定输入要求。

最后几节向我们介绍了张量索引、选择以及与设备无关的编码。PyTorch 中的张量索引和选择遵循与 Python 列表和 NumPy 数组类似的原理，使我们能够操作和选择数据集中的特定部分。我们学习了使用方括号进行索引和切片，以及使用`index_select()`方法进行更复杂的选择。我们还讨论了在 CPU 和 GPU 之间切换的必要性，并介绍了`.to()`方法。与设备无关的代码可以在不同的硬件上运行，并针对其特定优势进行优化。通过在脚本开头定义设备，我们的代码可以无需修改即可利用任何可用的硬件。这种灵活性对于机器学习至关重要，因为不同环境中的计算资源可能差异很大。

# 第4章：使用 PyTorch 2.0 构建神经网络

## PyTorch NN 模块概览

本章深入探讨 PyTorch 的`nn`模块——这是构建神经网络至关重要的模块。作为 PyTorch 用于神经网络的核心包，`nn`依赖`autograd`来定义和计算梯度，使其非常灵活且直观。

`nn`的核心是层，它们本质上是一些简单的数学函数，通过结构化方式从数据中学习。典型的神经网络由一系列层组成，每一层将前一层的输出作为其输入。例如，一个简单的全连接（或稠密）层，也称为线性层，对其输入应用线性变换，而卷积层则应用卷积操作。`nn`模块包含多种层，如`nn.Linear`、`nn.Conv2d`和`nn.MaxPool2d`等等。

激活函数是神经网络的另一个基本组成部分。它们为网络引入非线性属性，使其能够从复杂数据中学习。如果没有激活函数，神经网络将仅仅是线性回归模型，无法从错综复杂的模式中学习。常见的激活函数包括 ReLU（修正线性单元）、Sigmoid 和 Tanh。在 PyTorch 中，它们分别以`nn.ReLU`、`nn.Sigmoid`和`nn.Tanh`形式直接可用。

损失函数（也称为代价函数）衡量网络预测值与实际值之间的差距。在训练过程中，目标是使该损失最小化。不同类型的损失函数适用于不同类型的任务。例如，均方误差（`nn.MSELoss`）通常用于回归问题，而交叉熵损失（`nn.CrossEntropyLoss`）用于多类分类问题。

为你的网络架构选择合适的层、激活函数和损失函数组合，是深度学习项目成功的关键。做出这些选择通常需要结合领域知识、直觉和经验测试。PyTorch 的`nn`模块提供丰富多样的层和工具，能够帮助你构建几乎任何神经网络架构，从简单的线性模型到像 Transformer 或循环网络这样的复杂结构。通过充分理解和利用`nn`模块的能力，你可以有效地驾驭深度学习的力量。

## 理解前馈网络

### 概述

前馈网络，通常简称为神经网络，构成了许多现代机器学习模型的骨干。它们被称为“前馈”，是因为信息在网络中沿一个方向流动：从输入层，经过任意数量的隐藏层，到达输出层。信息不会在网络中循环回流，这使它们区别于允许这种循环的循环神经网络。

一个基本的前馈网络至少包含三种类型的层：接收初始数据的输入层；一个或多个隐藏层，实际处理通过加权连接系统在其中进行；以及产生最终结果的输出层。每一层由多个神经元（也称为节点）组成，并且一层中的每个神经元都与前一层和下一层中的所有神经元相连。神经网络的“深度”是指它拥有的隐藏层数量。

### 前馈网络的优势

前馈网络的主要优势之一是能够建模复杂的非线性关系。通过一个称为“反向传播”的过程以及损失函数的优化来调整连接的权重和偏置，前馈网络可以学习其输入和输出之间的非线性关系。这是将神经网络与更简单的线性模型区分开来的主要特征。

前馈网络也非常灵活，可以适应许多类型的预测建模问题。它们可以用于多种任务，如图像分类、语音识别、自然语言处理，甚至游戏对弈。这种灵活性还扩展到处理不同类型的数据，包括文本、图像、声音和数值数据。

此外，前馈网络可用于在隐藏层中学习数据的表示，这些表示随后可用于降维或探索性数据分析。这一特性在无监督学习中非常有用，其目标是发现数据中固有的结构。

前馈网络还受益于计算资源和技术的持续进步。GPU 和 TPU 等硬件加速器的发展大大提高了训练大型深层神经网络的速度和效率。此外，随机梯度下降（SGD）、RMSProp 和 Adam 等优化技术使训练过程更加高效。

然而，尽管有这些优点，前馈网络确实也存在一些局限性。它们需要大量的数据和计算资源才能有效训练，尤其是当网络的规模和复杂性增加时。此外，模型的“黑箱”特性使其难以解释如何得出特定输出，这在可解释性很重要的场景中可能会带来问题。

总而言之，前馈网络是机器学习工具箱中的强大工具。它们能够建模复杂的非线性关系，并具有适应广泛任务和数据类型的灵活性。尽管存在局限性，它们已在无数实际应用中证明了自己的价值，使其成为现代机器学习中不可或缺的资产。

### 使用 PyTorch 构建多层感知机

在 PyTorch 中创建前馈网络（也称为多层感知机或 MLP）的过程涉及几个步骤。下面，我们将逐步讲解这些步骤，详细说明网络的每个部分是如何构建和组合在一起的：

1. 导入必要的库：首先，你需要导入 PyTorch 和`torch.nn`模块，其中包含神经网络所需的构建模块。

```python
import torch
from torch import nn
```

2. 定义网络架构：为了定义前馈网络，我们对`nn.Module`（PyTorch 中所有神经网络模块的基类）进行子类化。在我们的新类中，我们在构造函数中定义网络的层，并在`forward`方法中指定数据应如何通过网络传递。

以下是一个带有一个隐藏层的简单前馈网络示例：

```python
class FeedforwardNetwork(nn.Module):

    def __init__(self, input_size, hidden_size, output_size):
        super(FeedforwardNetwork, self).__init__()
        self.hidden = nn.Linear(input_size, hidden_size) # Hidden layer
        self.relu = nn.ReLU()  # Non-linear activation function
        self.output = nn.Linear(hidden_size, output_size) # Output layer

    def forward(self, x):
        out = self.hidden(x)
        out = self.relu(out)
        out = self.output(out)
        return out
```

在此网络中，`input_size`是输入数据中的特征数量，`hidden_size`是隐藏层中的神经元数量，`output_size`是输出层中的神经元数量（对于分类任务，它应与类别数量匹配；对于回归任务，则应为 1）。

3. 实例化网络：一旦定义了网络架构，你就可以通过提供所需的维度来创建网络实例。

```python
input_size = 10  # for example
hidden_size = 50  # for example
output_size = 1  # for example

model = FeedforwardNetwork(input_size, hidden_size, output_size)
```

4. 定义损失函数和优化器：下一步是定义损失函数和优化器。损失函数用于衡量网络预测值与实际值之间的差距。优化器用于调整网络的权重以最小化损失。

```python
criterion = nn.MSELoss()  # for example
optimizer = torch.optim.Adam(model.parameters())
```

5. 训练网络：最后，你可以使用训练数据来训练网络。在每个 epoch（对训练数据的完整遍历）中，模型会进行预测、计算损失并更新权重。

```python
for epoch in range(num_epochs):
    # Forward pass
    outputs = model(inputs)
    loss = criterion(outputs, labels)

    # Backward and optimize
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()
```

### 理解循环神经网络

循环神经网络（RNN）是一类专门设计用于处理序列数据的神经网络。与前馈网络独立处理输入不同，RNN 具有内部循环，允许信息从序列中的一个步骤传递到下一个步骤。这种持久化信息的能力使其非常适合处理时间序列数据、自然语言处理、语音识别等任务。

为了更深入理解，RNN 引入了隐藏状态的概念，用于保存序列中过去输入的信息。在序列的每一步中，隐藏状态会根据当前输入和先前的隐藏状态进行更新。这使得网络能够保留序列中较早的信息，并利用这些信息影响后续的输出。理论上，RNN 可以记住过去任意时间点的信息。然而，在实践中，由于梯度消失问题，RNN 难以维持长期依赖关系——当梯度随时间反向传播时，损失函数的梯度会变得越来越小。这会使网络难以从许多时间步之前发生的经验中学习。

RNN 有一些专门的变体，例如长短期记忆（LSTM）单元和门控循环单元（GRU），它们具有缓解这些问题并处理更长序列的机制。这些机制允许模型根据需要学习保留或遗忘信息，从而使它们在学习长期依赖关系方面更加有效。将 RNN 与前馈网络进行比较，RNN 在处理序列数据方面具有明显优势。前馈网络缺乏处理时间相关数据的能力，因为它们独立地考虑每个输入。相比之下，RNN 可以通过在模型的不同部分共享参数来处理序列数据。这使它们能够对时间动态进行建模，从而更适合语言建模、时间序列预测和序列生成等任务。

然而，需要注意的是，由于其递归特性，RNN 的训练可能比前馈网络更复杂且计算量更大。此外，对于非序列数据或计算资源有限的情况，前馈网络通常是更好的选择。从更广泛的意义上讲，RNN 在处理序列数据方面具有独特的优势，使其成为许多机器学习应用中的强大工具。然而，与所有模型一样，它们也有自己的优点和缺点，模型的选择应取决于手头的具体任务。

### 在 PyTorch 中创建 RNN

在 PyTorch 中创建循环神经网络（RNN）与创建前馈网络非常相似，但有一些特定差异，这些差异反映了 RNN 的时间特性。

以下是在 PyTorch 中创建简单 RNN 的分步过程：

1. 导入必要的库：和往常一样，你需要导入 PyTorch 和`torch.nn`模块。

```python
import torch
from torch import nn
```

2. 定义网络架构：要定义 RNN，你同样需要继承`nn.Module`。在你的新类中，在构造函数中定义网络的层，并在`forward`方法中指定数据应如何通过网络。

以下是一个简单 RNN 的示例：

```python
class SimpleRNN(nn.Module):
    def __init__(self, input_size, hidden_size, output_size):
        super(SimpleRNN, self).__init__()
        self.hidden_size = hidden_size
        self.rnn = nn.RNN(input_size, hidden_size, batch_first=True)
        self.fc = nn.Linear(hidden_size, output_size)

    def forward(self, x):
        # x shape: (batch, seq_len, input_size)
        out, hidden = self.rnn(x)
        # out shape: (batch, seq_len, hidden_size)
        out = self.fc(out[:, -1, :])
        return out
```

在这个网络中，`input_size`是输入序列中每个时间步的特征数量，`hidden_size`是隐藏状态的大小，`output_size`是输出层的神经元数量。`batch_first=True`使输入和输出的形状为`(batch, seq_len, feature)`，更符合常见的习惯。



```python
class SimpleRNN(nn.Module):

    def __init__(self, input_size, hidden_size, output_size):
        super(SimpleRNN, self).__init__()
        self.rnn = nn.RNN(input_size, hidden_size, batch_first=True)
        self.fc = nn.Linear(hidden_size, output_size)

    def forward(self, x):
        out, _ = self.rnn(x)
        out = self.fc(out[:, -1, :])
        return out
```

在此网络中，`input_size` 是输入数据中的特征数量，`hidden_size` 是隐藏状态中的特征数量，`output_size` 是输出特征的数量。在 `out, _ = self.rnn(x)` 这一行，序列数据被传递到 RNN 层。`PyTorch` 会自动将隐藏状态初始化为零，因此无需手动初始化。在 `out = self.fc(out[:, -1, :])` 这一行，最后一个隐藏状态被传递到全连接层以生成输出。

- 实例化网络：创建 RNN 实例的方式与前馈网络相同：

```python
input_size = 10  # for example
hidden_size = 20  # for example
output_size = 1  # for example

model = SimpleRNN(input_size, hidden_size, output_size)
```

- 定义损失函数和优化器：选择方式与前馈网络相同。

```python
criterion = nn.MSELoss()  # for example
optimizer = torch.optim.Adam(model.parameters())
```

- 训练网络：训练网络涉及的步骤与前馈网络相同：进行预测、计算损失和更新权重。

```python
for epoch in range(num_epochs):
    # Forward pass
    outputs = model(inputs)
    loss = criterion(outputs, labels)

    # Backward and optimize
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()
```

创建 RNN 与前馈网络之间的关键区别在于网络架构的定义。在 RNN 中，我们使用 `nn.RNN` 创建一个循环层，该层会考虑数据的序列特性。RNN 还需要处理隐藏状态，隐藏状态代表了网络的“记忆”。与前馈网络不同，RNN 使用先前的输入来影响当前的预测，这对于涉及序列数据的任务至关重要。

然而，值得注意的是，这是一个非常简单的 RNN，并未考虑 RNN 中常见的长期依赖问题。对于能够处理这些问题的更复杂模型，你可以考虑使用长短期记忆（LSTM）或门控循环单元（GRU），两者都可以在 PyTorch 的 `nn` 模块中找到。

### 探索门控循环单元（GRU）

#### 概述

门控循环单元（GRU）是一种循环神经网络架构，旨在解决传统 RNN 中存在的梯度消失问题。该问题使 RNN 难以维持和学习序列中的长期依赖关系。GRU 由 Kyunghyun Cho 等人于 2014 年提出，比另一种解决梯度消失问题的架构——长短期记忆（LSTM）更简单，但在某些任务中表现出了相当的性能。

GRU 引入了与 LSTM 类似的门控机制概念。这些机制是控制网络中信息流动的一种方式，但与 LSTM 使用的三个门相比，GRU 使用两个门：

- 更新门（`z`）：该门决定丢弃哪些信息以及添加哪些新信息。它是当前记忆和新输入之间的混合。

重置门 (`r`)：该门用于决定忘记多少过去的信息。

这两个门都被训练用来选择性地过滤通过它们的信息，使用 sigmoid 激活函数输出 0 到 1 之间的值，表示保留或忘记的信息量。GRU 维护一个与 RNN 类似的隐藏状态，但它使用这些门控单元来控制该隐藏状态的更新。这有助于在长序列中保留信息，从而使模型能够更好地捕捉数据中的依赖关系。

### GRU 的优势

GRU 相较于标准 RNN 的主要优势在于其更好地处理序列数据中长期依赖关系的能力。这使得它们在涉及序列数据的任务中更有效，这些任务中过去许多时间步可能包含重要信息，例如时间序列分析、自然语言处理和语音识别。

另一个优势是，由于复杂度降低，GRU 通常比 LSTM 更高效地训练，同时往往能达到相当的性能。这使得它们在计算资源或数据有限时成为一个不错的选择。

综上所述，GRU 是一种有效且流行的循环神经网络类型，能够处理长序列数据，是许多序列预测任务的良好选择。与其他架构相比，它们在有效性能和降低复杂性方面的结合，使其成为深度学习领域中流行的选择。

### 创建门控循环单元（GRU）。

在 PyTorch 中构建门控循环单元（GRU）模型的过程与我们之前讨论的简单 RNN 类似。

下面是逐步讲解：

#### 导入必要的库

首先，你需要导入 PyTorch 和 `torch.nn` 模块。

```python
import torch
from torch import nn
```

#### 定义网络架构

PyTorch 中 GRU 模型的架构可以通过继承 `nn.Module` 类来定义。

以下是一个简单的 GRU 示例：

```python
class GRUModel(nn.Module):
    def __init__(self, input_size, hidden_size, output_size, num_layers):
        super(GRUModel, self).__init__()
        self.hidden_size = hidden_size
        self.num_layers = num_layers
        self.gru = nn.GRU(input_size, hidden_size, num_layers, batch_first=True)
        self.fc = nn.Linear(hidden_size, output_size)
    def forward(self, x):
        h0 = torch.zeros(self.num_layers, x.size(0), self.hidden_size).to(x.device)
        out, _ = self.gru(x, h0)
        out = self.fc(out[:, -1, :])
        return out
```

在此网络中，`input_size` 是输入数据中的特征数，`hidden_size` 是隐藏状态中的特征数，`output_size` 是输出特征数，`num_layers` 是 GRU 中的层数。

行 `out, _ = self.gru(x, h0)` 是序列数据通过 GRU 层的位置。初始隐藏状态 `h0` 手动初始化为零。

行 `out = self.fc(out[:, -1, :])` 是最后一个隐藏状态通过全连接层生成输出的位置。

#### 实例化网络

创建 GRU 实例的方式与其他模型相同：

```python
input_size = 10 # for example
hidden_size = 20 # for example
output_size = 1 # for example
num_layers = 2 # for example
model = GRUModel(input_size, hidden_size, output_size, num_layers)
```

#### 定义损失函数和优化器

它们的选择方式与其他网络相同。

```python
criterion = nn.MSELoss()  # for example
optimizer = torch.optim.Adam(model.parameters())
```

#### 训练网络

训练网络涉及与其它网络相同的步骤：进行预测、计算损失并更新权重。

```python
for epoch in range(num_epochs):
```

### 前向传播

```python
outputs = model(inputs)
loss = criterion(outputs, labels)
```

#### 反向传播并优化

```python
optimizer.zero_grad()
loss.backward()
optimizer.step()
```

你应该记住，GRU 与其他 RNN 一样，使用序列进行工作。这表明输入必须是三维张量。该张量的维度分别为批大小、序列长度和特征数，分别对应其相应的概念。为了实现这一点，在构建 GRU 层的过程中使用了 `batch_first=True` 选项。

### 理解卷积神经网络

#### 概述

卷积神经网络（CNNs）是一类神经网络，在图像识别和分类等领域已被证明非常有效。它们被设计用来模仿人类大脑中神经元的连接模式，并在识别人脸、物体和交通标志方面取得了很大成功，除此之外还为机器人和自动驾驶汽车提供视觉功能。

CNN 的“神经元”按三维排列：宽度、高度和深度。某一层的神经元仅连接到其前一层的某个小区域，称为感受野。靠近输入层的层学习识别简单模式，如线条和曲线。网络中更深层的层将这些简单模式组合起来识别更复杂的模式，如形状，甚至更进一步是物体。

#### CNN 的优势

CNN 在分析视觉数据方面特别出色，因此与图像和视频处理密切相关。以下是使 CNN 如此吸引人的关键属性和优势：

- 参数共享：一个在图像某一部分有用的特征检测器（如垂直边缘检测器）很可能在图像的其他部分也有用。这大幅减少了模型中的参数数量，使其不太可能过拟合、计算更高效且对内存要求更低。

- 局部连接：在 CNN 中，神经元之间并非完全连接，而是仅连接到下一层中一小部分神经元。这反映了人类视觉系统中神经元的连接方式：视网膜中的神经元仅连接到视觉皮层中一小部分神经元。

- 平移不变性：由于参数共享，网络具有平移不变性，意味着它可以识别视觉场中任何位置出现的物体。训练用于识别图像右侧猫的 CNN 也能识别左侧的猫。

需要了解的是，CNN 不一定比 RNN 或 GRU“更好”，但它们服务于不同的目的。虽然 CNN 在空间处理（如图像）方面表现出色，但 RNN 和 GRU 是为时间处理（如时间序列数据或语言）而设计的。最佳架构通常取决于所处理数据的性质和结构。话虽如此，它们的 capabilities 存在重叠，有时你会看到它们一起使用，例如使用 CNN 从图像中提取特征，然后将这些特征输入 RNN 进行图像描述。

### 创建卷积神经网络（CNN）。

在 PyTorch 中创建卷积神经网络（CNN）模型涉及多个步骤，与创建 GRU 或任何其他神经网络类似。以下是逐步讲解：

#### 导入必要的库

首先，你需要导入 PyTorch 和 `torch.nn` 模块。

```python
import torch
from torch import nn
```

#### 定义网络架构

PyTorch 中 CNN 模型的架构可以通过继承 `nn.Module` 类来定义。

以下是一个用于图像分类的简单 CNN 示例：

```python
class CNN(nn.Module):
    def __init__(self):
        super(CNN, self).__init__()
        self.conv1 = nn.Conv2d(1, 6, 5) # 1 input image channel, 6 output channels, 5x5 square convolution kernel
        self.pool = nn.MaxPool2d(2, 2) # Max pooling over a (2, 2) window
        self.conv2 = nn.Conv2d(6, 16, 5) # 6 input image channel, 16 output channels, 5x5 square convolution kernel
```

```
self.fc1 = nn.Linear(16 * 5 * 5, 120) # an affine operation: y = Wx + b

self.fc2 = nn.Linear(120, 84)

self.fc3 = nn.Linear(84, 10)

def forward(self, x):
    x = self.pool(F.relu(self.conv1(x)))
    x = self.pool(F.relu(self.conv2(x)))
    x = x.view(-1, 16 * 5 * 5)  # reshape before passing to fully connected layer
    x = F.relu(self.fc1(x))
    x = F.relu(self.fc2(x))
    x = self.fc3(x)
    return x
```

### 前向传播

```
outputs = model(inputs)

loss = criterion(outputs, labels)

# Backward and optimize

optimizer.zero_grad()

loss.backward()

optimizer.step()
```

请记住，在这种情况下，CNN 的输入是一个四维张量，其形状为（批次大小、通道数、高度、宽度）。前面的代码假设输入是由形状为（高度、宽度）的灰度图像组成的，因此只有一个输入通道。如果你处理的是彩色照片，则需要三个输入通道：一个用于红色，一个用于绿色，一个用于蓝色（也写作 RGB）。

### 结合 RNN 与 CNN

CNN 和 RNN 本身都是强大的模型，但将它们结合起来，可以发挥两种模型类型的优势，取得令人印象深刻的结果。由此产生的模型通常被称为卷积循环神经网络（Convolutional Recurrent Neural Network，CRNN）。CNN 擅长从图像等数据中提取空间特征，而 RNN 擅长从序列数据中学习，因此它们非常适合时间序列分析或自然语言处理。当这两种模型结合时，产生了一个能够有效处理同时涉及空间和时间依赖关系的任务的模型。

在典型的 CRNN 中，CNN 作为特征提取器，将输入转换为高层次表示。然后，这个表示被馈送到 RNN，由 RNN 处理问题的序列方面。例如，在计算机视觉领域，CRNN 可用于视频分类任务。CNN 组件可以处理单个帧以提取空间特征，而 RNN 可以利用这些帧的时间序列来理解跨帧发生的运动或变化。

在自然语言处理中，CRNN 的一个常见应用是图像字幕生成。CNN 处理图像并捕获其特征，然后 RNN 使用这些特征生成描述性字幕。

以下是一个 CRNN 可能的示例：

```
class CRNN(nn.Module):

    def __init__(self):

        super(CRNN, self).__init__()

        self.cnn = nn.Sequential(

            nn.Conv2d(1, 16, kernel_size=3, stride=1,
            padding=1),

            nn.ReLU(),

            nn.MaxPool2d(kernel_size=2, stride=2),

            nn.Conv2d(16, 32, kernel_size=3, stride=1,
            padding=1),

            nn.ReLU(),

            nn.MaxPool2d(kernel_size=2, stride=2)

        )

        self.rnn = nn.GRU(input_size=32*7*7,
        hidden_size=50, num_layers=2, batch_first=True)

        self.fc = nn.Linear(50, 10)  # 10 output classes

    def forward(self, x):

        batch_size = x.size(0)

        x = self.cnn(x)

        x = x.view(batch_size, -1, 32*7*7)  # Reshape before passing to RNN

        out, _ = self.rnn(x)

        out = self.fc(out[:, -1, :])  # Output of last time step
        return out
```

在这段代码中，一个两层 CNN 用于从输入图像中提取特征。然后将 CNN 的输出重塑并馈送到 GRU（一种 RNN 变体）。最后一个线性层产生分类输出。总而言之，CRNN 将 CNN 的空间特征提取能力与 RNN 的序列学习能力相结合，使其成为处理涉及空间和时间依赖关系的任务的强大模型。

现在，我们将继续训练 CRNN 模型。训练 CRNN 模型的过程与在 PyTorch 中训练任何其他神经网络模型非常相似。以下是具体做法：

定义损失函数和优化器：这些与其他模型的选择方式相同。例如：

```
criterion = nn.CrossEntropyLoss()

optimizer = torch.optim.Adam(model.parameters())
```

训练网络：训练网络涉及对轮次（epoch）进行循环、做出预测、计算损失并更新模型参数。



```
num_epochs = 100 # example value

for epoch in range(num_epochs):
    for i, (images, labels) in enumerate(train_loader):
        # Forward pass
        outputs = model(images)
        loss = criterion(outputs, labels)
        # Backward and optimize
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
```

```
total = 0

for images, labels in test_loader:
    outputs = model(images)
    _, predicted = torch.max(outputs.data, 1)
    total += labels.size(0)
    correct += (predicted == labels).sum().item()
print('Test Accuracy of the model on the test images: {} %'.format(100 * correct / total))
```

在这段给定的代码中，`test_loader` 是另一个加载测试数据的 `DataLoader` 实例。

这是一个简单的演示，在现实场景中可能还有其他复杂情况。数据可能需要预处理或增强，模型可能需要正则化以防止过拟合，学习率可能需要随时间调整等。然而，这个示例程序应该能为训练 CRNN 模型提供一个坚实的起点。

### 设计自定义层的必要性

在深度学习中设计自定义层和网络可以带来几个优势，特别是任务特定性、研究潜力和效率。这些方面中的每一个都有助于使自定义设计方法在各种场景中成为一种可行且往往有益的方式。

任务特定性在人们选择自定义层和网络的原因中起着关键作用。深度学习模型需要处理的各种任务无法全部使用标准层和架构来高效解决。有些任务需要独特的方法，可能需要特殊操作或现成架构中不可用的特定层排列。例如，您可能需要实现一个具有非标准激活函数的层，或者一个以独特方式整合不同类型数据的网络。在这种情况下，自定义层或网络变得不可或缺，使得能够创建有效满足这些特定需求的模型。

从研究的角度来看，新层和架构的开发是深度学习探索的基本组成部分。研究人员经常提出新技术来提升模型性能或解决该领域的特定挑战。实现这些新颖的想法往往需要创建自定义层或网络。如果您正在尝试一种新技术或新架构，几乎可以肯定您需要设计自定义元素来实现您的理论概念。

最后，自定义方法有时可以比标准替代方案带来更高效的解决方案。这里的效率既可以指计算资源，也可以指模型中的参数数量。自定义层或网络可以以优化资源使用的方式进行设计，可能带来更快的训练时间或更少的内存使用。在参数数量方面，自定义设计可能允许更紧凑的模型，这在存储空间或计算能力有限的情况下（如移动设备或嵌入式系统）尤其有利。

### 设计自定义层

要在 PyTorch 中将这些自定义层或网络变为现实，通常需要创建一个继承自 `nn.Module`（PyTorch 所有神经网络模块的基类）的类。在这个类内部，定义了 `forward` 方法，它概述了层或网络的前向传播。这就是您详细说明输入数据如何转换为输出数据的地方，基本上决定了层或网络的行为。重要的是要记住，虽然 PyTorch 会自动计算梯度以促进反向传播，但 `forward` 方法是您需要指定层或网络显式操作的地方。

我们将看一个简单的自定义层示例：

```
class MyLayer(nn.Module):

    def __init__(self):

        super(MyLayer, self).__init__()

        self.weight = nn.Parameter(torch.randn(1), requires_grad=True)

    def forward(self, x):
```

```
return x * self.weight
```

在上述代码中，`MyLayer` 是一个自定义层，它通过一个可训练权重对输入进行缩放。`nn.Parameter` 是一种特殊类型的张量，它会自动被包含在 `nn.Module` 的参数列表中。这意味着 PyTorch 会将这个权重视为模型的可训练参数。

现在，我们将定义一个使用该自定义层的自定义网络：

```
class MyNetwork(nn.Module):
    def __init__(self):
        super(MyNetwork, self).__init__()
        self.layer1 = MyLayer()
        self.layer2 = MyLayer()
    def forward(self, x):
        x = self.layer1(x)
        x = self.layer2(x)
        return x
```

`MyNetwork` 是一个自定义网络，它对输入依次应用两次 `MyLayer`。请注意，这些层在 `__init__` 方法中定义，并在 `forward` 方法中应用。

从更广泛的意义上讲，在 PyTorch 中设计自定义层和网络是一种灵活且强大的工具，它让你能够实现任何你能想象到的架构。无论你是在应用标准技术，还是在发明新技术，PyTorch 的灵活性都使其成为深度学习研究和开发的绝佳选择。

### 总结

总体而言，本章深入探讨了 PyTorch 的 `nn` 模块的功能，详细介绍了如何利用它来创建各种类型的神经网络。本章第一部分向你介绍了前馈网络的概念。前馈网络是许多其他类型神经网络的基础，数据沿一个方向流动——从输入到输出。它们已被广泛应用于众多场景，并具有简单且可解释性强的优点。

接下来，我们进入了循环神经网络（RNN）的领域。RNN 通过考虑数据的时间序列维度，为前馈网络增添了新的维度。这使得它们能够捕获随时间变化的模式，从而在时间序列分析、自然语言处理等领域尤为有用。我们还了解了如何在 PyTorch 中创建 RNN，演示了定义和训练这些网络是多么简单。本章随后介绍了更高级的 RNN 类型，即 GRU 和 CNN。门控循环单元（GRU）通过缓解梯度消失问题改进了传统 RNN，使其能够更好地捕获长期依赖关系。另一方面，卷积神经网络（CNN）凭借其从输入图像中提取高级特征的能力，在图像处理任务中表现出色。我们逐步演示了如何在 PyTorch 中创建这些模型，展示了整个过程是多么直接。

本章最后讨论了将 RNN 和 CNN 组合到单一模型中（CRNN），以及如何在 PyTorch 中设计自定义层和网络。PyTorch 的灵活性使我们能够创建新的架构，以专门满足特定任务的独特需求。我们了解到，可以通过扩展 `nn.Module` 类并定义自定义的 `forward` 前向传播方法来构建这些自定义模型。所有这些主题旨在让你全面理解 PyTorch 的能力和潜力，为你应对广泛的深度学习任务做好准备。

## 第 5 章 在 PyTorch 2.0 中训练神经网络

### 神经网络训练概述

训练机器学习模型涉及学习一组最优权重，以便在给定数据的情况下做出最佳预测。这是通过一个称为优化的过程实现的。训练过程是迭代式的，通常涉及前向传播、反向传播和权重更新等步骤。我们将更深入地探讨以下步骤：

前向传播是将输入数据传入网络以生成预测的过程。神经网络使用权重（在开始时随机初始化）来计算输出。例如，在一个简单的线性回归问题中，前向传播将涉及使用权重和输入 `x` 值来计算预测的 `y` 值。

在前向传播之后，下一步是计算损失。损失函数衡量网络预测值与实际值之间的差异。它提供一个数值，表示预测中存在的误差大小。常见的损失函数包括用于回归问题的均方误差、用于分类问题的交叉熵损失等。训练的目标是最小化这个损失值。

反向传播：反向传播（backward pass）是神经网络训练中发生“魔法”的步骤。反向传播算法通过应用链式法则，计算损失函数相对于网络中每个权重的梯度。本质上，它确定了每个权重对整体误差的贡献程度。

权重更新：一旦我们知道每个权重对误差的贡献程度，就可以调整权重以最小化损失。这通常使用优化算法来完成。最常见的优化器是随机梯度下降（`SGD`）。`SGD` 沿着梯度的反方向以一小步更新权重。这有助于减少损失。其他流行的优化器包括 `Adam`、`RMSProp` 等，它们会动态调整学习率以加速收敛。

轮次（Epochs）与批次（Batches）：前向传播、反向传播和权重更新的整个过程会在多个周期（称为轮次）中迭代进行。为了加速训练并更好地利用计算资源，数据通常被划分为较小的批次。

前向传播和反向传播是在每个批次上进行的，而不是在整个数据集上，并且权重会在每个批次之后更新。

多年来，人们对这些步骤进行了许多改进和变体。例如，`Adam` 和 `RMSProp` 等先进优化技术会在训练过程中自适应调整学习率。Dropout 和 Batch Normalization 等正则化技术也常用于训练过程中，以防止过拟合并帮助模型更好地泛化。简而言之，深度学习中的训练过程是前向传播、计算损失、反向传播和权重更新之间一场错综复杂的协作。这是一种系统且迭代的方法，用于教导神经网络做出准确的预测，其驱动力来自优化的力量和反向传播的微积分原理。

### PyTorch `optim` 模块

PyTorch 的 `optim` 模块包含了多种可用于训练神经网络的优化算法。这些算法至关重要，因为它们会影响训练的速度和质量。优化器的选择会影响模型收敛的速度，甚至决定其能否收敛。

PyTorch `optim` 模块中的所有优化器类都继承自基类 `torch.optim.Optimizer`。该类提供了基础功能，包括管理待优化参数、状态和超参数。每个优化器算法都利用这些功能，并在其 `step()` 方法中实现具体的优化策略，该方法执行单次优化步骤（即参数更新）。

#### 使用优化器

要在 PyTorch 中使用优化器，你首先需要实例化所选优化器类，传入待优化模型的参数以及必要的超参数（如学习率）。在计算梯度之后，调用 `optimizer.step()` 即可更新参数。

例如：

```
# 定义模型
model = torch.nn.Linear(10, 5)

# 定义优化器
optimizer = torch.optim.Adam(model.parameters(), lr=0.001)

# 训练步骤
for input, target in dataset:
    optimizer.zero_grad()
    output = model(input)
    loss = loss_fn(output, target)
    loss.backward()
    optimizer.step()
```

在上面的代码片段中，首先使用 `optimizer.zero_grad()` 将模型的梯度清零，以确保不会使用过时的梯度。然后，在通过 `loss.backward()` 计算出梯度后，优化器使用 `optimizer.step()` 基于这些梯度执行参数更新。

总体而言，PyTorch 的 `optim` 模块提供了广泛的优化算法，有助于高效地训练神经网络。

### 优化算法

优化算法对于训练机器学习模型至关重要。它们是用于改进模型性能的迭代方法，通过调整模型参数以最小化代价函数（也称为损失函数）来实现。

以下是几种最常见的优化算法的概述：

梯度下降：这是优化算法最基本的形式。它计算损失函数关于参数空间中当前位置参数的梯度，然后沿最陡下降方向移动。步长由学习率决定。该过程不断重复，直到算法收敛到局部最小值。

随机梯度下降（`SGD`）：这是梯度下降的一种变体，它在训练数据集中每计算一个样本的损失后就更新参数，而不是在整个数据集上计算。它在优化过程中引入了随机性，并且更容易逃离较浅的局部最小值。

小批量梯度下降：这是批量梯度下降和随机梯度下降之间的一种折衷。它将训练数据集分成小的子集或“小批量”。模型参数在计算每个小批量的损失后进行更新。这可以减少梯度估计中的噪声，并加快训练过程。

动量：这是一种用于加速`SGD`的方法。它计算梯度的指数加权平均值来更新参数，这可以帮助算法更快地收敛并避免局部最小值。

`Adagrad`：该算法根据梯度的历史为每个参数自适应调整学习率，这使得它非常适合处理稀疏数据。

`RMSProp`：这是对 `Adagrad` 的一种改进，解决了其学习率急剧下降的问题。它使用平方梯度的移动平均值来对梯度本身进行归一化。

`Adam`（自适应矩估计）：这是目前最流行的优化算法之一。它结合了动量和 `RMSProp` 的思想。它为不同参数计算自适应学习率，并像动量一样保存过去梯度的指数衰减平均值。

这些算法各有优缺点，优化算法的选择会显著影响最终模型的质量。某些算法可能更适合特定类型的数据或模型，选择正确的算法是模型设计过程中的重要组成部分。总的来说，`Adam` 通常是深度学习应用的不错选择，因为它在效率和易用性之间取得了平衡。

#### 梯度下降

梯度下降是最基本的优化算法形式。它通过沿最陡下降方向（即梯度的负方向）迭代移动来最小化代价函数。学习率决定了这些步骤的大小。

在机器学习的背景下，代价函数表示模型预测与实际数据之间的误差。梯度下降的目的就是调整模型参数，使这个误差最小化。

该算法可以总结如下：

-   计算代价函数关于参数集中每个参数的梯度。

    -   在神经网络的背景下，梯度是使用反向传播计算的。

-   通过从当前参数值中减去学习率乘以梯度来更新每个参数。

    -   重复上述步骤，直到算法收敛到局部最小值。

学习率是一个至关重要的超参数。如果它太小，模型将收敛得很慢。如果它太大，模型可能会跳过最小值，甚至可能发散。

#### 使用梯度下降

在 PyTorch 中，梯度下降和其他优化算法在 `torch.optim` 模块中实现。

下面是一个如何使用它的示例：

```
# Define a simple linear model
model = torch.nn.Linear(10, 5)

# Define the loss function
loss_fn = torch.nn.MSELoss()

# Define the optimizer
optimizer = torch.optim.SGD(model.parameters(),
lr=0.01)

# Example data
input = torch.randn(10,)
target = torch.randn(5,)
```

```
# Training loop
for i in range(100):
    # Compute the predicted output
    output = model(input)
    # Compute the loss
    loss = loss_fn(output, target)
    # Zero the gradients
    optimizer.zero_grad()
    # Compute the gradients
    loss.backward()
    # Update the parameters
    optimizer.step()
```

在训练循环中，调用 `optimizer.zero_grad()` 来清零梯度，因为 PyTorch 默认会累积梯度。`loss.backward()` 计算梯度，`optimizer.step()` 根据这些梯度更新模型参数。

#### 随机梯度下降

随机梯度下降（`SGD`）是梯度下降算法的一种变体，它不是在整个数据集上计算（这是标准（或“批量”）梯度下降的基础），而是基于数据的小子集（或“小批量”）来计算梯度并更新权重。

这有几个关键优势：

-   计算效率：它可以使大规模、计算密集型模型变得可行，因为每一步训练只需将一小部分数据加载到内存中。

-   频繁更新：频繁的更新可以更快地收敛到损失函数的最小值。

-   噪声：带有噪声的更新过程可能具有正则化效果，有助于模型避免过拟合。

然而，`SGD` 也有其缺点，比如更新过程中可能存在显著噪声，以及难以选择合适的小批量大小。

#### 使用随机梯度下降

在 PyTorch 中，`SGD` 也是 `torch.optim` 模块的一部分。

下面是一个示例，展示如何修改之前的示例以使用 `SGD`：

```
# Define a simple linear model
model = torch.nn.Linear(10, 5)

# Define the loss function
loss_fn = torch.nn.MSELoss()

# Define the optimizer - using SGD this time
optimizer = torch.optim.SGD(model.parameters(),
lr=0.01)

# Example data
input = torch.randn(100, 10)
target = torch.randn(100, 5)

# Training loop
for i in range(100):
    for j in range(input.shape[0]):
        # Compute the predicted output
        output = model(input[j])
        # Compute the loss
        loss = loss_fn(output, target[j])
        # Zero the gradients
        optimizer.zero_grad()
        # Compute the gradients
        loss.backward()
        # Update the parameters
        optimizer.step()
```

在上面的演示中，对 `j` 的循环表示遍历小批量。为简单起见，我们使用了批量大小为 1。在实际应用中，您可能会使用更大的批量大小，例如 32 或 64。

#### 小批量梯度下降



小批量梯度下降（MBGD），正如其名称所暗示，是批量梯度下降和随机梯度下降之间的一种折衷。在 MBGD 中，数据集被分成指定大小的小批量，每个小批量用于计算损失函数的梯度。

小批量梯度下降的优点如下：

- 计算效率：与批量梯度下降不同，MBGD 不需要将整个数据集放入内存，这使得它非常适合大型数据集。
- 降噪：与 SGD 不同，小批量内样本的平均值降低了梯度的噪声。
- 向量化：大多数现代计算库和硬件（如 GPU）可以利用向量化操作，这通常比执行大量较小的计算更高效。

## 使用小批量梯度下降

下面是一个很好的演练，展示如何修改之前的示例以使用小批量：

```python
model = torch.nn.Linear(10, 5)

# Define the loss function
loss_fn = torch.nn.MSELoss()

# Define the optimizer - still using SGD
optimizer = torch.optim.SGD(model.parameters(), lr=0.01)

# Example data
input = torch.randn(100, 10)
target = torch.randn(100, 5)

# Define the batch size
batch_size = 10

# Training loop
for i in range(100):
    for j in range(0, input.shape[0], batch_size):
        # Compute the predicted output
        output = model(input[j:j+batch_size])
        # Compute the loss
        loss = loss_fn(output, target[j:j+batch_size])
        # Zero the gradients
        optimizer.zero_grad()
        # Compute the gradients
        loss.backward()
        # Update the parameters
        optimizer.step()
```

在上述演示中，`j`循环以`batch_size`为步长递增，对每个小批量取输入数据和目标数据的一个切片。实际上，在每个 epoch 开始时，你也希望对输入数据进行洗牌，以确保模型不会从样本的顺序中学习到任何信息。

## 动量

动量是一个源自物理学的概念，已被巧妙地应用于优化算法领域以加速学习过程。动量的思想很简单：运动中的物体倾向于保持其轨迹，除非受到外力的作用。这一原理被应用于机器学习中的优化过程，以有效引导优化器，确保更平滑、更快速地收敛到损失函数的全局最小值。

在优化的上下文中，动量通过将上一时间步的一部分更新向量带到当前时间步发挥作用。这种机制有助于优化器更有效地沿相关方向移动，从而减轻不必要的振荡。动量项有效地充当了之前梯度的记忆，有助于通过减弱梯度方向的快速变化来引导优化过程。动量可以成为优化中的一种强有力工具，尤其是在曲率较高、梯度虽小但一致或梯度噪声较大的情况下。高曲率可能导致梯度方向快速变化，使优化过程剧烈振荡并可能错过最优解。虽小但一致的梯度可能导致向最优解的缓慢收敛。噪声会引入随机性，使优化器更难找到最优解。

在每种情况下，动量都可以显著提供帮助。它会增加梯度在同一方向上持续指向的维度的更新，加速这些维度的收敛。同时，它会减少梯度方向频繁变化的维度的更新，有助于抑制振荡。这种双重作用有助于使优化器的轨迹更直接、更不易振荡，从而实现更快的收敛并可能获得更好的解。

### 使用 SGD 时的动量

在 PyTorch 中向我们的 SGD 优化器添加动量与在实例化优化器时添加一个额外参数一样简单。

我们将看看在实践中它是什么样的：

```python
# Define a simple linear model
model = torch.nn.Linear(10, 5)

# Define the loss function
loss_fn = torch.nn.MSELoss()

# Define the optimizer - SGD with momentum
optimizer = torch.optim.SGD(model.parameters(), lr=0.01, momentum=0.9)

# Example data
input = torch.randn(100, 10)
target = torch.randn(100, 5)

# Define the batch size
batch_size = 10

# Training loop
for i in range(100):
    for j in range(0, input.shape[0], batch_size):
        # Compute the predicted output
        output = model(input[j:j+batch_size])
        # Compute the loss
        loss = loss_fn(output, target[j:j+batch_size])
        # Zero the gradients
        optimizer.zero_grad()
        # Compute the gradients
        loss.backward()
        # Update the parameters
        optimizer.step()
```

在上面的示例中，`momentum=0.9`表示上一步的梯度占动量的 90%，这可以被视为梯度对之前梯度的一种记忆。然后当前梯度被加到这个 90% 的累积梯度上，结果用于更新参数。这一概念可以帮助 SGD 穿越峡谷，即表面在某一维度比另一维度弯曲更陡峭的区域，这些区域在局部最优值附近很常见。在这些情况下，带动量的 SGD 会在峡谷的斜坡上振荡，同时在底部朝着局部最优值缓慢进展。

## 自适应梯度算法

自适应梯度算法，或 Adagrad，是一种值得注意的优化算法，旨在灵活地为各个参数调整学习率。这种差异化适应对于处理稀疏数据特别有益，因为它可以确保即使在面对出现频率低的特征时，优化过程仍然稳健。

Adagrad 的运行原理是并非所有参数对更新的敏感度相同。在数据稀疏且特征出现不均匀的高维空间中，一些参数可能与频繁出现的特征相关，而另一些则与不频繁的特征相关。Adagrad 通过对与频繁出现特征相关的参数进行较小的更新，而对与不频繁特征相关的参数进行较大的更新，巧妙地解决了这种差异。这种个性化处理有助于提升模型的性能，尤其是在涉及稀疏数据集的上下文中。

Adagrad 的一个独特特点在于其调整学习率的方法。它维护所有过去平方梯度的累积记录，并将其用作学习率的缩放因子。特征出现的频率越高，累积的梯度越大，因此有效学习率越小。这确保了与频繁特征相关的参数不会剧烈波动，从而提供稳定的学习过程。

然而，这种累积方法也存在潜在的缺点。由于所有过去的平方梯度都会无限制地累积，在长时间的训练中总和可能变得很大，导致有效学习率过小。这种学习率的快速衰减可能在长时间运行的任务中过早地停滞学习过程，使 Adagrad 在某些深度学习应用中不太适用。

### 使用 Adagrad 算法

以下是 PyTorch 中使用 Adagrad 优化器的示例：

```python
# Define a simple linear model
model = torch.nn.Linear(10, 5)

# Define the loss function
loss_fn = torch.nn.MSELoss()

# Define the optimizer - Adagrad
optimizer = torch.optim.Adagrad(model.parameters(), lr=0.01)

# Example data
input = torch.randn(100, 10)
target = torch.randn(100, 5)

# Define the batch size
batch_size = 10

# Training loop
for i in range(100):
    for j in range(0, input.shape[0], batch_size):
        # Compute the predicted output
        output = model(input[j:j+batch_size])
        # Compute the loss
        loss = loss_fn(output, target[j:j+batch_size])
        # Zero the gradients
        optimizer.zero_grad()
        # Compute the gradients
        loss.backward()
        # Update the parameters
        optimizer.step()
```

在上面的示例程序中，使用`torch.optim.Adagrad`实例化 Adagrad 优化器。与 SGD 类似，Adagrad 优化器的主要参数是要优化的参数集合，它还接受学习率（`lr`）作为可选参数。

## 自适应矩估计

自适应矩估计（Adam）是一种流行的优化算法，用于训练许多类型的深度学习模型。Adam 结合了来自两个其他流行算法的元素：`AdaGrad`，可处理稀疏梯度；以及 RMSProp，可处理非平稳（即快速变化）的目标。

名称“Adam”源自“adaptive moment estimation”，该算法旨在为不同参数计算单独的自适应学习率。它计算梯度和平方梯度的指数移动平均值，而参数`beta1`和`beta2`控制这些移动平均值的衰减率。

Adam 的主要优点包括：

- 易于实现。
- 计算效率高，内存需求小。
- 对梯度的对角线重缩放不变。
- 适用于数据或参数规模大的问题。
- 适用于非平稳目标。
- 在梯度非常嘈杂或稀疏的问题上表现良好。
- 提供一定的正则化效果。

现在，我们将看一个在 PyTorch 中使用 Adam 优化器的示例：

```python
# Define a simple linear model
model = torch.nn.Linear(10, 5)

# Define the loss function
loss_fn = torch.nn.MSELoss()

# Define the optimizer - Adam
optimizer = torch.optim.Adam(model.parameters(), lr=0.001)

# Example data
input = torch.randn(100, 10)
target = torch.randn(100, 5)

# Define the batch size
batch_size = 10

# Training loop
for i in range(100):
    for j in range(0, input.shape[0], batch_size):
        # Compute the predicted output
        output = model(input[j:j+batch_size])
        # Compute the loss
        loss = loss_fn(output, target[j:j+batch_size])
        # Zero the gradients
        optimizer.zero_grad()
        # Compute the gradients
        loss.backward()
        # Update the parameters
        optimizer.step()
```

在上面的示例程序中，使用`torch.optim.Adam`实例化 Adam 优化器。与之前的优化器一样，Adam 优化器的主要参数是要优化的参数。此外，Adam 优化器接受学习率（`lr`）作为可选参数，如果未提供则默认为`0.001`。

## 摘要

在本章中，我们深入了解了 PyTorch 中的训练过程，主要关注前向传播和反向传播的概念、权重更新以及 PyTorch `optim`模块中可用的不同优化技术。我们首先概述了训练过程，该过程涉及将输入数据通过模型正向传播（前向传播）、计算损失，并更新模型权重以最小化该损失（反向传播和权重更新）。该过程会迭代重复，直到模型表现令人满意为止。

然后我们探索了 PyTorch 的`optim`模块，该模块提供了常用优化算法的实现。该模块至关重要，因为它抽象了优化技术的复杂性，从而使我们能够专注于构建和训练模型。我们讨论了优化算法的概念，优化算法对于更新模型的参数和降低机器学习模型中的损失函数至关重要。我们的研究引出了各种优化技术，从梯度下降开始，梯度下降是最基本且最广泛使用的优化算法。然后我们讨论了随机梯度下降（SGD）和小批量梯度下降，这两者都是原始梯度下降算法的变体，旨在使计算更高效且更具噪声，从而实现更稳健的收敛。动量是我们引入的另一个概念，它通过沿相关方向导航来加速 SGD，并在无关方向上减弱振荡。

随后，我们探索了自适应梯度算法（Adagrad），该算法根据每个参数调整学习率，对不频繁的参数进行较大更新，对频繁的参数进行较小更新。之后，我们深入研究了自适应矩估计（Adam）优化算法，它是 RMSprop 与带动量的随机梯度下降的结合。它为模型中的每个权重自适应学习率，这在处理噪声问题上的稀疏梯度时尤其有帮助。这些技术每一种都通过代码示例进行了演示，展示了如何使用 PyTorch 实现它们。总体而言，本章提供了对 PyTorch 中模型训练过程和优化技术的全面理解。

# 第 6 章：PyTorch 2.0 高级

## 概述

在本章中，我们深入探讨模型序列化和优化这一高级主题，这是实际机器学习应用中的基本实践。

## 模型序列化

模型序列化在机器学习模型生命周期中发挥着至关重要的作用，使模型的完整状态能够转换为可保存、可传输和可重新加载的格式。这种全面的表示包括定义模型及其当前状态的各个方面，确保模型可以被恢复并在保存时完全按原样使用。

序列化期间封装的关键元素包括模型架构——定义模型结构蓝图的架构，包括层及其相互连接。这种设计对于描述模型如何处理输入并产生输出至关重要。另一个保留的重要元素是模型参数——模型在训练期间学习到的权重和偏置。这些参数是模型学习的精髓，定义了模型如何进行预测或决策。优化器状态也被保存，其中包括当前学习率和其他优化器特定参数（如 SGD 中的动量）等详细信息。这些参数对于从中断处继续训练过程至关重要。

最后，模型状态的任何其他变量，例如当前轮数或性能指标，也会被序列化。这种全面的保存确保了训练或推理的顺利恢复，不会丢失任何上下文或信息，使模型序列化成为机器学习模型管理中的一个重要过程。

## 模型优化

模型优化是部署机器学习模型的关键步骤，特别旨在提高推理阶段的效率和性能。该过程采用多种技术，旨在减少模型的尺寸，即其内存占用，并降低推理时间。更小的内存占用使模型更易于管理，允许将其部署在存储能力有限的设备上，例如移动设备或嵌入式设备。此外，它还能加快模型加载时间，有助于提高效率。

优化还旨在减少模型生成预测所需的时间，即推理时间。更快的推理时间意味着更快的响应，这对于速度至关重要的实时应用尤其有益。这可能涉及量化（降低权重的数值精度）、剪枝（移除冗余参数）和知识蒸馏（将大型模型的知识转移到小型模型）。

### 这些技术必不可少的原因有以下几点：

- 减小模型大小：通过优化模型，它变得更加紧凑，从而减少所需的存储空间。这对于部署到通常存储有限的边缘设备上尤其重要。
- 提高速度：优化后的模型可以更快地进行预测，因为它需要处理的参数更少。这导致决策更快，这是实时应用的关键标准。
- 降低能耗：计算能力越低意味着能耗越低，这是在移动设备或其他电池供电设备上部署模型时的重要因素。

简而言之，模型序列化和优化在开发高效有效的深度学习解决方案中发挥着至关重要的作用。在下一节中，我们将探讨 PyTorch 如何支持这些功能。

## 执行模型序列化

### 序列化模型

PyTorch 提供了两种主要序列化模型的方式：

`state_dict()`：此方法返回一个包含模型参数的`OrderedDict`。我们将考虑一个简单的模型：

```python
import torch
import torch.nn as nn

class SimpleModel(nn.Module):
    def __init__(self):
        super(SimpleModel, self).__init__()
        self.fc = nn.Linear(10, 10)

    def forward(self, x):
        return self.fc(x)

# Initialize the model
model = SimpleModel()

# Save model parameters
torch.save(model.state_dict(), 'simple_model.pt')
```

`torch.save`：此函数允许您保存整个模型，包括其架构，然后可以按如下方式加载：

```python
# Save the entire model
torch.save(model, 'simple_model.pth')

# Load the model
loaded_model = torch.load('simple_model.pth')
```

### 优化模型

现在我们将讨论模型优化。我们将讨论量化，这是一种优化方法。

## Quantization

PyTorch 支持动态和静态量化。以下是动态量化的示例：



```python
import torchvision.models as models
import torch.quantization as quantization

# Load pretrained ResNet model
resnet_model = models.resnet18(pretrained=True)

# Specify that we will be quantizing to int8
resnet_model.qconfig = quantization.default_qconfig

# Apply dynamic quantization
quantized_model = quantization.quantize_dynamic(
    resnet_model,
    {nn.Linear},
    dtype=torch.qint8
)
```

在上面的示例说明中，我们对预训练的 ResNet 模型应用动态量化。我们指定将量化为 `int8`，然后仅对 `nn.Linear` 层应用量化。

### Model Pruning

模型剪枝涉及消除模型中不必要的数值或权重，本质上减少了可学习参数的总数。通过移除冗余或不重要的参数，我们可以创建一个更高效的模型，同时保持相当的准确性水平。

我们将考虑一个使用 PyTorch 对预训练的 ResNet-18 模型执行模型剪枝的示例。

```python
import torch
import torch.nn as nn
import torchvision.models as models
from torch.nn.utils import prune

# Load a pretrained model
model = models.resnet18(pretrained=True)

# Pruning a specific layer (layer4[1].conv1 in this case)
parameters_to_prune = (
    (model.layer4[1].conv1, 'weight'),
)

# Using L1Unstructured method for pruning, and removing 20% of connections
prune.global_unstructured(
    parameters_to_prune,
    pruning_method=prune.L1Unstructured,
    amount=0.2,
)

# Iterating over pruned parameters to make pruning permanent
for module, parameter_name in parameters_to_prune:
    prune.remove(module, parameter_name)
```

在上面的示例程序中，我们首先加载一个预训练的 ResNet-18 模型。然后，我们选择一个特定的层进行剪枝（本例中为 `layer4[1].conv1`），使用 L1 Unstructured 剪枝方法，并根据其 L1 范数（衡量幅度的指标）移除 20% 的连接。最后，我们遍历剪枝后的参数并使用 `prune.remove` 使剪枝永久化。

需要记住，不同优化方法的影响会因具体的模型和应用而异。对一种场景最有效的方法和参数可能不是另一种场景的最佳选择。因此，通常有必要对模型进行实验和调优，以实现效率和性能之间的最佳平衡。

### Distributed Training of Deep Learning

分布式训练是指在多台机器上训练深度学习模型的做法，每台机器配备一个或多个 GPU。随着数据集和模型规模的增大，训练这些模型所需的时间也会增加。因此，为了加快训练时间，机器学习从业者通常选择分布式训练。

#### Methods of Distributed Training

分布式训练主要有两种方式：

- Data Parallelism: 在数据并行中，单个模型在多个 GPU 上复制，每个 GPU 获得一个唯一的数据批次进行前向和反向传播。然后收集各 GPU 的梯度并进行平均以更新模型权重。这是分布式训练最常见形式，当模型能够适应 GPU 内存时有效。
- Model Parallelism: 在模型并行中，模型的各部分放置在不同的 GPU 上。例如，如果你有一个具有许多层的深度神经网络，你可以将前几层放在一个 GPU 上，其余层放在另一个 GPU 上。模型并行用于模型太大而无法放入单个 GPU 内存的情况。这种方法实现起来有点棘手，因为它涉及手动将模型的不同部分分配到不同的设备。

#### Distributed Training in PyTorch

PyTorch 通过其 `torch.nn.DataParallel` 和 `torch.nn.parallel.DistributedDataParallel` 类支持分布式训练，用于数据并行。`torch.nn.DataParallel` 是一个包装器，可以将其放置在任何模块周围，使其在单台机器的多个 GPU 上并行运行。

以下是一个简短示例：

```python
model = MyModel()

if torch.cuda.device_count() > 1:
    model = nn.DataParallel(model)
```

对于多机数据并行，PyTorch 提供了 `torch.nn.parallel.DistributedDataParallel`。它比 `DataParallel` 更高效，但需要更多的设置，包括启动多个 Python 进程并提供网络地址和端口进行通信。

在 PyTorch 中，模型并行通常涉及手动工作，将模型拆分为不同的部分并使用 `.to(device)` 将它们分配到不同的设备。

分布式训练通过利用多个 GPU 有可能大幅减少训练时间，但它也会增加训练代码的复杂性，并可能导致更困难的调试情况。因此，通常只有在收益超过这些复杂性时才会考虑。

#### Using DataParallel to Perform Distributed Training

要在 PyTorch 中开始分布式训练，你需要在机器上拥有多个 GPU。PyTorch 提供了许多实用工具和类来帮助分布式训练，常见的起点是使用 `torch.nn.DataParallel`。

以下是一个如何使用 `DataParallel` 在多个 GPU 上训练模型的示例：

```python
# Import necessary modules
import torch
import torch.nn as nn
import torch.optim as optim

# Define your own model
class MyModel(nn.Module):
    def __init__(self):
        super(MyModel, self).__init__()
        self.linear = nn.Linear(10, 10)

    def forward(self, x):
        return self.linear(x)

# Check if multiple GPUs are available
if torch.cuda.device_count() > 1:
    print("Let's use", torch.cuda.device_count(), "GPUs!")
    model = MyModel()
    model = nn.DataParallel(model)

model.to('cuda')

# Your training code here
optimizer = optim.SGD(model.parameters(), lr=0.001)
criterion = nn.MSELoss()

for epoch in range(10):  # loop over the dataset multiple times
    for i, data in enumerate(trainloader, 0):
        # get the inputs; data is a list of [inputs, labels]
        inputs, labels = data[0].to('cuda'), data[1].to('cuda')
        # zero the parameter gradients
        optimizer.zero_grad()
        # forward + backward + optimize
        outputs = model(inputs)
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()
```

此脚本将自动使用机器上所有可用的 GPU。数据在批次维度上进行拆分，因此批次大小应大于使用的 GPU 数量。

然而，`DataParallel` 有其局限性，对于更复杂的情况，你可能希望转向 `DistributedDataParallel`。此 API 可以在多台机器的多个 GPU 上分配工作负载，但设置起来也更复杂。

还需要注意的是，分布式训练并不自动意味着训练更快。由于梯度需要在 GPU 之间共享和同步，因此存在通信开销，所以根据你的模型架构和批次大小，你可能看不到线性的加速。

### PyTorch Quantization API

#### Understanding Quantization

量化是一种技术，允许以低于原始数据表示的精度执行计算。量化背后的主要动机是节省内存和计算资源，使大型机器学习模型能够部署在资源有限的设备上，例如移动设备或嵌入式系统。

在深度学习上下文中，量化是减少表示神经网络权重和激活的位数数的过程。它是一种网络压缩形式，可以大幅减少神经网络的内存占用，并在具有定点运算能力的硬件上显著提高网络的计算速度。

PyTorch 的量化 API 为量化感知训练（QAT）和训练后量化（PTQ）提供了实现。量化感知训练模仿在网络前向传播过程中量化带来的影响，使网络能够学习补偿权重和激活值中的量化误差。这导致网络随后被量化时精度下降幅度要小得多。

另一方面，后训练量化是一种方法，其中模型使用传统方法训练，然后在训练后对权重进行量化。这种技术更简单、更快，但在与 QAT 相比时可能会导致精度下降更大。

### PyTorch 量化的组件

以下是 PyTorch 量化 API 的一些关键组件：

`QuantStub` 和 `DeQuantStub`：PyTorch 提供了 `QuantStub` 和 `DeQuantStub` 来标记模型中需要将数据从浮点数转换为量化表示以及反向转换的点。

量化算子：PyTorch 为许多常用算子提供了量化形式的实现，如卷积和线性层、ReLU、sigmoid 等。

`QConfig`：这是一个对象，定义了量化应如何应用于层或操作的几个重要细节。这包括量化类型（对称、非对称）、粒度（按张量、按通道）以及量化权重和激活值的方案。

`torch.quantization.prepare` 和 `torch.quantization.convert`：这些函数处理将量化应用于模型的细节。`prepare` 函数原地修改模型以使其与量化兼容，而 `convert` 函数通过将模型的权重从浮点数转换为适当的量化形式来完成量化过程。

量化感知训练（QAT）：PyTorch 还提供了对 QAT 的支持，它在训练期间模拟量化的影响。

请记住，量化经常会导致一定的精度损失，但在模型尺寸更小且运行速度更快至关重要的情况下，这种权衡可能是可以接受的。

### 为模型压缩和高效推理执行量化

我们将首先在 PyTorch 中创建一个简单模型，并对其应用后训练静态量化方法：

```
import torch

import torch.nn as nn

import torch.quantization as quantization

class SimpleModel(nn.Module):
    def __init__(self):
        super(SimpleModel, self).__init__()
        self.fc1 = nn.Linear(10, 10)
        self.relu1 = nn.ReLU()
        self.fc2 = nn.Linear(10, 2)
        self.relu2 = nn.ReLU()

    def forward(self, x):
        x = self.fc1(x)
        x = self.relu1(x)
        x = self.fc2(x)
        x = self.relu2(x)
        return x

# Create an instance of the model

model = SimpleModel()

# Set model in evaluation mode

model.eval()

# Fuse the model for better performance

model = quantization.fuse_modules(model, [['fc1', 'relu1'], ['fc2', 'relu2']])

# Specify quantization configuration

qconfig = quantization.get_default_qconfig('fbgemm')

# Prepare the model for static quantization

model.qconfig = qconfig

quantization.prepare(model, inplace=True)

# Calibrate the model with calibration data, this step is crucial to determine quantization parameters
# Assuming we have a DataLoader `calibration_loader` for calibration data

for data, labels in calibration_loader:
    model(data)

# Convert to quantized model

quantization.convert(model, inplace=True)
```

在这个简单示例中，我们创建了一个具有两个全连接层的基础神经网络，并对输出应用 ReLU 激活函数。模型首先使用 `fuse_modules` 函数进行融合，将每个操作的线性层和 ReLU 层组合成单个模块。这提高了量化模型的效率，并且是在量化之前推荐的一步。

然后我们使用 `prepare` 函数为模型准备量化。这通过在模型中插入观察器来为量化做准备，这些观察器将在校准期间观察权重和激活张量。

接下来，使用校准数据对模型进行校准。校准至关重要，因为它允许观察器确定权重和激活值的统计信息，然后这些统计信息用于确定适当的量化参数（scale 和 zero point）。

最后，我们使用 `convert` 函数将模型转换为量化模型。这用量化对应模块替换浮点模块，并将权重和激活值切换为量化等价物。

### 摘要

在本章中，我们深入探讨了 PyTorch 2.0 的高级功能，重点关注模型序列化、优化、分布式训练和 PyTorch 量化 API。

从模型序列化和优化开始，我们了解到 PyTorch 提供了强大的保存和加载模型的功能，这对于模型的中间检查点保存和最终部署都至关重要。通过序列化模型的 `state_dict`，我们可以保留学习到的参数以供以后使用或推理。另一方面，优化是关于提高模型速度和减少内存消耗。讨论了诸如模型剪枝和量化等技术，这些技术可以在性能没有显著下降的情况下大幅减少模型所需的计算资源。随后我们探讨了分布式训练，这是一种训练大型模型或处理海量数据集的重要技术。它允许我们在多个 GPU 甚至多台机器上并行化计算，从而加快训练过程。PyTorch 提供了多种促进分布式训练的方式，例如数据并行和分布式数据并行。给出了在 PyTorch 2.0 中执行分布式训练的实际示例，强调了需要遵循的关键步骤。

最后，我们讨论了 PyTorch 的量化 API，这是一个允许我们将权重和激活输出从浮点表示转换为较低位，通常是整数表示的功能。量化可以大幅减少模型的内存占用和推理所需的计算资源，这对于将模型部署到资源受限设备上尤其重要。我们学习了静态量化及其如何使用 PyTorch API 实现。在本章中，我们不断在 PyTorch 2.0 的基本原理之上构建，以探索其更高级的功能。这些知识对于开发高效的深度学习模型和系统至关重要。

## 第 7 章. 从 TensorFlow 迁移到 PyTorch 2.0

### 为什么选择 PyTorch 而非 TensorFlow？

在本章中，我们审视 TensorFlow 2.0 和 PyTorch 2.0 之间的比较分析，这两者是用于机器学习和深度学习项目最流行的开源库之一。虽然这两个库都提供了全面、灵活的平台用于开发和部署机器学习模型，但在设计理念、易用性、性能和对不同平台的支持方面存在若干差异。

TensorFlow 最初采用静态计算图范式，这意味着整个计算图必须在运行模型之前定义并编译。然而，随着 TensorFlow 2.0 的发布，引入了即时执行，使得操作可以在 Python 中调用时立即运行。这一变化使 TensorFlow 更接近 PyTorch 的动态计算图范式，其中计算会立即执行。PyTorch 的方法通常被认为更直观、更符合 Python 风格，为新手提供更平缓的学习曲线并实现更直接的调试。



PyTorch 通常因其用户友好性而受到赞赏。其动态计算图提供了更大的灵活性，并且比 TensorFlow 原始的静态图更容易调试。然而，随着 TensorFlow 2.0 的发布，TensorFlow 的易用性随着即时执行的引入和 API 的简化而显著提高。在性能方面，TensorFlow 和 PyTorch 都为各种算法提供了高效的实现。TensorFlow 传统上以高性能著称，并在分布式计算和生产部署方面具有强大的支持，尤其是在 Google Cloud Platform 上。然而，PyTorch 的性能在每次新版本中都有显著提升，并且具有出色的 GPU 加速和分布式计算支持。

TensorFlow 在部署方面表现出色，尤其是在生产环境中。它支持广泛的平台和语言，提供 TensorFlow Serving 用于服务器端应用、TensorFlow Lite 用于移动和边缘设备，以及 TensorFlow.js 用于浏览器端应用。另一方面，PyTorch 在部署选项方面也取得了长足进步，拥有 TorchServe 和 TorchScript 语言，后者允许将模型导出到非 Python 环境中运行。TensorFlow 和 PyTorch 都有庞大的，活跃的社区提供了丰富的资源、教程和预训练模型。TensorFlow 起步较早，拥有稍大一些的社区和更多可用的资源。然而，PyTorch 的流行度正在迅速增长，尤其是在研究社区中。TensorFlow 2.0 与 Keras 无缝集成，Keras 是一个高级神经网络 API，使得使用 TensorFlow 创建模型变得更简单。PyTorch 与 Python 生态系统的其余部分集成良好，包括 NumPy 和各种可视化库。

TensorFlow 2.0 和 PyTorch 2.0 各有其独特的优势，选择两者之间的差异通常取决于项目的具体要求、开发和部署环境以及个人偏好。尽管存在差异，但这两个库仍在不断发展，经常相互学习，并且是深度学习领域必不可少的工具。

### PyTorch 的主导地位

PyTorch 在研究人员和从业者中获得了相当大的流行度，这归因于以下几个因素：

- 用户友好性：PyTorch 的语法和工作流操作比 TensorFlow 更“pythonic”。其简单直观的 API 使其更容易使用和理解。易于调试以及能够与 Python 生态系统的其余部分无缝集成，使得 PyTorch 在用户体验方面更胜一筹。

- 动态计算图：PyTorch 使用动态计算图，也称为 define-by-run 方法，而 TensorFlow（2.0 版本之前）使用的是静态计算图，或 define-and-run 方法。这允许开发者即时更改图，并且操作可以立即执行。这在图会动态变化的模型中尤其有用，例如在循环神经网络中。这提供了更大的灵活性，使 PyTorch 更适合需要灵活性和速度的实验和研究。

- 研究采用：PyTorch 因其简单性、高效性和易用性在研究社区中获得了显著的关注。大多数新的研究论文，尤其是在需要复杂模型的研究领域，如强化学习和自然语言处理，都附带了 PyTorch 实现。PyTorch 代码清晰明确的特性使这些论文更易于获取和理解。

- 强大的向后兼容性：PyTorch 具有更一致的 API 和强大的向后兼容性。这降低了学习新方法的开销，并避免了因弃用或大幅更改的函数而产生的问题。

- 强大的生态系统：PyTorch 的生态系统庞大，包含 PyTorch Lightning 和 Hugging Face 的 Transformers 等强大的扩展。与其他 Python 库（如 NumPy）的互操作性也更优。

- 卓越的性能：虽然传统上 TensorFlow 在性能方面被认为占有优势，但 PyTorch 已显著缩小了差距，尤其是在新版本中。它提供出色的 GPU 加速和分布式计算支持。

虽然 PyTorch 和 TensorFlow 各有优势，但 PyTorch 的灵活性、易用性、动态性和稳健性使其成为许多研究人员和开发者的首选。然而，需要注意的是，PyTorch 和 TensorFlow 之间的选择应根据项目的具体需求和限制来确定。两个框架都在不断发展，并得到其社区的强力支持。

### 从 TensorFlow 迁移到 PyTorch 2.0

将模型从 TensorFlow 迁移到 PyTorch 的过程包含多个阶段。作为一个简单的示例，让我们来看一下将使用 MNIST 数据集训练的简单全连接（密集）神经网络转换的问题。

在转换模型之前，我们需要了解其架构、输入和输出维度以及训练配置。一个典型的 TensorFlow 2.0 模型可能如下所示：

```python
import tensorflow as tf

from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Flatten
from tensorflow.keras.datasets import mnist

# Load data
(x_train, y_train), (x_test, y_test) = mnist.load_data()

# Normalize the input data
x_train = x_train.astype('float32') / 255
x_test = x_test.astype('float32') / 255

# Define the model
model = Sequential([
    Flatten(input_shape=(28, 28)),
    Dense(128, activation='relu'),
    Dense(10)
])

# Compile the model
model.compile(
    optimizer='adam',
    loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True),
    metrics=['accuracy']
)

# Train the model
model.fit(x_train, y_train, epochs=5)
```

#### 创建等效的 PyTorch 模型

接下来，我们将创建等效的 PyTorch 模型。PyTorch 要求我们将模型定义为一个类，该类继承自 `nn.Module` 类：

```python
import torch
from torch import nn
from torchvision import datasets, transforms

# Load data
train_data = datasets.MNIST(root='data', train=True,
                            download=True, transform=transforms.ToTensor())
test_data = datasets.MNIST(root='data', train=False,
                           download=True, transform=transforms.ToTensor())

train_loader = torch.utils.data.DataLoader(train_data, batch_size=64)
test_loader = torch.utils.data.DataLoader(test_data, batch_size=64)

# Define the model
class Net(nn.Module):
    def __init__(self):
        super(Net, self).__init__()
        self.flatten = nn.Flatten()
        self.fc1 = nn.Linear(28*28, 128)
        self.fc2 = nn.Linear(128, 10)

    def forward(self, x):
        x = self.flatten(x)
        x = torch.relu(self.fc1(x))
        x = self.fc2(x)
        return x

model = Net()
```

#### 指定损失函数和优化器

在 TensorFlow 中，这些是在编译模型时指定的。在 PyTorch 中，你需要分别指定它们：

```python
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.001)
```

### 训练模型

在 TensorFlow 中，你调用 `model.fit()`。在 PyTorch 中，你必须自己编写训练循环：

```python
for epoch in range(5):  # loop over the dataset multiple times
    for images, labels in train_loader:
        # zero the parameter gradients
        optimizer.zero_grad()
        # forward + backward + optimize
        outputs = model(images)
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()
```

值得注意的是，还有像 ONNX（开放神经网络交换）这样的自动化工具和库，可以帮助在不同的深度学习框架之间迁移模型，包括 TensorFlow 和 PyTorch。然而，在进行转换时，了解流程和框架之间的潜在差异很重要。

### 复杂模型迁移的成功策略

TensorFlow 和 PyTorch 在处理计算、内存管理和其他方面的方式存在差异，这可能使从一个框架到另一个框架成功迁移复杂模型或自定义层变得困难。

以下是被证明最有效且仍可被视为有效的方法：

- 了解架构：首先全面了解你要转换的 TensorFlow 模型的架构。这包括各层的顺序、层类型以及每层使用的参数。

- 从小开始：先转换模型的小部分，以确保每个部分按预期工作。

- 重用预训练模型：TensorFlow 和 PyTorch 都有预训练模型库（分别为 `tf.keras.applications` 和 `torchvision.models`）。如果你要转换的模型与其中一个预训练模型相似，你可以修改现有的模型以匹配你的架构，这比从头创建更容易。

- 自定义层：在 TensorFlow 中，你通过子类化 `tf.keras.layers.Layer` 来定义自定义层。在 PyTorch 中，你子类化 `torch.nn.Module`。主要区别在于，在 TensorFlow 中，你将计算分为 `build` 方法（用于创建权重）和 `call` 方法（用于计算），而在 PyTorch 中，所有计算都在 `forward` 方法中完成。

- 不同处理数据：TensorFlow 和 PyTorch 处理和向模型输入数据的方式不同。TensorFlow 使用 `tf.data.Dataset`，而 PyTorch 使用 `torch.utils.data.DataLoader`。确保你正确转换数据管道。

- 梯度处理：PyTorch 允许对梯度进行更明确和细粒度的控制。如果你的模型涉及梯度裁剪或操作等复杂操作，你必须确认你了解 PyTorch 如何处理梯度。

### ONNX（开放神经网络交换）

ONNX，全称 Open Neural Network Exchange，是一个强大的开源、社区驱动项目，使得模型能够在各种人工智能（AI）框架之间互换。它由微软和 Facebook 于 2017 年发起，此后获得了包括 IBM、亚马逊、华为等众多公司的支持。它为 AI 模型提供了一种通用格式，使开发者能够根据项目需求使用和切换任何框架。这种通用性不仅提升了效率，还促进了开发者之间的高度协作与共享，推动了 AI 社区的发展。

ONNX 建立在计算图模型之上。在该模型中，节点代表数学运算，边代表在多维数据数组（张量）之间传递的数据。ONNX 规范定义了大量的运算符——涵盖原始线性代数和算术函数、基本信号处理操作以及神经网络中常见函数的数学运算。

ONNX 为机器学习互操作性提供了强大的框架。它可以将模型从一个框架导出，再导入另一个框架进行推理。例如，在 PyTorch 中开发和训练好的深度学习模型可以导出为 ONNX 格式，然后导入 TensorFlow 进行推理，反之亦然。这使得开发者能够根据手头的任务（无论是模型创建、训练还是推理）选择最合适的框架。

ONNX 的一大优势是它能够跨不同框架优化模型。一旦模型转为 ONNX 格式，就可以利用 ONNX 的优化 API 将多个节点融合为一个节点、删除无用节点或进行常量折叠，从而提高计算效率。这些共享的优化可以减少每个单独框架自行实现优化方法的需求，从而减少冗余并增强一致性。

ONNX 的另一个关键特性是与硬件和平台无关。由于 ONNX 模型可以部署在各种硬件和平台上，开发者可以选择自己中意的平台来部署模型。这可以是本地机器、Azure 或 AWS 等云平台，甚至可以是手机或物联网设备等边缘设备。这一特性极大地扩展了机器学习模型的覆盖范围，使其从高端服务器延伸到日常设备。

ONNX 还促进了模型的透明性。ONNX 基于 protobuf 的格式使得模型能够以人类可读的形式呈现。这种透明性允许开发者在需要时理解、检查甚至修改模型。在模型开发和调试阶段，拥有如此高的透明度是非常有价值的。

对 ONNX 的支持正在持续增长。包括 PyTorch、TensorFlow、Scikit-Learn、CoreML、CUDA 等在内的多个流行机器学习工具和库都支持 ONNX。除了这些工具之外，还有多种可视化工具可以提供 ONNX 模型的图形视图，有助于理解和调试。

总而言之，ONNX 是推动机器学习模型更具共享性和互操作性的重要一步。其标准化格式使得模型能够在不同框架之间自由流动，使开发者能够根据自己的需求选择最佳工具和平台。其共享优化、硬件无关性和模型透明性等特点使其成为现代机器学习开发中的关键工具。无论你是机器学习研究人员还是开发者，ONNX 都能帮助你简化工作流程，并扩大模型的覆盖范围。

### 使用 ONNX 转换 TensorFlow 模型

我们将从一个简单的示例开始，演示如何使用 ONNX 格式将 TensorFlow 模型转换为 PyTorch 模型。为简单起见，我们将使用一个预训练的 TensorFlow 模型。本示例演示将使用 TensorFlow 提供的预训练 MobileNet 模型。MobileNet 是一个用于移动和嵌入式视觉应用的轻量级模型。

#### 安装

在开始之前，我们需要确认已安装 TensorFlow、PyTorch、ONNX 以及一个名为 ONNX-TF 的转换库。

你可以使用 `pip` 安装这些库：

```
pip install tensorflow
```

```
pip install torch torchvision
```

```
pip install onnx
```

```
pip install onnx-tf
```

#### 加载预训练的 TensorFlow 模型

接下来，我们导入必要的库并加载预训练的 MobileNet 模型。

```
import tensorflow as tf
```

```
model = tf.keras.applications.MobileNetV2(weights='imagenet', include_top=True)
```

在上述代码中，`tf.keras.applications.MobileNetV2` 用于加载预训练的 MobileNet 模型，`weights='imagenet'` 指定我们要使用在 ImageNet 数据集上训练过的模型版本。

#### 将 TensorFlow 模型转换为 ONNX

加载 TensorFlow 模型后，我们使用 tf2onnx 转换器将其转换为 ONNX。

首先，你需要安装 tf2onnx 转换器。可以使用 pip 完成：

```
pip install tf2onnx
```

然后，我们转换模型：

```
import tf2onnx

# The input signature of the TensorFlow model needs to be specified for conversion.

input_signature = [
    tf.TensorSpec([1, 224, 224, 3], tf.float32, name='input')
]

onnx_model, _ = tf2onnx.convert.from_keras(model, input_signature)
```

在上述代码中，`tf2onnx.convert.from_keras` 用于转换模型。`input_signature` 参数定义了模型输入张量的形状和数据类型。

#### 保存 ONNX 模型

将模型转换为 ONNX 后，我们将其保存到文件中：

```
with open('mobilenet.onnx', 'wb') as f:
    f.write(onnx_model.SerializeToString())
```

#### 将 ONNX 模型转换为 PyTorch

接下来，我们使用 ONNX 模型创建相应的 PyTorch 模型。

```
import torch

import onnx

from onnx2pytorch import ConvertModel

# Load the ONNX model

onnx_model = onnx.load('mobilenet.onnx')

# Convert the ONNX model to PyTorch

pytorch_model = ConvertModel(onnx_model)
```



在上述代码中，`onnx.load`用于从文件加载 ONNX 模型，`ConvertModel`用于将 ONNX 模型转换为 PyTorch 模型。

## 使用 PyTorch 模型

现在我们可以使用 PyTorch 模型进行预测。我们将用一个虚拟输入来测试模型：

```
# Create a random tensor with the same shape as the model's input
input_tensor = torch.randn(1, 3, 224, 224)

# Use the PyTorch model to make a prediction
output_tensor = pytorch_model(input_tensor)
```

在上述代码中，`torch.randn`用于创建随机张量，然后通过像调用函数一样传入输入张量来使用 PyTorch 模型进行预测。

整个过程展示了获取预训练 TensorFlow 模型、将其转换为 ONNX 格式，再将 ONNX 模型转换为 PyTorch 模型的能力。需要记住的是，并非所有 TensorFlow 操作都受 ONNX-TF 转换器支持，因此复杂模型可能无法干净地转换。然而，对于许多常见模型，该过程可以成为在 PyTorch 环境中使用 TensorFlow 模型的强大工具。

在不同格式之间转换模型的能力为开发者提供了灵活性，使他们能够充分利用不同框架的优势。它促进了机器学习社区中更多的协作与共享，并帮助开发者避免被锁定在单一框架中。

## 验证模型转换

通过 ONNX 将模型从 TensorFlow 转换为 PyTorch 后，你可能需要验证转换是否成功。该过程通常涉及对原始 TensorFlow 模型和转换后的 PyTorch 模型进行推理，然后比较输出结果。

下面是一种验证转换后模型的简单方法：

### 进行 TensorFlow 模型预测

首先，使用你的 TensorFlow 模型对样本输入进行预测。

```python
import numpy as np

# Create a random input tensor in TensorFlow
input_tensor = np.random.rand(1, 224, 224, 3).astype(np.float32)
```

### 使用 TensorFlow 模型执行推理

```python
tf_output = model.predict(input_tensor)
```

### 使用 PyTorch 模型进行预测

然后使用相同的输入来用你的 PyTorch 模型进行预测。

```python
# Convert the input to a PyTorch tensor
```

```python
input_tensor = torch.from_numpy(input_tensor).permute(0, 3, 1, 2)
```

```python
# Perform inference with PyTorch model
```

```python
pytorch_output = pytorch_model(input_tensor)
```

### 比较输出

最后，你可以比较两个模型的输出。

一种简单的方法是计算两个输出之间的均方误差（MSE）。

```python
# Convert the PyTorch tensor to a NumPy array

pytorch_output = pytorch_output.detach().numpy()

# Calculate the MSE between the two outputs

mse = np.mean((tf_output - pytorch_output) ** 2)

print(f"Mean Squared Error between TensorFlow and PyTorch outputs: {mse}")
```

如果 MSE 接近于 0，则意味着 TensorFlow 模型和 PyTorch 模型产生的输出几乎相同，转换成功。请注意，由于 TensorFlow 和 PyTorch 中某些操作的底层实现存在差异，输出可能并非完全一致，但应该非常接近。

## 故障排除与解决方案

在不同的深度学习框架（如 TensorFlow 和 PyTorch）之间使用 ONNX 转换模型有时可能会引发问题。

以下是一些常见问题及其可能的解决方案：

### 不支持的层或操作

最常见的问题之一是 ONNX 不支持某些层或操作，或者不同框架对它们的实现存在差异。例如，TensorFlow 可能支持 PyTorch 或 ONNX 不支持的层，反之亦然。

解决方案：如果出现这种情况，你可能需要使用基本操作重新实现不支持的层，或者在目标框架中找到执行相同功能的等效层。

### 数据格式的差异

TensorFlow 通常使用 `NHWC`（批大小、高度、宽度、通道）数据格式，而 PyTorch 使用 `NCHW`（批大小、通道、高度、宽度）。这些差异可能会导致转换过程中出现错误。

解决方案：确保在转换和推理过程中正确转置输入张量。ONNX 模型通常期望 `NCHW` 格式。

### 动态形状处理上的差异

ONNX 对于使用动态形状的模型可能会遇到困难，尤其是当模型输入的维度在不同推理会话之间可能改变时。

解决方案：你可能需要为每个框架分别实现动态形状处理。PyTorch 原生支持动态形状，但对于 ONNX，你可能需要使用 ONNX Reshape 操作来处理动态形状。

### 转换后结果不匹配

即使转换成功，你也可能会遇到推理结果不匹配的情况。

解决方案：这可能是由于框架之间的精度差异、某些操作的实现方式不同等原因造成的。使用多种输入来测试模型，比较中间层输出，并在必要时在目标框架中对模型进行微调。

### 版本不兼容

不同版本的 TensorFlow、PyTorch 和 ONNX 之间可能存在差异，从而导致转换问题。

解决方案：确保所有软件库都已更新，并检查你的 TensorFlow 和 PyTorch 版本与 ONNX 版本的兼容性。

需要特别注意的是，每个模型都是不同的，因此你遇到的具体问题及其解决方案将取决于模型的复杂度和结构。在进行故障排除时，将模型的各个组成部分隔离开分别转换，有助于发现问题所在。

## 总结

本章主要关注 TensorFlow 2.0 与 PyTorch 2.0 之间的比较、PyTorch 相对于 TensorFlow 的优势，以及使用 ONNX 将 TensorFlow 模型转换为 PyTorch 模型的方法。

我们首先深入探讨了 TensorFlow 与 PyTorch 之间的差异，并从易用性、社区支持、性能等方面对二者进行了讨论。讨论强调，虽然这两个框架各有优势，但 PyTorch 在用户友好性和调试便捷性方面往往更胜一筹，这使其在研究人员和开发者中越来越受欢迎。接着，我们探讨了将 TensorFlow 模型迁移到 PyTorch 2.0 的过程。逐步演示表明，对于简单模型，这一过程可能很直接，但更复杂的模型可能需要一种策略性的方法，尤其是在处理自定义层和操作时。

然后我们了解了 ONNX（开放神经网络交换格式），这是一个开源项目，提供了一种与平台无关的计算图模型，用于在不同深度学习框架之间实现互操作性。ONNX 提供了一种在各种深度学习框架之间转换模型的方法，这有助于利用不同框架的优势。最后，我们进行了一个动手演示，使用 ONNX 将 TensorFlow 模型转换为 PyTorch 模型。文中讨论了可能出现的问题，如不支持的层或操作、数据格式的差异、动态形状的处理、转换后结果不匹配以及版本不兼容等，并提出了解决这些问题的方法，使读者对转换过程有一个全面的了解。

总的来说，本章深入探讨了深度学习框架的多样性，并强调了在不同框架之间切换时的重要注意事项。它提醒我们，选择合适的工具并了解如何在它们之间切换，是深度学习项目成功的关键部分。

# 第 8 章：端到端 PyTorch 回归模型

## 构建 PyTorch 模型的阶段

在 PyTorch 中构建深度学习模型通常涉及几个关键步骤，我们将在下面详细介绍：

### 问题定义

理解当前的问题并将其作为机器学习挑战来提出，始终是所有此类工作的第一步。你需要确定试图预测的目标（目标变量），以及可用于进行该预测的信息（输入特征）。此外，你还需要选择要解决的问题类型（二分类、多分类、回归等），因为这将影响网络的设计以及所采用的损失函数。

### 数据准备

在确定了问题之后，下一步是收集和组织相关数据。从各种来源收集数据，并对其进行清洗。

在训练过程中，模型会努力降低损失。PyTorch 在 `torch.nn` 模块中提供了许多预定义的损失函数供你使用，例如用于回归问题的 `MSELoss` 或用于分类问题的 `CrossEntropyLoss`。

### 优化器

优化器是一种根据损失函数的梯度来更新模型参数（权重和偏置）的算法。PyTorch 在其 `torch.optim` 模块中预定义了大量优化器，包括 `SGD`、`Adam`、`RMSProp` 等等。

### 训练

既然你已经准备好了数据、模型、损失函数和优化器，现在就可以训练模型了。在大多数情况下，训练包括反复多次遍历整个数据集（使用 epoch）。在每个 epoch 期间，模型都会计算损失、计算梯度并更新参数。此外，模型还会对每个数据点进行预测。

### 评估

训练阶段结束后，你需要评估模型在从未见过的数据（测试集）上的表现。通过这样做，你将会了解模型对新数据的泛化效果。务必牢记，模型在训练时的表现并不总能代表它在未见过数据上的表现。

### 模型保存与加载

当你对模型的性能感到满意后，你可以将模型参数保存到文件中。这样，之后加载这些参数时，就不再需要重新训练模型来生成预测。

构建 PyTorch 模型涉及这些步骤的组合，并根据你要解决的具体问题进行定制。一旦掌握了这些基本步骤，就可以学习更高级的技术，例如使用数据加载器处理更大的数据集、通过正则化或 dropout 改进模型，以及加速使用学习率调度或提前停止来结束训练。

## 理解数据集

在开始为构建线性回归 PyTorch 模型进行数据准备之前，我们先来了解以下网址提供的数据集：

该数据集包含 7 种用于市场销售的鱼类数据，共有七列，详细描述了鱼类的各种属性。它包括以下字段：

- 物种：这是鱼的种类。作为一个分类变量，它可以用于分类等任务，根据其他变量预测鱼的种类。然而，对于线性回归任务，我们可能会转而关注数值变量。
- 体重：这是鱼的重量，单位为克。作为一个数值变量，它可以作为回归任务的目标，我们旨在根据其他测量值预测体重。
- Length1：这是鱼的垂直长度，单位为厘米。
- Length2：这是鱼的对角线长度，单位为厘米。
- Length3：这是鱼的横截面长度，单位为厘米。
- Height：这是鱼的高度，单位为厘米。
- Width：这是鱼的对角线宽度，单位为厘米。

Length1、Length2、Length3、Height 和 Width 列是数值变量，可以作为回归任务的输入特征，例如预测鱼的体重。

## 加载数据集

要在 PyTorch 中加载此数据集，我们首先需要下载数据，并使用 pandas 将其加载到 DataFrame 中。然后，我们可以将数据转换为张量，并创建自定义 Dataset。

以下是一个示例，说明如何执行此操作：

```python
import pandas as pd
import torch
from torch.utils.data import Dataset

# Define a custom Dataset
class FishDataset(Dataset):

    def __init__(self, dataframe):
        self.data = torch.tensor(dataframe.values, dtype=torch.float32)

    def __len__(self):
        return len(self.data)

    def __getitem__(self, idx):
        # Separate the features (x) from the target (y)
        x = self.data[idx, 1:]  # All columns except the first (Weight)
        y = self.data[idx, 0]   # Only the first column (Weight)
        return x, y

# Load the data into a pandas DataFrame
dataframe = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Fish_Dataset_Pytorch.csv")

# Convert the species column to one-hot encoding
dataframe = pd.get_dummies(dataframe, columns=["Species"])

# Create a Dataset from the DataFrame
dataset = FishDataset(dataframe)

# Access the first item in the Dataset
x, y = dataset[0]

print(f"Features: {x}")
print(f"Target: {y}")
```

请注意，我们在创建 Dataset 之前将物种列转换为 one-hot 编码。这是因为 PyTorch 要求分类变量采用数值格式。One-hot 编码是将分类数据转换为数值数据的常用方法。

## 创建张量

将数据加载到 pandas DataFrame 后，下一步是将数据转换为 PyTorch 张量，这是 PyTorch 用于计算的数据结构。此过程通常包括：

- 分离特征（输入）和目标（输出）：对于此数据集，特征将是所有长度、高度和宽度测量值，目标将是体重。
- 将数据转换为张量：PyTorch 提供了多种将数据转换为张量的方法。例如，您可以使用 `torch.Tensor()` 或 `torch.as_tensor()` 函数。
- 将数据拆分为训练集和测试集：这是评估模型对未见数据泛化能力的重要步骤。您可以使用 sklearn 中的 `train_test_split()` 函数来完成此操作。

以下是一个示例，说明如何执行这些步骤：

```python
import pandas as pd
import torch
from sklearn.model_selection import train_test_split

# Load the data into a pandas DataFrame
dataframe = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Fish_Dataset_Pytorch.csv")

# Convert the species column to one-hot encoding
dataframe = pd.get_dummies(dataframe, columns=["Species"])

# Separate the features (x) and the target (y)
x = dataframe.drop('Weight', axis=1).values
y = dataframe['Weight'].values

# Convert the data to tensors
x = torch.as_tensor(x, dtype=torch.float32)
y = torch.as_tensor(y, dtype=torch.float32)

# Split the data into training and test sets
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=42)

print(f"Training set size: {len(x_train)}")
print(f"Test set size: {len(x_test)}")
```

请注意，我们使用 20% 的测试集大小，这意味着 20% 的数据被留出用于测试，其余数据用于训练。`random_state` 参数用于确保您生成的拆分是可重现的。不同的 `random_state` 值将生成不同的拆分。

## 创建 DataLoader 实例

现在我们已经准备好了数据并将其拆分为训练集和测试集，我们需要将数据转换为 PyTorch 的 DataLoader 实例。这一步是必要的，因为 DataLoader 负责在训练期间将数据输入模型。

DataLoader 设计高效，负责批处理、打乱和并行数据加载。它会在我们的数据集上创建一个可迭代对象，该可迭代对象的核心是批次，由 PyTorch 自动管理。

以下是我们如何为训练集和测试集创建 DataLoader 实例的示例：

```python
from torch.utils.data import TensorDataset, DataLoader

# Define batch size
batch_size = 32
```

### 为训练集和测试集创建 TensorDataset

```python
train_dataset = TensorDataset(x_train, y_train)
test_dataset = TensorDataset(x_test, y_test)
```

### 为训练集和测试集创建 DataLoader



```python
train_loader = DataLoader(train_dataset, batch_size=batch_size, shuffle=True)
test_loader = DataLoader(test_dataset, batch_size=batch_size)
```

在上述示例程序中，我们将批次大小设置为 32，这意味着我们的模型将在每一步使用 32 个样本进行训练。`shuffle=True` 参数意味着我们的训练数据将在每个 `epoch` 被打乱，这有助于防止模型学习训练数据的顺序，并提高泛化能力。

现在，我们的数据已准备好用于训练 `PyTorch` 模型。在训练循环中，您可以迭代 `train_loader` 以获取训练数据和标签的批次。

```python
for batch in train_loader:
    data, labels = batch
    # continue with the training process
```

这是使用 `PyTorch` 时的典型数据准备流程。`DataLoader` 负责处理打乱和批处理数据所需的重活。它还可以处理更高级的场景，并为处理无法放入内存的大型数据集等情况提供大量额外的灵活性。

### 定义模型架构

线性回归模型是最简单的神经网络类型之一，也是许多更复杂模型的基础。它对于理解输入和输出变量之间的关系特别有用。

在神经网络的背景下，线性回归模型可以被视为一个只有单层且没有激活函数的网络，或者等效地，一个单层后跟线性激活函数的网络。

对于鱼类数据集，如果我们试图预测鱼的体重（一个连续变量），线性回归模型将是合适的。

现在，这是在 `PyTorch` 中定义简单线性回归模型的最佳方式：

```python
import torch.nn as nn

# Define the model
class LinearRegressionModel(nn.Module):

    def __init__(self, input_size):
        super(LinearRegressionModel, self).__init__()
        self.linear = nn.Linear(input_size, 1)

    def forward(self, x):
        return self.linear(x)

# Initialize the model
# (We use x_train.shape[1] to get the number of input features)
model = LinearRegressionModel(x_train.shape[1])
```

这段代码定义了一个新类 `LinearRegressionModel`，它继承了 `nn.Module`，后者是 `PyTorch` 中所有神经网络模块的基类。`forward` 方法

定义模型的正向传播，即模型进行预测的方式。

最后，我们使用输入特征的数量作为参数实例化模型，该数量即为 `x_train` 张量中的列数。

该模型已准备好进行训练，训练涉及反复向其输入数据，并根据其所做的预测（以损失函数衡量）调整权重和偏置。

### 训练模型

为了训练我们的线性回归模型，我们需要同时定义损失函数和优化器。

对于此类回归任务，损失函数的常见选择是均方误差（MSE）损失。MSE 损失计算预测值与实际值之间平方差的平均值，我们在训练期间的目标是最小化该值。

至于优化器，我们将使用 Adam 优化器。Adam 代表自适应矩估计（Adaptive Moment Estimation），它是一个流行的选择，因为它结合了随机梯度下降的另外两种扩展的优点。具体来说，它计算梯度及其平方梯度的指数移动平均值，而参数 `beta1` 和 `beta2` 控制这些移动平均值的衰减率。

#### 定义 MSE 损失函数

以下是在 `PyTorch` 中定义 MSE 损失函数和 Adam 优化器的方法：

```
# Define the loss function and the optimizer

criterion = nn.MSELoss()

optimizer = torch.optim.Adam(model.parameters(),
lr=0.001)
```

`nn.MSELoss()` 函数创建一个准则，用于衡量输入 `x` 和目标 `y` 中每个元素之间的均方误差。

`torch.optim.Adam()` 函数创建一个 Adam 优化器。我们将模型的 `parameters` 传递给此函数，以便优化器知道应更新哪些张量。学习率 `lr` 指定优化器更新模型参数的速度。

现在，我们将把模型设置为训练模式并运行一次前向传播以检查初始预测。

这可以使用以下脚本完成：

```
# Set model to training mode

model.train()
```

```
# Run a forward pass on the model to get the initial predictions

with torch.no_grad():
    initial_predictions = model(x_train)
```

```
# Print the initial predictions

print(initial_predictions)
```

`model.train()` 函数将模型设置为训练模式。对于我们简单的线性回归模型来说这不会产生差异，但对于训练和评估期间行为不同的模型（如 dropout 或批归一化），使用它很重要。

接下来，我们在模型上运行前向传播以获取初始预测。我们使用带有 `torch.no_grad():` 的上下文管理器来指定在此操作期间我们不想跟踪梯度，因为仅检查预测时不需要它们。

初始预测很可能与实际值相差甚远，因为模型的初始参数值是随机的。这是正常的，一旦开始训练过程，模型应该会有所改进。

现在，我们将更深入地探讨损失函数和 Adam 优化器。

在机器学习和深度学习的上下文中，损失函数是评估算法对给定数据建模效果好坏的方法。如果预测与实际结果偏差太大，损失函数会输出一个较大的数字。良好的预测会得到一个较小的数字。

在此场景中，我们使用均方误差（MSE）损失。这是回归问题中流行的损失函数。它通过计算预测值与实际值之间平方差的平均值来工作。平方是为了消除负号。它还放大了较大误差的影响。MSE 的公式为：

`MSE = 1/n Σ(actual - predicted)²`

其中 Σ 是对所有示例求和，`n` 是示例总数，而 `actual - predicted` 表示每个示例的实际值与预测值之间的差值。

Adam（自适应矩估计）是一种为每个参数计算自适应学习率的方法。它结合了随机梯度下降的另外两种扩展的优点。具体来说：

- AdaGrad: Which scales down the learning rate for each parameter adaptively, so parameters with larger gradients that are updated more also have their learning rate reduced more.

- RMSProp: Which also scales down the learning rate according to the magnitude of the gradients, but unlike AdaGrad, it uses a moving average of the squared gradient, so it doesn't decrease as fast.

具体来说，Adam 通过对梯度的第一阶矩（均值）和第二阶矩（非中心方差）的估计来计算自适应学习率。

该算法为模型中的每个权重维护一个单独的学习率，并在随时间自适应地调整它们。与其他梯度下降优化方法相比，这带来了良好的性能，并且对初始学习率的敏感性更低。

“Adam” 这个名字来源于该方法的自适应矩估计，并且经实证表明它在实践中效果良好，并优于其他自适应学习方法算法。

现在我们已经介绍了损失函数和优化器的基础知识，我们将更好地理解训练过程，该过程涉及使用优化器最小化损失函数。

### 训练迭代

为了训练模型，我们需要在 `epoch` 中迭代训练数据。`Epoch` 是对整个训练数据的一次完整遍历。在每个 `epoch` 期间，我们执行以下步骤：

- 通过模型对输入数据运行前向传播以获取预测。

- 根据模型预测与实际值之间的差异计算损失。

- 通过模型运行反向传播（反向传播）以计算损失相对于模型参数的梯度。

- 使用优化器以最小化损失的方式调整模型参数。

下面是 `PyTorch` 中一个简单的训练循环示例。我们将使用相对较少的 `epoch` 数量（例如 100）用于演示目的：

```
# Number of epochs
```

```
epochs = 100
```

```
# Store the losses
```

```
losses = []

for epoch in range(epochs):
    # Forward pass
    y_pred = model(x_train)
    # Compute loss
    loss = criterion(y_pred, y_train)
    # Store the loss
    losses.append(loss.item())
    # Print loss every 10 epochs
    if epoch % 10 == 0:
        print(f'Epoch {epoch}, Loss: {loss.item()}')
    # Zero gradients
```

```
optimizer.zero_grad()

# Backward pass

loss.backward()

# Update weights

optimizer.step()

print('Training complete.')
```

在每个 `epoch` 期间，我们首先通过模型对 `x_train` 数据运行前向传播以获取预测 `y_pred`。然后我们使用 `criterion` 函数计算损失，该函数以预测值和实际值作为输入。`zero_grad()` 函数将上一次迭代的旧梯度清零。然后，`loss.backward()` 计算新的梯度，而 `optimizer.step()` 使用这些梯度更新模型的参数。

我们将每个 `epoch` 期间的损失值存储在一个损失列表中以供后续分析。我们还每 10 个 `epoch` 打印一次损失，以便在训练期间看到模型的改进情况。

这是一个简单的训练循环，但它涵盖了使用 `PyTorch` 训练神经网络模型的基本组件。实际输出将取决于数据和模型的特定初始化，但随着模型学习更好地拟合数据，您应该会看到损失随时间推移而减小。

现在我们已经训练了模型，下一步涉及评估模型，如有需要则调整模型，并在新的（未见过）数据上进行预测。

### 模型评估

首先，我们将评估模型以查看它从训练数据中学到的程度。为此，我们在测试数据上运行模型。步骤包括将模型设置为评估模式，运行前向传播，然后计算损失：

```
# Set model to evaluation mode

model.eval()
```

```
# Forward pass on test data

with torch.no_grad():
    y_pred = model(x_test)
```

```
# Compute loss

loss = criterion(y_pred, y_test)
```

```
print(f'Test Loss: {loss.item()}')
```

在这段代码片段中，`model.eval()` 告诉 `PyTorch` 我们处于评估模式，即我们不想更新任何参数。我们在测试数据上运行模型并计算损失。我们将此测试损失与训练损失进行比较。这两者之间存在显著差异可能表明发生了过拟合（模型在训练数据上表现良好，但在未见数据上表现不佳）。

### 模型调优

如果你的模型表现不如预期，有几个参数你可以调整以尝试提高性能：

Number of epochs: Training for more epochs might improve performance, up until a point. But be careful of overfitting.

训练轮数：训练更多轮数可能会提高性能，直到某个程度。但要注意过拟合。

Learning rate: If your training loss is fluctuating wildly during training, your learning rate might be too high. If your training loss is decreasing very slowly, your learning rate might be too low.

学习率：如果训练过程中训练损失剧烈波动，你的学习率可能太高。如果训练损失下降非常缓慢，你的学习率可能太低。

Model architecture: You might need a larger or more complex model to fit the data.

模型架构：你可能需要更大或更复杂的模型来拟合数据。

最后，我们可以使用训练好的模型对新的、未见过的数据进行预测。为此，我们只需在新数据上调用模型的 `forward` 函数即可。

以下是一个简单示例，假设我们有一些新的数据在 `x_new` 中：

```
# Forward pass on new data

with torch.no_grad():
    y_new = model(x_new)

# Print predictions

print(y_new)
```

请不要忘记，这新的数据应与训练和测试数据以相同的方式处理，即应以相同的方式进行归一化，并且应为 `PyTorch` 张量。

有了它，你就拥有了一个在 `PyTorch` 中使用线性回归模型进行训练、评估、调优和预测的工作流程！

### 保存模型

一旦你对模型的性能感到满意，你会想要保存它以便以后重复使用。在 `PyTorch` 中，通常只保存和加载模型参数，而不是整个模型，因为这样更便携。

要保存模型参数，可以使用 `torch.save`：

```
# Save the model parameters

torch.save(model.state_dict(), 'fish_weight_model.pt')
```

在这段代码中，`model.state_dict()` 返回一个包含模型参数（和梯度）的 OrderedDict，而 `'fish_weight_model.pt'` 是文件名。

### 加载模型

要加载模型参数，你需要先创建同一个模型的一个实例，然后使用 `load_state_dict()` 加载参数：

```
# Create a new model

model_new = LinearRegressionModel(input_size,
output_size)
```

```
# Load the parameters from the old model

model_new.load_state_dict(torch.load('fish_weight_model.pt'))
```

```
# Don't forget to call eval() method to set dropout and batch normalization layers to evaluation mode

model_new.eval()
```

完成这些步骤后，`model_new` 应该具有与你保存的模型相同的参数。你现在可以使用 `model_new` 进行评估或预测。

### 部署模型

部署模型用于生产涉及使其可用于对新数据进行预测。具体做法将取决于你的生产环境。

一种简单的方法是通过 Web 服务，模型驻留在服务器上并通过 API 调用进行预测。更复杂的方法可能是将模型部署在分布式系统上，以进行大规模实时预测。

为了准备模型部署，你需要确保它已保存并且可以正确加载。你还需要保存数据预处理步骤（如归一化参数），并确保新数据在传入模型之前能够得到适当处理。

总之，以下是在 `PyTorch` 中训练神经网络模型的一般步骤：

- 准备数据并将其转换为张量。

- 定义模型架构。

- 定义损失函数和优化器。

- 使用训练数据训练模型。

- 使用测试数据评估模型。

- 调优模型参数以获得更好的性能。

- 保存模型以供以后使用。

- 将模型部署用于生产使用。

这些步骤提供了一个通用蓝图。具体细节将取决于你试图解决的问题、可用的数据以及你工作的环境。但无论这些细节如何，这个蓝图都将为你在 `PyTorch` 中使用神经网络提供坚实的基础。

### 摘要

在本章中，我们专注于使用 `PyTorch` 2.0 构建线性回归模型来预测鱼的重量，使用 Fish Market 数据集。我们首先概念化了构建任何 `PyTorch` 模型所需的步骤，其中包括准备数据、定义模型架构以及使用选定的损失函数和优化器设置训练循环。我们讨论了 `PyTorch` 的设计理念强调灵活性和效率，使我们能够显式定义模型架构并手动控制训练过程。

我们随后深入探讨了准备数据的具体细节。我们导入了 Fish Market 数据集并执行了数据归一化和转换为 `PyTorch` 张量，这是 `PyTorch` 中使用的基本数据结构。我们还将数据拆分为训练集和测试集，强调在未见数据上评估模型的重要性。我们强调这些预处理步骤对任何机器学习模型都至关重要，而 `PyTorch` 提供了工具和实用程序使这些步骤高效且易于实现。接下来，我们讨论了线性回归模型架构及其在 `PyTorch` 中的实现。我们使用 `PyTorch` 的 `nn.Module` 类创建了一个简单的线性回归模型，并解释了每个组件的重要性。在模型定义之后，我们讨论了损失函数和优化器的作用。我们使用了均方误差（MSE）损失函数和 Adam 优化器，并解释了它们的工作原理及其在模型训练中的重要性。然后我们使用简单的训练循环训练模型，并观察到模型从数据中学习，这体现在损失值随轮数增加而下降。



最后，我们涉及了模型评估、调优和预测阶段。我们解释了如何评估模型在测试集上的性能，并讨论了如果模型性能不满意时可能采取的措施。我们还演示了如何对新数据进行预测。最后，我们介绍了如何保存和加载模型以供以后使用或部署。本质上，本章提供了使用 PyTorch 2.0 创建简单但完整的机器学习管道的详细演练。我们希望本章获得的知识能为探索更复杂的模型和深度学习概念提供坚实的基础。

Thank You

## 尾声

随着我们对 PyTorch 2.0 的深入研究接近尾声，我们希望我们的尊敬读者不仅获得了丰富的知识，而且在现实世界中使用这一尖端深度学习框架方面也获得了专业技能。本书的写作意图是作为一份包罗万象的指南。它经过精心准备，带你经历多个理解层次，从基础开始，一直到最复杂的概念。

这次旅程始于对张量这一引人入胜世界的深入探索，旨在帮助你更好地欣赏它们在 PyTorch 中发挥的关键作用。接下来，我们着手研究如何设计基础以及复杂的 PyTorch 模型，通过真实世界的示例阐明概念，并确保你在阅读材料的进展过程中不仅在阅读，而且在实践中学习。

揭开训练过程周围的神秘面纱是我们道路上的重要一步。本书应已成功剖析了这些过程看似复杂的结构，通过让你全面掌握前向传播、反向传播和权重更新。此外，我们还介绍了对 PyTorch optim 包以及多种优化算法的调查。任何对深度学习感兴趣或从事该领域工作的人都应从根本上理解训练过程的工作原理以及优化如何改善结果。

我们深入探讨了深度学习领域前沿的更复杂概念，例如模型序列化和优化、分布式训练以及 PyTorch 量化 API 的利用。这些概念处于深度学习领域的前沿。向你介绍这些概念的目的是确保你始终了解行业最新的趋势和突破。我们相信，如果你掌握了这些复杂的概念，它将为你开启新的大门，并推动你在未来项目中进行的创新。

TensorFlow 2.0 与 PyTorch 2.0 之间的对比是使本书区别于同类书籍的因素之一。我们预计通过给你这个

通过比较，你将能够就哪个框架最符合你情况独有的标准做出明智的决定。最值得注意的是，我们提供了详细的逐步指南，说明如何利用 ONNX 将在 TensorFlow 中创建的模型迁移到 PyTorch。本指南旨在充当两个平台之间的桥梁，从而扩展你的技能组合，并增强你作为深度学习从业者的多才多艺。

当我们即将结束这段旅程时，我们花些时间反思本书的主要目的，即为你做好成为网络管理员职业的准备。我们衷心希望对 PyTorch 2.0 的这项全面考察能帮助你更接近实现目标。在读完本书后，你应该已经在通往为深度学习领域做出重要贡献的道路上，因为它将为你提供所需的信息和实践能力。

总之，我们衷心感谢你选择本书作为你在探索 PyTorch 2.0 时的指南。我们真诚希望本书中呈现的理念、策略和见解，能在你努力获取更深入知识的过程中成为极有用的资源。当你翻到本书的最后一页时，请记住，这标志着你进入广阔且不断变化的深度学习世界这段迷人旅程的开始。继续探索新事物并自我教育，但最重要的是在旅途中享受乐趣！

## 致谢

我对 GitforGits 怀有深深的感激之情，感谢他们在撰写本书的整个过程中始终如一的热情和明智的建议。他们的专业知识和细致的编辑工作确保了这本书对各个阅读水平和理解能力的人都有用。此外，我还要感谢参与出版过程的每一个人，他们的努力使本书得以实现。从校对到广告，他们的努力造就了今天的项目。

最后，我想向在我一生中给予我无条件爱和鼓励的每一个人表达我的感激。他们的支持对本书的完成至关重要。我感谢你们对这一事业的帮助以及对我职业生涯的持续关注。
