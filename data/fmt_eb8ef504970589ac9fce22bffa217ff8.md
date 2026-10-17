
- **R 方系数 (`R²`)**：表示模型所解释的目标变量方差比例。值越接近 `1.0` 表示性能越好。

让我们来看一个 `scikit-learn` 中的评估用例：

```python
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score
import numpy as np
# 预测
preds = lr.predict(X_test)
# 评估指标
print("MAE:", mean_absolute_error(y_test, preds))
print("MSE:", mean_squared_error(y_test, preds))
print("RMSE:", np.sqrt(mean_squared_error(y_test, preds)))
print("R^2:", r2_score(y_test, preds))
```

这段代码展示了在 ChatGPT 等 AI 工具的帮助下如何快速生成并执行一个完整的评估流，特别是当配合如下提示词时：

# 使用 Scikit-learn 中的 MAE、MSE、RMSE 和 R² 评估回归模型。

> AI 提示：如果你从事业务或金融工作，可以让 ChatGPT 包含平均绝对百分误差 (`MAPE`)，因为基于百分比的误差具有更高的可解释性。

通过 AI 驱动的评估指导，开发者可以更好地解释其模型的性能，并快速识别进一步调优和改进的机会。

# AI 驱动的房价预测用例

一家房地产分析初创公司致力于开发一种利用结构化房产数据预测房价的智能解决方案。他们的目标是在不牺牲准确性或代码质量的前提下，快速交付一个高性能的模型。

该团队在整个模型开发周期中一直依赖 ChatGPT 作为 AI 助手来实现这一目标。以下是他们构建方法的方法：

- **流线自动化**：使用 ChatGPT

- **模型探索**：他们从 **`LinearRegression`** 开始建立一个简单的基准，然后过渡到 **`GradientBoostingRegressor`** 以捕捉非线性关系并提高性能。

- **超参数调优**：通过 ChatGPT 提示词，他们实现了 **`GridSearchCV`** 来调整学习率、估计器数量和树深度。

- **深度学习比较**：为了测试模型表达能力的极限，他们构建了一个基于 Keras 的 MLP，集成了 dropout 正则化和早停以防止过拟合。

- **性能评估**：团队使用 RMSE 和 `$R^2$` 衡量结果，实现了模型在准确性和解释力方面的直接比较。

**结果**：在 AI 辅助编程的支持下，该团队在不到一周的时间内交付了一个完全运行的回归模型。该项目受益于：

- 更快的迭代周期。

- 更整洁、模块化的代码。

- 预测准确性的提高，特别是对于 Gradient Boosting 和 MLP 模型。

最重要的是，ChatGPT 生成的建议帮助团队做出了更智能架构和调优决策，在保持稳健结果的同时加速了开发。

# 实现多层感知器模型

多层感知器 (`MLP`) 是强大且灵活的神经网络架构，广泛应用于分类和回归任务。凭借其分层结构和对线性学习的支持，MLP 可以模拟数据中的复杂模式，特别是在设计和调优有效的情况下。ChatGPT 和 GitHub Copilot 等 AI 工具通过提供架构建议、正则化提示和现用代码模板，使构建、优化和评估 MLP 变得更容易。本节探索了 Keras 和 PyTorch 中的 MLP 实现，并提供了贷款违约预测的实际指导和现实用例。

## MLP 架构与连接

每个 MLP 的核心都是结构化的、基于层的设计，使其能够从数据中学习。尽管概念上简单，但架构和训练选择的灵使得 MLP 能够解决各种机器学习问题。

让我们分解定义 MLP 的关键组件：

- **输入层**：接收输入特征集。神经元的数量与输入特征的数量对应。

- **隐藏层**：一个或多个中间神经元层，通常使用线性整单元 (`ReLU`) 激活函数。这些层使网络能够捕捉数据中的复杂关系。

- **输出层**：末端根据任务而异。二分类通常使用 `sigmoid` 函数；对于多分类使用 `softmax`；对于回归任务则使用线性输出。

