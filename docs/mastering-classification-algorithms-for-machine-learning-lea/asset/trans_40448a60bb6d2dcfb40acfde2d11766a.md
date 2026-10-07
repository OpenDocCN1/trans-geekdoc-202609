

我们看到，使用图 8.5 中的决策桩对表 8.8 中的数据集进行预测，$x = 3$、$x = 6$ 和 $x = 7$ 的预测是错误的。因此，我们得到 $r = 0.9$。现在，我们可以计算 alpha 的值：

$$\alpha = 1 * \ln^{\frac{1-0.9}{0.9}} = \ln^{\frac{0.1}{0.9}} = \ln\frac{1}{9} = 0.11 = -2.917.$$

我们将停止迭代。现在，我们得到了以下结果：

$$\alpha_1 = 1.386$。$\alpha_1$ 是第一次迭代模型在最终决策中的权重。

$$\alpha_2 = -2.917$。$\alpha_2$ 是第二次迭代模型在最终决策中的权重。

我们将使用这个用 AdaBoost 算法创建的模型来做预测。假设我们的新数据点 $x = 4.5$。那么，根据第一个决策桩（图 8.3），$y = 1$（我们将此称为 $p_1$），根据第二个决策桩（图 8.5），$y = 0$（我们将此称为 $p_2$）。

我们将使用以下公式来决定数据点 $x = 4.5$ 的预测：

$$\tilde{y} = \alpha_1 * p_1 + \alpha_2 * p_2 = (1.386 * 1) + ((-2.917) * 0) = 1.386 + 0 = 1.386$$

由于 $\tilde{y}$ 的值大于 1，我们决定对于 $x = 4.5$，$y = 1$。

我们用一个新数据点来测试模型。假设我们的新数据点 $x = 1.5$。那么，根据第一个决策桩（图 8.3），$y = 0$（我们将此称为 $p_1$），根据第二个决策桩（图 8.5），$y = 0$（我们将此称为 $p_2$）。

我们将使用以下公式来决定数据点 $x = 1.5$ 的预测：

$$\tilde{y} = \alpha_1 * p_1 + \alpha_2 * p_2 = (1.386 * 0) + ((-2.917) * 0) = 0 + 0 = 0$$

因此，我们决定对于 $x = 1.5$，$y = 0$。

当我们使用 AdaBoost 算法创建模型时，我们会创建许多决策桩。假设我们创建了 $n$ 个决策桩。那么，每个决策桩都将有一个对应的 alpha。我们将第 $k$ 个决策桩的 alpha 称为 $\alpha_k$。同样，我们将第 $k$ 个决策桩对新数据点的预测称为 $p_k$。那么，

$$\tilde{y} = \sum_{k=1}^{n}(\alpha_k * p_k).$$

# Boosting 提升算法

> 注意，在进行预测时，当在二分类场景中将两个类别考虑为 0 和 1 时，项 $(a_k * p_k)$ 会变为 0。我们使用这一点来作说明，并保持与书中讨论的其他分类问题保持一致。然而，在 AdaBoost 算法的实际实现中，对于二分类场景，我们将两个类别考虑为 1 和 -1。在这种情况下，当模型的预测值大于 0 时，我们得出预测为类别 1。当模型预测值小于 0 时，我们得出预测为类别 1。

# 用于多分类的 AdaBoost 算法

AdaBoost 算法可以用于多分类。分阶段法（Stagewise）使用多分类损失（SAMME）是 AdaBoost 的变体。Scikit-Learn 提供了两种算法，SAMME 和 SAMME.R（R 代表回归）。SAMME 用于离散分类，SAMME.R 通常比 SAMME 收敛得更快。AdaBoost 的其他变体包括基于概率的 AdaBoost、基于SAMME、改进 AdaBoost 以及惩罚性 AdaBoost。

正如我们所讨论，当数据是平衡的，AdaBoost 的准确率会更高。AdaBoost 算法的改进可以见 https://www.sciencedirect.com/science/10.1016/S020525200275

# 在 Scikit-Learn 中实现 AdaBoost

在 Scikit-Learn 中，AdaBoost 算法实现位于 `sklearn.ensemble.AdaBoostClassifier`。AdaBoostClassifier 的关键参数如下：

- **estimator**：该参数用于设置用于创建模型的算法。默认值为 DecisionTreeClassifier（决策树）。
- **n_estimators**：该参数决定了迭代的最大次数。默认值为 50。
- **learning_rate**：该参数设置计算 $\alpha$ 的值。默认值为 1。
- **algorithm**：Scikit-Learn 的 AdaBoost 算法使用 SAMME。

> 注意：AdaBoost 算法最初是为分类问题创建的。然而，对于回归问题，Scikit-Learn 软件包提供了 `sklearn.ensemble.AdaBoostRegressor`。对于回归问题，使用 Boosting 模型的强大且流行的实现是 XGBoost 和 CATBoost。注意，XGBoost 和 CATBoost 算法也可以用于分类问题。

