

## 第5章 决策树与梯度提升

-   dart——决策树，但其优化过程更具正则性

线性提升器（linear booster）促进链式线性模型的和。由于线性组合之和是线性的，你最终会为你使用的每个特征得到一个系数，类似于线性模型。你可以使用 `.coef` 方法访问这些系数。这是拟合 GBDT 的另一种方式，侧重于可解释性，因为由于使用了不同的复杂度惩罚和优化方法，该模型可以简化为线性组合，而这与你可能直接拟合的模型会有所不同。

最显著的区别在于，你不能像解释线性回归或广义线性模型产生的系数那样解释这些系数。此外，由广线性提升器（glinear booster）从分类器线性模型生成的截距，其解释也受到学习率和初始估计的影响。

dart 提升器与众不同，因为它将基于梯度的下降优化与一种类似的方法相结合，即深度学习中使用的技术。Rashid Koralai Vinayak 和 Ran Gil-Bachrach（伯克利分校和微软的研究员在论文《DART: Dropouts Meet Multiple Additive Regression Trees》（Artificial Intelligence and Statistics. PMLR, 2015）中提出），DART 关注由于每棵树的估计对之前节点的依赖而导致的过拟合问题。研究人员随后引入了深度学习中的丢（dropout）思想，即丢掩码（dropout mask）会随机并部分地阻塞神经网络层。神经网络不能总是依赖于特定层的信号来确定下一层的权重。在 DART 中，梯度不是计算到所有之前构建的树的残差和。尽管如此，算法在每次迭代中都会随机选择树的子集，并用 1/k 的因子缩放其叶片，其中 k 是被丢的树的数量。

glinear 和 dart 是唯一可用的替代提升器。例如，目前没有提升器可以混合随机森林（如 GBM 实现、LightGBM 那样）。虽然 XGBClassifier 和 XGBRegressor 不支持随机森林提升器，但你可以通过调整 XGBoost 的参数和函数来获得类似的结果：

-   使用 `num_parallel_tree` 参数并将其设置为大于 1 的数字。在优化的每一步中，梯度不是从单个决策树估计的，而是从决策树的袋装集成（bagged ensemble）估计的，从而创建一个提升的随机森林模型。在某些情况下，这种方法可能比梯度提升方法提供更好的结果，因为它以增加计算成本为代价降低了估计的方差。

-   使用 XGBClassifier 或 XGBRegressor，这两个来自 XGBoost 的两个类实现了随机森林方法。这些类仍处于实验性阶段。更多细节请参阅 https://mng.bz/rtKVB，但注意它与 Scikit-learn 提供的随机森林算法存在差异，因为 XGBoost 计算了一个由二阶导数组成的矩阵并计算了 Hessian 矩阵（Hessian matrix，数学定义参见 https://brilliant.org/wiki/hessian-matrix/）。

作为一个经验法则，`min_child_weight` 影响单棵决策树的构建方式，该参数的值越大，生成的树就越保守。通常测试的值范围从 0（意味着对叶节点的大小没有限制）到 10。在 2015 年于 NYC Data Science Academy 的题为 Owen Zhang 的演讲中，前 Kaggle 顶尖竞争者 Owen Zhang 建议通过用待预测数据中最稀有事件的百分比除以 3 来计算该参数的值。例如，遵循这一规则，由于我们的类别划分是 50%/50%，理想值是 3/0.5，结果为 6。

我们在示例中未使用的其他 XGBoost 参数如下：

-   `learning_rate`（也称为 eta）是 XGBoost 中的一个参数，决定了模型允许收敛更慢但更精确的速率，可能带来更好的预测准确性。然而，这将更多的迭代和更长的训练时间。另一方面，将值设置得太高可以加速过程但会导致模型性能变差，因为就像梯度下降中学习率过高一样，优化会超过目标。
-   `alpha` 和 `lambda` 分别是 L1 和 L2 正则化。两者都有助于避免 XGBoost 梯度下降优化路径中的过拟合。
-   XGBoost 中的 `max_depth` 参数控制复杂度。如果此值太低，模型可能无法识别许多模式（即欠拟合，原文此处误）。然而，如果它太高，模型可能会变得过于复杂，并识别出无法很好泛化到新数据的模式（即过拟合）。理想情况下，它是在 1 到 16 之间的一个值。
-   `gamma` 或 `min_split_loss` 是 XGBoost 中的一个正则化参数，范围从 0 到无穷，此值越高，正则化强度越强，降低了过拟合风险，但如果值过大可能会导致欠拟合。此外，此参数还控制生成的决策树的复杂度。我们建议从 0 或低值开始此值，并在设置所有其他参数后对其进行测试。
-   XGBoost 中的 `colsample_btree` 参数控制用于树训练的特征总数的比例。将此值设置为 1 意味着每棵树可以使用不同的特征子集进行预测，可能减少过拟合风险或减少受数据中单个特征的影响。它还通过在每棵树中不使用所有特征来提高训练速度。该参数的允许范围在 0 到 1 之间。
-   XGBoost 中的 `subsample` 参数控制用于树训练的样本总数的比例。将此值设置为 1 意味着每棵树可以使用不同的样本子集进行预测，可能减少过拟合风险或减少受数据中单个样本的影响。它还通过在每棵树中不使用所有样本来提高训练速度。该参数的允许范围在 0 到 1 之间。（注：原文此处将 subsample 描述为 features，已根据语境纠正为样本）

## 第5章 决策树与梯度提升

### 使用 XGBoost

接下来我们解释 XGBoost 为何更好

### 5.4.2 XGBoost 的原理

正如 Tianqi Chen 和 Carlos Guestrin 在《XGBoost: A Scalable Tree Boosting》（Proceedings of 22nd ACM SIGDD International Conference on Knowledge Discovery and Data Mining, 2016）中所述，XGBoost 的卓越性能归于几个创新：

- 列采样
- 二阶近似
- 改进的分点查找

目前，XGBoost 通过两种不同的 API 在 Python 中：原生 API 和 Scikit-learn API。在本书中，我们将完全使用 Scikit-learn API。

在使用原生 API 时，用户需要将数据转换为 DMatrix，这是一种针对内存效率和速度优化的 XGBoost 内部数据结构（https://mgc.io/v）。使用 DMatrix 格式使得列采样成为可能。然而，在使用 Scikit-learn API 时，用户可以使用 DataFrame 或 Numpy 数组导入数据，而无需显式转换。这是因为 XGBoost 在后台执行转换。

