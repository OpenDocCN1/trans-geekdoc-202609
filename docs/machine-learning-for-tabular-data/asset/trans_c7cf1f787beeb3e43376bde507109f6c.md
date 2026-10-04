

## LightGBM 简介

### 5.16 LightGBM 分类器

```python
from lightgbm import LGBMClassifier

accuracy = make_score(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)
lgbm = LGBMClassifier(boosting_type='gbdt',
                      n_estimators=100,
                      max_depth=5,
                      min_child_samples=3,
                      col_sample_bytree=0.8,
                      verbosity=0)
```

使用指定数量的估计器、最大树深度和最小子样本数初始化 LGBMClassifier

强制进行列级直方图构建

```python
model_pipeline = Pipeline([
    ('processing', column_transform),
    ('lightgbm', lgbm))
])

cv_scores = cross_validate(estimator=model_pipeline,
                           X=x_data,
                           y=target_median,
                           scoring=accuracy,
                           cv=cv,
                           return_train_score=True,
                           return_estimator=True)
```

创建一个包含列转换和 LGBMClassifier 步骤的模型流水线

```python
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"CV Accuracy {mean_cv:0.3f} ({std_cv:0.2f})")
print(f"fit time: {fit_time:0.2f}")
print(f"secs pred: {score_time:0.2f} secs")
```

使用模型流水线通过准确率评分进行五折交叉，并计算交叉期间期间测试分的标准差

以下是准确率、训练和预测时间的结果：

0.826 (0.004) fit: 1.16 secs pred: 

与 XGBoost 类似，LightGBM 通过 `n_estimators`、`learning_rate`、`lambda_1` 和 `lambda_2`（分别为 L1 和 L2 正则化）等参数来控制梯度下降。LightGBM 控制其复杂性最重要的参数如下：

- `max_depth`——该参数控制集合中每棵树的最大深度。值越大，模型的复杂度越高，使其越容易发生过拟合。如果设置为 -1，则意味着对树的生长不设限制。
- `num_leaves`——该参数指定了树中叶子节点的最大数量，因此决定了模型的复杂度。为了避免过拟合，该值应小于 `2**(max_depth)`。

## 第 5 章 决策树与梯度提升

- `min_data_leaf`——该参数控制每个叶子节点中所需的最小样本数。值越高可以防止树生长得过深导致过拟合，但如果设置得太高也可能导致欠拟合。默认值为 20。我们建议使用较小的值（如 10），然后进行测试，逐步将值增加到 300。

参数 `feature_fraction` 和 `bagging_fraction` 控制了 LightGBM 如何从特征和样本中采样：

- `feature_fraction`——该参数控制在每次分裂时考虑的特征比例。类似于 XGBoost 中的 `colsample_bytree` 参数，它可以帮助通过防止模型过度依赖任何特定特征来减少过拟合。
- `bagging_fraction`——该参数控制用于每棵树的数据比例。与 XGBoost 中的 `subsample` 参数不同，它能通过从数据中进行随机采样来帮助减少过拟合并改进训练。
- `bagging_freq`——该参数如果存在，决定了应用 bagging 的频率。当设置为 0 或指定了 `bagging_fraction` 时会禁用示例。值 `n` 意味着每 `n` 次迭代进行一次 bagging。例如，值 2 意味着你每两次迭代（一半的时间）进行一次 bagging。

与 LightGBM 在训练期间执行方式有关，`verbosity` 控制训练期间输出的信息量，而 `force_col_wise` 表示基于列构建用于树分裂的直方图。LightGBM 可以按列级或行级构建直方图。列级直方图构建通常更快，但可能需要更多内存，特别是对于数据集。行级直方图构建较慢，但在处理具有大量列的数据集时可能更节省内存。LightGBM 将自动为数据集选择构建直方图的最佳方法。你也可以通过设置 `force_col_wise` 或 `force_row_wise` 来强制 LightGBM 使用特定方法。对于 XGBoost ，LightGBM 也可以通过指定提升参数来使用不同的基础学习器：

- `gbdt`——默认选项，使用决策树作为基础学习器
- `rf`——实现随机森林
- `dart`——实现多加性回归

