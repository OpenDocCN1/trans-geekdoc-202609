

| | | 解决方案 |
|---|---|---|
| **量化与剪枝** | 支持模型量化和剪枝，这对于将模型部署到边缘设备至关重要 | 提供改进的支持和额外的模型量化、剪枝及优化技术 |
| **生态系统** | 拥有由社区开发的不断壮大的工具和库生态系统（例如 TorchVision、TorchText 和 TorchAudio） | 随着社区贡献的增加以及与其他库和工具的互操作性得到改进，生态系统进一步扩大 |
| **性能** | 在研究和生产环境中均表现良好 | 由于底层优化，提供了性能改进、更快的训练和推理时间 |

## 表 1.1：PyTorch 1.x 与 PyTorch 2.0

## 动态计算图与“定义即运行”范式

在深度学习领域，定义计算图主要有两种范式——静态（定义并运行）和动态（定义即运行）。

在静态图（TensorFlow 2.0 之前使用）中，图在运行会话之前被定义和优化。随后会反复运行同一图，这允许进行某些性能优化，但牺牲了灵活性。修改图需要完全重建，这使得调试和动态修改变得更加困难。

另一方面，PyTorch 使用动态或定义即运行图范式。每次前向传播都会定义一个新的计算图。图中的节点是 Python 对象，边是在它们之间流动的张量。随着操作的执行，图会即时构建。这提供了极高的灵活性，使得 PyTorch 非常适合那些在执行过程中需要动态更改架构的模型，例如循环神经网络（RNNs）以及带有循环或条件语句的模型。

```
# PyTorch dynamic graph example
import torch
x = torch.ones(2, 2, requires_grad=True)
print(x) # tensor([[1., 1.], [1., 1.]], requires_grad=True)
y = x + 2
print(y) # tensor([[3., 3.], [3., 3.]], grad_fn=<AddBackward0>)
```

在前面的代码中，我们首先定义了一个 2x2 张量 x。然后执行操作 y = x + 2，动态构建计算图。

## Autograd 系统

PyTorch 动态计算图系统的一个关键组件是其自动微分引擎 autograd。它负责计算导数，即参与计算的张量的梯度，从而促进反向传播。

当你创建 requires_grad=True 的张量时，PyTorch 开始跟踪其上的所有操作。计算前向传播后，可以调用 .backward() 自动计算所有梯度。这些梯度会累积到张量的 .grad 属性中。

```
# Compute forward pass
z = y * y * 3
out = z.mean()
print(z, out) # tensor([[27., 27.], [27., 27.]], grad_fn=<MulBackward0>) tensor(27., grad_fn=<MeanBackward0>)
# Compute backward pass
out.backward()
print(x.grad) # tensor([[4.5000, 4.5000], [4.5000, 4.5000]])
```

在前面的示例中，我们将 z 和 out 定义为 y 的函数并计算前向传播。然后调用 `out.backward()`，这会触发梯度计算，并打印 `x.grad` 以查看 x 对 out 的梯度。

理解 autograd 和动态计算图系统对于使用 PyTorch 有效实现和调试深度学习模型至关重要。二者的结合使 PyTorch 能够为定义和训练神经网络提供灵活且直观的接口，同时自动处理导数和反向传播的复杂细节。这使得 PyTorch 在需要模型灵活性和可定制性的复杂计算机视觉任务中非常流行。

## GPU 加速

图形处理单元（GPU）在加速深度学习任务中起着至关重要的作用。与 CPU 不同，GPU 专为高吞吐并行计算而设计，因此非常适合涉及大规模矩阵运算的任务，而此类运算在深度学习中无处不在。

PyTorch 提供对 GPU 计算的原生支持，利用 CUDA 平台。张量计算可以无缝移至 GPU，显著加快执行速度。以下是在 GPU 上运行 PyTorch 张量操作的示例：

