

DataLoader 确保数据以可控的批次输入模型，这有助于优化内存使用并提高计算效率。它还处理数据洗牌和并行加载，这对于提高模型性能和缩短训练时间至关重要。

- 定义了 `create_data_loader` 函数，用于将预处理后的数据转换为 PyTorch 张量，并为训练集和测试集创建 DataLoader 对象。该函数接收特征和标签作为输入，这些是来自上一模块的预处理数据。它们被转换为 `TensorDataset`，将特征和标签组合成一个数据集。然后，基于此数据集创建一个 DataLoader，指定所需的 `batch_size`，并启用每个纪元的数据洗牌。
- 接下来，定义了 `train_model` 函数，用于使用 DataLoader、定义的损失函数（criterion）和优化器，在训练数据上训练神经网络回归模型。该函数对数据进行指定纪元次数的迭代，每次迭代都会计算损失，并根据反向传播过程中计算的梯度更新模型参数。
- 在训练循环中，对于从 `train_loader` 加载的每个输入和标签批次，首先将优化器的梯度清零（`optimizer.zero_grad()`），确保来自之前迭代的梯度不会累积。然后，模型应用于输入以生成预测值（`outputs = model(inputs)`）。使用指定的 criterion 计算这些预测值与实际标签之间的损失。
- 计算损失后，梯度通过网络向后传播（`loss.backward()`），使 PyTorch 能够计算损失相对于模型参数的梯度。最后，优化器基于这些梯度更新模型参数（`optimizer.step()`）。
- 在整个训练过程中，会打印当前纪元和损失等信息，以监控模型进度。这个迭代训练循环将持续指定的纪元次数，随时间逐渐提高模型性能。

## 模块 3：model_evaluation.py

该模块旨在评估训练后的 PyTorch 模型在测试数据集上的性能：

```python
import torch

def evaluate_model(model, test_loader, criterion):
    """
    在测试数据上评估训练好的模型，
    以评估其性能。
    计算测试损失以及额外的
    评估指标，
    例如 R 平方得分。
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
        print(f"Test Loss: {test_loss:.4f}")
        print(f"R-squared Score: {r_squared:.4f}")
        return test_loss, r_squared.item()
```

让我们分解代码以理解其功能：

- 代码首先导入 torch 库，这是 PyTorch 的核心库。
- 定义了 `evaluate_model` 函数，用于评估模型在测试数据集上的性能。它接受三个主要输入：`model`，即待评估的训练好的 PyTorch 模型；`test_loader`，包含测试数据的 DataLoader 对象；以及 `criterion`，用于评估的损失函数，通常与训练时使用的相同。
- 在函数内部，评估过程封装在一个 `with torch.no_grad()` 块中（由于评估期间不需要梯度，因此禁用梯度计算），并使用 `model.eval()` 将模型切换到评估模式。
- 接下来，函数初始化空列表 `predictions` 和 `targets`，分别用于存储模型的预测值和实际目标值。此外，`test_loss` 被初始化以累加整个测试数据集的总损失。
- 该函数迭代遍历来自 `test_loader` 的数据批次，利用模型为每个批次计算预测值。使用指定的 criterion 计算预测输出与实际标签之间的损失。测试损失通过将损失乘以批次大小并加到 `test_loss` 上来累加。
- 然后通过使用 `outputs.squeeze().tolist()` 移除额外维度后，将预测输出追加到 `predictions` 列表中。同样，实际标签被追加到 `targets` 列表中。
- 遍历完所有批次后，通过将 `test_loss` 除以测试数据集中的样本总数，计算出整个数据集的平均测试损失。
- 将 `predictions` 和 `targets` 列表转换为 PyTorch 张量。然后脚本计算残差平方和（`ss_res`）和总平方和（`ss_tot`），以计算 R 平方得分，这是一个衡量回归模型拟合数据程度的指标。
- 最后，打印测试损失和 R 平方得分以供评估。该函数以元组形式返回测试损失和 R 平方得分。

## 模块 4：utils.py

实用模块通常是一组在整个项目不同部分中使用的函数的集合。在我们要做的案例中，只有一个函数 `spark_df_to_tensor`，它负责将 Spark DataFrame 列转换为 PyTorch 张量：

```python
import numpy as np
import torch
from typing import Tuple
from pyspark.sql import DataFrame

def spark_df_to_tensor(df: DataFrame) -> Tuple[torch.Tensor, torch.Tensor]:
    """
    将 Spark DataFrame 列转换为 PyTorch 张量。
    """
    features = torch.tensor(
        np.array(
            df.rdd.map(lambda x: x.scaled_features.toArray())
            .collect()
        ),
        dtype=torch.float32
    )
    labels = torch.tensor(
        np.array(
            df.rdd.map(lambda x: x.Close).collect()
        ),
        dtype=torch.float32
    )
    return features, labels
```

`spark_df_to_tensor` 函数接收 DataFrame 作为输入，并返回一个包含特征和标签（作为 PyTorch 张量）的元组。在函数内部，它使用 NumPy 和 PyTorch 进行必要的转换。这个函数对于训练和评估深度学习回归模型之前的数据预处理至关重要。

## 模块 5：main.py

现在我们来到主模块，它协调整个工作流程——数据预处理、模型训练、模型评估以及实用函数：

```python
import logging
import torch
import torch.optim as optim
import torch.nn as nn
from torch.utils.data import DataLoader
from typing import Tuple
from pyspark.sql import DataFrame
from data_processing import load_data, preprocess_data
from model_training import create_data_loader, train_model
from model_evaluation import evaluate_model
import utils

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def main(
    data_file_path: str,
    num_epochs: int = 100,
    batch_size: int = 32,
    learning_rate: float = 0.001
):
    """
    用于训练和评估特斯拉股价预测深度
    学习模型的主函数。
    参数:
        data_file_path (str):
            包含股价数据的 CSV 文件路径。
        num_epochs (int):
            模型训练的纪元数量。
            默认为 100。
        batch_size (int):
            训练期间数据加载的批次大小。
            默认为 32。
        learning_rate (float):
            优化器的学习率。
            默认为 0.001。
    异常:
        FileNotFoundError: 如果指定的数据
        文件未找到。
    """
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
    except FileNotFoundError as e:
        logger.error(f"File not found: {e}")
        raise
    # ... (代码继续)
```

