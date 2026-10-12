

# 模型性能评估

在本章中，我们将重点关注模型性能评估的关键概念、评估流程，以及评估模型拟合度所需的关键指标。正如[第 2 章](#chapter2.xhtml)所述，数据挖掘中的常见做法是使用不同的机器学习方法构建多个模型，然后比较它们的性能以选择最佳的“冠军”模型。在比较模型之前，我们必须首先确定用于评估模型拟合度的适当指标。

该领域存在一些可互换使用的术语，这可能会令人困惑。因此，我将提供这些术语的清晰定义和解释，以及何时使用它们。拥有这种基础性理解对于选择正确的指标和遵循适当的评估流程至关重要。重要的是要注意，本章涵盖的指标仅适用于监督学习，即存在预定义的目标变量，且目标是预测该变量。这些指标不适用于无监督学习，因为无监督学习不涉及预测。此外，关联模型（具有连续目标变量）使用的指标与分类模型（具有分类目标变量）使用的指标不同。因此，必须注意目标变量的尺度，以确保选择正确的指标。

## 基本概念

![](images/ufig6_2.jpg)

在深入探讨模型评估主题之前，我将介绍一些关键的基本概念，这些概念概述在[表 6.1](#chapter6.xhtml#tbl6_1)中。这些概念对于理解本章中使用的术语至关重要。随着我们的进展，请将该表作为参考。我将详细解释每个概念，您随时可以返回该表以复习记忆或在需要时查阅特定术语的定义。

**表 6.1** 模型性能评估中的基本概念 [返回正文.⏎](#chapter6.xhtml#b6tbl6_1)

| 术语 | 描述 |
| --- | --- |
| `Model fit` | `Model fit` 衡量模型与数据的拟合程度。它评估模型捕捉数据中模式和关系的程度。 |
| `Predictive power` | `Predictive power` 指模型准确捕捉和表现数据中潜在模式、关系或趋势的能力，并有效地将这些结果泛化到新的、未见过的数据集。 |
| `Overfitting` | `Overfitting` 发生在模型过度训练以拟合训练样本时，甚至捕捉到了数据中的噪声和微小波动。结果，模型无法泛化到其他数据集，使其对于现实世界的预测无效且不可用。 |
| `Model reliability` | `Model reliability` 指模型的内部一致性。这意味着模型在使用不同数据集的不同运行中产生一致的结果。 |
| `Model validity` | `Model validity` 指模型的准确性。这意味着模型始终能对目标变量产生准确的预测。 |
| `Champion model` | `Champion model` 是在我们训练和测试的所有模型中表现最佳的模型。 |
| `Prediction errors` | `Errors` 衡量训练模型与数据拟合不良的程度。误差越低，模型越准确。 |
| `Sum of squared error (SSE)` | `SSE` 衡量未解释的方差，即数据偏离模型预测值的程度。 |
| `Sum of squared regression (SSR)` | `SSR` 衡量已解释的方差，即均值偏离模型预测值的程度。 |
| `Sum of squared total (SST)` | `SST` 衡量总方差，即数据偏离均值的程度。 |
| `Root mean squared error (RMSE)` | `RMSE` 是关联模型的常用指标。它衡量数据集中预测值与实际值之间的平均差异，以与预测变量相同的单位表示。 |
| `Mean absolute percentage error (MAPE)` | `MAPE` 是关联模型的常用指标。它衡量数据集中预测值与实际值之间的百分比差异。 |
| `Relative squared error (RSE)` | `RSE` 是关联模型的常用指标。它衡量模型预测相对于始终预测实际值均值的简单基线模型的相对改进。 |
| `Explanatory power (EP)` | `EP` 指预测模型（特别是关联模型）解释或预测数据中观察到的变异性的能力。它衡量模型捕捉输入变量（预测变量）与目标变量之间潜在关系的程度。 |
| `Actual by Predicted Chart` | `Actual by Predicted Chart` 将实际值与预测值进行比较，展示训练模型与数据的拟合程度。 |
| `Residuals` | `Residuals` 衡量数据集中实际值与预测值之间的差异。 |
| `Residual by predicted chart` | `Residual by predicted chart` 不仅展示实际值与预测值的接近程度，还指示残差中的任何模式。 |
| `Confusion matrix` | `Confusion matrix`，也称为分类矩阵，是总结分类算法性能的表格。 |
| `True positive (TP)` | `TP` 是正确指示事件存在的预测。 |
| `True negative (TN)` | `TN` 是正确指示事件不存在的预测。 |
| `False positive (FP)` | `FP` 是错误地指示事件存在的预测。 |
| `False negative (FN)` | `FN` 是错误地指示事件不存在的预测。 |
| `Misclassification rate (MR)` | `MR` 衡量模型对目标变量（包括实际正例和实际负例）误分类（做出错误预测）的频率。 |
| `Prediction accuracy (ACC)` | `ACC` 衡量模型预测目标变量（包括实际正例和实际负例）的准确程度。 |
| `Sensitivity, recall, or true positive rate (TPR)` | `Sensitivity` 是正结果（事件）的概率，或模型预测真正例（事件）的能力。 |
| `Specificity, selectivity, or true negative rate (TNR)` | `Specificity` 是负结果（非事件）的概率，或模型预测真负例（非事件）的能力。 |
| `F1 score` | `F1 score` 是灵敏度（召回率）和精确率（阳性预测值）的调和平均数；高 `F1 score` 意味着低假正例 (`FP`) 和低假负例 (`FN`)。 |
| `Receiver operating characteristic (ROC) chart` | `ROC chart` 在垂直轴上显示真正例率，在水平轴上显示假正例率，反映灵敏度和特异性之间的平衡。 |
| `Lift chart` | `Lift` 是预测模型有效性的指标，计算为使用模型获得的结果与不使用模型获得的结果之比。`Lift chart` 或 `Lift curve` 展示提升值与响应率之间的图形表示。 |
| `Gini coefficient` | `Gini coefficient` 是模型区分能力的度量，即模型区分正例和负例的有效性。`Gini coefficient` 衡量某一特征的各属性间正例率的均等程度。 |
| `Cost sensitive learning` | `Cost sensitive learning` 是一种基于误分类成本来评估和选择模型的方法。 |
| `Decision matrix` | `Decision matrix` 是呈现误分类成本的表格，包括假正例的成本和假负例的成本。 |

## 模型拟合度与预测能力

![](images/ufig6_3.jpg)