- **损失函数**：通过量化预测值与实际目标之间的差异来引导学习。损失函数的选择取决于任务。

- **优化器**：在训练期间更新模型权重。常见的优化器包括 `Adam`（自适应学习）和**随机梯度下降 (`SGD`)**。

## 输出、任务与损失函数

表 8.6 为不同类型的机器学习任务选择正确的输出激活函数和损失函数提供了快速参考：

| 任务类型 | 输出激活函数 | 损失函数 |
|---|---|---|
| 二分类 | Sigmoid | Binary crosentropy |
| 多分类 | Softmax | Categorical crosentropy |
| 回归 | Linear | Mean squared error |

**表 8.6**：按任务划分输出层和损失函数

AI 提示：根据数据集的大小、维度和复杂性，让 ChatGPT 推荐理想的隐藏层数和每层神经元数。你还可以提示它使用 Keras 或 PyTorch 生成建议的层宽度、激活函数选择和 dropout 率。

通过利用 AI 工具微调架构，开发者可以更快地获得适用于其用例的高性能 MLP 模型。

## 使用 Keras 进行分类的 MLP

Keras 提供了一个直观且高级的 API 来构建深度学习模型，是实现用于分类的 MLP 的理想选择。通过几行代码，开发者就可以定义稳健的架构，并利用正则化和早停等最佳实践来提高泛化。

以下是一个使用 Keras 的 Sequential API 构建用于二分类 MLP 的示例：

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout
from tensorflow.keras.callbacks import EarlyStopping
```

```python
# 定义模型架构
model = Sequential(
Dense(128, activation='relu', input_shape=(X_train.shape[1]),),
Dropout(0.3), # 防止过拟合的正则化
Dense(64, activation='relu'),
Dense(1, activation='sigmoid') # Sigmoid 用于二分类
)
```

```python
# 编译模型
model.compile(
optimizer='adam',
loss='binary_crossentropy',
metrics=['accuracy']
)
```

```python
# 早停法：在验证性能停止改进时停止训练
early_stop = EarlyStopping(patience=3, restore_best_weight=True)
```

```python
# 训练模型
model.fit(
X_train, y_train,
epochs=30,
batch_size=32,
validation_split=0.2,
callbacks=[early_stop]
)
```

### MLP 模型的关键函数

模型架构和训练设置设计如下，以有效处理具有潜在类别不平衡的二分类：

- 输入层：接收来自 `X_train` 的特征向量。

- 隐藏层：两个使用 `ReLU` 激活函数的全连接层，并使用 `Dropout` 进行正则化。

- 输出层：单个带有 `sigmoid` 激活函数的神经元，用于输出二分类的概率。

- 优化器：`Adam`，能够调整学习率以实现更快收敛。

- 回调函数：`EarlyStopping` 在验证集上连续三个 epoch 内没有观察到改进时停止训练。

> AI 贴士——你可以提示 ChatGPT：在 Keras 中构建一个带有 dropout 和早停的二分类 MLP，以便立即获得此经过优化的、生产就绪的代码，包括架构建议和调优选项。

## 使用 Keras 进行回归的 MLP

MLP 不局限于分类；当设计得当时，它们对于回归任务也非常有效。在 Keras 中构建用于回归的 MLP 需要量身定制输出层、损失函数和评估指标，以匹配连续的变量变量。

以下是一个使用 Keras 用于回归问题的样本 MLP 实现：

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout
# 定义回归模型
```

```python
model = Sequential([
    Dense(64, activation='relu', input_shape=(X_train.shape[1],),
    Dropout(0.2), # 有助于防止过拟合
    Dense(64, activation='relu'),
    Dense(1) # 连续输出不需要激活函数
])
# 使用回归特定的损失函数和指标编译模型
model.compile(
    optimizer='adam',
    loss='mse',      # 回归使用的均方误差
    metrics=['mae'] # 平均绝对误差作为额外指标
)
# 使用早停法训练模型
model.fit(
    X_train, y_train,
    epochs=50,
    validation_split=0.2,
    callbacks=[early_stop]
)
```