```
# Specify device to be used
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')

# Create a tensor and move it to GPU
x = torch.ones([3, 3], device=device)

# Perform operations on the GPU
y = x + 2
```

这里，我们首先创建一个 torch.device，如果 CUDA 可用则设置为 'cuda'，否则设置为 'cpu'。然后在此设备上创建张量 x，任何涉及 x 的操作也将在此设备上执行。

始终记得将模型和数据都移至 GPU。PyTorch 不会自动将数据或模型移至 GPU。忘记移动数据或模型到 GPU 是一个常见错误，如果尝试对位于不同设备上的对象执行操作，PyTorch 会抛出错误。

```
# Moving model to GPU
model = model.to(device)

# Moving data to GPU
data, target = data.to(device), target.to(device)
```

## 分布式计算

随着数据集和模型规模的增长，分布式计算已成为深度学习的必需品。分布式计算允许你在单机多 GPU 或多机（每台配备多个 GPU）之间并行化计算。

PyTorch 提供多个包，例如 torch.nn.DataParallel 和 torch.nn.parallel.DistributedDataParallel，以促进分布式计算。推荐使用 torch.nn.parallel.DistributedDataParallel，因为它提供了更大的灵活性和效率。

以下是使用 DistributedDataParallel 的简短示例：

```
# Import the package
from torch.nn.parallel import DistributedDataParallel

# Assume your model is on the GPU and you are using two GPUs
model = model.to(device)

model = DistributedDataParallel(model, device_ids=[0, 1])
# Now any tensor you pass to model will be split on its first dimension
# and fed to separate GPUs and the outputs are then concatenated
output = model(data)
```

这会将数据按第一个维度（通常是批次大小）拆分，分发到不同的 GPU。每个 GPU 计算其部分，然后收集并拼接输出。请记住，输入数据应与模型位于同一设备上。

除此之外，PyTorch 2.0 对其分布式计算能力引入了许多优化，实现了更高效的资源利用和更好的性能。其中包括对多种后端的更好支持、对网络通信的更好处理，以及用于梯度聚合和模型同步的高级算法。

能够有效使用 GPU 加速和分布式计算，可以显著加快模型训练速度，并让你处理更大规模、更复杂的任务，这在计算机视觉领域尤其关键，因为该领域的数据集和模型可能非常庞大。

请记住，分布式计算不仅有助于将训练过程扩展到多台机器，还允许使用混合精度训练以及进程间优化的通信，从而充分发挥硬件性能。这确保你可以高效处理大规模计算机视觉任务，使 PyTorch 成为此类任务的理想选择。

## TorchScript 简介

TorchScript 是一种序列化 PyTorch 模型的方式，使其能够在非 Python 环境中运行。在将 PyTorch 模型部署到生产环境时，这一点尤为重要，因为在生产环境中，Python 可能不可用，或因其性能特性而不受欢迎。

TorchScript 使用 PyTorch 模型的静态图表示，该表示可针对特定硬件进行优化。这种静态图表示也更适合在低延迟、高吞吐的生产环境中部署，因为它可以直接加载到 PyTorch C++ API 中。

TorchScript 通过称为**追踪**或**脚本化**的过程，提供了从 eager 模式到图模式的无缝过渡。

### 追踪

追踪允许你获取现有模块，并将其在前向传播期间执行的所有张量计算记录到 **torch.jit.ScriptModule** 中。

以下是一个示例：

```
import torch
import torchvision.models as models

# An instance of your model.
model = models.resnet50()

# An example input you would normally provide to your model's forward() method.
example = torch.rand(1, 3, 224, 224)

# Use torch.jit.trace to generate a torch.jit.ScriptModule via tracing.
traced_script_module = torch.jit.trace(model, example)
```

在此示例中，我们首先创建一个 ResNet 模型。然后，生成一个示例输入张量，并将模型和示例输入都传递给 **torch.jit.trace**，它会记录模型在运行时执行的计算。

