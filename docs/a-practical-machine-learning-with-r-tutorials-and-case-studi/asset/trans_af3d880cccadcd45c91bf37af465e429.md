

# 8.4 使用逻辑回归分析流失 213

从输出结果中可以看到，数据框 DataTestWithPred 包含了真实值（Churn）和估计值（.pred_class）的列。因此，我们可以使用 DataTestWithPred 来生成混淆矩阵：

```r
conf_mat(DataTestWithPred, truth=Churn, estimate=.pred_class)
```

| 真实 / 预测 | 是 | 否 |
|---|---|---|
| **是** | 239 | 150 |
| **否** | 322 | 149 |

接下来，创建一个新的指标命令，我们将其命名为 FctMetricsSet。FctMetricsSet() 命令接受与 `conf_mat()` 命令相同的参数，并输出准确率（accuracy）、灵敏度（sensitivity）和特异性（specificity）。

```r
FctMetricsSet=metric_set(accuracy, sensitivity, specificity)
FctMetricsSet(DataTestWithPred, truth=Churn, estimate=.pred_class)
```

```
## A tibble: 3 x 3
## .metric estimator estimate
## <chr> <chr> <dbl>
## 1 accuracy binary 0.777
## 2 sensitivity binary 0.426
## 3 specificity binary 0.903
```

一眼看去，一切看起来都很好。准确率约为 78%，特异性甚至达到了 90%。然而，灵敏度的结果并不理想。流失的客户中只有 43% 被正确识别。仅仅通过掷硬币来决定客户是否流失，就能给我们提供 50% 的灵敏度。

# 哪里出了什么问题？

使用下方代码中的 `count(DataTrain, Churn)` 命令提供了答案：

```
## Churn n
## 1 Yes 1308
## 2 No 3621
```

你可以看到训练数据集是不平衡的。训练数据集中未流失客户的观测数量是流失客户观测数量的三倍。这种不平衡的数据集导致优化器（Optimizer）产生偏差，倾向于预测 Churn = No（不流失）。⁸

> ⁸ 第 4.8 节中的信息框提供了关于不平衡数据集如何导致预测问题的更多详细信息。

下一节将介绍三种算法，可以帮助完全或部分地平衡不平衡数据集。之后，在交互式的第 8.6 节中，你将应用你的知识，重复本节执行的逻辑回归分析，但使用的是更平衡的数据集。

# 8.5 通过下采样、上采样和 SMOTE 平衡数据

在上一节中，由于数据集不平衡，预测结果倾向于过度代表的 Churn = No 类别，这被称为多数类（majority class）。多数类代表数据集中最常见的分类。相比之下，少数类（minority class）代表在数据集中很少发生的分类（在电信 Telco 数据集中为 Churn = Yes）。

轻微不平衡的数据集不会引起任何问题，但像 Telco 数据集这样，多数类有 3,621 个观测，而少数类有 1,038 个观测（见下文的表 8.2），会导致预测倾向于多数类。

处理不平衡数据集的最常用方法是从多数类中删除样本（下采样）和/或向少数类添加观测值（上采样）：

- **下采样（Downsampling）：** 该过程从多数类中随机删除观测值，直到多数类和少数类的观测值比例达到所需的比例（例如 1:1）。
- **上采样（Upsampling）：** 在最简单的版本中，上采样通过复制少数类中随机选择的观测值为少数类创建新的观测值，直到多数类和少数类的观测值比例达到所需的比例（例如 1:1）。

通常需要结合上采样和下采样，我们必须决定是同时平衡训练数据和测试数据，还是只平衡训练数据。正确的决定是平衡训练数据而不平衡测试数据。这是因为当模型完全训练完成后，测试数据用于评估模型在生产阶段面对新数据时的真实表现。因此，由于真实世界包含不平衡的数据，测试数据也应该包含不平衡的数据，既不经过下采样也不经过上采样。

在接下来的内容中，我们将介绍一种下采样方法和两种上采样方法。这些方法可以结合使用，也可以单独使用。本教程提供了相关的命令 `step_downsample()`、`step_upsample()` 和 `step_smote()`。这些命令默认只处理训练数据，而不处理测试数据。⁹

