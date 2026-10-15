
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
