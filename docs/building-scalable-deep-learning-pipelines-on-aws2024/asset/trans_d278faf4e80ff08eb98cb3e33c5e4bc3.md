
## 数据加载器与数据洗牌

数据加载器（DataLoader）对于数据洗牌同样至关重要。在模型训练期间，打乱数据顺序是必需的，以防止模型学习到特定于数据集的顺序或模式。

DataLoader 提供了洗牌数据的选项，确保模型在训练过程中看到的每个批次都包含来自数据集的随机样本选择。这种随机性有助于防止模型对训练数据过拟合，并提高其泛化到未见过数据的能力。

关于 `create_data_loader` 函数的实现细节：

- 在函数内部，预处理后的特征和标签使用 TensorDataset 构造函数组合成一个 PyTorch TensorDataset。
- 通过向 DataLoader 构造函数传递 TensorDataset 以及指定的批次大小和洗牌参数，为训练集和测试集分别创建 DataLoader 对象。
- 然后，该函数返回这些 DataLoader 对象，它们可用于在模型训练和评估过程中迭代遍历数据批次。

通过创建 DataLoader 对象，`create_data_loader` 函数实现了机器学习管道中训练和测试阶段的数据高效加载与管理。DataLoader 处理数据批处理和洗牌的能力有助于提高训练效率、模型性能及泛化能力。

### 第 6 步：模型训练函数（`train_model`）

在这一步中，我们创建 `train_model` 函数，该函数负责使用训练数据训练神经网络模型：

`train_model` 函数的任务是利用训练数据训练神经网络模型。神经网络的训练涉及根据预测输出与实际目标之间的差异，迭代更新模型的参数（权重和偏置）。

让我们更详细地解释这一过程：

#### 迭代训练

- 该函数针对指定的轮次（epochs）次数遍历训练数据集。每个轮次代表对整个训练数据集的一次完整遍历。
- 在每个轮次中，该函数遍历数据的小批次（mini-batches）。此过程由 DataLoader 对象辅助完成，它自动对数据进行批处理。
- 对于每个小批次，模型使用当前参数值进行预测（前向传播），计算预测输出与实际目标之间的损失，然后更新模型参数以最小化损失（反向传播）。

#### 使用反向传播进行参数更新

- 反向传播是训练神经网络的关键算法。它涉及计算损失函数相对于模型参数的梯度，这些梯度表示每个参数对误差的贡献程度。
- 在计算梯度后，优化器（在此情况下为 Adam 优化器）沿最小化损失的方向调整模型的参数。
- 此过程对训练数据集中的每个小批次以及多个轮次重复进行，通过最小化损失函数逐步提高模型的性能。

关于 `train_model` 函数实现的具体细节：

- 在函数内部，存在一个嵌套循环结构，其中外层循环遍历轮次，内层循环遍历数据的小批次。
- 对于每个小批次，调用优化器的 `zero_grad` 方法将所有模型参数的梯度重置为零。
- 然后调用模型的前向方法对输入数据进行预测，随后使用指定的损失函数（criterion）和实际标签计算损失。
- 在计算损失后，调用 backward 方法计算损失相对于模型参数的梯度。
- 最后，调用优化器的 `step` 方法基于计算出的梯度更新模型参数，有效地执行一次优化步骤。

通过实现迭代训练过程和基于反向传播的参数更新，`train_model` 函数使 PyTorch 神经网络模型能够从训练数据中学习，并在随后的轮次中提高其性能。这种迭代优化过程是机器学习中神经网络训练成功的基础。

### 第 7 步：模型评估函数（`evaluate_model`）

在这一步中，我们创建 `evaluate_model` 函数，该函数在测试数据上评估训练好的神经网络模型：

```python
def evaluate_model(
    model,
    test_loader,
    criterion
) -> Tuple[float, float]:
    """
    在测试数据上评估训练好的模型，
    以评估其性能。
    计算测试损失以及额外的
    评估指标，如 R-squared 分数。
    """
    with torch.no_grad():
        model.eval()
        predictions = []
        targets = []
        test_loss = 0.0
        for inputs, labels in test_loader:
            outputs = model(inputs)
            loss = criterion(outputs, labels.unsqueeze(1))
            test_loss += loss.item() * inputs.size(0)
            predictions.extend(outputs.squeeze().tolist())
            targets.extend(labels.tolist())

        test_loss /= len(test_loader.dataset)
        predictions = torch.tensor(predictions)
        targets = torch.tensor(targets)
        ss_res = torch.sum((targets - predictions) ** 2)
        ss_tot = torch.sum((targets - torch.mean(targets)) ** 2)
        r_squared = 1 - ss_res / ss_tot
        logger.info(f"Test Loss: {test_loss:.4f}")
        logger.info(f"R-squared Score: {r_squared:.4f}")
        return test_loss, r_squared.item()
```

`evaluate_model` 函数评估训练好的神经网络模型在未见过的测试数据上的性能。评估对于理解模型对新的、未见过的样本的泛化程度以及识别任何潜在问题（如过拟合）至关重要。

该函数计算测试损失，该损失衡量模型预测与测试数据集中实际目标之间的差异。这通常使用诸如均方误差（MSE）或平均绝对误差（MAE）等损失函数完成。在此情况下，使用 MSE 损失函数。通过平均测试数据集中所有样本的个体损失来计算总测试损失。

除了测试损失外，该函数还计算一个额外的评估指标：R-squared 分数（也称为决定系数）。R-squared 分数衡量目标变量（在此情况下为收盘价）的方差中，可以通过模型中的自变量（特征）预测的比例。它的取值范围从 0 到 1，较高的值表示更好的模型拟合度。分数为 1 表示完美拟合，而分数为 0 表示模型的预测效果不比简单使用目标变量的平均值更好。

在 `evaluate_model` 函数内部，使用 `model.eval()` 将模型设置为评估模式。该函数遍历测试 DataLoader 中的数据小批次，使用训练好的模型进行预测，并计算每个小批次的测试损失。它还累积预测值和实际目标，以便在遍历完所有小批次后计算 R-squared 分数。

R-squared 分数使用以下公式计算：

```python
r_squared = 1 - ss_res / ss_tot
```

其中 `ss_res` 是残差平方和（预测值与目标值之间的差值之和的平方），`ss_tot` 是总平方和。

`logger.info` 记录测试损失和 R-squared 分数，以提供有关模型在测试数据集上性能的见解。这些指标有助于评估模型的预测能力并识别改进领域。

### 第 8 步：主函数（`main`）

在这一步中，我们将讨论主函数，它是执行代码的入口点：

```python
def main(
    data_file_path: str,
    num_epochs: int = 100,
    batch_size: int = 32,
    learning_rate: float = 0.001
):
    """
    用于训练和评估特斯拉股价预测深度学习模型的
    主函数。

    参数：
        data_file_path (str): 包含股价数据的
        CSV 文件的路径。
        num_epochs (int): 训练模型的轮次数。默认为 100。
        batch_size (int): 训练期间数据加载的批次大小。默认为 32。
        learning_rate (float): 优化器的学习率。默认为 0.001。
    """