### 关键组件与考虑

在设计和训练用于回归任务的神经网络时，以下关键组件和考虑至关重要：

- **输出层**：单个没有激活函数的神经元，用于产生连续的数值。

- **损失函数**：`MSE` 广泛用于回归任务，以惩罚较大的误差。

- **指标**：`MAE` 提供了关于平均预测误差更具解释性的视角。

- **Dropout 正则化**：用于隐藏层之间，以减少过拟合，特别是在较小数据集上。

- **早停**：重用上一节中的 `early_stop` 回调函数来监控验证损失并避免过度训练。

> **AI 贴士**——**你可以这样提示 ChatGPT：** *使用 ReLU 激活和 dropout 创建一个 Keras回归 MLP，使用 MSE 损失和 MAE 指标，以立即获得像之前共享的那种结构化、优化的模型。*

## 使用 PyTorch 使用 MLP

PyTorch 为寻求更大控制和灵活性的开发者提供了一种动态且模块化的方法来构建和训练 MLP。相比于 Keras 的上手操作，PyTorch 允许进行精确的定制，使其成为研究、实验和生产规模部署的首选。

以下是一个使用 PyTorch 构建用于二分类 MLP 的样本实现：

```python
import torch
import torch.nn as nn
import torch.nn.functional as F
# 定义 MLP 架构
class MLP(nn.Module):
    def __init__(self, input_dim, output_dim):
        super().__init__()
        self.fc1 = nn.Linear(input_dim, 128)
        self.fc2 = nn.Linear(128, 64)
        self.fc3 = nn.Linear(64, output_dim)
    def forward(self, x):
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        return self.fc3(x)
```

### 初始化模型、损失函数和优化器

```python
model = MLP(X_train.shape[1], 1).to(device)
criterion = nn.BCEWithLogitsLoss() # 结合了 sigmoid + 二元交叉熵
optimizer = torch.optim.Adam(model.parameters(), lr=0.01)
# 训练循环
for epoch in range(30):
  model.train()
  outputs = model(X_train_tensor)
  loss = criterion(outputs.squeeze(), y_train_tensor)
  optimizer.zero_grad()
  loss.backward()
  optimizer.step()
```

### 影响模型有效性的因素

以下设计选择有助于模型高效处理二分类任务：

- **模型架构**：使用 `ReLU` 激活函数的简单三层 MLP，适用于隐藏层。

- **损失函数**：`BCEWithLogitsLoss()` 以数值稳定的方式结合了 sigmoid 和二元交叉熵。

- **优化器**：`Adam` 用于自适应学习率，适用于深度网络。

- **设备支持**：通过 `.to(device)` 将模型传输到 GPU，加速训练。

> AI 贴士——使用 ChatGPT 自动生成：

- 完整的训练和验证循环。

- 针对大型数据集的 DataLoader。

 使用 使用 `torch.save` 和 `torch.load` 的模型保存逻辑。提示示例：

> "带有验证和检查点的完整 PyTorch 分类流水。"

这可以大幅减少重复工作并帮助团队扩展项目。

## 正则化与优化技巧

在训练 MLP 时，获得高性能不仅需要良好的架构，还需要对正则化和优化技术的仔细应用。这些策略有助于提高泛化能力、防止过拟合并加速收敛。

在本节中，我们涵盖了一些最有效的技术，这些可以通过 ChatGPT 和 Copilot 等 AI 工具轻松集成。

### 早停

在训练期间监控验证损失，并在多个 epoch 内没有改进时停止过程。早停是一种监控验证损失以防止过拟合的训练策略，具有以下关键优势：

- 在最佳点停止训练以防止过拟合。

- 对于较小数据集或使用强大的模型特别有效。

### 批量归一化