此外，如果你将 `linear_tree` 参数设置为 `true`（由于你使用的是默认的 `boosting=gbdt`），将拟合一个以线性模型作为终端节点的树。这是一种结合了决策树的非线性能力和线性外推能力的折中方案。

## LightGBM 简介

在后续章节，我们将仔细检查区分 LightGBM 和 XGBoost 的所有创新。

### 5.5.1 LightGBM 如何生长树

让我们检查区分 LightGBM 和 XGBoost 的每个特征，从 LightGBM 如何生长树开始。与其像 XGBoost 那样按层生长（也称为深度优先），LightGBM 是按叶子生长（也称为最佳优先）。这意味着算法选择提供最大信息增益的叶子节点并对其进一步分裂，直到不再有利为止。相比之下，层级方法会同时分裂相同深度的所有节点。

总结一下，在 XGBoost 的层级生长中，算法让所有叶子生长到同一层。然后它们同时进行分裂，这可能导致对最终预测贡献不大的叶子。相比之下，LightGBM 的叶子生长方法在每一步都分裂减少量最大的叶子，减少的叶子较少但准确性更高。叶子级减少允许 LightGBM 仅关注对目标变量影响最显著的特征。这意味着算法可以用较少的划分快速收敛到最优解。

图 5.10 显示了这两种方法的表示：左侧是叶子级方法，右侧是层级方法，两者都限制为具有终端节点。两种方法在所应用的规则和分割数据的方式方面采取了完全不同的路径。

![](img/def89cc47fa394c54bd34e78d91674_205.png)

图 5.10 叶子级（左侧）和层级（右侧）树生长的差异

需要指出的是，如果你允许两棵树使用相同的数据生长，一个使用叶子级方法，另一个完全使用层级方法，它们将定义相同的终端叶子和预测。区别在于它们的构建方式，叶子级方法在优先分裂提供最大收益的节点方面更为激进。在这种情况下，叶子级方法可以导致更小的树、更快的训练和更高的准确性，但它增加了过拟合的风险。为了控制叶子级生长的深度并解决过拟合，你可以控制 LightGBM 中的 `max-depth` 参数。

### 5.5.2 通过互斥分绑和基于梯度的单侧采样获取速度

为了进一步缩短训练时间，梯度提升等许多机器学习算法中的基本策略是减少处理的示例数量。减少处理值数量的最简单方法是通过随机采样（例如行缩减）和/或降维技术，如列采样或主成分分析（即列缩减）。虽然采样可以提高噪声数据的准确性，但过度采样会损害训练过程。在 LightGBM 中，基于梯度的单侧采样算法（GOSS）决定了采样的方式和程度。降维技术依赖于识别数据中的冗余并可以使用线性组合（通常是加权和）。然而，线性组合可能会破坏数据中的非线性关系。如果解决问题的成功取决于弱信号，那么丢弃信号会导致模型准确性下降。在 LightGBM 中，降维由互斥分绑（EFB）处理，这是一种在不丢失信息的情况下减少维度的方法。

让我们解释 LightGBM 的两个主要改进，从 EFB 如何工作开始。EFB 是一种在不损害数据完整性的情况下有效减少特征数量的技术。使用大量的独热编码和二进制特征，许多特征变得稀疏，值很少且充满零。你可以通过对这些特征求和并编码来保留所有非零值。LightGBM 通过将这些特征分组为互斥分绑来优化计算和数据维度，确保维持预测准确性。

图 5.1 显示了如何将两个特征绑在一起。解决方案是对所有非零值将特征 B 加到 A，使用特征 A 中的最大值。这种组合特征将保留原始特征的顺序，因为特征 A 的值与特征 B 的值是分开的，位于分布的不同区域。

寻找绑定互斥特征的最佳方法是一个复杂的问题，归类为 NP 类。然而，根据 Guolin Ke 及其团队的 LightGBM 论文，贪心算法可以通过自动绑许多特征提供良好的近似。特征分绑按顺序进行，选择重叠值最少的特征并将它们绑在一起。如果发现另一个重叠最小的特征，则继续绑。否则，启动一个新的绑，直到没有更多为止。停止规则由两个特征之间的冲突程度提供。