让我们从 `downsampling` 开始。在下面的代码中，我们首先加载 recipes 包（Harsley (2023)），然后将 `step_downsample()` 添加到我们在 8.4 节用于流失模型的 recipe 中。

```r
library(recipes)
set.seed(678)
recipe(Churn~, data=DataTrain) |
  step_dummy(Gender)|
  step_downsample(Churn)
```

稍后，我们将类似的 recipe 添加到 workflow 中，workflow 将执行平衡少数类和多数类的 recipe。

此时，我们想要弄清楚 recipe 是否成功改变了训练数据的位置。为了测试这一点，我们必须显式地将 recipe 应用于训练数据，并将其存储在一个新帧 `DataTrainBal` 中进行分析。

为此，我们使用 `juice()` 命令¹⁰ 它像从柠檬中挤出柠檬汁一样从 recipe 中提取训练数据。注意，你必须在 recipe 之后添加 `prep()`，以确保在用 `juice()` 提取数据之前执行其 执行。

```r
DataTrainBal <- recipe(Churn~, DataTrain) |
  prep() |
  juice()
count(DataTrainBal, Churn)
```

```
## tibble: 2 x 2
## Churn
## <int>
## 1 1388
## 2 No 1388
```

使用 `juice()` 命令后，你可以看到数据集现在是完美平衡的。当你将 `DataTrainBal` 中的数据与原始 Telco 训练数据相比（见下方的表 8.2）时，也可以发现我们可以丢失少数类的观测值，因为多数类被减少到了 1,388 个。当然，丢失这么多记录意味着丢失了大量信息。

> `skip` 参数决定 `step_*` 命令是应用于测试数据，还是跳过测试数据。对于大多数 `step_*` 命令，默认值是 `FALSE`，因为通常我们希望 `step_*` 同时应用于训练数据和测试数据。然而，`step_downsample()`、`step_upsample()` 和 `step_smote()` 的默认值为 `TRUE`，即跳过测试数据。

> ⁰ 在书中后续章节中，我们将不使用 `juice()`。因此，不需要跳过测试数据。

# 表 8.2 原始电信训练数据集计数

| Churn | n | Proportion |
|---|---|---|
| Yes | 1308 | 0.2654 |
| No | 3621 | 0.7346 |

这带来了上采样。上采样的原理是复制少数类中的观测值，直到少数类达到所需的数量（默认值与多数类数量相同）。下面的代码块与之前的代码块相同，只是用 `step_upsample()` 替换了 `step_dummy()`：

```r
library(recipes)
set.seed(678)
recipe(Churn~, data=DataTrain) |
  step_dummy(Gender) |
  step_upsample(Churn)

DataTrainBal = recipeChurn |
  prep() |
  juice()
```

```
## A tibble: 2 x 2
## Churn n
## <fct> <int>
## 1 Yes 3621
## 2 No 3621
```

count(DataTrainBal, Churn)
```

正如你所看到的，与表 8.2相比，数据集是平衡的。但是，由于我们复制了现有的观测值，我们并没有获得任何信息。

在这种背景下，通过上采样拥有相同的观测值并不是最佳解决方案。因此，需要改进的方法来增加少数类的数量。其中一种方法是 SMOTE（合成少数过采样；参见 Chawla 等人 (2002)）。SMOTE 的原理是人工生成少数类的观测值，这与现有观测值相似但不相同。SMOTE 算法通过 `recipes` 包中的 `step_smote()` 实现，工作如下：

1. 从少数类中随机选择一个观测值。
2. 使用 K 近邻（k-Nearest Neighbors）找到该观测值的最近邻（详情见第 4 节近邻算法）。
3. 根据步骤 1 选择的观测值及其最近邻，为每个预测变量计算随机加权平均值。
4. 使用计算出的变量值为少数类创建一个新观测。

重复步骤 1 到 4，直到少数类的观测数量达到所需的数量（默认值与多数类数量相同）。
下面的代码块与之前的代码块相同，只是我们使用了 `step_smote()`：

```r
library(recipes)
set.seed(678)
recipeChurn = recipe(Churn~, data=DataTrain) |
  step_dummy(Gender) |
  step_smote(Churn)

DataTrainBal = recipeChurn |
  prep() |
  juice()
```

在少数类和多数类观测值的结果与我们通过 `step_upsample()` 得到的结果相同。SMOTE 的改进在于

