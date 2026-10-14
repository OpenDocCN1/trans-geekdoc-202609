
对于每个数据点 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>x</mi></math>![x](images/c003_dequ14.png)，Z-score <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>z</mi><mo>=</mo><mfenced close=")" open="("><mrow><mi>x</mi><mo>&#8211;</mo><mi>&#956;</mi></mrow></mfenced><mo>/</mo><mi>&#963;</mi></math>![z equals open paren x minus mu close paren all over sigma](images/c003_dequ15.png)。

因为正态分布具有以下特征：

*   一个标准差覆盖约 68% 的数据。
*   两个标准差覆盖约 95% 的数据。
*   三个标准差覆盖约 99.7% 的数据。

Z-score 大于 3 或小于 –3 的数据点被视为异常值。换句话说，可以统计学上安全地假设 Z-score 大于 3 或小于 –3 的 0.3% 数据点距离均值足够远，可被视为异常值。

Z-score 异常值检测方法也可以通过编程方式计算。以下代码片段展示了如何操作：

```python
import numpy as np
import pandas as pd
from scipy import stats

# Load dataset
data = np.array([[4, 11], [3.8, 12], [4.5, 12.5], [8, 8], [9, 8.5], [9.5, 7.5], [13, 5], [14, 4.7], [13.7, 6], [25, 23]])
df = pd.DataFrame(data, columns=['Feature1', 'Feature2'])

# Detect outliers using Z-score
z_scores = np.abs(stats.zscore(df))
outliers = (z_scores > 3).any(axis=1)
df['Outlier'] = outliers

print("Original Data with Outlier Flags:")
print(df)

# Treat outliers by removing them
df_cleaned = df[~df['Outlier']].drop(columns='Outlier')

print("\nCleaned Data without Outliers:")
print(df_cleaned)
```

上述代码生成的输出如 [Figure 3.11](#c003.xhtml#c03-fig-11) 所示。

![FIGURE 3.11 Failing outlier detection.](images/c03f011.png)

[FIGURE 3.11](#c003.xhtml#rc03-fig-11) Failing outlier detection.

可以看到，Z-score 方法未能检测出异常值 `[25, 23]`。这是因为我们数据集中数据点的分布不是正态分布，而是右偏分布。

使用 AWS Glue DataBrew，您还可以检测数据中的异常值，并使用各种转换进行处理。这种方法包括使用您刚学到的方法（即 Z-score 和 IQRs）来替换、移除、重新缩放或标记异常值。

## 执行去重

去重是从数据集中移除重复数据点的过程。去重不仅仅是整理数据——它关乎使您的模型更准确、性能更高、更可靠。

从数据质量角度来看，重复数据会扭曲结果并导致不准确的预测。移除重复项可确保用于训练模型的数据干净且准确。

模型性能和可靠性是 ML 生命周期中模型评估和部署阶段需要考虑的关键因素。重复项可能导致过拟合，即模型学习的是噪声而非信号。干净、去重的数据有助于创建更具泛化能力的模型。

从可靠性角度来看，重复项可能引入偏差，特别是当某些条目重复出现的频率高于其他条目时，会导致训练数据不平衡。

因此，有效的去重策略对于确保 ML 模型训练数据的质量至关重要。

为追求简单易用，AWS Glue DataBrew 可能是从数据集中移除重复项的最佳选择。AWS Glue DataBrew 提供了直观的可视化界面，无需复杂代码即可清理和准备数据。AWS Glue DataBrew 用户友好且高效，使移除重复项等数据清理任务变得快速且无麻烦。

## 标准化和重新格式化

通过实施标准化，您可以防止具有大数值的特征相比数值较小的特征对模型产生不成比例的影响。此技术对于对特征尺度敏感的 ML 算法（如线性回归和支持向量机）尤为重要，这些将在下一章介绍。

ML 中的重新格式化是指将数据重构为适合分析的统一格式。它包括转换数据类型、协调格式，并确保所有数据条目遵循相同结构。

要使用 AWS 执行标准化和重新格式化，可以使用 Amazon SageMaker 和 AWS Glue。主要步骤如下：

*   **加载数据。** 您可以使用 SageMaker 笔记本从 S3 存储桶加载数据集，如以下代码片段所示：

```python
import pandas as pd
data = pd.read_csv('your_dataset.csv')
```

*   **标准化数据。** 您可以使用 `sklearn.preprocessing` 模块中的 `StandardScaler` 类来标准化特征，如以下代码片段所示：

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
data_scaled = scaler.fit_transform(data)
```

更多归一化和标准化技术将在后续章节介绍。

*   **导出数据。** 您可以将标准化后的数据集保存到 S3。
*   **创建 AWS Glue 作业。** 创建 AWS Glue 作业以根据需要重新格式化数据。
*   **加载干净数据。** 使用清理和标准化后的数据训练 ML 模型。

## 移除噪声和错误

前文简要介绍了自然噪声和人为错误。因为特征工程的主要目标是为 ML 模型生成尽可能最佳的训练数据量，所以该过程的关键方面之一是处理噪声和错误的能力。

通过创建新特征或转换现有特征，您可以使训练数据对 ML 模型更具信息量和相关性。此过程有助于提高模型准确性、效率和泛化能力，从而增强模型的预测能力。

在有噪声的数据上训练的模型往往会学习训练数据集中存在的特定怪癖或错误，而不是潜在模式。这会导致*过拟合*，即模型在训练数据上表现很好，但在新的、未见过的数据上表现不佳。通过妥善处理噪声和错误，您有助于确保模型更好地泛化到真实场景。我们将在[第 5 章](#c005.xhtml#c005)详细介绍解决过拟合的方法。

# 特征工程技术

在上一节中，介绍了清理数据集的方法。数据清理是为模型准备训练数据的初步步骤。

下一步的目标是有效地将原始数据转化为能提高 ML 模型性能的有意义特征。这是特征工程的主要关注点。最终，经过特征工程后，您的 ML 模型将准备好进行训练。

掌握特征工程对于展示您在 AWS 上构建和部署可扩展、高效 ML 解决方案的专业知识至关重要。后续章节将介绍考试所需的特征工程技术。

我们将从结构化数据的技术开始，然后介绍以图像、文本和时间序列形式存在的非结构化数据技术。

## 结构化数据技术

对于结构化数据，您可以使用多种特征提取技术来降低数据集的维度。使用特征提取时需要注意的一点是：当您将模型投入生产或自动化管道时，这些特征可以轻松复制，但仍能降低数据的高维度。

### 数值数据的特征工程

数值数据最终是您想要输入 ML 模型的数据类型。无论您的数据是分类、文本还是图像，特征工程的结果都需要以一组独特且组织良好的数字形式呈现，以便用于训练 ML 算法。
