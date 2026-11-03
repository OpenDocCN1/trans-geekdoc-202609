

### 2. `class_sampling_factors`
此参数可与 `balance_classes`（设为 `TRUE`）一起使用，以指定对数据进行上采样或下采样的程度。它要求我们按类词典顺序传递上采样或下采样比率。它是可选参数，如果未传递此参数，则采样因子将在模型训练期间自动计算。

### 3. `max_after_balance_size`
当 `balance_classes` 设为 `TRUE` 时，此参数用于控制训练数据的相对大小。值为 1.0 表示在消除类别不平衡后，将训练数据的大小设置为与原始训练集相同。

## 8.4.6 随机行选择（Bootstrap）
以下方法用于在 RF 中采样记录（*来源：* docs.h2o.ai）。

### 1. `sample_rate`
此参数指定为每个树随机选择的行的比例（无放回）。此参数取值介于 0.0 和 1.0 之间。默认值是 0.6320000291。此参数值越高，可能提高训练准确率。此参数可与 `col_sample_rate_per_tree` 一起使用以微调模型。

### 2. `sample_rate_per_class`
此参数是可选的，是 `sample_rate` 的替代项（二者其一可用）。对于集成模型中的每棵树，此参数可用于控制需要为每个类别无放回采样的行的比例。该参数期望传递一个列表，值介于 0 和 1 之间（行的相对比例）。这可用于在不使用 [第 8.4.5 节](#16_Chapter08.xhtml#sec8.4.5) 中描述的参数的情况下消除类别不平衡。

在使用 `sample_rate_per_class` 参数时，可忽略 `balance_classes` 和 `class_sampling_factors`。在 NPS 预测案例中，`sample_rate_per_class` 似乎比使用 `balance_classes` 和 `class_sampling_factors` 参数的任何组合效果更好。

## 8.4.7 控制生长
Brieman（2001）建议分类器，即随机森林中的决策树无需剪枝。然而，从实现角度来看，包提供了限制树生长的选项。以下参数可用于限制树的生长。

### 1. `min_split_improvement`
此参数可通过限制树的生长来减少过拟合。该参数值表示将一个节点拆分为两个所需的平方误差的最小变化。默认值设为 10^(−5)。此参数的最优值范围可在 10^(−10) 至 10^(−3) 之间。

### 2. `max_depth`
此参数用于减少过拟合。它用于控制树可生长的深度。此参数值越高，树越复杂。如果值设为 0，则表示树生长无限制（高度复杂的树）。默认值设为 20。

### 3. `min_rows`
此参数指定叶节点中必须存在的最小观测数。默认值设为 1，这可能导致过拟合问题。

## 8.4.8 随机森林（h2o）– 超参数
让我们创建一个列表并为每个超参数提供值：

![](images/page300-01.png)

## 8.4.9 随机森林（h2o）– 搜索标准
在上一节中，我们为三个参数创建了一个值列表 `hyper_params`，以便找到最佳组合值。`hyper_params` 中的值可通过采用 `strategy = Cartesian` 或 `strategy = RandomDiscrete` 进行搜索。

### 1. 指定搜索标准
指定 `search_criteria = list(strategy = "Cartesian")` 将应用 Cartesian 策略。

Cartesian 将搜索超参数的所有组合。然而，如果基础设施有限或超参数组合数量过大，则可能需要 RandomDiscrete。在 RandomDiscrete 策略的情况下，有三种随机搜索空间并指定何时停止搜索的方法：

### 2. 最大模型数
`search_criteria = list(strategy = "RandomDiscrete", max_runtime_secs = 600, max_models = 100, stopping_metric = "AUTO", stopping_tolerance = 0.00001, stopping_rounds = 5, seed = 123456)`

### 3. 最大时间
`search_criteria = list(strategy = "RandomDiscrete", max_models = 42, max_runtime_secs = 28800)`

### 4. 基于指标的提前停止
`search_criteria = list(strategy = "RandomDiscrete", stopping_metric = "AUC", stopping_tolerance = 0.00001, stopping_rounds = 5)`

我们可以在验证 logloss 连续五次评分事件中至少未改善 0.01% 时应用提前停止。

![](images/page301-01.png)

## 8.4.10 随机森林 – 网格搜索
在使用 `caret` 包在 [第 6 章](#14_Chapter06.xhtml) 和 [第 7 章](#15_Chapter07.xhtml) 中时，我们讨论了基础包中的 `expand.grid()` 方法。`expand.grid()` 方法有助于从所提供的向量，即 `hyper_params` 的所有组合创建数据框。h2o 中的类似方法是 `grid`。我们将使用 h2o 的 `grid` 方法并传递模型参数、搜索标准和超参数列表。也传递 `train` 和 `validate` 数据框。

默认情况下，`grid` 方法的 `balance_classes` 参数会对案例进行上采样。为了应用下采样，让我们计算下采样的比例。**[表 8.5](#16_Chapter08.xhtml#tab8.5)** 显示了 `train_h2f` 中 `NPS_CLASSIFICATION` 的案例数量。

**表 8.5** | `train_h2f` 中 `NPS_CLASSIFICATION` 的案例数量

| `NPS_CLASSIFICATION` || 计数 |
| --- | --- |
| Detractor || 59 |
| --- | --- |
| Passive || 573 |
| Promoter || 709 |

为了下采样并使观测值与 Detractor 类别成比例：
1. 将 Passive 下采样为 59/573 = 0.102（约）
2. 将 Promoter 下采样为 59/709 = 0.083（约）

因此 `grid` 方法中的 `class_sampling_factors` 可设为 `class_sampling_factors = c(1.0,0.102,0.083)`。数字是按照类别的词典顺序书写的。

另一个选项是在 `grid` 方法中设置 `sample_rate_per_class` 为：
`sample_rate_per_class = c(1.0,0.102,0.083)`。数字是按照类别的词典顺序书写的。

在尝试上述两种选项用于多类分类问题时，我们发现 `sample_rate_per_class` 与使用 `class_sampling_factors` 相比效果更好。

具有不同超参数组合的模型将在 `validation_frame` 和/或交叉验证框架（`nfolds`）上使用适用指标进行验证。

![](images/page302-01.png)

`h2o.grid` 还有 `parallelism` 作为参数，可用于在模型训练时定义并行处理。
1. 值为 1 表示顺序构建，是此参数的默认值。
2. 值为 0 表示自适应并行，即 h2o 包将决定如何利用并行处理。
3. 值大于 1 表示并行构建这么多模型。

![](images/page303-01.png)

我们将在构建 `gbm` 和 `xgboost` 模型时使用 `parallelism`。请注意，`grid` 方法还具有诸如 `calibrate_model` 和 `calibration_frame` 等参数。这些用于改进集成模型（`randomforest`、`gbm`、`xgboost`）关于概率估计（Platt 缩放）的性能。然而，目前它仅在二元分类问题中有效。

## 8.4.11 模型诊断
在本节中，我们将讨论模型诊断。我们可以使用以下指标之一对模型进行排序：

`r2`, `mean_per_class_accuracy`, `max_per_class_error`, `err`, `total_rows`, `rmse`, `accuracy`, `err_count`, `logloss`, `mse`, `mean_per_class_error`

