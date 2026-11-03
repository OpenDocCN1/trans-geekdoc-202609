
由 [表 8.13](#16_Chapter08.xhtml#tab8.13) 可观察到 `ntrees`、`max_depth` 和 `min_rows` 导致 `logloss` 显著改善。尽管 `gbm` 中还有其他感兴趣的参数，但它们似乎并不能改善 `NPS` 问题中的 `logloss`。

构建 `NPS` 模型的目的是在客户中识别出 `Detractors`。错误率为 0.40，该模型在正确预测 `Detractors` 方面似乎不如 `Random Forest` 模型。然而，在测试集上整体准确率为 71% 的情况下，`GBM` 比 `Random Forest` 模型更好。

我们可以利用一组微调后的参数并使用完整数据集，即 `filter_h2f`，来构建最终模型。

### 8.7.12 最终 GBM 模型

最终模型使用数据划分 (0.60,0.25,0.15) 并采用 `model_iter4` 参数构建，得出 [表 8.16](#16_Chapter08.xhtml#tab8.16)：

![](images/page321-01.png)

模型的准确率为 82%。

### 8.7.13 保存模型

模型现在可以用一组微调后的参数保存。

![](images/page321-02.png)

创建 `h2o` 的新实例后，可以调用此模型对新客户进行评分。假设 `test_h2f` 是新的一组客户，我们可以使用保存的模型来预测这些新客户的类别。参考 [第 8.4.13 节](#16_Chapter08.xhtml#sec8.4.13) 以了解保存的模型在对新案例进行评分时的使用方法。

## 8.8 使用 h2o 包的 XGBoost

`XGBoost` 是另一种流行的提升技术，它进一步基于梯度提升机 (`GBM`) 框架构建，并且是最佳的 `GBM` 框架之一。`XGBoost` 的目标函数使用损失函数的泰勒展开式推导而来。[⁴](#16_Chapter08.xhtml#ch8-r-fn4) `XGBoost` 也更强调正则化参数。

`XGBoost` 中的参数可分为通用参数、助推器参数和任务参数。

### 8.8.1 使用 h2o 的 XGBoost – 通用参数

通用参数与用于开发模型的 `booster` 相关。这些通常是树模型或线性模型：

`booster`: 可以是 `gbtree`、`gblinear` 或 `dart`；`gbtree` 和 `dart` 使用基于树的模型，而 `gblinear` 使用线性函数。默认值为 `gbtree`。

根据所选的 `booster`，其他助推器参数变得适用。`h2o` `XGBoost` 方法还能高效处理其他通用参数。

### 8.8.2 使用 H2O 的 XGBoost – 学习任务参数

在 `h2o` 中，`distribution`（即损失函数）参数决定了学习场景。选项包括 `AUTO`、`Bernoulli`、`multinomial`、`Gaussian`、`Poisson`、`gamma` 或 `Tweedie`（Anon, 2016）根据 doc.h2o.ai：

1. 对于 `Bernoulli` 分布，因变量列必须是二分类的。
2. 对于 `multinomial` 分布，因变量列必须是分类的。
3. 对于 `poisson` 分布，因变量列必须是数值型的。
4. 对于 `Tweedie` 分布，因变量列必须是数值型的。
5. 对于 `gaussian` 分布，因变量列必须是数值型的。
6. 对于 `gamma` 分布，因变量列必须是数值型的。

根据 docs.h2o.ai 网站，“默认执行 `AUTO` 分布。在这种情况下，算法将根据因变量列类型猜测模型类型。如果因变量列类型为数值型，`AUTO` 默认采用 ‘`gaussian`’；如果为分类型，`AUTO` 则根据响应类别的数量默认采用 `binomial` 或 `multinomial`（Anon, 2016）”。

### 8.8.3 使用 h2o 的 XGBoost – 助推器参数

这取决于所选的 `booster`。在 `h2o.xgboost` 中，对于 `booster = gbtree`，定义了以下助推器参数：

#### 随机子空间选择

以下方法可用于子空间选择（*Source:* docs.h2o.ai）：

1. “`col_sample_rate` (`colsample_bylevel`) – 该参数指定为每棵树随机选择的列的比例（不放回）。默认值是 1，但可以取 0.0 到 1.0 之间的任意值。该参数值越高，可能提高训练准确率。
2. `col_sample_rate_per_tree` (`colsample_by_tree`) – 该参数指定为每棵树随机选择的列的比例（不放回）。取值范围在 0.0 到 1.0 之间。默认值是 1，表示为每棵树的生长选择所有列。该参数与 `col_sample_rate` 协同工作。因此设置 `col_sample_rate = 0.7` 且 `col_sample_rate_per_tree = 0.7` 将导致在任何给定节点分裂时仅考虑 49% 的列。

#### 随机行选择（Bootstrap）

`sample_rate` (`subsample`) – 根据 docs.h2o.ai，该参数，“指定训练实例的行采样比例（*x*-axis）。请注意，此方法为不放回抽样。例如，将此值设置为 0.5 会使 `XGBoost` 随机收集一半的数据实例来生长树。默认值是 1，范围为 0.0 到 1.0。值越高可能提高训练准确率。当对列或行进行采样时，测试准确率会提高。详情请参阅‘Stochastic Gradient Boosting’（Friedman, 1999）”。

#### 类别不平衡

`max_abs_leafnode_pred` (`max_delta_step`): 根据 docs.h2o.ai，该参数，“指定每棵树权重估计中允许的最大增量步长。默认值是 0。将此值设置为 0 表示无约束。将此值设置为大于 0 可以使更新步骤更保守，并通过限制叶节点预测的绝对值来减少过拟合。此选项在类别极度不平衡时也有帮助。将值设置为 1-10 可能会有助于控制更新”。

#### 其他助推器参数

可用于控制树生长的参数（*Source:* docs. h2o.ai）。

1. `min_split_improvement` (`gamma`) – 该参数可通过限制树的生长来减少过拟合。该参数的值表示将节点分裂为两个所需的平方误差的最小变化。该参数的最佳值范围可在 10^(−10) 到 10^(−3) 之间。
2. `max_depth` – 这是另一个用于减少过拟合的参数。它用于控制树的生长深度。该参数值越高，树越复杂。如果值设为 0，则表示树生长无限制（高度复杂的树）。默认设置为 5。
3. `min_rows` (`min_child_weight`) – 指定叶节点的最小观测数，默认为 1。
4. `learn_rate` (`eta`) – 指定用于收缩特征权重的学习率。在每次提升步骤后收缩特征权重会使提升过程更保守并防止过拟合。`learn_rate` 的范围在 0.0 到 1.0 之间。该值默认为 0.3。
5. `reg_lambda` (`lambda`) – 权重上的 L2 正则化项，默认值为 1。增加该值会使模型更保守。
6. `reg_alpha` (`alpha`) – 权重上的 L1 正则化项，默认值为 0。增加该值会使模型更保守。

### 8.8.4 使用 h2o 的 XGBoost – 创建数据集

让我们创建用于训练的数据集。我们还将使用 `columns_weight` 参数来微调 `XGBoost` 模型。为此，我们将在 `filter_h2f` 数据框中创建一个 `WEIGHT` 列。

![](images/page323-01.png)![](images/page324-01.png)

```
sample_rate_per_class = c(Detractor = 1.0,passive = 0.102,Promoter 0.083),
```

![](images/page324-02.png)

`train`、`test` 和 `validate` 数据框的维度如下：

![](images/page324-03.png)

### 8.8.5 使用 h2o 的 XGBoost – 超参数

`h2o` 包具有 `XGBoost` 方法，可直接调用以构建 `XGBoost` 模型。如同在 `randomForest` 和 `gbm` 模型中一样，这里我们也将使用 `grid` 方法来微调超参数。让我们创建一个网格空间来搜索最佳超参数。

