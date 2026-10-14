
# 使用 GradientBoostingRegressor 的类构造函数

要查阅 XGBoost Python 版本的文档，请搜索 "xgboost python api"。查看标题为 "Python API Reference"（Python API 参考）的部分。在该部分中，你会找到 "Core Data Structure"（核心数据结构）。它定义了 XGBoost 为内存和速度优化而使用的一种专用输入数据结构。你会看到一个名为 `DMatrix()` 的函数，它接受特征和标签作为 numpy 数组，并返回所需的数据结构。下一节（清单 7-1）中的代码示例将向你展示这有多么易用。

接下来是学习 API 和 scikit-learn API 的描述，它们定义了训练函数、交叉验证训练，以及类 scikit-learn 的回归器和分类器类。对于这些，你需要为各种控制训练过程的参数提供值。通过搜索问题，你几乎可以找到任何问题的答案。

以下列表描述了你需要熟悉的参数和方法，并在适当的地方给出了一些关于选择和权衡的评论。你需要了解这些才能入门（文档中有更长的列表）：

*   `max_depth` (`int`)——基学习器的最大树深度。
*   `learning_rate` (`float`)——提升学习率。
*   `n_estimators` (`int`)——要拟合的树的数量。
*   `verbosity` (`int`)——冗长程度。有效值为 `0`（静默）到 `3`（调试）。
*   `objective` (`string` 或 `callable`)——指定学习任务及相应的学习目标。这基本上是在训练过程中被最小化的损失函数。对于回归问题，通常的选择是 `'reg:squarederror'`；对于二分类问题，则是 `'binary:logistic'`。文档的 "learning parameters"（学习参数）部分概述了其他选择。
*   `booster` (`string`)——指定使用哪种 booster：`gbtree`、`gblinear` 或 `dart`。这里你只会看到 `gbtree` 的用法，但我鼓励你尝试其他一些类型。
*   `n_jobs` (`int`)——用于运行 XGBoost 的并行线程数（替代 `nthread`）。
*   `subsample` (`float`)——用于逐棵树构建的数据采样比例。

    接下来的三个参数通过为每棵树、每层或每个节点随机选取特征子集，将集成中的树变为随机森林树。

*   `colsample_bytree` (`float`)——构建每棵树时的列采样比例。
*   `colsample_bylevel` (`float`)——每层的列采样比例。
*   `colsample_bynode` (`float`)——每次分裂的列采样比例。
*   `reg_alpha` (`float` [xgb 的 `alpha`])——权重上的 L1 正则项。
*   `reg_lambda` (`float` [xgb 的 `lambda`])——权重上的 L2 正则项。
*   `seed` (`int`)——随机数种子。（已弃用，请使用 `random_state`。）
*   `random_state` (`int`)——随机数种子（替代 `seed`）。

使用 XGBoost 进行建模的过程是：实例化 `XGBRegressor` 或 `XGBClassifier`，并提供将定义训练和评估过程的参数值。然后你将在该对象上调用一系列类函数。你将经常看到的包括 `fit()`，它将触发训练和相关输出；`predict()`，它将使用训练好的模型生成预测；以及 `feature_importances()`，它将给出特征重要性的估计。这些足以让你入门了。

对于新用户来说，为梯度提升设置参数可能有点令人困惑。以下列表建议了梯度提升的参数设置和调整序列：

1.  从默认设置开始，但设置 `subsample=0.5`。训练一个模型，并观察集成中树的数量与样本外 (OOS) 性能的曲线。在第一次和后续运行后，观察 OOS 性能曲线的形状。
2.  如果图表右端的 OOS 性能正在快速提升，则增加 `n_estimators` 或增加 `learning_rate`。
3.  如果图表右端的 OOS 性能正在快速恶化，则减小 `learning_rate`。
4.  一旦 OOS 性能曲线在其整个长度上都有所改善（或仅非常轻微地恶化），并在图表右侧趋于平稳，尝试调整 `max_depth` 和 `max_features`。

# 使用 GradientBoostingRegressor 实现回归模型

清单 7-1 展示了为葡萄酒质量数据集构建梯度提升模型所需的内容。

## 清单 7-1：构建梯度提升模型预测葡萄酒质量——wine_gbm.py
