
![](img/1c89d4486f90c87568fa6a42d46ae02a_318_0.png)

Figure 5-1. Actual vs. Predicted Values

  这张图允许对模型预测值与实际值之间的吻合程度进行可视化评估。我们可以看到点沿着对角虚线紧密聚集，这表明实际值与预测值之间存在强相关性，暗示模型性能良好。

## TensorFlow vs. PyTorch

  利用前一章中我们使用 PyTorch 的结果以及当前章节中使用 TensorFlow 的结果，我们现在可以比较这两种模型的性能。通过分析训练损失、测试损失和 R2 分数，我们可以了解这两种算法在预测 TSLA 股票价格方面的表现。

  下表比较了 PyTorch 和 TensorFlow 在前十个 epoch 和第 100 个 epoch 的训练损失：

| Epoch | PyTorch | TensorFlow |
| :--- | :--- | :--- |
| 1/100 | 48,533 | 41,731 |
| 2/100 | 40,969 | 40,362 |
| 3/100 | 26,663 | 39,658 |
| 4/100 | 13,865 | 33,450 |
| 5/100 | 3,026 | 19,520 |
| 6/100 | 1,683 | 5,492 |
| 7/100 | 1,077 | 2,532 |
| 8/100 | 475 | 1,984 |
| 9/100 | 1,195 | 1,657 |
| 10/100 | 1,362 | 1,231 |
| ... | ... | ... |
| 100/100 | 11 | 14 |

  基于此数据，我们可以做出以下评论：

- PyTorch 的初始训练损失值通常高于 TensorFlow。
- 两种框架都显示训练损失随着 epoch 的增加而持续下降，表明优化是有效的。
- PyTorch 和 TensorFlow 在损失减少方面表现出相似的趋势，两者最终都收敛到较低的值。
- 在某些 epoch 中，PyTorch 和 TensorFlow 之间的损失值存在微小差异，但总体而言，趋势是可比的。
- 在训练接近尾声时，两种框架都达到了较低的训练损失值，表明模型有效地收敛了。

  关于测试损失和 R 平方分数，我们有以下数据：

| Metric | PyTorch | TensorFlow |
| :--- | :--- | :--- |
| Test loss | 20.54 | 12.11 |
| R-squared | 0.998 | 0.998 |

  该表显示，PyTorch 模型获得的测试损失为 20.54，而 TensorFlow 模型实现了更低的测试损失 12.11。有趣的是，两种模型都表现出几乎相同的 R 平方值 0.998，表明在捕捉测试数据方差方面具有极高的解释力和预测准确性。尽管测试损失存在差异，但可比的 R 平方值表明两种框架在解释 TSLA 股票价格方面都产生了具有相似预测性能的模型。

  虽然这种比较在很大程度上是公平对等的（因为我们使用了相同的特斯拉股票数据集），但在 PyTorch 和 TensorFlow 中实现模型的实际差异超出了数据模型架构的范围。在 TensorFlow 中，静态计算图的使用要求预先定义模型的结构。这种方法允许 TensorFlow 优化图以提高性能，使其特别适合效率至关重要的生产环境。然而，这种静态特性可能会使开发过程变得更加僵化，因为对模型的任何修改都需要重新定义图。这可能会减慢模型优化的迭代过程，尤其是在灵活性至关重要的研究环境中。

  另一方面，PyTorch 的动态计算图允许实时修改，提供更灵活、更直观的开发体验。这种动态性使 PyTorch 在实验阶段具有高度优势，此时模型经常被调整和测试。能够随时更改图简化了调试，允许开发者在运行时检查和修改模型的行为，从而更快地迭代和解决问题。

  此外，每个框架的易用性和生态系统也起着至关重要的作用。TensorFlow，特别是自 TensorFlow 2.0 以来取得的进步以及 Keras 作为其高级 API 的持续集成，变得越来越易于访问和用户友好。该框架的综合生态系统，包括用于部署的工具如 TensorFlow Serving，使其成为从开发到生产的全流程机器学习流水线的可靠选择。

  相比之下，PyTorch 简洁的界面，加上其与 NumPy 等 Python 库的无缝集成，为开发者提供了更直观的体验，特别是对于深度学习新手来说。其生态系统正在快速发展，PyTorch Lightning 和 TorchServe 等工具进一步扩展了其功能。它仍然在研究环境中表现出色，其灵活性和易用性是其显著优势。

  最终，虽然两种框架都是强大且能够交付高性能模型的，但选择 TensorFlow 还是 PyTorch 往往取决于项目的具体需求。TensorFlow 的静态图和稳健的部署工具使其成为生产环境的有力候选者，而 PyTorch 的动态图和直观界面则特别适合研究和实验。

## Bringing It All Together

  在本节中，我们将整合本章代码探索中的各种元素，以开发一个内聚的代码库。我们还提供了更多关于为什么为模型选择特定层和激活函数的背景，以帮助读者理解设计选择。此外，我们包含一个 environment.yml 文件，以便读者轻松复制环境。

## Layers and Activation Functions

**Layer Selection:**
  模型使用一系列密集层，分别包含 64、32 和 16 个神经元。这种神经元数量的逐渐减少有助于模型通过更多神经元在初始层中捕获复杂模式，随后的层专注于精炼和降低数据复杂性。这种设计通过逐步缩小模型的关注点来帮助防止过拟合。

**Activation Function—ReLU:**
  ReLU（修正线性单元）被用作隐藏层中的激活函数，因为它在处理非线性数据和避免梯度消失问题方面效率很高。ReLU 以加速训练期间的收敛而闻名，使其成为许多深度学习模型的优选，特别是对于涉及股票价格等复杂数据的任务。

**Output Layer:**
  输出层由一个没有激活函数（线性）的单个神经元组成。这种选择对于旨在预测连续值的回归模型来说很典型。线性激活确保输出可以跨越所有可能的值，这对于准确预测股票价格是必要的。

### environment.yml

  此文件指定了项目中使用的 Python 包版本，使读者能够轻松重建相同的设置。

  以下是配置：

```
name: tsla_regression
channels:
 - defaults
dependencies:
 - python=3.12.3
 - numpy=1.26.4
 - tensorflow=2.17.0
 - pyspark=3.5.2
 - scikit-learn=1.5.1
 - matplotlib=3.9.2
```

### TensorFlow Regression Code

  以下是构建、训练和评估用于预测特斯拉股票价格的 TensorFlow 回归模型的代码：

```python
[In]: import logging
[In]: import numpy as np
[In]: import tensorflow as tf
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from sklearn.metrics import r2_score
[In]: from tensorflow.keras.models import Sequential
[In]: from tensorflow.keras.layers import Dense
[In]: import matplotlib.pyplot as plt
[In]: class TSLARegressor:
    """
    Class for TSLA stock price regression.
    """

    def __init__(self):
        """
        Initialize TSLARegressor object.
        """
        self.logger = logging.getLogger(__name__)
        self.spark = (SparkSession.builder
                      .appName("TSLA_Regression")
                      .getOrCreate())
        self.input_shape = None
        self.model = None

[In]:     def preprocess_data(
            self,
            file_path,
            feature_cols=['Open', 'High', 'Low', 'Volume'],
            train_ratio=0.8,
            seed=42
        ):
            """
            Preprocesses the data.

            Parameters:
            - file_path (str): Path to the CSV file.
            - feature_cols (list): List of feature columns.
            - train_ratio (float): Ratio of training data.
            - seed (int): Random seed for splitting data.
            """
```
