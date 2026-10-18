

### Shrinkage

`Shrinkage` 在集成中充当学习率。与梯度下降一样，你必须设定一个合适的学习率，以避免跳得太远而偏离解，这与 GBM 相同。较小的 shrinkage 值会带来更好的预测。

### Subsampling

`Subsampling` 模拟了 pasting 方法。如果每棵后续树都基于训练数据的一个子样本构建，结果就是一种随机梯度下降。对于许多问题，pasting 方法有助于减少噪声和异常值的影响，从而改善结果。

### Trees of fixed size

`Trees of fixed size`：在 boosting 中固定树的深度，就像为你放入集成中的学习函数设定一个复杂度限制，但依赖于比 Adaboost 中使用的树桩更复杂的树。深度就像多项式展开中的幂次：树越深，展开越大，从而既增加了拦截复杂目标函数的能力，也增加了过拟合的风险。

Scikit-learn 使用本章迄今描述的所有特性实现 GBM。你可以在 [`https://scikit-learn.org/stable/modules/ensemble.html#gradient-boosting`](https://scikit-learn.org/stable/modules/ensemble.html#gradient-boosting) 处找到 GBM 的讨论。以下示例延续了之前的测试。在此示例中，你为葡萄酒质量数据集创建一个 GBM 分类器并测试其性能（此示例可能也会运行一段时间）：

```
from sklearn.ensemble import GradientBoostingRegressor
gbm = GradientBoostingRegressor(n_estimators=500, subsample=0.9, max_depth=12, learning_rate=0.1, random_state=42)
gbm.fit(X_train, y_train)
preds = gbm.predict(X_test)
mae = mean_absolute_error(y_test, preds)
print(f"test mean absolute error for gbm: {mae:0.3}")
```

### Considering the state of the art in tabular data

Scikit-learn 的梯度提升实现不是创建数据模型更好性能解决方案的唯一可用方案。梯度提升是一种算法，你可以通过改进决策树的构建方式、分割方式以及算法处理缺失数据和分类特征的方式来完善它。

第一个替代梯度提升包是 XGBoost ([`https://github.com/dmlc/xgboost`](https://github.com/dmlc/xgboost))，这是一个因其速度和相对于现有 Scikit-learn 版本的增强性能而令人惊叹的解决方案。特别是，XGBoost 利用现有计算机的多核计算能力，尽管 GBM 是一种顺序算法。XGBoost 通过在决策树内部找到最佳分割来实现这一点。然后它并行化并使算法操作可以在多台计算机上分布。

接下来，Microsoft 创建了 LightGBM ([`https://github.com/Microsoft/LightGBM`](https://github.com/Microsoft/LightGBM))，它比 XGBoost 更快（因为它使用了一些聪明的近似），并且在某些问题上表现更好，因为它以不同的方式构建决策树。LightGBM 使用深度优先搜索策略；也就是说，它构建非常深的树，猜测某些示例比广度优先方法更好，在广度优先方法中，你构建宽树以尽可能多地拟合示例。

另一个解决方案是来自俄罗斯搜索引擎 Yandex 的 CatBoost ([`https://catboost.ai/`](https://catboost.ai/))。CatBoost 在处理复杂分类数据（如地理地址或产品标识符）方面处于领先地位。此外，Scikit-learn 开发者（如 Olivier Grisel）设计了一个受 LightGBM 启发的 GBM 实验版本。（你可以在 EuroPython 2019 上听 Grisel 谈论这些开发者在算法方面的工作：[`https://www.youtube.com/watch?v=urVUlKbQfQ4`](https://www.youtube.com/watch?v=urVUlKbQfQ4)）。

## Averaging Different Predictors

截至本节，本章讨论的集成由同一种机器学习算法组成，但平均和投票系统在使用混合不同机器学习算法时也可以很好地工作。这是 `averaging` 方法，当你无法以其他方式减少估计方差时，它被广泛使用。

当你尝试从数据中学习时，你会尝试不同的解决方案，从而使用不同的机器学习解决方案来建模数据。比较解决方案并寻找最佳验证拟合是很好的做法，但你也可以利用所做的工作，检查是否可以将其中一些解决方案成功地放入集成中，使用预测平均值或通过计算预测类别。原理与 bagging 不相关预测相同，当混合在一起的模型可以产生受方差影响较小的预测时。要实现有效的平均，你必须

1. 将数据分为训练集、验证集和测试集。

2. 使用不同机器学习算法的训练数据。

3. 记录每个算法的预测，并使用验证集评估结果的可行性。

对回归任务平均结果（也可以使用不同的权重），或对分类任务选择最频繁的结果。你的平均值就像一个二级模型。一旦你生成了最终预测，你仍然可以在尝试测试集之前在验证集上验证它们。

### Blending solutions

平均不同的解决方案也称为 `blending`，用于混合它们的过程通常被称为 `blender`。Scikit-learn 提供了 `VotingClassifier` 和 `VotingRegressor` 类，可以为你安排混合。此示例将之前最好的模型（梯度提升回归器）与一个完全不同的模型（支持向量回归器）进行混合，因为当你混合不同模型时，通常会更成功。运行代码后，你会发现混合 GBM 和 SVR 对葡萄酒质量数据效果最好。

```
from sklearn.ensemble import VotingRegressor
from sklearn.svm import SVR
gbm = GradientBoostingRegressor(n_estimators=500, subsample=0.9, max_depth=12, learning_rate=0.1, random_state=42)
svr = SVR(C=10.0, gamma=0.3, epsilon=0.0001)
blender = VotingRegressor(
    estimators=[('gbm', gbm), ('svm', svr)],
    n_jobs=-2)
blender.fit(X_train, y_train)
preds = blender.predict(X_test)
mae = mean_absolute_error(y_test, preds)
print(f"test mean absolute error for blender: {mae:0.3}")
```

![Tip](images/tip.png)当你混合表现几乎相当的不同类型模型时，混合可以提供比混合元素本身更好的结果。平均只是调整了一些弱点，同时保持其性能。

使用 `VotingRegressor` 和 `VotingClassifier`，你可以通过在 weights 参数中提供权重来决定执行加权平均。此外，`VotingClassifier` 允许你计算多数分类（`voting='hard'`）或混合不同类别的概率（`voting='soft'`）。

### Stacking diverse solutions

混合不是集成更多模型并从而减少预测方差的唯一方法。另一种方法是将模型的预测作为特征，再加上另一个模型。这是 `stacking`，它要求你适应相当复杂的准备工作。Scikit-learn 通过提供 `StackingRegressor` 和 `StackingClassifier` 类使过程更加容易，这些类为你处理所有过程。你提供一个有效的交叉验证方法、你的估计器和一个最终模型，如示例所示。在这种情况下，结果并非该问题的最佳结果。然而，混合多个解决方案通常能提供最佳结果。