在批次内归一化激活以稳定并加速学习。通常放在全连接层之后激活函数之前。批量归一化是一种用于稳定和加速神经网络训练的技术，其优点如下：

- 有助于减少内部协方差。

- 允许更高的学习率和更快的训练。

### 学习率调度

根据验证损失等指标动态调整学习率。

- 技术包括：

  - `ReduceLROPlateau`：当验证损失停滞时降低学习率。

  - `ExponentialDecay` 或 `StepDecay`：随时间预定义的减少。

> AI 贴士使用 ChatGPT 提示词如：

- 为带有 ReLU 激活的三层 MLP 建议 dropout 率。

- 为我的 Keras 模型添加 ReduceLROPlateau 以稳定学习。

- 在 Sequential Keras 模型中应该在哪里插入 BatchNormalization？

AI 工具可以根据你的模型和数据集推荐超参数并生成完整的实现。

## 使用多层感知机预测贷款违约的案例

一家金融机构决定使用结构化借款人数据（如收入、信用历史和就业状况）构建一个贷款违约风险的预测模型。虽然传统的随机森林模型已经交付了

为了获得合理的结果，团队希望探索深度学习方法以获得更好的性能和适应性。

团队将 ChatGPT 集成到他们的工作流中，以加速开发并缩短实验时间。这个 AI 驱动的助手帮助指导了架构决策、优化策略和模型评估技术。

### AI 辅助开发工作流

以下步骤概述了一个 AI 辅助开发工作流，其中 ChatGPT 在指导设计、训练优化和评估方面发挥了关键作用：

- 1. **MLP 架构设计**：ChatGPT 帮助团队使用 Keras 构建了一个 3 层 MLP，结合了 Dropout 和批归一化（batch normalization）以增强泛化能力并防止过拟合。

- 2. **训练优化**：在 ChatGPT 的建议指导下，团队实现了 EarlyStopping，以监控验证损失并在最佳 epoch 处停止训练。

- 3. **模型评估**：使用 ROC-AUC 和 F1 分数衡量了 MLP 的性能，确保对贷款违约预测中常见的不平衡数据集进行稳健的评估。

### 结果

与基准模型相比，通过 AI 辅助 MLP 实现了以下结果：

- MLP 优于之前的随机森林基准模型，验证指标上提升了 10%。

- 得益于 dropout、批归一化和 AI 引导调优，模型在未见数据上表现出更好的泛化能力并减少了过拟合。这一用例说明了 AI 辅助编程在现实世界的影响，它使金融等高风险领域能够更快速迭代、更智能的架构选择以及真实的性能提升。

## 构建和微调卷积神经网络

卷积神经网络（CNN）是现代计算机视觉系统的基础，用于捕捉图像数据中的空间模式。凭借其分层架构和跨复杂视觉任务的泛化能力，CNN 是分类、检测和医学影像的理想选择。像 ChatGPT 和 GitHub Copilot 等 AI 工具使得设计、训练和微调 CNN 变得更快更高效，指导了从架构设计到迁移学习和超参数调优的所有过程。本节将探讨 CNN 基础、在 Keras 和 PyTorch 中的实现，以及一个由 AI 辅助驱动的真实医疗应用。

在代码中探索 CNN 架构之前，理解如何评估模型性能（尤其是在分类任务中）至关重要。

## 分类模型的评估

在分类任务中，仅仅衡量模型正确的频率是不够的。你需要评估它区分类别的良好程度、如何处理不平衡，以及产生何种类型的错误。选择正确的指标对于构建不仅准确而且在实际部署中既可靠又有效的模型是关键。让我们来看一些关键的评估指标。

## 准确率 (Accuracy)

准确率是一种广泛使用的评估指标，但其有效性取决于数据分布，概述如下：

- **衡量内容**：在所有预测中正确预测的比例。

- **注意事项**：在使用不平衡数据集时可能会产生误导。例如，一个总是预测多数类别的模型可以获得高准确率，但无法检测到少数类情况。
